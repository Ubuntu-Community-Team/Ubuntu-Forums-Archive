---
title: "[SOLVED] out of memory"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by loren41 on 2008-04-13
After trying to remove several unwanted appls, I was forced to reboot.  Now I can't login because I am out of memory.  Any advice?

---

### Post by tamoneya on 2008-04-13
can you post the output of ```
sudo fdisk /dev/sda
```Replace /dev/sda with whatever your primary drive is.

---

### Post by loren41 on 2008-04-13
I'm afraid I am too much of a newbie.  I tried rebooting in GRUB using the restore option (Ubuntu 6.06) which gave me a command line, but I don't know the name of my primary disk.

---

### Post by tamoneya on 2008-04-13
okay just post the output of ```
sudo fdisk -l
``` That will give us more or less the same information.  Note that is a lower case "L" not a "1" of an "i".

---

### Post by loren41 on 2008-04-13
Disk /dev/hda: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot   Start       End          Blocks        Id      System
/dev/hda1              1      391       3140676        83     Linux
/dev/hda2          734      789         449820          5     Extended
/dev/hda3          392      733       2747115        83     Linux
/dev/hda5          754      789         289138+     82     Linux swap / Solaris
/dev/dha6          734      753         160587        82     Linux swap / Solaris


Sorry, but I had to type this into my desktop (Windows) pc.

---

### Post by mister_pink on 2008-04-13
At what point does it give you the out of memory error? And what did you uninstall? Is that definitely all you did in that sesson?

---

### Post by loren41 on 2008-04-13
I was trying to uninstall some education programs that I installed in error.  I was given warning that I was nearly out of memory and thought I was removing, but was in fact installing.  After discovering the error I tried to uninstall them and after running for several hours, I rebooted.

During reboot, I was prompted for my userid and password.  The response message said that there was no room left to build an authorization file, thus leaving me locked out.

---

### Post by mister_pink on 2008-04-13
Tried uninstalling some stuff or deleting some rubbish from the recovery console? This should gain you some space:

apt-get clean

---

### Post by forestpixie on 2008-04-13
when you do get back in this will give you an idea of how much room you have

```
df -h
```

---

