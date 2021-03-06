---
layout: default
title: "Beam Quickstart for Python"
permalink: /get-started/quickstart-py/
---

# Apache Beam Python SDK Quickstart

This guide shows you how to set up your Python development environment, get the Apache Beam SDK for Python, and run an example pipeline.

* TOC
{:toc}

## Set up your environment

### Install pip

Install [pip](https://pip.pypa.io/en/stable/installing/), Python's package manager. Check that you have version 7.0.0 or newer, by running:

```
pip --version
```

### Install Python virtual environment

It is recommended that you install a [Python virtual environment](http://docs.python-guide.org/en/latest/dev/virtualenvs/)
for initial experiments. If you do not have `virtualenv` version 13.1.0 or newer, install it by running:

```
pip install --upgrade virtualenv
```

If you do not want to use a Python virtual environment (not recommended), ensure `setuptools` is installed on your machine. If you do not have `setuptools` version 17.1 or newer, install it by running:

```
pip install --upgrade setuptools
```

## Get Apache Beam

### Create and activate a virtual environment

A virtual environment is a directory tree containing its own Python distribution. To create a virtual environment, create a directory and run:

```
virtualenv /path/to/directory
```

A virtual environment needs to be activated for each shell that is to use it.
Activating it sets some environment variables that point to the virtual
environment's directories.

To activate a virtual environment in Bash, run:

```
. /path/to/directory/bin/activate
```

That is, source the script `bin/activate` under the virtual environment directory you created.

For instructions using other shells, see the [virtualenv documentation](https://virtualenv.pypa.io/en/stable/userguide/#activate-script).

### Download and install

Install the latest Python SDK from PyPI:
  `pip install apache-beam`

## Execute a pipeline locally

The Apache Beam [examples](https://github.com/apache/beam/tree/master/sdks/python/apache_beam/examples) directory has many examples. All examples can be run locally by passing the required arguments described in the example script.

For example, to run `wordcount.py`, run:

{:.runner-direct}
```
python -m apache_beam.examples.wordcount --input README.md --output counts
```

{:.runner-dataflow}
```
# As part of the initial setup, install gcp specific extra components.
pip install dist/apache-beam-*.tar.gz .[gcp]
python -m apache_beam.examples.wordcount --input gs://dataflow-samples/shakespeare/kinglear.txt \
                                         --output gs://<your-gcs-bucket>/counts \
                                         --runner DataflowRunner \
                                         --project your-gcp-project \
                                         --temp_location gs://<your-gcs-bucket>/tmp/ \
                                         --sdk_location dist/apache-beam-*.tar.gz
```

## Next Steps

* Learn more about these WordCount examples in the [WordCount Example Walkthrough]({{ site.baseurl }}/get-started/wordcount-example).
* Dive in to some of our favorite [articles and presentations]({{ site.baseurl }}/documentation/resources).
* Join the Beam [users@]({{ site.baseurl }}/get-started/support#mailing-lists) mailing list.

Please don't hesitate to [reach out]({{ site.baseurl }}/get-started/support) if you encounter any issues!

