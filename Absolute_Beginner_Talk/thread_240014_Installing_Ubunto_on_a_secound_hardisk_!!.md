---
title: "Installing Ubunto on a secound hardisk !?!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Data-Base on 2006-08-20
Hello,

I have problem not only with Ubuntu, i have it with SuSE too !!

I have Windows XP installed on a hardisk (WD SATA Raptor - sdb)
and I installed Linux on another hardisk (WD SATA Raptor - sda)
with the second hardisk, I already used 12 GB from it's space for games (NTFS Partition) and I'm trying to install Linux on the empty space what is left, 


installation went OK (in both SuSE or/and Ubuntu) but when I boot, it's start Windows as there is not Linux installed (no boot menu).

to access linux, in SuSE I start Linux by the DVD (there is an option to boot Installed Linux from the SuSE's DVD for fixing problems or for any other reason) but this is not what I want.

I'm not good in the MBR, and all these stuff.

note: I'm not trying to have both Ubuntu or/and SuSE installed in the same time, just a normal dual boot Windows/Linux

any help ?

---

### Post by noof on 2006-08-20
The thing is that your computer is set to boot from the windows disk in the bios. The easiest solution is to change in the bios so that the computer boots from the linux disk instead. Then you can choose ubuntu or windows when it boots.

---

### Post by Data-Base on 2006-08-20
in the boot I can press F8 (function build in Asus Motherboards) and it will list all the hardisks and the Dvd Drives then I can chose which one to boot from I did test the Linux Hradisk and it show that there is no OS on it (invalid .. bal bal bal) !!!!

---

### Post by noof on 2006-08-20
You need to install grub to the MBR of the linux disk. I don't have access to a grub-box atm, so I can't check how you do it.

*edit* 
[http://ubuntuforums.org/showpost.php?p=1396158&postcount=2](http://ubuntuforums.org/showpost.php?p=1396158&postcount=2)
might do the trick

---

### Post by Data-Base on 2006-08-20
I just may know why, but not sure

do you think because there is a 12GB NTFS partition located on the beginning of the HDD ???

---

### Post by noof on 2006-08-21
> **Data-Base said:**
> I just may know why, but not sure

do you think because there is a 12GB NTFS partition located on the beginning of the HDD ???There's no boot record on the disk at all, that's why it fails. You need to install grub to the disk.

---

### Post by Data-Base on 2006-10-04
OK i have tested to install it on the main HDD where the main Windows partition,

Ideleted windows and installed Ubuntu, when I start my PC i get **error 22**

any one know why ?

---

### Post by Old Pink on 2006-10-04
Ubunt**u** LOL.

---

### Post by msandoy on 2006-10-04
Since you have already deleted everything on your computer, there is no more damage to be made. Go into BIOS and make sure you choose the first SATA HD as the boot disk. Then you do a clean install of UBUNTU or SUSE on any of the HD's. The main thing is that Grub will by default use MBR on te first HD. After testing, and if it works, the easiest will be to install Windows first then to install linux. Windows XP normally fucks up the GRUB boot loader if it is installed second. Good Luck... :-)

---

