---
title: "Saving settings with a Live CD"
date: 2007-04-21
forum: Apple PPC Users
---

### Post by microfox on 2007-04-21
Hi


I'm brand new to Ubuntu. I got version 7.04 for PPPC and tried it for the first time, yesterday. After it had finally loaded, I started making some cosmetic changes and also added some softwares and codecs, only to to realize I couldn't find a way to save the new settings after I had logged off. So, it looks like all the changes I made won't be there, the next time I load the Live CD.

Is there a way to save Ubuntu's settings on a hard drive (like it's possible in Knoppix, I think) until I decide to install it permanently ?


thanks

---

### Post by jerrylamos on 2007-04-21
One way to save changes in previous Ubuntu levels is called "persistent".  A USB pen drive can be formatted and labelled so that most all changes are preserved and can be used on subsequent boots.  This also has the great advantage of being largely computer independent - you can take the CD and the USB to different computers and have your changes, package installs,  and files with you.

This worked on Ubuntu Feisty Fawn Alpha until about February 7, 2007.   Sometime in the following three days it stopped working.  Reading between the lines, it appears some boot scripts were picked up from Debian Linux which broke "persistent".  Right before final release one of the canonical experts tried to fix the bug but was not successful.  See [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)

Yes there are CD Live Linux's that can save changes and files from one boot to the next - earlier levels of Ubuntu like 6.10 Edgy Eft and 6.06 Dapper Drake LTS (Long Term Service to be supported for another 2 years), Knoppix, Puppy, Simply Mepis, ... Some of these like Knoppix, Puppy, and others have user friendly menu's to use the USB.  In Ubuntu there are a few command line entries needed.

Personally I think "persistent" changes and files would be a good way to expand the Linux base and get more users on board.

I don't know if the Ubuntu developers will try to put out a fix on an upgrade to Feisty, or whether we have to wait for 6 months for the next release for them to try again.  Everybody scream please....

Thanks, Jerry :(

---

### Post by amgadpasha on 2007-04-23
PLEASEEE!!!!

my work laptop has encryption on the hard drive, i can't install ubuntu on it.. i've been using the persistent mode since Dapper..
why, why would they do something like this :(

---

### Post by The Gladiator on 2007-04-30
I was screaming in another part of the forum [http://ubuntuforums.org/showthread.php?t=424121](http://ubuntuforums.org/showthread.php?t=424121) . I scream here too :-))))

---

