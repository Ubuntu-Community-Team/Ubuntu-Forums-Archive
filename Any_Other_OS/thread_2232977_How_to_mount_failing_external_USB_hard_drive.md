---
title: "How to mount failing external USB hard drive"
date: 2014-07-05
forum: Any Other OS
---

### Post by jimster99 on 2014-07-05
Hello! I carelessly dropped my 3TB external USB hard drive on the ground and damaged it. I have been backing it up using Gnu DD Rescue for the past week and am about 70% of the way through the recovery processs (with a surprisingly small number of errors). However the drive is getting more and more weak (it now takes 30 seconds to 1 minute for Linux to find the drive) and now most of the time ddrescue says it "cannot find" the drive, and essentially terminates the recovery by marking the rest of the unrecovered data as faulty, at which point I have to power-cycle the drive at least once, and sometimes many times, before I can get DD Rescue to resume.

Now it may be that the drive has finally died (and it is certainly on the way out). However the drive spins up and makes a normal noise (no "click of death") and is found by Linux - and I can see the drive and the partition using the lsblk command. Sometimes I can also actually restart DD Rescue and it copies a bit more data (2GB in the most recent run today) from the drive before stopping. When I run the "dsmesg" command I get a bunch of error messages saying there was an "input/output error" drive from the drive. Fdisk and Gsmartmon both crash and then Fdisk is often unable to see the drive.

I feel the issue may be that when I start the computer, Linux interrogates the external drive, finds some errors and then eventually gives up. So, I want Linux to wait a *lot* longer when starting up the drive before aborting due to errors. Is there any way of doing this? Am I living in a fantasy land thinking this might make things work?

I am essentially a total beginner with Linux (although I am learning fast). I did find mention of a "USB Delay" command, but am not sure how to use this.

Any help gratefully received. Thanks!!!

PS I am using Mint Linux v 17 32 bit if that makes a difference

---

### Post by coffeecat on 2014-07-05
> **jimster99 said:**
> I am using Mint Linux v 17 32 bit if that makes a difference

It does. The first two sections are for official Ubuntu flavours only. But you are very welcome to ask your questions here, and we have a special section for other distros, and I've moved your thread there.

But to your problem - I would go about this another way. If there is damage, which is more than likely, it could be to the actual hard drive, or to the circuitry of the USB enclosure, which latter could lead to the I/O errors you describe. Or, worst case scenario, to both. In the hope that the damage is confined to the enclosure circuitry, I would remove the HD from the enclosure and test it by putting it in another enclosure. Do you have another USB HD enclosure?

Failing that, or perhaps in preference, if your machine is a desktop rather than a laptop, you could simply connect the bare drive directly to one of the motherboard SATA headers. 

Either of those a possibility for you?

---

### Post by jimster99 on 2014-07-05
Thanks - I did consider removing the drive from its enclosure and connecting it to a USB-SATA connector. However, I want to do this as a last resort given that its a 3TB drive and has a GPT partition, which I am worried will not be handled properly by the replacement connector.

So currently my aim is to find a way of more robustly mounting the drive in Linux, and allowing to try more times before it gives up (if possible)!

---

