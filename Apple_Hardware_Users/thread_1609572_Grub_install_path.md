---
title: "Grub install path"
date: 2010-10-30
forum: Apple Hardware Users
---

### Post by afzalnaj on 2010-10-30
Hi,
So I've got my Ubuntu and Windows dual boot setup running but both are on separate physical hard drive.

The ubuntu hard drive boots first (with GRUB) and allows me to choose which OS to boot.

The problem is that when I actually installed Ubuntu, it didn't boot first. Now when I update the kernel, it reinstalls GRUB to hd1 (which is my Windows drive)and runs update-grub, which messes a bit of my grub.cfg

Is there any way to stop this from happening? Perhaps a file that stores where GRUB is installed when Ubuntu was installed, so that I can change it and then GRUB will not be installed in hd1 but in hd0 like it should be?

Thank you

---

### Post by ajgreeny on 2010-10-30
I am pretty sure update-grub after a kernel update will simply update grub wherever it is; I certainly don't think that updating the kernel will suddenly change the disk on which grub is installed by moving it to the other hard disk.

Let's be sure what we are dealing with here, so download and run the Boot-info-script shown in my signature and attach the Report file back here.

---

### Post by afzalnaj on 2010-11-27
Already have the boot script, anyway I'm marking this as solved because somehow (since the last update) it's been installing on the correct partition (to my utter surprise)...and if it was something I did/didn't do then damn lol.

I must be drunk to create this topic in "Apple users" :s 

Excuse my mistake.

Thank you @ajgreeny. I use that script a lot already :p

---

