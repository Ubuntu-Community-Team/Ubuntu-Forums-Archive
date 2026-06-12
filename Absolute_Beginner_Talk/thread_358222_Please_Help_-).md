---
title: "Please Help :-)"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by CA55IUS on 2007-02-10
Bit of help please for a newbie. :KS  :confused: 

I want to try Ubuntu, I have never really tried linux before, but on my old pc I booted up with a Ubuntu CD and it looked pretty cool.

**I HAVE A PROBLEM.  I have 3 SATA Harddisks, 2 are Western Digital and I have set them up as a Raid 0 array using a nvidia force driver(as my motherboard is a asus P5N32-E SLI PLUS NVIDIA 680i chipset).**
[B]
The other one is a Samsung- a SATA drive also- no raid.  Both the 2 Western Digital and Samsung Drives are partioned.  Making 2 partions on the Western Digital(which are now classed as one because of the Raid 0). And 2 on the the Samsung.
[/B]
**_I want to install unbuntu onto the samsung, when i boot from the cd that I got from Unbuntu, I get to the menu, goto install and then it says something about a KERNAL error and crashes, it never installs._**

I set it to boot from the dvd drive(which it does), but it cant install.

I have tried a opensuse dvd as well as a linspire and all fail right at the start of installing, loading, they wont even load.

I am now downloading the latest unbuntu, i will try that, what do you think the prob is tho.

It is set to boot dvd first, then the raid drives(western digital), then the smasung if needed.

Im confused please help

Thank you :guitar:

---

### Post by equal on 2007-02-10
wow this is a bit beyond what we usually answer in the absolute beginners forum. You might want to ask in the Hardware & Laptops section.

---

### Post by CA55IUS on 2007-02-10
Thanx, I have raised a post there now :)

---

### Post by risbac on 2007-02-10
I think the RAID is the problem, but that's just a guess...

You can try to have a look using your motherboard reference and "RAID" in those forums.

If you can't find anything, here is what I would try, coz we all want to be proud of our installation, not matter what problem we can meet. We have the full control on the OS, so let's try:

unplug both RAID hard drives, and try to install. The computer should not "see" anymore the RAID, so no more problem with this if it's really the problem. Install Ubuntu on the Samsung. Then replug the harddrives for the Raid, and reboot. Then you can try to see if Ubuntu sees the RAID partitions, and mount them.

I had more or less the same kind of problem with my Asus motherboard. Finally I got rid of the RAID, performances were not that much better anyway. 

Anyway, RAID is maybe not your problem, no need to write an essay on it.

---

### Post by CA55IUS on 2007-02-10
Thanx m8, ill give it a try. :) 

Sorry the post was a bit long, I do go on a bit lol, just wanted to make sure every1 was aware of the setup.

Hopefully if I unplug the raid install ubuntu on the samsung, then reset with them plug in it will all be cool.

Thanx

---

### Post by carverj on 2007-02-10
> I have tried a opensuse dvd as well as a linspire and all fail right at the start of installing, loading, they wont even load.
Just curious, is this a brand new system or have you installed an operating system on this machine previously?

---

