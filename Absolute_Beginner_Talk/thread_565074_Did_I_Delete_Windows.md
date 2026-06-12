---
title: "Did I Delete Windows ??"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by LaDeDa on 2007-10-01
I installed Ubuntu 7.04 from a CD and had a dual boot capability with Win98.
Recently, I had a screen resolution problem and decided to reinstall Ubuntu.
Now, only Ubuntu or Recovery or MemTest show up after hitting escape.
Is there an option to repartition the entire drive when installing from the CD ??
Did I delete Win98 with the reinstall and is there anyway to get it back short of reinstalling ??
TIA

---

### Post by 3rdalbum on 2007-10-01
There is an option to repartition your entire hard disk in the Ubuntu installer.

Please post the output of the following command:

```
sudo fdisk -l
```

And we'll be able to tell if your Windows is still there.

---

### Post by twist2b on 2007-10-01
one thing that you might have done is actually messed up grub if you tried to kill ubuntu... try re-installing ubuntu... i dont know though i cant understand the exact problem

---

### Post by llamakc on 2007-10-01
Do NOT try reinstalling until following the advice by 3rdalbum, please.

---

### Post by overlord.gaurav on 2007-10-01
Reboot your computer with the Ubuntu CD. Select "Rescue broken system".
When it starts copying the files cancel it. Scroll down to "Install Grub Loader".
Install it. Reboot. And it will be fixed.

---

### Post by llamakc on 2007-10-01
Not if he formatted the entire disk.

---

### Post by LaDeDa on 2007-10-01
Well, it looks like Windows is gone;

sudo fdisk -l

/dev/sda1    5968116     Linux
/dev/sda2     329332 +  Extended
/dev/sda5      329301     Linux Swap  /  Solaris

I think it's only a 6gb hard drive.

---

### Post by llamakc on 2007-10-01
> **LaDeDa said:**
> Well, it looks like Windows is gone;

sudo fdisk -l

/dev/sda1    5968116     Linux
/dev/sda2     329332 +  Extended
/dev/sda5      329301     Linux Swap  /  Solaris

I think it's only a 6gb hard drive.

Windows is gone.

---

### Post by LaDeDa on 2007-10-01
No biggie.  I had previously prepared the unit for a charity donation.  After I installed Ubuntu, it looked like fun and I could learn something new.  So, I'll keep the old dog.  Thanks for the help.

---

### Post by coolen on 2007-10-01
I've seen some horrific things happen from just clicking Next throughout the install.
All's well that ends well, I guess. I hope you enjoy using Ubuntu.

---

