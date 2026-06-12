---
title: "Save Ubuntu"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-02-21
my system has a problem...... my friend has put Mandriva on my laptop and i have ubuntu on it. So we partioned it and has 2 partions. Now partion editor says there is no partions on my harddrive but once i restart is goes to Mandriva. Even the Grub loader will not let me go to ubuntu

---

### Post by jan quark on 2008-02-21
try to restore the grub loader:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

don't know exactly what has happened 
can you please post some more info

---

### Post by masque7 on 2008-02-21
I think [[COLOR="Blue"]this[/COLOR]](http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva) may help you (or at least help you to understand what's happened.) 

If not, google: *dual-boot 2 linux distros*

---

### Post by stoodleysnow on 2008-02-21
When you installed Mandriva you probably got the partitioning wrong. Did you tell Mandriva to use GRUB or LILO during boot when you installed it?

---

### Post by gecko113 on 2008-02-21
I told it to use grub with text loader. And for more info: Once i open Gparted it reads my hard drive as all unallocated space on it. But if i go through the back door on it i can still access ubuntu in low graphics. But the weird thing is when i start up it Mandriva loads. is there a way for me to get rid of it with out reinstalling Ubuntu

---

### Post by Joeb454 on 2008-02-21
can you post the output of the following commands (run the from the terminal :))

```
sudo fdisk -l
``` that's a lower case L :)

and ```
cat /boot/grub/menu.lst
```

We might be able to keep both.

The first command will tell us if Gparted is lying ;)

---

### Post by jeffus_il on 2008-02-21
Do you remember using a different disk label with mandriva? that could result in the symptoms you have.

---

### Post by gecko113 on 2008-02-21
Well i currently Save Ubuntu and now i have no access to Mandriva. I just did a grub rescue and it saved ubuntu

---

### Post by gecko113 on 2008-02-21
But Gparted is still Lying to me since i'm on  Ubuntu on my hard drive not the live disk now thanks for the help with that problem but now i have the problem with Mandriva still being on my partion and having no access to it. I want to uninstall it right now and look more into it for my laptop. How would i uninstall it without accessing the partion and deleting it.

---

### Post by jeffus_il on 2008-02-21
I think you may have each system using a different disklabel or partition table. There are different types of disk partitioning schemes, the most popular being msdos, there are also solaris, bsd, and many more. If diskdrake used a different partition table to gparted then you would have the kind of problems you describe.

---

### Post by jeffus_il on 2008-02-21
Here is someone else with the same problem.
[http://ubuntuforums.org/archive/index.php/t-652178.html](http://ubuntuforums.org/archive/index.php/t-652178.html)

---

### Post by gecko113 on 2008-02-21
What would be the best way to fix this

---

