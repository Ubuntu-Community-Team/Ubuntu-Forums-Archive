---
title: "Powermac"
date: 2011-09-16
forum: Apple Hardware Users
---

### Post by slc2015 on 2011-09-16
Hi!
I'm trying to install Ubuntu 10.04 Server on my Powermac G4 (Yikes) and when it is decking the disks, I get a message asking me to select a disk drive driver. I don't know which driver to pick! Help me! 
Sam

---

### Post by rsavage on 2011-09-17
Is this your problem? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131)

---

### Post by svtguy88 on 2011-09-17
Hmm....I wonder the same.  Is the bug rsavage suggested the same that you are seeing?

It seems possible, as the Yikes and the B&W G3 seem to have shared a lot of things.  

Regardless, I would try installing using a newer distro, as Ubuntu 10.04 uses a kernel that is (according to the bug above) prior to the bugfix.  

Maybe give the [Lubuntu Live CD]("http://cdimage.ubuntu.com/daily-live/current/") a try?  Note:  currently the PowerPC image is oversized apparently, so you'll need a DVD drive to install from.  Eventually this should be fixed, and a CD will be sufficient.  

Hopefully the newer kernel will alleviate your problem.

---

### Post by slc2015 on 2011-09-17
Thanks so much for the link! And I do believe thats my problem. So should I try 10.10?
Sam

---

### Post by slc2015 on 2011-09-17
Hi,
I just downloaded 11.04, and I tried the install, and it still has the same problem....

---

### Post by svtguy88 on 2011-09-17
I don't recall what kernel 11.04 uses, but I'm sure it's before 3.0.0-7.9, and per the bug report, that is the kernel where the fix showed up.

If you click on the link in my post above, it will take you to the Lubuntu Live CD page, and you can scroll down and download the PowerPC image.  Again, this is a development build, so it may not work perfectly (or at all..but most seem to be having alright luck).

Also, you need to burn it to a DVD, as it too large to fit on a CD right now.  Does your machine have a DVD drive?

**edit**
I reread the bug report, and it even mentions that the Yikes G4's used the same motherboard as the B&W G3's.  So, that is definitely the bug affecting you right now.

---

### Post by slc2015 on 2011-09-17
Yes, i realize that, but I need the server version of ubuntu as it contains all the packages needed to set up a web server. (web, mail, etc.)

---

### Post by svtguy88 on 2011-09-17
You should be able to install any and all packages you need via synaptic, once you have a bootable system.

---

### Post by rsavage on 2011-09-18
The server cd is here [http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

Or you can install it via the mini.iso.

On the original link I gave were instructions for how to get 10.04 working.  You could possibly adapt these for the server edition?

---

### Post by slc2015 on 2011-09-18
OK. I have the 10.04 CD and am trying to install. I tried to use the driver that was in the bug post. It didn't work. It gave me an error about the kernel version. And I have no clue how to modify code of change the drivers to work with other versions of Ubuntu... I just need a working solution for Ubuntu Server. And as for Lubuntu, I have debian right now and I tried to set up the server software that I need, and I messed it up and I need to reinstall, and I don't want to have to go through that with Lubuntu.

---

### Post by rsavage on 2011-09-18
I don't understand your post.  I gave you the link to the most recent server (admitedly still in testing) that has the kernel you require?

---

### Post by svtguy88 on 2011-09-18
^^^Agreed.

If you really don't want to install the server software separately, use the link that rsavage posted.  It will have the newer kernel, and is the server edition...

---

