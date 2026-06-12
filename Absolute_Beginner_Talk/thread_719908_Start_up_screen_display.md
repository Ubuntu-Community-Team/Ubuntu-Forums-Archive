---
title: "Start up screen display"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by gbnogkfs on 2008-03-09
During start-up, my monitor refuses to work saying "input out of parametres; set to 1280x1024-60MHz": I don't have a clue on how to do that.

note that graphics do work normally during the session: the problem olny gets out at startup and closingdown...

---

### Post by anim on 2008-03-09
probably because ubuntu reverts to 800x600ish resolution on boot/shutdown. It seems very strange to me that your monitor doesn't support this. See if it has a some sort of scaling setting on it and change it to "1:1" scaling. That should theoretically solve the problem until I can hunt down a software solution. What monitor do you use?

---

### Post by Tatty on 2008-03-09
[http://ubuntuforums.org/showthread.php?p=248755]("http://ubuntuforums.org/showthread.php?p=248755")
This thread might help

---

### Post by anim on 2008-03-09
Here ya go.
[http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970)

---

### Post by gbnogkfs on 2008-03-09
> **anim said:**
> probably because ubuntu reverts to 800x600ish resolution on boot/shutdown. It seems very strange to me that your monitor doesn't support this.


to me as well: I don't even know if it's the resolution or the frequency that gets it mad...

> 
 See if it has a some sort of scaling setting on it and change it to "1:1" scaling.


really don't know what you are talking about...

> 
 That should theoretically solve the problem until I can hunt down a software solution. What monitor do you use?

HP vs17x

---

### Post by gbnogkfs on 2008-03-09
> **Tatty said:**
> [http://ubuntuforums.org/showthread.php?p=248755]("http://ubuntuforums.org/showthread.php?p=248755")
This thread might help

there it says "go Applications->System Tools->Configuration Editor" : I have no "Configuration editor" down there...

---

### Post by gsiliceo on 2008-03-09
> sudo apt-get install gconf-editor
ANd you'll get it

---

### Post by Tatty on 2008-03-09
> **gbnogkfs said:**
> there it says "go Applications->System Tools->Configuration Editor" : I have no "Configuration editor" down there...

I actually meant this bit of the thread...

> **mohaham said:**
> you can force this by adding  xres=1024x768 in the boot options
in /boot/grub/menu.lst  file
like this...

title Ubuntu
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5  xres=1024x768
initrd (hd0,4)/boot/initrd.2.6.10
savedefault

---

### Post by gbnogkfs on 2008-03-09
> **gsiliceo said:**
> ANd you'll get it

it says I already have it installed and up to date...

however, i managed to start it, but really don't know what to do with it...

---

### Post by gbnogkfs on 2008-03-09
> **Tatty said:**
> I actually meant this bit of the thread...

no way it did work :(

---

