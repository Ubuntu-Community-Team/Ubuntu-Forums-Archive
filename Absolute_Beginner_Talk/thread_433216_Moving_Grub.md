---
title: "Moving Grub"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by nomiss90 on 2007-05-04
I currently have ubuntu 7.04 "Feisty Fawn" installed on my external drive.  I have a Toshiba Satellite and my other OS is XP Home SP2 if any of that information is needed.  What with my computer being a laptop i am not always able to connect my external HDD to my computer.  I was wondering if it is at all possible to move grub to my linux partition _without_ reinstalling ubuntu.  I only installed ubuntu last weekend and i hate having to go through installs again and again.  

Thankyou all in advance for any suggestions or help offered.  

I apoligise for any spelling or grammatical errors i might have.

---

### Post by bobplano on 2007-05-04
well you have to reinstall grub to hd1,0 so then its on your external hard drive. im not sure what you need to install grub, but i assume you could just edit the files. then restore your windows mbr with the cd and set your BIOS to boot from the external drive first

---

### Post by nomiss90 on 2007-05-04
bobplano
Sorry to have to bother you with this question but which Cd are you referring to and can you please check [this site]("http://www.gnu.org/software/grub/") out and tell me if this is the right way to go.  sorry to be such a pain in the neck  about all this but I feel that in my case it would be better to be safe then sorry.

---

### Post by bobplano on 2007-05-05
don't worry you're not being a pain. the cd i was talking about was the XP cd. if you don't have that then search the internet for something like fixmbr and you can download the windows mbr. yes that site should have everything you need for GRUB

---

### Post by nomiss90 on 2007-05-06
will try
Will i need to do anything tricky to get grub on the linux drive?
Also as my External Hdd is partitioned will this effect what number it is?
thank in advance.

---

### Post by bobplano on 2007-05-06
i don't think partitioning it will affect the numbers other than hd1,1 for another partition instead of hd1,0. as for installing grub on the external hard drive you just need to change that on the final screen before installing. it will list out everything you put in and it will also have a grub section. just change that to hda1 or sda1 or something like that, then grub should be put on the external drive

---

