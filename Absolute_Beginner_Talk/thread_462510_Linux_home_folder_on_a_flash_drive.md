---
title: "Linux home folder on a flash drive"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2007-06-02
Hi all,

I wasn't sure exactly where to post this, so I'm just going to try here for now.

I was wondering if there is any way to install linux on a machine so that individual users can use a flash drive as their home folder to keep their settings and files with them. What I am thinking of is a central computer, maybe at a cafe or something, where users can basically bring their computers with them, but in the form of a pen drive rather than lugging around a laptop. I believe I've seen a website with something similar, but I have no clue how to find it.

Thanks a lot,

Chris

---

### Post by Inxsible on 2007-06-02
> **herrma29 said:**
> Hi all,

I wasn't sure exactly where to post this, so I'm just going to try here for now.

I was wondering if there is any way to install linux on a machine so that individual users can use a flash drive as their home folder to keep their settings and files with them. What I am thinking of is a central computer, maybe at a cafe or something, where users can basically bring their computers with them, but in the form of a pen drive rather than lugging around a laptop. I believe I've seen a website with something similar, but I have no clue how to find it.

Thanks a lot,

Chris

Wouldnt the cafe have to install linux without the home drives on the computer itself ?

But seriously, it could be done, but you would have to make sure that you never boot up without pen drive attached and at the same port (i m not really sure if it changes address by port)

But lets say you had another external HDD attached while installing, you would have to be very very sure of the name of the device.

If the pen drive was name /dev/sdb1, then when someone else comes in to boot up, they need to make sure that their drive is also named /dev/sdb1.

Also if you attache any other external device before attaching the pen drive, the device names could change creating troubles while booting up because it wont find the home drive on the device that is listed in the fstab or some other files.

I know thats not very articulate...but you get the drift.

---

### Post by tgalati4 on 2007-06-02
I grabbed an Ulteo disk at the SCALE 5X conference.  Haven't played with it; I have 7 other distros to go through first.

Here's a link:

[http://www.ulteo.com/main/](http://www.ulteo.com/main/)

I agree with the above, it would create more problems.  What is the exact purpose that you are trying to accomplish?

In a cafe, leave Linux running all the time.  If someone wants to plug in a flash drive, so be it.  It will show up under /media/flashdrivevolumename.  If someone knows how to use a flashdrive to load files in the first place, then they can figure out how to configure Linux.  It would be better to simply create user accounts on the machine--the old fashion way--with usernames and passwords.  That would be good for repeat business.

The machine stays up all the time, and the user simply logs off when they are done.  New users could use a guest or house account.  Frequent users would get their own account that they can customize (perhaps for a small fee).  Put a notice of "Presumption of Risk":  If you are watching a baseball game, expect to get hit by a baseball.  If you are using Linux, expect to bitch about Windows.

---

### Post by duphenix on 2008-01-18
I want to be able to do this as I have two laptops both with sd card readers and it would make it much more convenient to only have to move my sd card back and forth instead of always double checking to see which files I have copied and which ones I haven't.  This way my documents _and_ settings folders would be the same on both machines all the time, without one set getting updated and the other not. (For instance with gaim, buddies added on one machine but not the other.)

---

### Post by dcstar on 2008-01-18
> **herrma29 said:**
> 
.........
I was wondering if there is any way to install linux on a machine so that individual users can use a flash drive as their home folder to keep their settings and files with them. What I am thinking of is a central computer, maybe at a cafe or something, where users can basically bring their computers with them, but in the form of a pen drive rather than lugging around a laptop. I believe I've seen a website with something similar, but I have no clue how to find it.
.........

You would set up an /etc/fstab entry something like this:

```
LABEL=USB_HOME /home ext3 rw,errors=remount-ro,nodiratime,noatime  0  2
``` 

And you would create ext3 partitions on each USB device and label all of them "USB_HOME".

In theory, if a USB drive set up like this was already plugged in when the machine is booted up it should mount the home drive on it (I don't know, you would have to try it).

---

