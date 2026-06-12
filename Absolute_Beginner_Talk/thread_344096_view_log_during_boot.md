---
title: "view log during boot"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by vbdanl on 2007-01-22
Hi.  Is it possible to "show details" during the bootup and shutdown process in Ubuntu similar to fedora ?  I like to see what it is doing, and if it is having any trouble..
thanks.

---

### Post by Shatrat on 2007-01-22
I believe you can hit Escape to get rid of the usplash and see the boot process.

---

### Post by taurus on 2007-01-22
Or remove **quiet** from the kernel entry in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by vbdanl on 2007-01-22
i thought i tried hitting escape, but maybe not at the right time.  it didn't do anything.  what is gksudo?  i use sudo, but haven't used gksudo.  i will try to do the edit tonight and see what happens.  if i remove the quiet will it also show details during shutdown?
thanks for your responses.

---

### Post by pizzutz on 2007-01-22
gksudo, (or gksu) behaves much like sudo in that it executes the command as root.  the only difference is that sudo prompts you for a password in the terminal, and gksu prompts you for you password with a popup box.  gksu is useful when running applications that do not run in the terminal, such as gedit

---

### Post by taurus on 2007-01-22
> **vbdanl said:**
> i thought i tried hitting escape, but maybe not at the right time.  it didn't do anything.  what is gksudo?  i use sudo, but haven't used gksudo.  i will try to do the edit tonight and see what happens.  if i remove the quiet will it also show details during shutdown?
thanks for your responses.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by vbdanl on 2007-01-22
Thanks, that worked.
the blue on black/chocolate is a little hard to see, but at least it is there.  the font could be a little bigger, if that is possible.  i didn't see a font option in the menu.lst file.

I have another question, if someone wants to answer it..

when i use gedit, why do i get the following error and how do i fix it?

dan@Dan-linux-Antec:/boot/grub$ gksudo gedit /boot/grub/menu.lst

(gedit:5827): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

thanks.

---

### Post by taurus on 2007-01-22
If you want to remove the progress bar and the background, remove **splash** and add **vga=773** to the entry for the kernel in /boot/grub/menu.lst.

---

### Post by vbdanl on 2007-01-22
thanks taurus, that worked great.  I also found the answer to the gedit authentication error - guess its been reported and nothing to worry about.

---

