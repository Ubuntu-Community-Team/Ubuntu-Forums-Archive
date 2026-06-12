---
title: "Please help... I'm in a complete mess."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by spacy_goldfish on 2007-10-29
A bit nervous to expose my absolute newbie-ness to the whole world...
I think I messed up my system while trying to fix it after I upgraded from 7.04 to 7.10.  

Now all I want to do is a fresh install of 7.10. I have my personal files already backed up and I don't even care about any setting or just anything that might be lost during the process. 

However, I have problems...

1. I can't install anything anymore whatsoever. Every time I try to install or update anything, it gives me an error message saying some package contains empty filenames. (This is the beginning of the whole mess I've been dealing with.)

2. My dvd/cd drive isn't working. It might be physically broken (it's a 4 years old hand-me-down), but I think my system is so messed up it's just not working right. I've been hearing the drive making a constant noise as if the system is trying to read a disk (even when there's nothing in the drive). 


So I've been trying to install 7.10 using the method described here [https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28install%29](https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28install%29)

Since I did not have Gparted installed I'm trying to do things in the command line. I originally installed 6.06 from a Live CD, and upgraded to 7.04. There seems to be a separate partition that has been storing 6.06 on my HD. I have no clue how this happened, but is it possible to just delete whatever that's on it and then use it as a new partition?

Here's the output of fdisk -l...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26d8c60a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9872    79296808+  83  Linux
/dev/sda2           19088       19457     2972025    5  Extended
/dev/sda3   *        9873       19087    74019487+  83  Linux
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris
/dev/sda6           19088       19272     1485949+  82  Linux swap / Solaris


/dev/sda1 is the partition I'm trying to use.  I even deleted it and created a new one on the same spot. But it doesn't work. When I get to the point where I mount it, the system tells me it's already mounted. So I try to unmount it, then it tells me it's not mounted. What is going on? I want to fix it but don't even know where to start. Please Help!

---

### Post by Hospadar on 2007-10-29
can you boot from the livecd (the 7.10 or any other?) or boot from any cd for that matter?  If you can boot from other cds, but not 7.10, I would first suggest a re-download and re-burn (at a slow burn speed) of your 7.10 cd.

What exactly is the error you get when you try to install stuff? (If you crashed or screwed something up mid-upgrade I would bet it's not really resolvable, but it might be completely unrelated)

You might also try getting a gparted livecd (you can get a .iso from the gparted website) and use that to format your drive.

---

### Post by spacy_goldfish on 2007-10-29
My cd/dvd drive isn't able to read anything, even though it's making a noise like it's trying to read something.

Here's the error message I get...

E: /var/cache/apt/archives/language-pack-gnome-en-base_1%3a7.10+20071012_all.deb: files list file for package `language-pack-gnome-en-base' contains empty filename

---

### Post by mistergq on 2007-10-29
I think the question was can your computer boot from a CD, not if it can read the cd once you boot up Gutsy.  Make sure you have the option to boot from cd turned on in your bios.

If it can boot, I would recommend getting the alternative CD version of gutsy, and install it that way.  I find the alternative cd, while not as pretty, can pretty much install on any machine.

---

### Post by spacy_goldfish on 2007-10-29
I'm sorry for having not made that clear; it won't boot from the CDs.

---

### Post by Hospadar on 2007-10-29
well If it won't boot from any cd's, I would say your cd drive is probably bad.  To make sure, I'd track down some other bootable cd's (try a windoze cd, or cds for another linux distro) also try totally disabling hdd boot in your bios.

If it is the case that your cd drive is totally shot, then that would be the place to start for fixing.

---

### Post by Hospadar on 2007-10-29
You might look into installing off a usb drive if you have a big enough one (~1gig) have a look here [https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28installation%29%7C%28usb%29]("https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28installation%29%7C%28usb%29") 
on how to do that.  The guide is for 6.06, but it will probably work for later versions.  If not you could always either try 6.06 and upgrade again (ick) or google around for how to install 7.10 off a usb drive (better)

To do this you'd need another machine you can use that would work probably (or extract the files from a downloaded 7.10 .iso since your cd drive is apparently busted)

Edit:
Also, you might look into puppy linux or dsl (damn small linux) as I believe they have installations designed specifically for usb sticks.  This might at least get you to a point where you can get your partitions straightened out and do some more testing of you cd drive.

---

### Post by spacy_goldfish on 2007-10-29
Thanks Hospadar, I tried all the bootable CDs I had and none worked. I guess the cd drive is shot. I think I'm gonna buy myself a new (yay!) cd drive.

---

### Post by spacy_goldfish on 2007-10-29
Thanks Hospadar, I tried all the bootable CDs I had and none worked. I guess the cd drive is shot. I think I'm gonna buy myself a new (yay!) cd drive. Thanks!

---

