---
title: "Tar install problem..."
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by WFGeppetto on 2008-04-06
I am very puzzled, as this is not my first tar to install.  I have never had a problem with them, although I haven't installed more than, say 20 things from tars (all my compiz plugins, to mention a few).

I definitely have the build essentials thing, or I don't know how I would have done it all before.

My normal operation is as follows:

-extract the tar to desired folder using the file browser
-cd to the dir in terminal
-./configure
-make
-sudo make install
-walla!

This is the thunderbird tar, and I'm pretty sure I can find it in the repositories, but I'd like to know what I am doing wrong, and do it this way, so as to learn more.

I *am* in the right directory, and the tar *is* extracted, and all the files are there, but when I
./configure
I get... nevermind, I'll just paste my terminal:

```
wfgeppetto@GPTO:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wfgeppetto@GPTO:~$ cd dump
wfgeppetto@GPTO:~/dump$ cd thunderbird
wfgeppetto@GPTO:~/dump/thunderbird$ dir
chrome              libfreebl3.so    libsoftokn3.so          removed-files
components          libldap50.so     libssl3.so              res
defaults            libmozjs.so      libxpcom_compat.so      run-mozilla.sh
dependentlibs.list  libnspr4.so      libxpcom_core.so        thunderbird
dictionaries        libnss3.so       libxpcom.so             thunderbird-bin
extensions          libnssckbi.so    libxpistub.so           updater
greprefs            libplc4.so       license.html            updater.ini
icons               libplds4.so      LICENSE.txt             updates
init.d              libprldap50.so   mozilla-installer-bin   xpicleanup
isp                 libsmime3.so     mozilla-xremote-client
libfreebl3.chk      libsoftokn3.chk  README.txt
wfgeppetto@GPTO:~/dump/thunderbird$ ./configure
bash: ./configure: No such file or directory
wfgeppetto@GPTO:~/dump/thunderbird$ sudo ./configure
sudo: ./configure: command not found
wfgeppetto@GPTO:~/dump/thunderbird$ make
make: *** No targets specified and no makefile found.  Stop.
wfgeppetto@GPTO:~/dump/thunderbird$ 

```

What the hell?  Please teach me...

---

### Post by mrpixels0 on 2008-04-06
looks like it is a Binary only tar, meaning it is already compiled and there is no make or configure files.

just do a sudo sh run-mozilla.sh

and that should take care of it. hope this helps

MP0

---

### Post by WFGeppetto on 2008-04-06
Thanks, but that didn't work either, although, if what you said makes sense, it helped me understand the nature of tars...ahm lurnin!

```
wfgeppetto@GPTO:~$ cd dump
wfgeppetto@GPTO:~/dump$ cd thunderbird
wfgeppetto@GPTO:~/dump/thunderbird$ sudo sh run-mozilla.sh
[sudo] password for wfgeppetto:

run-mozilla.sh: Cannot execute .

wfgeppetto@GPTO:~/dump/thunderbird$ 

```

---

### Post by wormser on 2008-04-06
It probably needs to be made executable.

```
chmod +x run-mozilla.sh
```

---

### Post by Irihapeti on 2008-04-06
There's page called ThunderbirdNewVersion in the Ubuntu community documentation which explains how to deal with this.

---

### Post by WFGeppetto on 2008-04-06
Ah, thank you, I'll see if I can find it.

So, I'm not a dufus, eh?  Or at least not in this case...

---

### Post by p_quarles on 2008-04-06
> **WFGeppetto said:**
> Ah, thank you, I'll see if I can find it.

So, I'm not a dufus, eh?  Or at least not in this case...
No, not at all. What you did would have worked fine if this had been a source package.

Tarballs (files such as *.tar.gz, *.tgz, *.tar.bz2) are just compressed archives. Like *.zip or *.rar files in Windows, the file format only indicates that it contains other files, and says nothing about the contents of those files.

---

### Post by schiznik on 2008-04-06
try running ./mozilla-installer-bin from the unpacked folder.

Why not just install thunderbird from the repositories?

---

### Post by joshrobinson on 2008-04-06
```
sudo apt-get install thunderbird
```
to install it from the repo's

or just run

```
./thunderbird
```
in the thunderbird directory, or double click the thunderbird file in nautilus

its pre-built, no need to compile anything

---

### Post by WFGeppetto on 2008-04-07
Thanks, I did end up installing it from repositories, I just sudo apt-get install mozilla-thunderbird.  Now I have it.  I was just wanting to learn how to deal with the problem at hand, the hard way, hoping to learn something.

Now I have a new problem. I am trying to get it to read my yahoo mail.  I found [ypops](http://ypopsemail.com/), which is supposed to make it work without upgrading my yahoo account.  I would just use gmail, but my yahoo is on all my resumes, and everyone knows how to reach me with it.

The problem is, the file for ypops, is also a tar.gz, and the same problem occurs.  There is the option of downloading the source code, but I don't know how to deal with that either.

Terminal trying to deal with the tar:

```
wfgeppetto@GPTO:~$ cd dump
wfgeppetto@GPTO:~/dump$ dir
firefox-3.0b4.tar.bz2              winff-0.33-i386.deb
GDM-LoginScanFusion.tar.gz         ypops_0.8.6.2
realplay_10.0.9-0feisty1_i386.deb  ypops_0.8.6.2_linux_x86.tar.bz2
thunderbird-2.0.0.12.tar.gz
wfgeppetto@GPTO:~/dump$ cd ypops_0.8.6.2
wfgeppetto@GPTO:~/dump/ypops_0.8.6.2$ dir
docs  ypops  ypops.ini
wfgeppetto@GPTO:~/dump/ypops_0.8.6.2$ ./configure
bash: ./configure: No such file or directory
wfgeppetto@GPTO:~/dump/ypops_0.8.6.2$ 

```

Now, not knowing much, but knowing enough to be dangerous, I'd assume there is some kind of command that can make the ini file work, but, if my level of knowledge is as I believe it is, this sentence probably sounds stupid.

Is there a forum page, or a website that outlines common syntax and commands for linux/terminal, where I might more easily learn what I am doing?  Maybe a nice "noobies guide to linux" type of thing?

---

