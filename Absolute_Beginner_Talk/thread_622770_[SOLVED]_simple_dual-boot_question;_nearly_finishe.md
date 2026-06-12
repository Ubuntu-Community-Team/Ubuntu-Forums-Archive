---
title: "[SOLVED] simple dual-boot question; nearly finished"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-11-25
Hi I have successfully installed both ubuntu Gutsy Gibbon and windows XP on two seperate partitions, however i have set up another partition for the linux swap and /boot directories.

/dev/sda1 (my ubuntu directory)

/dev/sda2 (linux-swap)

/dev/sda3(extended) - > /dev/sda5(/boot)

/dev/sda4 (windows XP)

I installed gutsy first, set up the partitions and then installed windows xp in whats now sda4. I got rid of the problem where XP takes over the MBR and just boots without any choice to boot into ubuntu using the live cd.

So now Im at the point where both OS's are installed on my PC and by default now it boots into ubuntu and am in the process of setting up GRUB using the command: "sudo gedit /boot/grub/menu.lst" 

The tutorial says to type in this in the file at the correct point :

title Windows XP

root (hd0,1)

makeactivechainloader +1 

....However of course my partitions are different, I tried typing in "root (sda4)" but obviously that didnt work, would anyone know what I would have to type in for it to work??

---

### Post by wjp.reg on 2007-11-25
(hd0,3) in your example, but I have to say that is a pretty strange setup and I'd be surprised if it worked.  Go ahead, surpirse me! :-)

---

### Post by Partyboi2 on 2007-11-25
> **nite owl said:**
> Hi I have successfully installed both ubuntu Gutsy Gibbon and windows XP on two seperate partitions, however i have set up another partition for the linux swap and /boot directories.

/dev/sda1 (my ubuntu directory)

/dev/sda2 (linux-swap)

/dev/sda3(extended) - > /dev/sda5(/boot)

/dev/sda4 (windows XP)

I installed gutsy first, set up the partitions and then installed windows xp in whats now sda4. I got rid of the problem where XP takes over the MBR and just boots without any choice to boot into ubuntu using the live cd.

So now Im at the point where both OS's are installed on my PC and by default now it boots into ubuntu and am in the process of setting up GRUB using the command: "sudo gedit /boot/grub/menu.lst" 

The tutorial says to type in this in the file at the correct point :

title Windows XP

root (hd0,1)

makeactivechainloader +1 

....However of course my partitions are different, I tried typing in "root (sda4)" but obviously that didnt work, would anyone know what I would have to type in for it to work??
You could try root (hd0,0)

---

### Post by nite owl on 2007-11-25
> **Partyboi2 said:**
> You could try root (hd0,0)

I have tried all combinations from hd0,0 to hd0,6, when I press enter on the grub menu when turing on my computer nothing happens, the screen flickers briefly but I dont leave the menu and just have to press the ubuntu option??


....however the others have abit more to them, but the tutorial only say i need to enter the text as above, this is how the ubuntu grub is set up:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=328cfce7-6d15-4110-bf26-7a0e7a3303a5 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

---

### Post by Schalken on 2007-11-25
GRUB cannot boot Windows directly like it can Linux, that is why the Ubuntu entry in the menu is much different, it has to apss control over to the Windows bootloader which does the dirty work.

It is my guess that the correct partition for your Windows partition is (hd0,3) since it is the fourth partition on the first hard drive, as given by the device /dev/sda4. The following should therefore work.

rootnoverify (hd0,3)
chainloader +1
makeactive

However, I am not sure whether makeactive command is supposed to go before or after the chainloader command. :S

Hope it helps!

---

### Post by wjp.reg on 2007-11-25
> **nite owl said:**
> I have tried all combinations from hd0,0 to hd0,6, when I press enter on the grub menu when turing on my computer nothing happens, the screen flickers briefly but I dont leave the menu and just have to press the ubuntu option??


....however the others have abit more to them, but the tutorial only say i need to enter the text as above, this is how the ubuntu grub is set up:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=328cfce7-6d15-4110-bf26-7a0e7a3303a5 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

And you can boot into linux with this?  My interpretation of the above grub entry is that ubuntu root is on the first HD, partition 5.

---

### Post by Schalken on 2007-11-25
> **wjp.reg said:**
> And you can boot into linux with this?  My interpretation of the above grub entry is that ubuntu root is on the first HD, partition 5.

/dev/sda1 = (hd0,0)
/dev/sda2 = (hd0,1)
/dev/sda3 = (hd0,2)

and so on...

---

### Post by nite owl on 2007-11-25
I fixed the problem and it works, I just entered this to the file:

title Microsoft Windows XP 
root (hd0,3)
makeactive
chainloader +1

....I googled some key words and found out that makeactivechainloader +1, is nt meant to be one word...So much for the other tutorial. Anyway it all works perfectly now using GRUB I can boot up into either XP or gutsy :P

---

### Post by Schalken on 2007-11-25
LOL I thought that was just a typo in your original post :P

Glad you got it working!

---

### Post by wjp.reg on 2007-11-25
nite owl; you're welcome :-)

I'm surprised!!

---

