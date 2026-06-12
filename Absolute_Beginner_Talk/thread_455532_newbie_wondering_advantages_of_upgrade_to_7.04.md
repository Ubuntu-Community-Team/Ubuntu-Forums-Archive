---
title: "newbie wondering advantages of upgrade to 7.04"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by mgh on 2007-05-26
Hi All,

Still very much a newbie to Linux. I have two distros and XP, and using Ubuntu 6.10 the most. So far doing OK, managing most of what I want to do. One issue I have is automounting USB devices. I have my music files on an external NTFS HHD. I can read it fine, but to use with one program (SlimServer) I have to unmount it, and remount with a command line given to me every time I start up Ubuntu. This command line changes the umask. I was told that Ubuntu 7.04 has automounting built in.

Firstly, would V7.04 take care of automounting issues?

Second, would someone explain to a newbie the advantages and disadvantages to upgrading?

I read that V6.10 has longer support. I don't exactly know what that means regarding Linux distros, but to a newbie, longer support would seem to be better.

I have tried three or four threads here and elsewhere on how to set automount options with Ubuntu 6.10, but have had no answers. One poster had links to something called autofs (if I remember the name correctly), but I could not figure out as a NOOB if it would do what I needed. I could not understand all the instructions.

Any advice on upgrading?

Thanks for all help.

---

### Post by oilchangeguy on 2007-05-26
6.10 does not have support any longer than 7.04 does. version 6.06 is the lts version (long term support)

---

### Post by Happy_Man on 2007-05-26
Advantages of Feisty over Edgy:

1. Shiny Compiz goodness

2. Better wifi support

3. Restricted Drivers Manager (a godsend, this is)

4. Slicker, more polished

5. Yes, it automounts!

6. Just, overall, better. That's the only word for it. Better.

---

### Post by shanepardue on 2007-05-26
More goodness...

1) Migration Assistant - carries your documents and settings from other ubuntus or windows setups

2) Network manager with wpa2 even on the livecd

3) did we already mention Restricted Drivers and Management? (Hallelujiah!!)

4) Solid, stable, and "better"

---

### Post by zero244 on 2007-05-26
I agree with the new updates with Feisty buts its not all peachy keen. There are several posts here where people are having stabiity issues with Feisty. I for one went back to Edgy.........seems VMware Server wont work with Feisty unless you do some serious compiling etc.
The restricted drivers feature is nice.......but I have yet to get Beryl or Compiz to work for more than a minute with my Geforce 7600 card.
I dont plan on ever using Beryl again until you see it in Automatix.
By the way all my drives automount and have since I installed Edgy.
Download Automatix2 and install the ntfs support that should fix your automount problem and give you read and write access to your ntfs drives.

---

### Post by shanepardue on 2007-05-26
VMware server does work without compiling. Unfortunately VMware isn't compatible out of the box with the recent 
kernel feisty uses, but they do have a patch available. It is a script though and very easy to follow. Personally, I 
would recommend other virtualization options anyhow, but that's just my opinion.

As for Beryl, it still has it's issues, but I run it day in and day out without any problems.

Feisty definitely has more advantages than edgy in the long haul, but there's always a chance it's not for everyone.

---

### Post by mgh on 2007-05-26
Thanks for the replies.  I think I will try the upgrade to 7.04.  Interested to see what beryl is all about.

The automount issue is not a read issue.  I can plug in my USB drive, and Ubuntu 6.10 will see it, I can play music files off it, but the umask is set so that SlimServer can not get permission to use or see it.  Maybe what I need is permissions settings, so that any USB device, camera, thumb, whatever, will automount  properly.

Thanks for the help.

---

### Post by evolving_monkey on 2007-05-27
I am wondering if Feisty 7.04 is as good or better than v6.06 LTS for slightly older systems. I have a Gateway 6100 pc.
3Ghz p4
1gig (2 x 512mb ddr) dual channel
Nvidia 5200 OEM video card
157gig Maxtor SATA HD (7200rpm)
Intel pro 100 ethernet
SoundBlaster Audigy 2 OEM soundcard

It is a few years old but it is still pretty quick and stable for the age. 

Both versions of Ubuntu seem to detect my hardware pretty well. Both seem to install and dual boot well with Windows XP without any problems. I am new to Linux and I am trying to figure out which would be the most stable for the system I want to put it on (described above). Trying to learn with least amount of caffeine fueled all nighters as possible.

Thanks for the help.

---

### Post by evolving_monkey on 2007-05-29
I decided to play with both. 6.06 LTS could not mount the partitions on the hardrive (ntfs or fat32).  In the end Feisty 7.04 seemed to have better support for the computer. It could mount all of the partitions (still can not write to ntfs partition on computer even with ntfs-3g) but I can write to ntfs on the server. I don't think that this is a problem with ntfs-3g. I think it has something to do with the way the bios on older mainboards report the hard drive geometry (just a guess based on some reading). My main need was to write to the server so this is something I can easily live with.

Also, with feisty 7.04 i was able use the nvidia restricted driver. With 6.06LTS when I tried to load the nvidia restricted driver  it would leave me hanging after reboot at a command prompt. I could not get it to work.

Feisty seemed faster and more stable in general on this particular system. 

Keep in mind that I am new to Linux so you might get different results if you have more experience.

---

### Post by evolving_monkey on 2007-05-31
Wanted to add...the reason 6.06LTS couldn't see the partitions was because of an installation error on my part. I figured it out after the fact.

---

### Post by eentonig on 2007-05-31
Your problem with the ntfs drive, doesn't seem to be related to mounting. But to the fact that linux by default, can't write on ntfs disks.

Do you have "ntfs-3g" installed? (a program to allow writing to ntfs drives.)

---

