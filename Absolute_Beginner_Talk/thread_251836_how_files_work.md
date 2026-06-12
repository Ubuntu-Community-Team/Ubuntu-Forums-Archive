---
title: "how files work"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by empcrono on 2006-09-06
I'm trying to figure out how and ware files install. I was woundering if there was a way to specify ware the the files install. What is the reasoning behind ware they install. (this way i can keep files orginized cleanly for the system). Is there a way to move aplications that are installed to anthor section. I mean so that i can keep everything pointed ware there supposed to be pointing. I'm looking for both an easy or advance way i.e. a udamated command or how to go about it manualy. any help would be apriciated thanks.

---

### Post by amohanty on 2006-09-06
Typically you would have to take the 'compile from source' route to install pkgs in your own dir tree. Usually source packages are dstributed with an autoconf file, which generates a makefile. The steps you take are:
1. download sources
2. Type **./configure --options**
3. Type **make**
3. Type **make install**

Usually in (2) you specify where to install instead of default. If you would like to use the dpkg package management system to keep track of your sources, look into **checkinstall**

HTH
AM

---

### Post by David Corrales on 2006-09-06
Actually, you'll want to use the package manager because it takes care of all those nuances.
In linux, installed programs usually go to the the /usr directory but only root can modify it (which is the way it should be :)).
So, once again, just stick to the package manager and you shouldn't have any trouble with adding/removing software.

---

### Post by aysiu on 2006-09-06
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by empcrono on 2006-09-06
thanks everyone but i perfer the command line. i have been using it for the installation of programs and modifying them through the command line i find it much easier and much more stable. however is there a way to specify ware the file installs with out having to compile packages from source? IF not and i do have to compile from source (witch i have done to a very limited to dagree) can any one then point me in the right direction on understanding how to compile packages from source. i would like to get to know it more if i have to maintain that sort of controle. 

btw: you guys own, i have never had help that quick on a site before. also so you know i think UBUNTU OWNS i like KDE better but for some reason UBUNTU seems to run more stable maybe after i understand linux better i'll switch back over to kubuntu.

---

### Post by aysiu on 2006-09-06
If you don't compile from source, you don't need to know where the files install. All you need to know is how to launch it. The application usually gets a menu item--if not, you can usually launch it by typing the name of the application in the run (Alt-F2) dialogue. For example, to run Firefox, you press Alt-F2 and type ```
firefox
``` You don't need to know that the launcher for Firefox is in /usr/bin or that the files for Firefox are in /usr/lib/firefox.

The link I gave before gives an overview of how to install software (yes, via the command-line, which, apparently, is what you prefer).

If you must compile from source, amohanty's giving you good tips.

---

### Post by powder on 2006-09-06
You also might be interested in the "whereis" command.  You can use it to easily find directories of programs.  For example:

$ whereis xmms
xmms: /usr/bin/xmms /usr/lib/xmms /usr/bin/X11/xmms /usr/share/xmms /usr/share/man/man1/xmms.1.gz

---

### Post by empcrono on 2006-09-06
> **aysiu said:**
> If you don't compile from source, you don't need to know where the files install. All you need to know is how to launch it. The application usually gets a menu item--if not, you can usually launch it by typing the name of the application in the run (Alt-F2) dialogue. For example, to run Firefox, you press Alt-F2 and type ```
firefox
``` You don't need to know that the launcher for Firefox is in /usr/bin or that the files for Firefox are in /usr/lib/firefox.

The link I gave before gives an overview of how to install software (yes, via the command-line, which, apparently, is what you prefer).

If you must compile from source, amohanty's giving you good tips.

thanks i will bookmark and study this, some more i know most of what is stated in this howoto but there are a few things im not so good with. mostly just the compile from source. however the reason i want to know how to install stuff in other directories is because what if one hard drive is too full i installed ubuntu on a buddies computer a old computer i got everything working and such but he ran out of space but his other hard drive wasnt touched. To be more specific i installed the other hard drive after i installed ubuntu i got it formated and such and ubuntu reconized it but like i said his hard drive the first one with the os installed on it is full to the brime.

---

### Post by amohanty on 2006-09-06
> **empcrono said:**
> thanks i will bookmark and study this, some more i know most of what is stated in this howoto but there are a few things im not so good with. mostly just the compile from source. however the reason i want to know how to install stuff in other directories is because what if one hard drive is too full i installed ubuntu on a buddies computer a old computer i got everything working and such but he ran out of space but his other hard drive wasnt touched. To be more specific i installed the other hard drive after i installed ubuntu i got it formated and such and ubuntu reconized it but like i said his hard drive the first one with the os installed on it is full to the brime.

Typicaly in this situation, you would want to plan out your partition layout. As David mentioned, most of the apps get installed in /usr. if you feel you do not have enough space on an hdd, you want to set a partition aside for /usr during the install. As a rule of thumb this is usually how I assign space. modify it to your needs, also you dont have to follow the same layout.

/boot    200 Mb (you can do with as little as 50Mb too)
/usr      5Gb     (if you can allocate 5g to / that would work too)
/           500 Mb (assuming /usr and /home has its own partition)
/home  at least 1G 

IMO the barrier to compiling from source is mainly a perception issue. You dont actually have to be a programmer to know what options to use. At the very least you would need to know:
1. How to decompress a tar.gz file.
   > man tar
man gzip
man bzip2
will help.

2. > ./configure --help is also quite helpful.

regarding your query, jus look at the 
> ./configure --prefix format.


HTH
AM

---

### Post by xhaan on 2006-09-06
If you have space problems but still want to add more programs to the system, you can just move your usr directory to a bigger partition, even on another disk.

For example, I had everything in one partition and only had like 1.5 gb space left, but I wanted to play games that were too big to fit in that space, so I  booted up the Ubuntu live cd, ran gparted, shrunk my Windows partition and made a new 90gb ext3 partition, then moved all the files in usr to the top level of the new partition, edited fstab to mount the new partition to /usr, then I moved my /home directory into the new partition and symlinked /usr/home to /home. 

Now my /usr directory has over 85 gb of space to install new programs and my root partition gained some more space, intstead of having 1 gb it now has 4.5 gb to work with.

---

### Post by empcrono on 2006-09-06
> **xhaan said:**
> If you have space problems but still want to add more programs to the system, you can just move your usr directory to a bigger partition, even on another disk.

For example, I had everything in one partition and only had like 1.5 gb space left, but I wanted to play games that were too big to fit in that space, so I  booted up the Ubuntu live cd, ran gparted, shrunk my Windows partition and made a new 90gb ext3 partition, then moved all the files in usr to the top level of the new partition, edited fstab to mount the new partition to /usr, then I moved my /home directory into the new partition and symlinked /usr/home to /home. 

Now my /usr directory has over 85 gb of space to install new programs and my root partition gained some more space, intstead of having 1 gb it now has 4.5 gb to work with.

Thanks man that solves that problem. I must say also in regrades to author post, that most things, i have a little difficulty, with, in Linux, now, and in the past, has been perception. Windows gets in your brain in the form of habit. However once I do get past that and use the Linux alternative or use something windows doesn't even do at all it feels so natural that i then start havening a problem with windows when i help others with there windows computers. Linux is sure awesome. anyhow this is all good stuff however i sure wish there was a way to say ware it installs without compiling from source however i don't see this as a prob right now and see it being a problem is not such a big deal and would rarely come up so any way thanks guys.

---

