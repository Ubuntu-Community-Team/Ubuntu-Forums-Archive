---
title: "Trying to install ArcReader"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by urbaneezer on 2006-07-18
So I've got an ArcReader (ESRI gis viewer) for Linux cd and I'm trying to see if it will install and work with Ubuntu.  

I've received some info from a friend which follows: 

> I notice that the Setup script should just flat out be executable, unless the noexec option is engaged on your CD-ROM.

Okay, let's try something slightly different.

Do this:

sudo su -
#You will be prompted for your password here.
cd /usr/src
#Just seems like a good place to use
mkdir GIS
#Seems like a good name for the directory.
cd /media/cdrom0
tar -cf - . | (cd /usr/src/GIS; tar -xvf -)
#You will see a bunch of files scroll by.
cd /usr/src/GIS
./Setup

What you are doing is copying the files off of the CD-ROM onto your hard drive, then installing from there.

I began his instructions...sudo su and password went fine, but when I entered cd /usr/src I got back the following:

> bash: cd: usr/src: No such file or directory 

Yes, I did put a space between cd and /usr/src...still get the same error.  

Also, I've gone to Places<Computer<filesystem and there is the usr folder (and therein the SRC folder).

Wonder why I'm getting the error?

---

### Post by Kurt` on 2006-07-18
> **urbaneezer said:**
> ```
 bash: cd: usr/src: No such file or directory
```

You need the / before usr. / means "start from the root of the drive". Without the /, it's looking for a folder called "usr" in the current folder.

---

### Post by urbaneezer on 2006-07-18
It got all the way thru the process and the ArcGIS Reader splash screen came up...then a system error message popped up that said:

> ArcReader setup cannot be run from root.  Please exit from root then restart the setup.

What does this mean?

---

### Post by Afishionado on 2006-07-18
Root is Unix-speak for Administrator Mode. You went into this mode with the "sudo su" line. Press ctrl+D to exit the mode.

Now try running:

/usr/src/GIS/Setup

and cross your fingers.

---

### Post by urbaneezer on 2006-07-18
Cha-ching!

Thanks everybody!  I'll let you know how it works out if it's cool!  :cool:

---

### Post by PaulHuffman on 2008-05-14
I got ArcReader 9.2 downloaded from ESRI.com.  I used File Roller to unpack the tar into a directory in my home directory. It wouldn't let me unpack in /usr/scr unless I was root. 

Then I tried running Setup with sudo but got a window from ESRI that Setup cannot be run as root.  So I tried running ./Setup as my user.  It ran for quite a while then hangs at "Installing Merge Module".  I had to give it the cntrl-c.  Still not running.

---

