---
title: "Install Ubuntu before XP how to?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by turbo63 on 2006-01-06
If I install Ubuntu before XP when I install XP will GIMP recognize it?  I have done quite a bit of reading but can't find the answer.    

Below are my plans
Use Ubuntu to partition my drive like below
1) UBUNTU partition
2) Fat 32 (to save files to from XP and UBUNTU to share)
3) NTFS (to be made by XP when I install it?)

Any suggestions or good links on how to do this?
Thanks for the help!

---

### Post by diggs on 2006-01-07
in regards to your NTFS system, you can get XP to format it as fat32. when you are setting up the partition it will give you this option. doesn't really help you out much, but hey.
The way I do it is to start with the XP disk. I ahve a 60gbhd.
soo....
15gb XP fat32
15gb ubuntu 
30 fat32 for sharing. 

Install XP first, ubuntu second. there is a really good page out there, but I donut remember the link. if you have set up ubuntu before you shouldn't need it though, everything is pretty straightforward.

I would use the XP disk to setup the first partition, then ubuntu for the other two.

---

### Post by Mission 10 on 2006-01-07
My first ubuntu install I did it Ubuntu first and Windows second. This messed with GRUB bootloader and only loaded Windows. during the install process GRUB scans to see any OS's already on there, if there is non then it does not configure one. You can fix this by repairing the bootloader but is needless work. 

 Like diggs I also formated the windows partition using the Fat system and was glad I did, this way you can use all the space allocated can share easily from the shared partition.

---

### Post by eklypze on 2006-01-07
I'm not sure if this belongs here or not, but I have also installed Ubuntu first and XP second. Now only Windows XP will boot, how do I repair the GRUB bootloader to boot both XP and Ubuntu now?

---

### Post by lemmy999 on 2006-01-07
I think it is generally recognized that you should install XP first, then Ubuntu. 

Diggs partitioning scheme sounds good to me:)

---

### Post by eklypze on 2006-01-07
So is it better to just re-install Ubuntu rather to try and fix the bootloader?

---

### Post by alamba on 2006-01-07
Surprisingly...yes. The basic problem is that Windows overwrites the MBR because of which you loose the grub settings which you get with ubuntu. I have'nt really seen anyone install XP first and then hack the MBR, would be interested if you come across an article that shows you how to do that.

Akshay

---

### Post by lha on 2006-01-07
It it possible to install Windows after Ubuntu, but Windows will overwrite MBR during installation. You can restore GRUB using [these instructions]("http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub").

I'm not familiar with Windows XP, but atleast with older versions of Windows there is another way. Install GRUB to your /boot (or root partition if you don't have separate /boot), **not** to mbr, when installing Ubuntu. Then install Windows. After that, use fdisk to make Ubuntu's partition bootable and Windows' partition not bootable. Finally, edit /boot/grub/menu.lst to include lines that let you boot Windows.

All in all, it is easier to first install Windows and then Ubuntu.

---

### Post by turbo63 on 2006-01-07
Thanks for all the help!  Looks like XP first it is.  Now if I could just need to find my XP disk, since my HD with XP on it failed.

If anyone else needs help with install partitions the below website is great.  
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

