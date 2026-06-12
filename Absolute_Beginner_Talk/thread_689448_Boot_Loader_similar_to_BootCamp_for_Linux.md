---
title: "Boot Loader similar to BootCamp for Linux"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2008-02-06
So in OSX they have a program called Boot Camp which allows the user to dual boot their computer with Windows and Ubuntu. I'm not sure how many people have used Boot Camp before, so I'll give you a quick run down.

When you hit the power button, if you hold the [Option] key down while booting it gives you a menu where you can choose between OSX and Windows (or whatever other OS you have). Otherwise, if you don't hold the button down, it just boots into OSX.

Has anyone seen anything like this for Linux? I currently use GRUB and though its great and all, I would like to have it where if I want to go to Windows, I can just hold a key and select it from a menu or just have it go automatically into Windows. I currently have GRUB setup it will load Ubuntu after 10 sec and you have to hit [Esc] to get to the menu.

---

### Post by ubutufan on 2008-02-06
You may edit the options of Grub to your likes.
You may for example shorten the timeout period from 10 to any seconds that you like or even have the menu (to choose the os) appear without hitting Esc.
in reality there are so many things to configure Grub

---

### Post by brettg102 on 2008-02-06
Hello!

Consider GAG, the Graphical Boot Manager. I've used it before, and it should do exactly what you want.
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

---

### Post by AegisTalons on 2008-02-06
What I'm more interested is being able to hold down a key while booting to have it go to Windows and not holding the key going to Linux. Basically skipping the menu screen for which OS to load.

---

### Post by LowSky on 2008-02-06
well, you can set Grub to not have a ten second counter, in which it boots the first OS on the list. you can still get to the list by pressing ESC.

if you want to set up Grub to boot an OS if you hit say W for Windows, I dont know if that is possible, maybe... this manual will help

[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

---

### Post by TheBoat on 2008-02-06
You could just set grub up to load Linux by default and then list windows first in the menu so that if you didn't press a button it would load Linux and if you press enter on the grub menu it will load Windows. You can lower the timeout to something like 2 seconds so there won't really be a delay.

> # Boot automatically after 2 secs.
timeout 2

# By default, boot the second entry.
default 1 

# For booting Windows
title  Windows
root (hd0,0)

# For booting GNU/Linux
title  Ubuntu
root (hd0,0)
kernel /boot/vmlinuz-2.6.7 root=/dev/hda1 lang=us

Or something similar to this

---

### Post by ugm6hr on 2008-02-06
> **TheBoat said:**
> You could just set grub up to load Linux by default and then list windows first in the menu so that if you didn't press a button it would load Linux and if you press enter on the grub menu it will load Windows. You can lower the timeout to something like 2 seconds so there won't really be a delay.

Does this work?

I thought if you set a default - that is automatically highlighted when you enter Grub, irrespective if it is at the top of the menu list or not.

---

### Post by TheBoat on 2008-02-06
I am pretty sure that the number following default chooses which entry to load.  0 for the first entry, 1 for the second entry, etc.  that is why I gave > default 1 in my earlier post  and not > default 0

---

### Post by ugm6hr on 2008-02-06
> **TheBoat said:**
> I am pretty sure that the number following default chooses which entry to load.  0 for the first entry, 1 for the second entry, etc.  that is why I gave  in my earlier post  and not

This is not what I am disputing.

You suggest that the entry that will be selected by pressing Enter without using arrow-keys will be the **top** entry in the list.  I think it is actually the **default**. i.e. in your example - Ubuntu would boot irrespective if Enter is pressed or not.

I am not 100% certain about this though.

---

### Post by TheBoat on 2008-02-06
I just checked to confirm and it will highlight the second entry in the grub menu, e.i. the menu is not reorder to put the default first.

---

### Post by ugm6hr on 2008-02-06
> **TheBoat said:**
> I just checked to confirm and it will highlight the second entry in the grub menu, e.i. the menu is not reorder to put the default first.

Again - never suggested it would.

If it highlights the second entry (i.e. default), then pressing Enter will also boot the second entry (i.e. default).  Not pressing Enter will also boot the default.

So this will not solve the OP problem.

---

### Post by TheBoat on 2008-02-06
i.e. not e.i.

---

### Post by TheBoat on 2008-02-06
Yeah, I see now what you are saying. I guess your right. Thanks for catching my error.

---

