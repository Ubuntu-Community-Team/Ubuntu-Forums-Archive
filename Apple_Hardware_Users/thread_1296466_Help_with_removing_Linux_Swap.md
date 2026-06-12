---
title: "Help with removing Linux Swap"
date: 2009-10-20
forum: Apple Hardware Users
---

### Post by Under the Sky on 2009-10-20
Alright I used Boot Camp to partition my 250gb hard drive so that I'd have 32gb to install Ubuntu on. I installed it and had all kinds of fun, but I realized that it really didn't serve a purpose for me and decided to remove it. 
  Here is my problem: I had somehow managed to create 3 additional drives on my computer: one called Boot Camp (32gb), one whose name I don't actually remember now (I think it had something like 200mb on it), and one called Linux Swap (with 1.3gb on it). I used Disk Utility to remove the first two, but Linux Swap is still there. I cannot mount it and Disk Utility is unable to remove it or erase it, and in addition won't resize my Macintosh HD. Therefore, I can't regain the 32gb which I originally set aside for Ubuntu. I'm not sure why.
     In an attempt to fix this, I downloaded GParted from the GParted wesite and burned the iso file to a cd immediately after it gone done downloading. With the disk in the drive I tried to boot my computer holding the 'c' button, you know, to boot to the cd. It makes some noise at first, but then boots to osx.
       I have tried all of these things multiple times (which might be why I'm having trouble?). But I really am very new at this and am quite inept. I'm running osx 10.5 on a 2009 aluminum intel macbook, and although it might not seem like Linux Swap takes up that much space, it is somewhat annoying to have on there. I just need to be walked through on how to fix this, if possible, and if someone could that would be awesome!

---

### Post by B_Free on 2009-10-21
Did you burn an image of the iso or did you just copy the iso to the disk?

---

### Post by Under the Sky on 2009-10-22
Um I just stuck a blank cd in the drive and followed the [default apple] finder prompts and what not to burn the GParted iso file (that I just got done downloading) to it. This same process worked for me to make a live cd of ubuntu so I was pretty sure that I was doing it right. If not I could use some instructions on how to not completely mess everything up, as I think that is what I've been doing.

---

### Post by fslezak on 2009-10-22
Hmmm... Very interesting. Did you ever hear of Parted Magic? That is a UNIX based media that has GParted on it. It came in handy to partition my disk, but I'm not to sure about undoing the effects...

Keep Trying!:KS

---

### Post by Under the Sky on 2009-10-22
Thanks I will give that a try, but first off I was wondering: could I return my harddrive to its original, unpartitioned state with the use of my mac install disks that (I think?) came with my macbook? By this I mean can it unpartition everything but still keep all my data? If so, how do I do this magic? And do you know if  Parted Magic would work without any adverse effects on my mac?

---

### Post by mackandall on 2009-10-23
Use the disk utility in Leopard to change the partition to mac os journaled format then you will have the  ability to manipulate it as you please. That is, you are going to  choose to erase the partition opting to change the format to mac os journaled (i think that is the name).

---

### Post by Under the Sky on 2009-10-26
I tried that but I am unable to mount the Linux Swap drive in disk utility, so therefore I am unable to do anything with it.

---

