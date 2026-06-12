---
title: "Total switch to Ubuntu. Need help with partitioning"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Zerol on 2007-09-21
Hello,

I just installed Ubuntu from the LiveCD and told it to use my total hard drive. I did some research before the install and after the research I wanted to make 3 partitions. One root for the Linux OS and programs. One for media. And one swap. 10GB, 69GB and 1GB big.

But when I installed Ubuntu it just asked me to format and make a ext3 partition and a SWAP partition. I didnt have any further choice.

Since I want to reinstall anyways since I made the OS language Dutch but that pretty much sucks I wanted to ask how to do this when I install Ubuntu again with the LiveCD.

Ive read a lot on the forums but when I saw people having partitions just like that it seemed to me that during the install you would be asked how to form the partitions.

Hope somebody can help me and yes I am really new to all this :P.

Oh and one other thing.. During the use of the LiveCD my Broadcom43188 worked after just running a simple script (not ndiswrapper) now when I totally installed the OS, Wireless doesnt even show up when I open Networking. Leave alone let it make connection with a network. How can that be?

---

### Post by leedsdevil on 2007-09-21
when u reinstall from the live cd pick the option manually partion the hard drive this will give you the choice of how to set up your drive GL

---

### Post by arkara on 2007-09-21
ok
you can boot from the live cd and to to system>administration>gnome partition editor
from there delete all your partitions
and then create one partition for your media to any filesystem you want just not ntfs
the rest of you hd will be unallocated space.leave it that way..
apply your changes and then install ubuntu
during the installation when you get to partitioning click the use the largest continius free space
and proceed normaly this shoud do the job

---

### Post by Zerol on 2007-09-21
Wow.

Great community! I'm going to try it in a bit. Thanks for the help. After the re-install ill play around a little to make my broadcom work.

---

### Post by jw5801 on 2007-09-21
> **Zerol said:**
> Oh and one other thing.. During the use of the LiveCD my Broadcom43188 worked after just running a simple script (not ndiswrapper) now when I totally installed the OS, Wireless doesnt even show up when I open Networking. Leave alone let it make connection with a network. How can that be?
Did you run the script again after you installed? Any changes you make whilst running the LiveCD will **not** be translated to your hard drive, everything is simply written to RAM.

---

### Post by Zerol on 2007-09-21
Hello again.

I did run the script after I installed. But on the LiveCD I also had the option Wireless already without the script under Networking.

Anyways..

When I use GNOME Partition Editor I first cant access the partitions. Then I do unmount and I want to format it to a ext3. I get this error; 

mke2fs 1.40-WIP (14-Nov-2006)
/dev/hda1 is mounted; will not make a filesystem here!

Then it goes to an unknown type of partition and seems to be mounted again. Unmounting and then trying it again gives the same error..

---

### Post by jw5801 on 2007-09-21
Open a terminal (Applications > Accessories > Terminal) and type ```
sudo killall gnome-volume-manager
```to stop gnome auto-mounting the partition you're trying to edit. As for the wireless, we'll sort that out once you get installed and up and running.

If that doesn't work, then you can always set up your partitions using the GParted LiveCD (see the link in my sig.): It's basically a LiveCD with a simple interface to run GParted (the GNOME Partition Editor). It runs a much much newer version of GParted than is on the LiveCD, however, and you won't have any of the automounting issues you get using the Ubuntu LiveCD.

---

### Post by Zerol on 2007-09-21
Thanks! It worked.

Got it running fine now.

Though on the Wireless part. Ive got a Broadcom Wireless 4318[AirForce] for this type of card there is a special topic on this forum.

I got a script of that topic and it worked while using the LiveCD. Now when I was running Ubuntu for real for the first time I had the option of Wireless again under Connections when you go to Administration > Network.

But when I installed the script for this specific card again the option vanished and now it looks like its not recognised at all anymore.. Looking at my hardware with a command with the Broadcom wireless card it says; UNCLAIMED.

Whats this? Should I make a new topic for this or..

---

### Post by Pumalite on 2007-09-21
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by SpiritIsReality on 2007-09-21
howdy

partitioning:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

trails

---

### Post by Zerol on 2007-09-21
Solved the partitioning. Moving my Wireless problem into another topic. Thanks for the help but the links didnt quite work for me but added some information from them into the new post in another topic.

---

