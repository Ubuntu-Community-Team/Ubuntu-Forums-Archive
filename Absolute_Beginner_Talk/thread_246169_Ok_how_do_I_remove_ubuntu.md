---
title: "Ok how do I remove ubuntu?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by priest15 on 2006-08-28
I can't get into windows now that i've installed unbuntu so how do I remove it or format the drive that its on so that it'll be gone from my pc for now?

---

### Post by L_o_N_e_R on 2006-08-28
just delete the partition........

but wait hwo did u install ubuntu? how did u format partitons"(default was to start over hd[delete everything])\


GURB bootloader is suppose to config so u can boot ubuntu and windows if windows is still there

---

### Post by priest15 on 2006-08-28
I installed it on a completely seperate empty HDD

---

### Post by L_o_N_e_R on 2006-08-28
ok good i thought u deleted ur win partiton lol


sry man i cant help u with that....

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

read that :p its in there somewhere

---

### Post by cstudent on 2006-08-28
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by szf on 2006-08-28
You went to a bit of effort to install Ubuntu - only to remove it when you couldn't boot to Windows?

If you wish to boot both, I suggest search these forums for grub + chainloader - otherwise google "fix mbr" since grub will overwrite the _M_aster _B_oot _R_ecord on installation.

---

### Post by Toxicity999 on 2006-08-28
Well if it's on its own hd switch the Windows HDD to the Primary and the Ubuntu to the slave and format the Ubuntu HDD in the Windows environment you're familiar with. Easier than learning something new for something you're getting rid of anyway.

---

### Post by priest15 on 2006-08-28
Look ubuntu looks interesting, but being that I have a USB keyboard I can't choose what to boot in dos. So for now I need to be able to get into windows to do my normal thing.

---

### Post by confused57 on 2006-08-28
> **cstudent said:**
> [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Use the above method to get your Windows mbr repaired, and since you have a 2nd hard drive, you might want to consider setting up a dualboot this way:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Toxicity999 on 2006-08-28
yea... I mean Don't think we will refuse to teach you how to 'remove it or anything. But if you need to use windows more than actually remove ubuntu just set up a dual boot. Not as hard as you may think! Otherwise restore the MBR on your windows harddrive set it to main and format the slave. Assuming the Slave contains Ubuntu alone and not anything else you may need.

---

