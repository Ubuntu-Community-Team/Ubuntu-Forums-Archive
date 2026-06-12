---
title: "Help dual booting Ubuntu and Win XP"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by slave on 2006-09-13
After spending the whole day Defragmenting, Qtparting, Partitioning, Formatting, Installing and Editing 'boot.ini' When I select Ubuntu Linux on the OS Menu the cursor blinks forever on the next screen. It is still blinking. (Sahara Laptop)

---

### Post by b_martinez on 2006-09-13
> **slave said:**
> After spending the whole day Defragmenting, Qtparting, Partitioning, Formatting, Installing and Editing 'boot.ini' When I select Ubuntu Linux on the OS Menu the cursor blinks forever on the next screen. It is still blinking. (Sahara Laptop)

I take it you are trying to use the Windows bootloader to boot linux? If so , you need to intall grub to the root partition of Ubuntu. Otherwise, when windows' bootloader tries to hand off the boot sequence, there is nothing to hand off to.
The easiest way to fix this is to re-install Ubuntu, and allow it to install GRUB to the MBR. Use the linux bootloader to boot both.
If you are going to install GRUB to the root partition of Ubuntu, you will need to know which partition it is. Then boot the install cd, choose the rescue option and at the terminal type in 

sudo grub --install /dev/hdX,Y

where X= the hard drive number. 

example setup
hda1= Windows
hda2= root partiton of Ubuntu
hda3= swap 
hda4= home

[example] sudo grub --install /dev/hda2 [example]

hope this helps.
Bill

---

### Post by whizbaby on 2006-09-13
*Boot.ini* means that you try to start ubuntu with the m$dozer bootloader on a laptop. As far as I know you'll need to make a special grub install because linux has to be loaded with a bootloader. Look at this
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)
(did you really expect Darth Gates to spend money for making other-OS-access easy?)
Why not trying it the way it's meant to be? If not shure try this:
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by slave on 2006-09-13
Thanks to both of you guys. I can finally get some sleep.

PS: This is the first time I have ever registered in a forum. I did not know that one can get a response in a few minutes. I am beggining to love Ubuntu.

---

