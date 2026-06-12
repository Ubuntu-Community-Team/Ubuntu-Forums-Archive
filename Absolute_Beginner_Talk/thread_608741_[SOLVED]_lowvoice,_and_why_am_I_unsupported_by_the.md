---
title: "[SOLVED] lowvoice, and why am I unsupported by the Ubuntu team?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by speirint on 2007-11-10
I'll be as descriptive as possible here, though there's stuff that may or may not have anything to do with why my computer says it has errors or is unable to retrieve anything from the [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages

Every time I sudo apt update or upgrade something I get an error saying this:
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 206.112.100.151 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I recently tried to upgrade to Gutsy Gibbon (from feisty fawn), and it also said that it failed to access the lowvoice stuff also and then kicked out of the upgrade. Is there anything I can do to fix this?


For a semi-detailed story, the person that got me to use ubuntu was determined to get compiz on my computer. Later, he discovered something wrong with the default kernal (the first one that ubuntu would load up to) and wound up editing some stuff per suggestion of some website that I can't find. My biggest concern is the fact that somewhere in the sources list there are lines that say the N.B. software from the repository is entirely unsupported by the Ubuntu team.  Is there any way I can return to having a more orthodox ubuntu?

Also, I tried to remove compiz a while ago. Not sure if it worked.

Here's the cat /etc/apt/sources.list business:


# 
# deb cdrom:[Ubuntu 6.10 _feisty Eft_ - Release i386 (20061025.1)]/ feisty main restricted


# deb cdrom:[Ubuntu 6.10 _feisty Eft_ - Release i386 (20061025.1)]/ feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
#AUTOMATIX REPOS END

# Treviño&#8217;s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by dpar on 2007-11-10
I'd be willing to bet that if you comment everything out between 'Automatix repos start' and 'automatix repos end' your problems will go away.

---

### Post by speirint on 2007-11-10
Thanks, I'll give it a try.  But first, that brings me to another question-how do I get in to edit the text.  I'm assuming I use the # key to comment everything out correct? or can I use ! as well?

---

### Post by deep.tinker77 on 2007-11-10
Yes, you use the # to comment items out. You can use gedit or any other editing tool you like. I personally like vi. Good luck.

---

### Post by Maestro23 on 2007-11-10
> **speirint said:**
> Thanks, I'll give it a try.  But first, that brings me to another question-how do I get in to edit the text.  I'm assuming I use the # key to comment everything out correct? or can I use ! as well?

To edit the file:

> gksudo gedit /etc/apt/sources.list

The** /etc** direcotry is owned by**[B] roo**t. [/B] Hence you need root privileges to edit the dir/files under it.

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by speirint on 2007-11-10
Thank you for the suggestions and well wishes to everyone that replied thus far.

I was reading the help manual for gedit and understand how to do most of the things in it, however I don't know how to put it into application.  I've accessed gedit through the terminal and now through the gi (under applications->accessories->text editor).  I'm currently reading the gedit manual through terminal. [edit, the manual makes some sense, but again, I don't really know how to apply what it is showing me]

What confuses me about gedit through the gui is that it looks like I'm using notepad to make a new document (for scripting HTML using notepad) when I would assume that I actually need to open a file* (document?) to edit it rather than create a new one...

  Can someone please explain to me the following:

1) how to actually call up the lines of code or initiate the editing process

ex. do I just copy and paste the lines in, or find the files they are kept in through the computer?

2) how do I finalize this editing process, I believe I'm supposed to click save at the end after I've edited the text, but I haven't even figured out how to initiate editing beyond opening the application.

3) as an aside, what's the difference between scripting and coding?

Having discovered this, I've come to realize that the source of my frustration probably comes from a lack of understanding as I have a hard time figuring out anything that doesn't require point, click, and visible menus/submenus. I basically know very little about programming with the exception of basic thanks to my graphing calculator and a tidbit of HTML and DOS.

---

### Post by dpar on 2007-11-10
As Maestro23 said, the code you want to type into the terminal to edit your sources.list is
> gksudo gedit /etc/apt/sources.list

Your sources.list file is int the apt directory, which is in the etc directory, that is why you type the /etc/apt/sources.list

The reason for gksudo is because you need root permission to edit that file.

Before editing the file, though, it might be a good idea to do a 
> sudo cp /etc/apt/sources.list /etc/apt/sources.bak to backup the file before editing.

Good luck:biggrin:

---

### Post by speirint on 2007-11-12
Thanks a lot everyone, and thanks for the explaination dpar. The edit worked out fine and I was able to understand what was going on.  I updated to Gutsy and now have a myriad of different (hopefully less frustrating) issues like screen resolution and stuff... ever onward!

---

