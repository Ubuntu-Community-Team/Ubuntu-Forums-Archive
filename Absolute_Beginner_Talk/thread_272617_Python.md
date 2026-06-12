---
title: "Python"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-06
How do I find out where Python was installed?

---

### Post by Abstract on 2006-10-06
A useful command is:

```
dpkg -L <package name>
```

It lists all files 'owned' or made by a package. I use it often.

---

### Post by Omnios on 2006-10-06
Personally I lauch synaptic package manager ans search for the files as it also has a description for it.

---

### Post by Buffalo Soldier on 2006-10-06
type "**python -V**" in the terminal. If python is installed something like this will appear:```
Python 2.4.4c0
```

---

### Post by jordanmthomas on 2006-10-06
to find where the python binary is, type
```
which python
```
To find everything else, do what was suggested earlier.

---

### Post by saintj0n on 2006-10-07
cool..thanks! Playing with these commands has taught me a bit more about Linux. Could these commands be used to find which files are causing a partial install or corrupt files to be copied in an install? That was why I needed the path for my python anyway. When I installed python, it said something about python2-3.4-suite being incomplete when it installed but it didn't say what got messed up.

---

### Post by rccharles on 2006-10-07
> **saintj0n said:**
> When I installed python, it said something about python2-3.4-suite being incomplete when it installed but it didn't say what got messed up.

Did you install from stable?

cat /etc/apt/sources.list

I'd try reinstalling...

Use your favorite package manager.

aptitude update       # re-load package description database

aptitude purge python # delete package and configuration files
aptitude install python


also,
aptitude reinstall python  # not sure about configuration files
                           # assume they are keep


you could add a little verbosity with:

aptitude -vv reinstall python

Robert

---

### Post by saintj0n on 2006-10-07
I just checked my python application and it is loading up at least.  Of course, that may not mean anything because I don't even know any python commands yet. So there is no way to tell if it works until I really check it out.

---

### Post by saintj0n on 2006-10-07
Here is what I got with aptitude -w reinstall python 


This aptitude does not have Super Cow Powers.

---

### Post by uk_sphinx on 2006-10-07
h

---

### Post by jordanmthomas on 2006-10-07
It's not a w, it's two v's

---

### Post by saintj0n on 2006-10-10
ok..Here's the result...

root@jonathan-laptop:~# aptitude -vv reinstall python2.3-4-suite
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "python2.3-4-suite"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite
root@jonathan-laptop:~# 

I think I need to renistall from a different source. I can't imaging why though. I installed my copy of ubuntu off of the Ubuntu Unleashed CD.

I wonder if I can just download a deb file of python and just rerun it. Or do I need to uninstall python first then reinstall with the new one?

---

### Post by rccharles on 2006-10-14
> **saintj0n said:**
> ok..Here's the result...

root@jonathan-laptop:~# aptitude -vv reinstall python2.3-4-suite

Couldn't find any package whose name or description matched "python2.3-4-suite"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I wonder if I can just download a deb file of python and just rerun it. Or do I need to uninstall python first then reinstall with the new one?

The package name for Python 2.3 should be python2.3-4suite.  Notice the lack of a dash after the 4.

What version of Ubuntu do you have?  I have dapper and I have Python 2.4.  I tried to install python2.4-4suite but aptitude install could not find the package.  Yet, the package appears here:
[http://packages.ubuntu.com/dapper/python/python2.4-4suite](http://packages.ubuntu.com/dapper/python/python2.4-4suite)

when I tried to list the package from the console, it could not be found

apt-cache search python2.4-4

 ----- also ---------

The fact that aptitude reinstall tried to run some script after it could not find the package you wanted to reinstall seems to be a bug to me.  This is the error code 1 you report.

Robert

---

### Post by saintj0n on 2006-10-15
I thought so too... I think something is corrupted in my python package.. I should be able to go to type in apt-get <packagename> install (or something like that) and install a fresh copy right off the web, correct?

---

### Post by rccharles on 2006-10-18
> **saintj0n said:**
> I thought so too... I think something is corrupted in my python package.. I should be able to go to type in apt-get <packagename> install (or something like that) and install a fresh copy right off the web, correct?

As you hinted at ealier, you can download the deb file.  Use dpkg to install the package.

You will have to download the dependent packages too.  Can be a pain.

Robert

---

### Post by rccharles on 2006-10-19
I was able to install python2.4-4suite today! ( I wasn't able to install yesterday. I am assuming there was some problem with the repository. )

I suggest you try re-running the install command.

Here was my setup.

Here is the /etc/apt/sources.list file:
Quote:
root@kubuntu:~# cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

I did a ping to see if I could access the repository.

ping archive.ubuntu.com

do a control-c to stop

sudo aptitude install python2.4-4suite


--------------

You may be running a different version of ubuntu than me, so you sources list file and install will be different.

To create a new version of /etc/apt/sources.list, aysui provided this link:
Try source-o-matic:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Robert :)

---

### Post by saintj0n on 2006-10-19
Hot dang!
That got it. I don't know what is different, other than the version python2.3-4-suite vs. python2.4-4-suite. I also installed Edubuntu on my pc today, although I don't know why that would matter...

---

