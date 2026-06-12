---
title: "Partioning a second hardrive"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by stringer630 on 2008-01-11
Hi everyone

I know there are loads of post and helpful guides on here about dualbooting and ive read most of them. However my situation isnt really covered in any of them. Its probably an easier setup in fact =D

I already have winxp running on a 80gb hardrive. Its pretty much full and ive just bought a secondary hardrive. I want to partion it with an install of Ubuntu 7.10, and another partion for extra storage for windows. 

Also, anyway to setup the second partion for both win and ubuntu storage?

Help much apreaciated, cant wait to get using Ubuntu! 
Thanks in advance

---

### Post by Arthur Archnix on 2008-01-11
Yes indeed. I've seen people run into problems adding a second hard-drive and then installing ubuntu. My advice to you is to unplug the windows hard-drive, and plug the new hard-drive into the space freed by removing the windows hard-drive. Then toss in the ubuntu installation cd (live or alternate) and install it. When you come to the point of the install where it asks you how you want to partition the hard-drive you have to choose manual. Depending on the size of the disk, and how much space you want to share between windows and ubuntu, the size of the partitions will vary.

If you're not sure you can use this as a guide:

5GB for /   <-- that means root, where all the necessary OS stuff goes, like C:\Windows
1GB for swap   <--some people say double your RAM, others say no more than 1GB
At least another 5GB for /home  <-- this is where all you settings and personalization is stored. Wallpaper choices, themes, etc. It's also where most of your files go by default. Like C:\Documents and Settings\Arthur\MyDocuments. If you plan on putting lots of files here maybe give it more space. If you plan on using your windows disk and the shared partition on the second hard-drive (ubuntu) then leave it at five, that should be plenty.

Except for swap, which you don't get to choose how it's formatted, make these partitions ext3. I like to add the "noatime" and "nodev" options as well for performance reasons, but they are potential downsides so you may just want to go with the defaults.

Finally, make your last partition the remainder of your drive, format it to ntfs, and mount it somewhere like /mnt/shared

Once you're installed and up and running, plug in your windows hard-drive (leave Ubuntu hard-drive where it is) and then add Windows to your grub options. I can explain this step as well if you decide to go this route. 

This is a little more complicated than just plugging it in and installing, which may very well work without issue, but I've found dual Sata drives in a dual boot situation to be troublesome.  If it were me, I'd put windows and ubuntu on one HD, then use the second hard-drive as a shared drive between them. That would be even more work I think. ;)

---

### Post by jfl on 2008-01-11
First you have to install the new hardrive either as a slave (jumpers in back) or as master on the other IDE channel if it is free.
Then run the Live CD install; when you get to the partition screen choose "manual". On the next screen, create an ext3 partition mounted as root(/), another as "swap" twice the amount of RAM is a good size ; I like to have my /home directory in a separate partition but you don't have to. Leave the rest blank for your Windows partition. You can always configure it later.
That's basically it.
Good luck and enjoy Ubuntu !!!


Art posted a much more complete answer while I was typing ...

---

### Post by L1nchp1N on 2008-01-11
I had an issue that was almost similar when I first tried to install Kubuntu to dualboot with XP.

 I put a new SATA drive in, figuring it would be easier to install Kubuntu to that than partition the main drive.  I installed Linux, got that running fine (till I played with something and discovered that I really shouldn't have .. :D ), however trying to mount the Windows drives so they could be read  managed to corrupt the XP install so that it wouldn't boot, and all the usual fixes ( fixmbr, fixboot, repair, etc) didn't work.

 One XP reinstall later, I'm about to try installing Kubuntu again onto the new drive.  Anyone have any idea's or tips and tricks on how to not break things next time?

---

### Post by stringer630 on 2008-01-11
Thanks for the advice. I think that this is my best option becuase reinstalling windows is not an option.
> **Arthur Archnix said:**
> 
Once you're installed and up and running, plug in your windows hard-drive (leave Ubuntu hard-drive where it is) and then add Windows to your grub options. I can explain this step as well if you decide to go this route. 

If you could explain the steps to add windows to my grub options, or point me somewhere that will, it wouldl also be great help.

Thanks again

---

### Post by Arthur Archnix on 2008-01-11
From ubuntu, in a terminal,
```
gksudo gedit /boot/grub/menu.lst
```
Then add the following, below the other three entries that are there (ubuntu, recovery, memtest)
```
title           Microsoft Windows
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```
You may need to change those numbers by "root  (hd#,#)" Offhand, I think it's going to be "root  (hd1,0)". We can troubleshoot this later if need be.

---

### Post by stringer630 on 2008-01-11
OK wil give that a go then. Got to wait for the hardrive to arrive now lol, should be here monday.

Any good places to get some info on what grub is, how it works, that kinda stuff. Just for my own knowledge as im planning to get more into linux

---

### Post by Arthur Archnix on 2008-01-11
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

Good luck with the install.

---

### Post by stringer630 on 2008-01-11
Thanks for the help. Hope all goes smoothly and will check back with an update ;)

---

### Post by stringer630 on 2008-01-16
Ive just started the installation and have a few questions. Not sure if ive set the partions the right way. Please see the screenshot below:

[[IMG]http://img142.imageshack.us/img142/4458/screenshotma5.th.png[/IMG]](http://img142.imageshack.us/my.php?image=screenshotma5.png)

Also, how do I add the partition that is to be shared between ubuntu and windows? Do I just make the  mount point /mnt/shared? If so I don't get the ntfs option.

Thanks

---

### Post by Arthur Archnix on 2008-01-16
Looks good. For the shared partition you have it exactly right, create a mount point called /mnt/storage or /mnt/shared or whatever you like, and format it as ntfs (not ext3).

That's the live cd which I've never really used, so I can't tell you exactly what you'll see when you try to change the partition type. If you're in the middle of an install, and using the live cd, fire up pidgin (>applications >internet >pidgin) and create an irc account. Then when the box comes up saying you've logged in successfully type /join #ubuntu

This will take you to the live chat-room where people can answer your questions on the spot.

---

