---
title: "if liveCD worked will install work? &amp; dual-booting (Solved)"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-18
hi, i tried the Live CD a few days ago and it worked fine apart from my speedtouch modem which i expected. so if the Live CD worked OK does that mean the install will behave in the same way?

also, i want to dual boot with XP, how should i partiton my drive? should i leave unallocated space, make a linux Ext2 or Ext3? and do i need to make a Linux swap partition as well? thanks

---

### Post by 23meg on 2005-11-18
Most likely it will work. You can also expect some things that didn't work quite the way you wanted them to work better, since you can tweak them after install. 

If you'll be installing XP from scratch, install XP first and leave unallocated space. You'll do the rest of it with the Ubuntu installer.

---

### Post by Danielle on 2005-11-18
thanks, 23meg. i'll diffinately go ahead with it then.  i just did a XP reinstall about 3 weeks ago and i have the HDD partitioned (C, E) with alot of data on both partitions already. i'll go and get rid of what i can and make the E partition as small as possible meaning Ubuntu will go on a new partition - F will that be OK if i make sure there's at least 13GB for Ubuntu to be installed on? thanks.

---

### Post by Danielle on 2005-11-18
hi, can i ask another question? which kernel is being used ATM? is it still the Hoary 2.6.10 build? i'm just asking because of my modem which i don't think will work with the default settings. it's the speedtouch 330 USB ADSL Modem (UK)

i got the kernel build from [here](http://ubuntuforums.org/showthread.php?t=44763) oh, i see now, you don't have cute names for the kernels, not as geeky as i thought, Hoary runs in Ubuntu somewhere, what's Hoary? thanks

---

### Post by 23meg on 2005-11-18
13GB will be more than enough, sure. Do not create a separate partition though, just leave empty space after your two windows partitions and the Ubuntu installer will take care of creating the partition.

The Breezy (5.10) kernel is version 2.6.12. There's a chance that some of your devices that didn't work with the Hoary kernel will work with this one. Hoary is the codename of the previous version of Ubuntu (5.04).

---

### Post by Danielle on 2005-11-19
hi, thanks for the help. i have made 7.1GB of free space available at the end of my HDD. i want to install Ubuntu now. but, i want it to be dual-booting with XP, partly because i'll need to download files to get my modem to work with Ubuntu using XP. how do i make it dual-booting? do i just install it on the free space? is that it? or do i need to do something with Grub? thanks :)

---

### Post by Danielle on 2005-11-20
thanks for the help, 23meg. i just installed it and the dual-boot works fine.

---

