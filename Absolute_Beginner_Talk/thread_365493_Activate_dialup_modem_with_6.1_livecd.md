---
title: "Activate dialup modem with 6.1 livecd"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-02-19
I am using 6.1 Live CD but I cannot get my dial-up modem
to work.  The modem is recognized in Device Manager (USR
3610b), and I configure and configure in system -> administration
-> networking, but don't know how to get ubuntu to dial.  I check
enbale connection, but this does nothing.

I have read the ubuntu bible by Hagen and part of my problem is
that I don't have certain buttons on my window:  for example, no
Activate and Deactivate buttons under Properties, and no autodetect
feature next to the ports.

Do I need to download drivers?  The modem documentation says
that kernels 2.4 and up include drivers for this modem.

HELP!
Michl

---

### Post by ieee488 on 2007-02-19
I prefer to use gnome-ppp or kppp when dialing out on a modem.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Autodetect doesn't work on my modem even though it is Linux-compatible.
I don't bother with it.

---

### Post by Michl on 2007-02-19
But don;t I have to have access to the internet to
download the gnome packages?  I will look again,
but I tried this and failed because I wasn;t online.

Michl

---

### Post by the.phantom on 2007-02-19
might read this thread?
[http://www.ubuntuforums.org/showthread.php?p=1695130#post1695130](http://www.ubuntuforums.org/showthread.php?p=1695130#post1695130)
and ANY computer can download the packages ;-D
you can just double click to install
or do the edit like one post

but you will have to do that each time as live cd can't save the info !!!
good luck !
NOTE: if you are just checking out UBUNTU. if you get the live disk of 6.06  that part worked fine !
they made a few changes and kinda messed up that part on 6.1

so if you like it you can install 6.1 then download and install the other dialers to get it to work

---

### Post by yankeebisbis on 2007-02-19
hi had the same probem with dial up and i wrote to the developer to do something about it. this operating system is becoming like a joke.

---

### Post by ieee488 on 2007-02-19
> **Michl said:**
> But don;t I have to have access to the internet to
download the gnome packages?  I will look again,
but I tried this and failed because I wasn;t online.

Michl

You can download on a Windows PC. Copy the files to a USB flash drive. Take the flash drive over to the PC with Ubuntu. Insert the flash drive into a USB slot. Copy the file by dragging and dropping to the desktop.

---

### Post by ieee488 on 2007-02-19
> **yankeebisbis said:**
> hi had the same probem with dial up and i wrote to the developer to do something about it. this operating system is becoming like a joke.

OMG, that is too funny. :lolflag:

---

### Post by Michl on 2007-02-19
> **the.phantom said:**
> might read this thread?
[http://www.ubuntuforums.org/showthread.php?p=1695130#post1695130](http://www.ubuntuforums.org/showthread.php?p=1695130#post1695130)
and ANY computer can download the packages ;-D
you can just double click to install
or do the edit like one post

but you will have to do that each time as live cd can't save the info !!!
good luck !
NOTE: if you are just checking out UBUNTU. if you get the live disk of 6.06  that part worked fine !
they made a few changes and kinda messed up that part on 6.1

so if you like it you can install 6.1 then download and install the other dialers to get it to work

That link seems like the right road.  I will follow it.  Thank you!

I want to migrate to Linux.  I
have tried live PClinuxos and Gentoo in addition to ubuntu and ubuntu
is the one.  I installed a second harddrive ready to format in linux, bought
the bible, and so on.  But I made getting the dial-up modem to work
on the live cd the final test for switching away from Windows.  I think
if I can't get the modem to work, then linux just is too hard from me and I must
remain stuck in the MS cage.
Michl

---

### Post by the.phantom on 2007-02-19
a quote from the top of this forum ;-)

Note:If you have no compelling reason to upgrade to Edgy, please consider staying with your current version. As with ANY Operating System upgrade, it is important to fully back up your system before attempting the process.


"Compelling reason" here does NOT mean "well, I want to be as up-to-date as I can be." If you can't think of a single thing that's in Edgy that you can't live without, then you probably don't have a compelling reason.

Also note that Edgy 6.10 is considered a development platform for testing new ideas,and technology. Use of this version,and coming versions there after are at your own risk.


First Time Linux/Ubuntu users are advised to use dapper,and not edgy as their frist step into Linux.


so as i said if you use the 6.06 version you will be able to get the modem working and have a stable version ;-D
the part you are having trouble with works on 6.06 (daper)

---

### Post by ramjet_1953 on 2007-02-19
> **yankeebisbis said:**
> hi had the same probem with dial up and i wrote to the developer to do something about it. this operating system is becoming like a joke.

I don't know where you are coming from?????
If a manufacturer of a dial-up modem locks it into Windows and doesn't release the drivers, where is Linux at fault?

Quite often WinModems are just part of a soundcard these days and the driveres are not open source.

It really is quite amazing that so many drivers have been developed by dedicated hackers that must have spent countless hours and resources in doing so. All for free.

Regards,
Roger :cool:

---

### Post by Michl on 2007-02-19
I am a happy man.  I am writing this running the livecd 6.1.  Followed
the alternative way 1 (wvdial) logged on, wrote some emails, and
checked-in here.  I passed my test and installing Ubuntu tomorrow.

I guess this is the first lesson of linux:  there are many ways to
do the same thing.

Thanks for the quick help. 
Michl

---

### Post by ramjet_1953 on 2007-02-20
> **Michl said:**
> 
I guess this is the first lesson of linux:  there are many ways to
do the same thing.
Michl

Yep! You are exactly right!

When you start to dabble with the command line, it is amazing how many ways there are to do the same thing. That is the power of Linux. It allows you to "get under the hood" and change things to suit yourself.

Regards,
Roger :cool:

---

