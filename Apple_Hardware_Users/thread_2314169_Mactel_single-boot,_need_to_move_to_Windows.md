---
title: "Mactel single-boot, need to move to Windows"
date: 2016-02-18
forum: Apple Hardware Users
---

### Post by ryan-n-waggoner on 2016-02-18
I have a Mac Mini (6,1), which I single-booted to Saucy a number of months ago, and recently updated to Trusty. In the time since I did this, my needs for the computer have changed, and I'm needing to run Windows 7 on it. The problem I'm running into is that I can't seem to boot from my USB DVD drive as I did when I installed Saucy -- it seems the Mac boot-up options no longer function, and since it seems Macs run EFI rather than BIOS, I'm kind of at a loss for what to do here.

I did manage to edit my grub file so that I can access a command line and see what I can do, but the Mac does not seem to be mounting the USB DVD at all.

I have verified that my Windows 7 install disc does work (I was able to boot to it on my Asus laptop), and the USB DVD drive itself also works.

Any help would be greatly appreciated.

---

### Post by newbie-user on 2016-02-19
So holding down the option key while booting doesn't bring up a boot menu? Because that should be available before the OS starts.

---

### Post by ryan-n-waggoner on 2016-02-19
Holding down the option key DOES bring up a boot menu. However, it identifies the hard disk as Windows, and still fails to recognize the USB DVD. I even tried waiting until I was in the boot menu to connect the optical.

---

### Post by ryan-n-waggoner on 2016-02-19
I'm writing it off as something funky with my Win 7 install disc -- on a whim I grabbed a Puppy Linux live CD that I had laying around, put it in the optical, and held down C as it was booting, and I was welcomed with monochromatic ASCII renderings of puppies.  So, I guess the issue I was experiencing truly IS unique.

Now, off to figure out how my Windows install disc can work on one system but not another.

---

### Post by ryan-n-waggoner on 2016-02-19
Also, +1 @newbie-user -- yours was the answer that sent me down the path to figuring this out.  Thanks.

---

