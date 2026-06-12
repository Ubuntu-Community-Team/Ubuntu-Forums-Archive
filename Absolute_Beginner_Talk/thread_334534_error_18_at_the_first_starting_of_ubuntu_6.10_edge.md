---
title: "error 18 at the first starting of ubuntu 6.10 edge"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by debianLAM on 2007-01-09
--------------------------------------------------------------------------------

i have installed on my machine ubuntu 6.10 edge 
all a steps of installation passed without a probleme until the cd rom ejected but when the system rebooted an error appears on screen like this :

GRUB LOADING STAGE 1.5

GRUB LOADING PLEASE WAIT 
ERROR 17
and no thing appears on screen 

after that i reinstalled ubuntu and always the same error appear but in this case i have this one :
ERROR 18 

i tried to run command sfdisk on shell mode but no thing happenned and when i saw the main directory i found this directory /sbin /root /etc ........but this directory i dont found it /boot 


please help me to solve this problem


debianlam

---

### Post by xyz on 2007-01-09
Hi,
Can you please post the outputs to the following command lines:
```
sudo fdisk -l
gksudo gedit /boot/grub/menu.lst
cat /boot/grub/device.map
```

---

### Post by sardion on 2007-01-09
I agree, the output of those commands would be quite useful.

Did you install ubuntu on the entire drive or set up dual booting?

How old is this computer?  Older BIOSes sometimes require that the /boot stuff be in the first part of the drive so if you did a dual boot and put ubuntu at the "end" of the drive that could cause this.

---

### Post by debianLAM on 2007-01-09
yes i have installed ubuntu on the entire of the disc but when i used the cd installation to enter to shell mode and i  type this command 

$sfdisk -l/dev/hda
an error message that have appeare said  some thing like this unknown command 



$ls 

/sbin    /root   /mount  ......
all those directories appears 


but a /boot  directory doesn't  appears  

thanks for all your help 

debianLAM

---

### Post by xyz on 2007-01-09
Sorry I wasn't clear! Copy and Paste this in a terminal:
```
sudo fdisk -l
```
Pressing the Enter key will ask for your password which you'll obviously type in.
Now on Enter again.

What you'll see now is the output of the "sudo fdisk -l" command line. So simply copy/paste this output along with your next post.

Run the 2 other command lines ONE AT A TIME in a terminal:
```
gksudo gedit /boot/grub/menu.lst

```
```

cat /boot/grub/device.map
```
And now post the outputs of those 2 command lines also along with your next post.
Let us know...

---

### Post by debianLAM on 2007-01-10
i cant run all those commande on my shell because i am running a shell from ubuntu disk that it is of ubuntu installer  main  menu  
and the grub menu it never appear just only appear  grub start  error 18

---

### Post by xyz on 2007-01-11
Take a look at this and see if it makes any sense to you:
[Grub Errors 17/18 explained]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5")

---

### Post by sixsigma on 2007-01-14
I have the exact same experience.

sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot      Start   End         Blocks            Id     System
/dev/hda1  *          1        9541       76638051       83     Linux
/dev/hda2             9542   9729       1510110          5      Extended
/dev/hda5             9542   9729       1510078+       82     Linux swap / Solaris

There is no such file as /boot/grub/menu.lst

$ls /boot

abi-2.6.17-10.generic   System.map-2.6.17-10-generic
config-2.6.17-10-generic   vmlinuz-2.6.17-10-generic
memtest86+.bin

==================
I only put ubuntu 6.10 on this machine (not a dual boot machine).  I installed by default, and wipe the entire harddrive for the installation.

Last few times I got grub error 17, now I got grub error 18.

---

### Post by sixsigma on 2007-01-14
Based on the grub ERROR 18 help link above, I manually created the partitions and set the boot partition to be 6GB (less than 8GB).

Everything is working now.

---

