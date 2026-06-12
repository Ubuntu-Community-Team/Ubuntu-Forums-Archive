---
title: "installing joomla"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Frequent Modulation on 2008-04-18
[http://help.joomla.org/ghop/feb2008/task048/joomla_15_quickstart.pdf](http://help.joomla.org/ghop/feb2008/task048/joomla_15_quickstart.pdf)

How can i adapt this guide for ubuntu server 7.10?

More specifically:
 since 7.10 already comes with most (all?) of the components in the xampp software, I dont need to install it..do I?

also, I am using the cli in 7.10 and have recently apt-got one of the text based browsers and went to download joomla from joomla.org. There are 3 options for download
Joomla_1.5.2-Stable-Full_Package.tar.gz
Joomla_1.5.2-Stable-Full_Package.zip
Joomla_1.5.2-Stable-Full_Package.tar.bz2

which one of these should i download? Into which folder should it be downloaded to? Once downloaded, how do i go about installing it? Which folder do i install it to?

I do want to accomplish this with the command line. Is it my imagination or is alot of the documentation for ubuntu and joomla written for use with the gui?

---

### Post by unutbu on 2008-04-18
On a standard Ubuntu system, the one to choose is 
Joomla_1.5.2-Stable-Full_Package.tar.bz2

The bz2 extension refers to a file that has been compressed with bzip2, which in general compresses better that gzip (which makes .gz files). .zip is even worse and is mainly for compatibility with windows.

You can put it anywhere you like. Where you put it is mainly a matter of taste, but may also be influence by how much space you have in various partitions. /usr/local/src is a traditional place to put such things.

To unpack:

```
bunzip Joomla_1.5.2-Stable-Full_Package.tar.bz2
tar xvf Joomla_1.5.2-Stable-Full_Package.tar
```

You'll be left with a directory called Joomla_1.5.2-Stable-Full_Package.

Inside this directory you'll most likely find a file called README and/or INSTALL. Sometimes there is a doc directory too.
In one of these places there should be instructions on how to install joomla.

If you need to compile joomla, you'll also need the build-essential package:

```
sudo apt-get install build-essential
```

And you may also want to install the checkinstall package because it makes it much easier to uninstall if the need arises. (It creates a package which you can install/remove using apt/dpkg commands. Very cool.)

---

### Post by Frequent Modulation on 2008-04-18
> **unutbu said:**
> On a standard Ubuntu system, the one to choose is 
Joomla_1.5.2-Stable-Full_Package.tar.bz2

The bz2 extension refers to a file that has been compressed with bzip2, which in general compresses better that gzip (which makes .gz files). .zip is even worse and is mainly for compatibility with windows.

You can put it anywhere you like. Where you put it is mainly a matter of taste, but may also be influence by how much space you have in various partitions. /usr/local/src is a traditional place to put such things.

To unpack:

bunzip Joomla_1.5.2-Stable-Full_Package.tar.bz2
tar xvf Joomla_1.5.2-Stable-Full_Package.tar

Thank you for the reply Unutbu. Ill follow your advice and get this package installed this evening. Now after I unpack (and if this is an option) will I unpack or install to /var/www/joomla?

---

### Post by unutbu on 2008-04-18
I've never installed joomla, but for almost all (linux/gnu) software packages the first instruction is to run a script call configure or configure.sh

If joomla uses a configure script, it will control where joomla gets installed. Usually a reasonable default value is offered, but it can be overridden. 

```
./configure --prefix=/var/www/
```

may work, but read the installation instruction to be sure.

---

### Post by Frequent Modulation on 2008-04-18
Groovy dude! This info gives me something to play with tonight... other than myself.   \\:D/

---

### Post by unutbu on 2008-04-18
Oops! Some of what I told up above does not apply to Joomla.
I just downloaded it and looked inside. The file you need to read to install seems to be called INSTALL.php. There is no configure script.

---

### Post by adamos on 2008-04-24
there is a lot of help in joomla.org 
extract the tar.gz file in you web server directory and just point your browser to your web server and you will put the appropriate info for sql and ftp account to install it. then make sure that you will remove your installation directory! (in terminal and joomla dir do a sudo rm -R installation ) or if you ar working with ftp client just remove the installation directory

---

