[**Please read the blog post that goes with this code!**](http://www.wildml.com/2015/09/implementing-a-neural-network-from-scratch/)

### Setup on Ubuntu 14.04 TLS

1. Create and activate new virtual environment which inherits the global packages using virtualenvwrapper (optional but recommended).

```bash
mkvirtualenv --system-site-packages nn-from-scratch
```

To switch to the virtual environment,

```bash
workon nn-from-scratch
```

To exit the virtual environment,

```bash
deactivate
```

2. Install required packages. The option "--ignore-installed" will install what you've requested locally even though a system-wide version exists.
The python interpreter will look first in the virtualenv's package directory, so those packages should shadow the global ones.

```bash
pip install --ignore-installed -r requirements.txt
```

3. Start the notebook server (optional)

```bash
jupyter notebook
```

### Setup errors on Ubuntu 14.04 LTS

1. "gcc /usr/bin/ld: error: cannot find -lncurses"

```bash
sudo apt-get install lib32ncurses5-dev
```

2. "ImportError: No module named numpy.distutils.core" or "ImportError: numpy.core.multiarray failed to import"

```bash
pip install --ignore-installed xgboost
```

### Run-time errors on Ubuntu 14.04 LTS

1. "module compiled against API version a but this version of numpy is 9" when import sklearn.

```bash
pip uninstall numpy
pip install numpy
```

2. matplotlib.pyplot.show() does nothing.

Most likely this is a matplotlib backend issue. To fix this, we need to change the backend of matplotlib into a different one, e.g., qt4agg.

(1) Find the location of matplotlib config file matplotlibrc.

```python
>>> import matplotlib
>>> matplotlib.matplotlib_fname()
```

(2) Open the file matplotlibc and search for the line starting with "backend". Change the line into:

```
backend      : qt4agg
```

### To follow the tutorial step by step, you can run the python program nn_from_scratch.py.
