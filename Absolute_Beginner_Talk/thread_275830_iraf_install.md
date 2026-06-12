---
title: "iraf install"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by abu_nawas on 2006-10-11
does anyone konw how to install IRAF in  ubuntu?

---

### Post by pay on 2006-10-12
Try downloading the source tarball then compilling it. The general way to compile is```
tar -zxvf package.gz #or tar -jxvf package.bz2
cd package
./configure #and options
make
sudo make install
```also you can install checkinstall and make a basic debian file by replacing sudo make install with sudo checkinstall -D make install.

---

### Post by mikalh on 2006-11-07
I've made a walkthrough for installing [IRAF on Ubuntu Edgy](http://mjhutchinson.com/journal/2006-05-11/install_iraf_on_ubuntu_edgy_amd64) which should work with both i386 and AMD64.

---

### Post by shouravv on 2007-06-15
I was looking around and found this

[http://geco.phys.columbia.edu/~rubab/iraf/](http://geco.phys.columbia.edu/~rubab/iraf/)

---

### Post by n.l.o on 2008-03-21
Hey
I've actually made a bash shell script that installs IRAF/PyRAF/IPyRAF on to a Ubuntu machine.

[http://web.comhem.se/webspace/astroinstall_ubuntu.sh]("http://web.comhem.se/webspace/astroinstall_ubuntu.sh")


To run it, just save it in your home catalogue,e.g. in terminal run:
```

wget http://web.comhem.se/webspace/astroinstall_ubuntu.sh

```

After this you make it executable by e.g. typing 
```
chmod +x astroinstall_ubuntu.sh
```
in the terminal where the file is located.

THEN just run it!
```
./astroinstall_ubuntu.sh
```

After this you will get to a menu that asks you what you want to install.
```

 ############################# 
 
 Choose what to install: 
1 for IRAF/PyRAF/IPyRAF
2 for IRAF-Termcap fix
3 for XS
4 for Karma Toolkit
5 for GDL
Q to Quit
 
 ############################# 
   :

```

Obviously, you choose 1 for IRAF.
IRAF installs in "/iraf".


It assumes that you, after the installation, create a catalogue "iraf" in your home directory, i.e. in terminal
```
mkdir ~/iraf
```
where you run the command "mkiraf" from the terminal inside the "~/iraf" catalogue and select terminal type as "xterm". This catalogue is where all the parameter files will be stored, along with logs, "login.cl" file and so on.

Creates a desktop icon/link to IPyRAF that executes the shell script "ipyrafshell" that creates a xterm window with ipyraf and a ds9 instance. There are 3 different scripts that is placed in "/usr/local/bin":
irafshell - ecl in xterm along with ds9 window
pyrafshell - pyraf in xterm along with ds9 window
ipyrafshell - ipyraf in xterm along with ds9 window

Successfully run on Kubuntu Gutsy and Ubuntu Gutsy.

The other choices also works:

Choice 2, Termcap fix is if you like the original IRAF CL or the IRAF ECL, then this will fix so that it will work. 
Taken from [http://geco.phys.columbia.edu/~rubab/iraf/]("http://geco.phys.columbia.edu/~rubab/iraf/")

Choice 3, Per Bergman's XS: 
[http://www.chalmers.se/rss/oso-en/observations/data-reduction-software]("http://www.chalmers.se/rss/oso-en/observations/data-reduction-software")

Choice 4, for more info about what Karma is see 
[http://www.atnf.csiro.au/computing/software/karma/]("http://www.atnf.csiro.au/computing/software/karma/")

Choice 5, GDL, GNU Data Language
[http://gnudatalanguage.sourceforge.net/]("http://gnudatalanguage.sourceforge.net/")


As of today, Friday March 21st 2008, all the installations are the most recent versions (i hope ;))

IRAF 2.14
STSCI Python ver 2.6 (PYRAF 1.5 etc)

Use this script at your own risk and reprogram it in your own pleasure.

Cheers
Magnus

---

### Post by n.l.o on 2008-03-21
ooh, btw, the GDL installation is run with the flags "--with-netcdf=no --with-hdf=no --with-hdf5=no"
so you know

Magnus

---

