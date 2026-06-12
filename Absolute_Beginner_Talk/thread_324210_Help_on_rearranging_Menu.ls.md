---
title: "Help on rearranging Menu.ls"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-12-23
Help on rearranging Menu.ls

I think I know what I am doing but I thought I would have it checked out if possible.
I currently have a dual boot Ubuntu and Winxp.

What I would like to do is to rearrange my menu.ls just a little.

title        Ubuntu, kernel 2.6.15-23-386
title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
title        Ubuntu, memtest86+
title        Other operating systems:
title        Microsoft Windows XP Professional

What I would like to do is move the WinXp to the second position instead of last.
If I understand it right I would move the following code up to the top.

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1[/B]

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

Is this correct?  I believe it is but just want to check.

---

### Post by bulldog on 2006-12-23
Why do you want to do that?
It's certainly possible just do so.

---

### Post by Greevous on 2006-12-23
> **gargoyle said:**
> 
Is this correct?  I believe it is but just want to check.

Gargoyle, 

 Just know that whenever Ubuntu updates the kernel, it will rearrange that list and you will have to move Windows XP to "second place" again.

---

### Post by gargoyle on 2006-12-23
> **Greevous said:**
> Gargoyle, 

 Just know that whenever Ubuntu updates the kernel, it will rearrange that list and you will have to move Windows XP to "second place" again.

I am not sure of what you are telling.  Does this happen when I install new software or is like and upgrade to the basic operating system?

Why I want do it,  just so it more convenient then at the bottom of the list.

---

### Post by Greevous on 2006-12-23
> **gargoyle said:**
> I am not sure of what you are telling.  Does this happen when I install new software or is like and upgrade to the basic operating system?


When you update Ubuntu, every now and then comes a new kernel and the GRUB menu will be updated with the new patch (right terminology?). Anyways, in my experience whenever that happens, the list is recreated with Ubuntu, Ubuntu (recovery mode), Memtest, and XP. 

Basically, if XP ever ends up at the bottom again, edit your menu.lst again the same way as before.

---

