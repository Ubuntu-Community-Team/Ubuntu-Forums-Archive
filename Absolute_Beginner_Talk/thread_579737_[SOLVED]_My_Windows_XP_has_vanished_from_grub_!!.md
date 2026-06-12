---
title: "[SOLVED] My Windows XP has vanished from grub !!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-10-18
Hi folks,

My dual boot ( Feisty Fawn+ Win XP) was working fine till yesterday. After some live updates to Feisty, I found that Win XP has vanished from the grub listing. I have attached a screenshot of my hard disk. 
Could someone guide me how to get back to dual booting ? 
Thanks a million in advance,

jaggu

---

### Post by overdrank on 2007-10-18
> **jagannath said:**
> Hi folks,

My dual boot ( Feisty Fawn+ Win XP) was working fine till yesterday. After some live updates to Feisty, I found that Win XP has vanished from the grub listing. I have attached a screenshot of my hard disk. 
Could someone guide me how to get back to dual booting ? 
Thanks a million in advance,

jaggu

HI and you could see if window is still in the grub using this command
```
gksudo gedit /boot/grub/menu.lst

```

---

### Post by jagannath on 2007-10-18
No it is not in the menu.lst !! It used to be there, though. I have tried to insert it again but looks like I'm not able to define its exact location on the hard drive. That is why I have posted the screenshot. 

My menu.lst  ( the relevant portion) is as below:
It appears to me that there is some mistake in the lines below XP
The XP appears in the grub menu but when I select it it gives me Error 21 !!

title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=ee5d79e9-0b78-47fe-b56f-5b7a0d9cc69a ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Any ideas??
Thanks
Jaggu

---

### Post by overdrank on 2007-10-18
Hi and I do apologize the grub is not my specialty but I would suggest trying to reinstall the grub. I have include some links that may help. Good luck! 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=542683](http://ubuntuforums.org/showthread.php?t=542683)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by blazerw on 2007-10-18
Look in "/boot/grub/" and see if there is a backup of "menu.lst". If there is, look for the Windows entry.

---

### Post by stchman on 2007-10-18
> **jagannath said:**
> Hi folks,

My dual boot ( Feisty Fawn+ Win XP) was working fine till yesterday. After some live updates to Feisty, I found that Win XP has vanished from the grub listing. I have attached a screenshot of my hard disk. 
Could someone guide me how to get back to dual booting ? 
Thanks a million in advance,

jaggu

You problem was that you edited the menu.lst and put MS Windows first.  Mistake.  When you get a kernel upgrade your entry will be erased.  Follow my tutorial on GRUB here.  You will need to count the place in line that MS Windows is in line and make that your default.

[http://www.stchman.com/grub_menu.html](http://www.stchman.com/grub_menu.html)

---

### Post by jagannath on 2007-10-18
Thanks a lot Stchman ! Worked like a breeze. 
Well I didn't know that a kernel update would rub out the windows entry from the menu!!
Thanks again.

Jaggu

---

### Post by jagannath on 2007-10-18
Thanks to you too overdrank. If you observed I have marked the thread as 'solved' . 
That was a useful hint.

Jaggu

---

### Post by stchman on 2007-10-18
> **jagannath said:**
> Thanks a lot Stchman ! Worked like a breeze. 
Well I didn't know that a kernel update would rub out the windows entry from the menu!!
Thanks again.

Jaggu

I don't know which kernel you use, but I would uninstall all the other kernels via synaptic.  They each take up about 100MB.  Select completely remove when you do.

Looks like you upgraded your Edgy to Feisty.

Remove the 2.6.20-15-generic as the -16 replces it.

The 2.6.17-11-generic and 2.6.17-10-generic are Edgy kernels so they are just taking up space for no reason.

When you remove the kernels via synaptic it will update your menu.lst file as well.

---

