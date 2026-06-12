---
title: "how to install nicotine+-1.2.8.tar.gz"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-29
i have just downloaded latest nicotine+-1.2.8.tar.gz from site to upgrade my old running , now how to install it in ubuntu Fiesty Fawn 7.04 GNOME. extracted and saved on desktop. after that what to do to install it :(

---

### Post by chamberlain2006 on 2007-06-29
This is easy.  Go into terminal, and type:

```

cd /path/to/the/extracted/folder
sudo python setup.py install
nicotine (to run)

```

---

### Post by ferronica on 2007-06-29
tushar@tushar-desktop:~/Desktop/nicotine+-1.2.8$ nicotine
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
You do not have Python Vorbis bindings installed. 
Others will not be able to see the lengths and the bitrates 
of Ogg Vorbis files that you share. You can get the from
[http://www.andrewchatham.com/pyogg/](http://www.andrewchatham.com/pyogg/). 
If you're using Debian, install the python-pyvorbis package.

Nicotine supports a country code blocker but that
        requires a (GPL'ed) library called GeoIP. You can find it here:
        C library:       [http://www.maxmind.com/app/c](http://www.maxmind.com/app/c)
        Python bindings: [http://www.maxmind.com/app/python](http://www.maxmind.com/app/python)
        (the python bindings require the C library)

Note: Python Bindings for libsexy were not found. To enable spell checking, get them from [http://www.chipx86.com/wiki/Libsexy](http://www.chipx86.com/wiki/Libsexy) or your distribution's package manager. Look for sexy-python or python-sexy.

---

### Post by chamberlain2006 on 2007-06-29
Is it loading?  Those seem to just be warnings, though you might want to install what it tells you to.

---

