# Development Environment

This site is built using Python 3.3 and PostgreSQL. The following
python packages are required:

* pip
* virtualenv

In addition, to install the lxml package, the following C libraries' development
header are necessary to be installed. Here are some example commands:

```
apt-get install libxml2-dev libxslt-dev
yum install libxml2-devel libxslt-devel
pacaur -S libxml2 libxslt
```

Since the site shares code with Sublime Text 3 (and Sublime Text 2),
some of the python uses `u""` unicode literals which are not supported
on Python 3.0-3.2. *Because of this, only Python 3.3 will work.*

Currently the production site runs with PostgreSQL 9.2, however all of
the features used should be available with 9.1 also.

To work on this project you will need gcc on your machine since some of
the packages have C components.

Additionally, you are going to need nodejs installed on your machine
since the JS on the site is written in coffeescript. Yeah, I know,
another language dependency. It’s worth it.

Set up the required packages:

```
# A number of packages have custom versions to run on Python 3.3
pip install git+https://github.com/wbond/pymeta
pip install git+https://github.com/wbond/pybars
pip install git+https://github.com/wbond/python-textile@python3
pip install git+https://github.com/wbond/python-creole

pip install git+https://github.com/wbond/gears-coffeescript
pip install git+https://github.com/wbond/gears-handlebars
pip install git+https://github.com/wbond/watchdog@python3-compat
pip install git+https://github.com/wbond/pyrollbar@python3

pip install -E venv -r setup/requirements.txt
```

Run the server:

```
python dev.py
```

Start the compiler to automatically compile `.coffee` and `.scss` files:

```
python compile.py
```

Whenever one of these files is saved, the resulting JS or CSS files will be
regenerated.
