---
title: "Running Ubuntu with no X window manager"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-04-06
I have started to get serious with the command line and am trying to switch to and from KDE and the complete command line (using Ctrl+Alt+F1), my questions are these:

- How to change the font size of the full screen terminal (it is currently too big)
- How to get back into KDE after pressing Ctrl+Alt+F1 (tried startx but it says that it is already running, hence my question is how to switch back to it)
- What are the commands to reset and shutdown from the command line?

Thanks

---

### Post by taurus on 2007-04-06
1.  You can add "vga=773" at the end of the kernel line in /boot/grub/menu.lst.

```
sudo nano -Bw /boot/grub/menu.lst
```

2.  <Alt>F7.

3.  ```
sudo shutdown -r now <- to reboot
sudo shutdown -h now <- to shutdown
```

---

### Post by solar george on 2007-04-06
> How to get back into KDE after pressing Ctrl+Alt+F1 (tried startx but it says that it is already running, hence my question is how to switch back to it)

CTRL+ALT+F7

If it is not that try all of the virtual terminals (F1-F12) untill you find it .

> What are the commands to reset and shutdown from the command line?

Shutdown:
```
shutdown -h now 
```
or
```
halt
```

Reset:
```
reboot
```

These will need to be run as root so to reboot you could go
```
sudo reboot
```

> - How to change the font size of the full screen terminal (it is currently too big)
In my experience what you need to do is set the terminal resolution, find the correct setting from the gentoo handbook [here]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10") under Framebuffer.

Add this to the end of the line # defoptions=quiet splash in the file /boot/grub/menu.lst
You will need to be root to do this,
```
sudo gedit /boot/grub/menu.lst/
```

For me the line looks like
```
# defoptions=quiet splash vga=0x318
```
(My screen is 1024x786)

---

### Post by tommy1987 on 2007-04-07
If I am in the console and I log in, it displays a message for me:

```
you have new mail
```

How do I read this, and what is it?

---

### Post by solar george on 2007-04-07
The mail will just be system mail, notifications from programs and the like.

You can just use a text viewer (like less or more) to view it (it won't set the mail to read though) just,
```
less /var/mail/*username*
```

Most email programs can connect to the mailspool file though, you just need to add a new account (in evolution) with the type "Local delivery" and point it to your /var/mail/*username*.

---

