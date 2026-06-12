---
title: "compiling tightVNC"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Jakykong on 2005-12-16
Hi!
Well I guess this is the best forum to come to ... my only experience thus far with linux is through knoppix (desktop install is a LOT different ...). That was enough to convince me that WINDOWS SUCKS. so i got kubuntu :-)

The problem i am going to ask about is on an almost untouched install of Kubuntu running on an AMD64 processor.

I'm trying to install TightVNC so i can show off to a friend :-). It comes in either a binary RPM or a source .tar.gz. i downloaded the source. (RPM is red hat ... i know that much ... and i don't know how to use alien)

I did the following (in order):
1. extract the contents of tightvnc-1.2.9_unixsrc.tar.gz to /home/jack/vnc_unixsrc
2. read the readme file (in widows i generally ignored this ... but i didn't know if it might tell me something actually useful under linux ... it did :-))
3. open a shell. Sudo to root. 
4. cd over to /home/jack/vnc_unixsrc
5. type "xmkmf" at the prompt (it returned: "imake -DUseInstalled -I/etc/X11/config/cf")
6. type "make World"
7. recieve 200kb of errors

I installed gcc and the JPEG and zlib libraries that the readme file called for (i assumed jpeg meant that it wanted a library to work with jpegs ... so i picked the first one i could find in Adept ... turned out it was installed, as with zlib). Other then that, and apt-get'ing a few programs, i have done nothing to change the system so far. 

Could anyone help? (help does include finding another VNC server ... tightVNC was the only one i found that looked any good)

Thanks so much!

P.S. i wasn't 100% sure which forum to post this question in - whether under Kubunto>AMD64 or here, because i have almost no experience running a desktop linux, much less administrating one, but i have used linux before, in the form of knoppix ... wasn't sure if that really counted. forgive me if this is the wrong forum, i think i can keep up with whatever you throw at me ... but that might be cocky :-D Regardless, thanks so much for the help.

---

### Post by NotJustANewbie on 2005-12-16
```

sudo apt-get update
sudo apt-get install tightvncserver
sudo apt-get install xtightvncviewer
sudo apt-get install tightvnc-java
```

The forth line does a nice java applet that can run on a webserver for people to view your computer through a browser.

For more info on installing TightVNC from source, [click here.]("http://www.tightvnc.com/doc/unix/README.txt")

---

### Post by andrewk8 on 2008-04-08
The version in Synaptic is only 1.2.9.  I would like to compile 1.3.9 from source since tightvnc only offers RPMs and am having the similar issues.

I already installed build-essentials (suggested in another post).  "xmkmf" worked without returning any errors, but I got many errors running "make World".  Here is a sample:

[INDENT]vncviewer.h:33:28: error: X11/IntrinsicP.h: No such file or directory
vncviewer.h:34:28: error: X11/StringDefs.h: No such file or directory
vncviewer.h:35:23: error: X11/Shell.h: No such file or directory[/INDENT]

Am I missing more packages?  Any other fundamental errors?

---

### Post by popzero on 2008-04-14
Hi andrewk8, 

You'll need to add the following packages to get it to compile:

sudo apt-get install xorg-dev
sudo apt-get install libjpeg62-dev


Then just build as stated in the README instructions

P.S. you might also need this package:
sudo apt-get install xfs
I didn't have this and when it tried to start up Xvnc it complained. Works now.

---

### Post by andrewk8 on 2008-04-15
> **popzero said:**
> You'll need to add the following packages to get it to compile:

sudo apt-get install xorg-dev
sudo apt-get install libjpeg62-dev

Then just build as stated in the README instructions

P.S. you might also need this package:
sudo apt-get install xfs
I didn't have this and when it tried to start up Xvnc it complained. Works now.

Thanks!  Tried searching for files in the error messages with 'apt-file' and it didn't return x-org-dev (at least for the files I was search for).  Never would have figured this one out.  Didn't need xfs.

---

