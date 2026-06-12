---
title: "Simple way to install Gnumeric?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Woody_in_MN on 2007-02-28
I am trying to install Gnumeric.  For Abiword I was able to find a "package" to install - and work with that thru GUI.

I did some seraches trying to find an install package for Gnumeric.  I could not.  I did find some versions that had folders filled with files that end in *****.tar.gz.  I do not know what to do with these tar.gz files.

Can someone point me to an install package for Gnumeric, or (alternatively) explain how I use these tar.gz files.

BTW - I am trying to install Gnumeric on a PC that is not connected to the Internet.  For now, I will have to download what ever files I need to my XP PC, and then burn a CD, and use the CD to install to my Ubuntu PC.

Thanks in advance,

 - w

---

### Post by xyz on 2007-02-28
Would this help:
[Gnumeric]("http://linux.softpedia.com/get/Office/Groupware/Gnumeric-2602.shtml")

---

### Post by Maestro23 on 2007-02-28
Also try here.  Pick your distro and the packaged you want.

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

*If you are going to compile form source (.tar.gz) files, be careful.  A new person new to linux can mess some things up.  One thing you must have installed prior to compiling is "build-essential".

> sudo aptitude install build-essential

Once you extract your file, it will create a directory.  In that directory is a README an INSTALL doc, make sure you read these.

Good luck.

---

### Post by Woody_in_MN on 2007-02-28
Well OK.  Ubuntu 6.10 is "edgy" ?  

 - w

---

### Post by Maestro23 on 2007-02-28
> **Woody_in_MN said:**
> Well OK.  Ubuntu 6.10 is "edgy" ?  It seems like I still get directed to files that end in tar.gz - so I down load that (or those?) files - copy the tar.gz files to a CD - take my cd to the Unbuntu PC, and then find the tar.gz file, and what next? - double click on it - then it will install?  Or do I use some kind of package/application installer?


This is what drives me nuts about Linux - there seems to be no easy way to install programs.

 - w

Edgy = 6.10  Dapper = 6.06

When you don't have internet access, installing stuff is a pain.

The link I gave you lets you search for packages by distro.  Pick your distro and search for your package.  These will be .deb packages.  You can install them from GUI or command line.

Command line: Navigate to the directory you downloaded the package to and:

> sudo dpkg -i package


Great link on installing: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Installing programs in Ubuntu is not hard at all.  If you are installing stuff from the Repositories you use Synaptic(GUI) or command line (sudo apt-get/aptitude).  

As I said before, compiling from source (.tar.gz) can totally overwhelm some that is new to linux.  Also can hose their system up if they are not familiar with linux file structure.

Use that link I gave you.  Dowload the packages you need and put them on a CD-RW/R, flash drive etc... and transfer them to your Ubuntu box with no internet.

---

### Post by Woody_in_MN on 2007-02-28
Thanks all.

Regarding non-connectivity to Internet:  This is my Dad's PC (who passed away last year).  At first I was going to junk the PC - but then got interested in Ubuntu.  I Thought I would try it on that older PC (HP Pavillion Celeron - only 256kb ram).  Not sure what the future of that PC will be.

 - w

---

### Post by Woody_in_MN on 2007-02-28
OK - This question is for the AbiWord 2.2.8 install (I have not tried Gnumeric install yet):

I have the files & folders extracted to my home directory.  I have been clicking on files/icons under those folders to see if it will run an install - so far no luck.  I can not find a text doc that tells me how to install on the stuff I have extracted.

Once I have the files/folders extracted to my hard drive (which I have) - what do I do next to actually run the install?

BTW - I tried using the application/package manager  "Synaptic" - but it can not see the package to install.  I mean all the folders and files are there right on my hard drive (in filespace) and it can not even see it!!!  And I can not do a "browse" thru the filespace to look for it!!!  I mean I know right where it is:  home//bkail//ABIWORD2.2//Abiword2.2.8 - and it can not see it!!!)  I'm getting really frustrated.  I just seems like it should not be this hard.

Thanks in advance,

 - w

---

### Post by Maestro23 on 2007-02-28
Sounds like you are mixing/matching different install methods.  First things first:

1. Where did you d/l the file from?

2. What kind of file is it?

---

### Post by Woody_in_MN on 2007-02-28
I got the file from:

[http://linux.softpedia.com/get/Office/](http://linux.softpedia.com/get/Office/)

it downloaded as a  ...tar.gz file.  But like I say - its already extracted to my hard drive the archinve manager did this - I just need to know what to do next.

What kind of file am I supposed to look for?

Is there any conventions where the actual install files, scripts, routines - what ever you call them are typicially located?

I did see a folder called "Autopackages" - is there something in there I can install from?

 - w

---

### Post by Maestro23 on 2007-02-28
> **Woody_in_MN said:**
> I got the file from:

[http://linux.softpedia.com/get/Office/](http://linux.softpedia.com/get/Office/)

it downloaded as a  ...tar.gz file.  But like I say - its already extracted to my hard drive the archinve manager did this - I just need to know what to do next.

What kind of file am I supposed to look for?

Is there any conventions where the actual install files, scripts, routines - what ever you call them are typicially located?

I did see a folder called "Autopackages" - is there something in there I can install from?

 - w

Ok, you are installing from source(the hardest thing to do for person new to linux).  When you extracted the tarball, it should have created a directory for the program.  Inside that directory there should be a README or INSTALL doc with installation instructions.  Take a look.

When installing from source.  You must have "build-essential" installed, as well as "make".

> sudo aptitude update && sudo aptitude install build-essential make

The following link gives steps for compiling from source(toward the bottom): [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

After you find either the README/INSTALL doc and read it, post back here.

---

### Post by Woody_in_MN on 2007-02-28
> **Maestro23 said:**
> Ok, you are installing from source(the hardest thing to do for person new to linux). .. 

OK - well I do not want to do it the hard way - I want to do it the easy way.

So the hard way is installing from a tzr.gz file.  What is the easy way to install Abiword? 

ps - Just remember that PC is not internet connected.  I will have to copy the files I need (what ever I have to down load) from a XP PC - burn to CD - then copy to the Ubuntu PC to install.

 - w

---

### Post by Woody_in_MN on 2007-02-28
OK - I got too frustrated.  I am going back to Xubuntu - the install disk of Xubunt I have already has Gnumeric, and AbiWord as part of the build.

When I have time - I will read over:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

This may have what I have been missing.  It looks klike there is a section on installing tar.gz files.

Is there a good book, paperback, I can get that would give me the important stuff I am missing?  

BTW - I dabbled with FreeBSD for awhile - but bailed on it for the same reason - it seemed to complicated to install new programs.  If I can get over that curve, I would be willing to look at giving up XP.

 - w

---

