---
title: "dvdrip - unmet dependencies (transcode)"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by nic2 on 2005-08-27
After I tried to apt-get dvdrip I received the following message:

The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not installable

I downloaded the transcode-1.0.0.tar.gz file, and after reading the install file I am at a total loss as to what I am supposed to do (link to the Transcode Wiki: [http://www.transcoding.org/cgi-bin/transcode](http://www.transcoding.org/cgi-bin/transcode) ).

Any assistance in this regard will be greatly appreciated, thank you!

---

### Post by iH8forcedRegistration on 2005-08-28
apt isn't clever enough to detect that you've installed something yourself. If you succesfully manage to install transcode from a tgz, you'll still get that same depends message.

What you should try to do is figure out why transcode is not installable. Run this in a terminal:
```
sudo apt-get install transcode
```

It should tell you what's wrong.

---

### Post by claydoh on 2005-08-31
Here is the error I get trying to install transcode:

> The following packages have unmet dependencies:
  transcode: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
E: Broken packages


---

### Post by erbogasto on 2005-09-18
Add these lines to your /etc/apt/sources.list:(#sudo gedit/etc/apt/sources.list)

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted 

This is my complete sources.list

## Main archive
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

## Security
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

## Backports
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Debian-Marillat
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then via synaptic update the repos and install dvdrip and trnscode with no problems !!!
Bye Andrea

---

### Post by Jenda on 2005-10-02
I have the exact same problem.

```
**jenda@niniel:~$ sudo apt-get install dvdrip**
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not going to be installed
E: Broken packages
**jenda@niniel:~$ sudo apt-get install transcode**
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transcode: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
E: Broken packages
```

It seems to me that one package depends on **libgcc1, version 1:4.0-0pre6ubuntu7** while the other requires **libgcc1, version 1:4.0.0-7 or newer** and you aren't allowed to have both. I would say this is an error in the package that requires the older version. Anyone have a solution?

---

