---
title: "I Can't Boot Into Lubuntu 12.04 LTS"
date: 2017-06-16
forum: Apple Hardware Users
---

### Post by z970mp on 2017-06-16
First of all, hi. I'm new to Ubuntu Forums. I was referred to here by someone on Mac Rumors in the hopes that someone here might be more knowledgeable on the subject of booting a stubborn Linux.

Second of all, yaboot is located on the second hard drive, on the second partition.  I've tried many things to get it to boot with that, but it always comes  up with either an error, or the forbidden sign.

What's happening is that in Open Firmware, after everything's installed the Desktop CD and all is dandy, I'm putting in  "boot hd1:2,yaboot". 'hd1' being that everything Linux is on the second  hard disk, and '2' because the bootstrap is on the second partition, ON the second  drive. So after that's entered, some text gets thrown up for a split  second, there's a bit of orange, and then it goes to a grey screen as if  an OS is being booted up, only the "forbidden" or  "cross-inside-a-circle" sign comes up and doesn't go away. I'm  absolutely stumped! Anything anyone might have in mind?

This was even done after the automatic install by the CD desktop installer! I've been at this for a couple weeks and I'm at my end! Help!

---

### Post by ernsteiswuerfel on 2017-06-17
What does **sudo ybin -v** tell you when you write your /etc/yaboot.conf to disk?

---

### Post by z970mp on 2017-06-17
I'm confused. I just install it using the installer, not a drag and drop. Please explain.

In Open Firmware, OS X Terminal, or Linux Terminal?

---

### Post by ernsteiswuerfel on 2017-06-17
> **z970mp said:**
> I'm confused. I just install it using the installer, not a drag and drop.
Just using the installer won't be enough on PPC machines most of the time. ;) 

Your boot configuration the installer created is in **/etc/yaboot.conf**. Most propably you need to edit this file manually via a terminal. After changing your yaboot.conf you need to write the changes to disk with **sudo ybin -v**, via terminal. If you start the machine from DVD or USB, you need to mount the partition with your yaboot.conf on it first. Then use sudo ybin -v -C /pathtoyourpartition/etc/yaboot.conf where pathtoyour... is of course the place where you mounted your partition to.

For more info use **man yaboot**, **man ybin** and **man yaboot.conf** from terminal.

---

### Post by z970mp on 2017-06-18
How can I edit the file via Terminal? What do I need to edit? Where is the place where I would have mounted my partition? It's on the desktop, I don't know what more I can tell you.

I feel like a confused old man.

---

### Post by rsavage on 2017-06-24
I can definitely fix this for you (12.04 had a known bug), but I don't see the point of installing 12.04 (unsupported).  The easiest thing to do is install 14.04 and hit the option key on start up.  That would work.  Newer versions had another problem, but I don't know anything about that.

---

### Post by Bucky Ball on 2017-06-24
I would also forget 14.04. That is unsupported, too. Lubuntu LTS releases have three years support, not five.

Install 16.04 LTS which is supported until April 2019 and report back if you have issues. There is no point in installing 12.04 LTS or 14.04 LTS.

---

### Post by rsavage on 2017-06-24
<removed unnecessary verbiage>If you can't install 12.04 you probably won't be able to install 16.04.  14.04 is the way to go until you find your feet.  Then you can upgrade or install 16.04 when you know what your're doing.

---

