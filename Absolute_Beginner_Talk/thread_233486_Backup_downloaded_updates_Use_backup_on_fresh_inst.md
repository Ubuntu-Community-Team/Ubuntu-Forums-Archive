---
title: "Backup downloaded updates? Use backup on fresh install?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Boju! on 2006-08-10
Hi,

I need to replace my video card as its old and causing instability in windows and ubuntu (99% sure its the AGP card - GeForce4 ti4600). I have absolutely no idea how linux/ubuntu handles hardware changes so here is my plan of attack filled with questions.

After searching the forums for half a hour I THINK that all the updates I have downloaded are in this directory?
/var/cache/apt/
Is this true?

If so can I
1) burn /var/cache/apt/ directory onto a CD/DVD
2) change video card
3) reinstall ubuntu from the live CD
4) copy all the files from the CD/DVD into /var/cache/apt/
Will the update manager then
A) understand that those files have not actually been installed yet?
B) See and install those updates without downloading them again?

Am I going about all this the wrong way? Is there a possibility that I can just swap video card and linux will figure it all out automatically?

Or is there a repair option or similar whereby I don't have to wipe the drive and reinstall from scratch from the live cd - rather it will repair itself?

Please help :)

---

### Post by arjun.shankar on 2006-08-10
Put in the new card and reboot. If you don't have the required kernel modules already, you can get them usind apt or aptitude or synaptic as per your choice.

---

### Post by yopnono on 2006-08-10
> **Boju! said:**
> have downloaded are in this directory?
/var/cache/apt/
Is this true?
Yes. (Well the files are in /var/cache/apt/archives)
> Will the update manager then
A) understand that those files have not actually been installed yet?
B) See and install those updates without downloading them again?


All you have done is that you have moved the install files to the cache.
From there you can use synaptic and install the files, and it will use the cache = no need to download them, since you already have them in the cache.

---

### Post by MrHorus on 2006-08-10
> **Boju! said:**
> Am I going about all this the wrong way? Is there a possibility that I can just swap video card and linux will figure it all out automatically?

Sort of.

Download the latest nvidia drivers (if you are staying with nvidia) and kernel headers.

Just take out the old graphics card and put the new card in.

Once you reboot it is likely that your xserver config will be nivalid and X will not start, leaving you with a command prompt.

At this point you will want to login and install the driver, at which point you will be asked to reconfigure the xserver.

After this, all should work!

---

