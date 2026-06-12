---
title: "Stuck at Ubuntu Command Line"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by m_sarrow on 2006-05-26
Yes, it's true. Embarassing. Loaded Ubuntu 5.10 on an old 386 PC. It begins the boot up okay, then prompts for user name and password. I enter those and get a prompt with ~$...so I have no idea what that means. Just trying to get to the GUI mainscreen. Help?

---

### Post by %hMa@?b&lt;C on 2006-05-26
what happens when you type 
```
startx
``` into the console

---

### Post by johnc4510 on 2006-05-26
Type this and then hit enter:
startx

---

### Post by Sutekh on 2006-05-26
At the main installation screen did you just press 'Enter' or did you type **server or expert** then Enter?

If you did a server install then you didn't install a desktop environment. Now you will have to choose one to install. You can choose GNOME, KDE or XFCE

Have a look at this site, and click on the Desktops at the bottom for some screenies on these environments, and maybe you can decide what you want.

[http://xwinman.org/]("http://xwinman.org/")


If you want [GNOME]("http://www.gnome.org/") - Default Ubuntu Desktop, I'd use this command
```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.

If you want [KDE]("http://www.kde.org/") - Most Common Linux Desktop, I'd use
```
sudo apt-get install kubuntu-desktop
``` 
If you want [XFCE]("http://xfce.org/") - very light desktop, I'd use
```
sudo apt-get install xubuntu-desktop
``` 
These commands will install the respecitve desktops with most of the basic programs you will need.

---

### Post by m_sarrow on 2006-05-27
Thanks for the fast reply.
okay. after the ~$ I entered 
sudo apt-get install ubuntu-desktop
the response was
sudo: unable to look up ubuntu via gethostbyname ()

I also tried startx (recommended by a couple others,) but that shuts down the monitor.  What's next?

---

### Post by m_sarrow on 2006-05-27
The screen shuts off, the computer keeps doing stuff.

---

### Post by lumpki on 2006-05-27
quote: "Loaded Ubuntu 5.10 on an old 386 PC. It begins the boot up okay..."

This is just incredible. You actually installed/booted Ubuntu on a 386? How?! I have a couple old 386's in my basement, they don't even have cdrom drives... just (dual 3.5" and 5.25") floppy drives. Anyway, you've got what, something like 4 MB of memory? I don't think X-windows will even run, or be of any use if it did.

You should have a Pentium computer with at least 128MB RAM (256 is better) to run a Linux desktop. If the Ubuntu GUI fails to come up, use
```
sudo dpkg-reconfigure xserver-xorg
```
on the command line to set up your screen.

---

### Post by m_sarrow on 2006-05-27
[QUOTE=mukta]quote: "Loaded Ubuntu 5.10 on an old 386 PC. It begins the boot up okay..."

This is just incredible. You actually installed/booted Ubuntu on a 386? How?! I have a couple old 386's in my basement, they don't even have cdrom drives... just (dual 3.5" and 5.25") floppy drives. Anyway, you've got what, something like 4 MB of memory? I don't think X-windows will even run, or be of any use if it did.

You should have a Pentium computer with at least 128MB RAM (256 is better) to run a Linux desktop. If the Ubuntu GUI fails to come up, use
```
sudo dpkg-reconfigure xserver-xorg
```
on the command line to set up your screen.[/QUOTE]


Well, the CD rom was installed later, yeah it probably doesn't have the power to handle more than Windows 98...it would have been a PII. I loaded Ubuntu off a CD, it hasn't been configured to be online yet. When I turn it on the kernel boots, then it says "unable to locate RSDP" following that the little brown ubuntu logo appears and reports what is loading. 
I tried your suggestion above, but get the same message as before.

---

### Post by Sef on 2006-05-27
> Loaded Ubuntu 5.10 on an old 386 PC.

How much ram do you have?

---

### Post by erniewinner on 2006-05-28
the requirements for win98 was a dx66 486? i don't think it would install on anything less... i had to overclock my 486 to do it.. and if you did try you got a nag screen not letting you do it. you could try damn small linux... i know its set to run on as low a machine as a 486 but 386? :mrgreen:

---

### Post by erniewinner on 2006-05-28
he he he! :D 

[http://distro.ibiblio.org/pub/linux/distributions/baslinux/](http://distro.ibiblio.org/pub/linux/distributions/baslinux/)

---

