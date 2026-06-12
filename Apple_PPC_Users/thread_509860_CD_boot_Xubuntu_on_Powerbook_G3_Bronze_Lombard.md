---
title: "CD boot Xubuntu on Powerbook G3 Bronze Lombard"
date: 2007-07-25
forum: Apple PPC Users
---

### Post by gvigorus on 2007-07-25
Hi folks. I know this post might seem repetitive, but I seem to have tried everything i could find still no results.
Basically, I have a Powerbook G3 Lombard with 400 Mhz chip and 512 MB RAM 6GB HDD and currently running OS X 10.2 Jaguar
I really want to wipe off OS x and install Xubuntu as the sole OS on this Lombard, given that this is an old machine and Xubuntu will most likely to run the best on this old hardware.

I followed Xubuntu installation guide for PPC and also followed all guides on checking MD5 and burning ISO images. I tried booting my machine per booting instructions holding "C" down but CDROM does not read the burned ISO disk. Also, when In OSX the CD won't mount if inserted into CDROM. Burned CD is visible under Windows and burned in Windows with tool suggested in Burning ISO guide for PPC. I think it's called something IntraBurner or something.

I also tried doing a HDD boot, but still no success. When I get to Yaboot boot: prompt and enter Kernel, i get error message that file is corrupt of incorrect or something.

Can someone please share what I should do to put Xubuntu on this Lombard? I don't even care how to boot, just whatever to get the Xubuntu to boot and run. 

Thanks for any help. This is really getting frustrating and especially being a newb at this is more so frustrating.

---

### Post by pxwpxw on 2007-07-26
Heres an outline how to do a network or hd-media install without the CD

[http://ubuntuforums.org/showthread.php?t=390770]("http://ubuntuforums.org/showthread.php?t=390770")

But first you should confirm that the CD drive is indeed unusable, can you mount any other cd from macosx, and can you run macosx installer dvd (not sure if the Lombard has DVD). Can you get someone to check the cd in another mac and make sure it is a ppc cd, not an i386. Is it xubuntu704 feisty.

---

### Post by gvigorus on 2007-07-26
Hi Px! I've read a lot of great responses from you on other threads, you are so resourceful!!!
My Lombard has a CD/DVD ROM. It can mount Mac OSX boot disk, that's how I got 10.2 on it. I think it doesn't like burned Feisty Xubuntu for some reason. I've also tried some other PPC bootable burned CDs in the past, they never worked either.
The ISO is indeed PPC. Here's where I got it from:
[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/)
(the one i downloaded was the Desktop CD titled Mac (PowerPC) and IBM-PPC (POWER5) desktop CD)
Tested MD5 and burned with these instructions on an XP machine:
[https://help.ubuntu.com/community/BurningIsoHowto?](https://help.ubuntu.com/community/BurningIsoHowto?) Software is called Infra Recorder and I burned just like in instructions from ISO image, not just data.
RadicalSpud said that CD might not boot if burned above X4 (mid page [http://ubuntuforums.org/showthread.php?t=487256&page=11](http://ubuntuforums.org/showthread.php?t=487256&page=11))
I burned my ISO at about X8 but I'll try burning it as slowly as possible to see if that helps.
I also saw your post on that same thread to me about different sets. I indeed have CD installer set. So, to boot from HD i need HD set. If my slowly burned CD install does not work I'll go for HDD media set.
Thanks for all the help Px! Hope I can get this thing to work just like Youngwun did:)

---

### Post by gvigorus on 2007-07-26
Fro reading about netboot, i see that the only thing i need is to place those four files in rood directory.
So, is VMLINUX file essentially an executable linux kernel that can be booted with Yaboot? I guess once VMLINUX boots then I can load XUbuntu Faisty, right?
Thanks for helping out!!!

---

### Post by gvigorus on 2007-07-26
Px, in your post [http://ubuntuforums.org/showthread.php?t=390770#4](http://ubuntuforums.org/showthread.php?t=390770#4)
where you talk about network installation. I downloaded the four files to my HDD root directory and looked at the yaboot.conf file. It was for Ubuntu. Will this also work for Xubuntu? I mainly want Xubuntu because of my old hardware. Thanks again Px!!!
Also, after I boot from OF into Yaboot and enter Install, will that start erasing my HD and reformating everything? At what point do I want to backup?!

current links yaboot.conf file starts with:

## This yaboot.conf is for hd-media booting only, do not use as reference.
## Ubuntu 7.04 PowerPC

As you can see it's Ubuntu 7.04 But where you I get Xubuntu 7.04 or is this the same process for either Ubuntu or Xubuntu?

---

### Post by gvigorus on 2007-07-27
Got Xubuntu to work!!! It took a while but I'm fully on now!
OMG this is so awesome!!! Thanks for all the tips:)

---

