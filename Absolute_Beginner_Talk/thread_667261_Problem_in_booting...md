---
title: "Problem in booting.."
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by alamjadtawfiq on 2008-01-14
I've installed Ubuntu 64-bit version on my Compaq Presario v2414nr laptop along with windows XP. The installation went fine, and everything was perfect (except that it told me during the installation that it couldn't download the security update which I can download later).

But when I rebooted my computer, the system asked me to choose the operating system. I chose 'Ubuntu 7.10', there were other two systems which started also with Ubuntu. The first one did not work, which I suppose the default Ubuntu, while the second two worked, which have command lines etc.

When I chose the first choice, I mean Ubuntu 7.10, it works and runs two or three lines of commands, then a black screen appears. I waited for it for a long time but id didn't work. Please help me, what might the problem be?

p.s. I've posted this topic from my windows XP...

---

### Post by Cypher on 2008-01-14
The first option is indeed the default GUI version of Ubuntu. There should be another "(recovery mode)" option in the menu as well, not sure about the third option.

It might be that the GUI is messed up, so choose the second option that drops you to a command line and type
```

dpkg -reconfigure -phigh xorg-server

```
This should allow you to reconfigure the XORG system and hopefully gets the video working again..

---

### Post by njparton on 2008-01-14
Or it might be that you're experiencing the splash screen bug loads of people have with gutsy.

Remove the "splash" and "quiet" words from appropriate lines in grub.

This seems to be affecting people with nvidia cards the most.

```

sudo gedit /boot/grub/menu.lst

```

or if you can't get into gnome:

```

sudo nano /boot/grub/menu.lst

```

---

### Post by dgray_from_dc on 2008-01-14
> **Cypher said:**
> The first option is indeed the default GUI version of Ubuntu. There should be another "(recovery mode)" option in the menu as well, not sure about the third option.

It might be that the GUI is messed up, so choose the second option that drops you to a command line and type
```

dpkg -reconfigure -phigh xorg-server

```
This should allow you to reconfigure the XORG system and hopefully gets the video working again..

The third option is probably the MEMTEST.

I'm not too knowledgeable on grub, but njparton makes sense.

I agree with Cypher, that reconfiguring the x-server (if possible) may help.

Another thing to check, when you get the black screen, try hitting Alt+Ctrl+F2.  Just to see whether or not the system has booted completely.  Alt+Ctrl+F2 will take you to a text-mode terminal were you can log in (that's if the system came all the way up).

---

### Post by alamjadtawfiq on 2008-01-15
Thank you everybody. 

When the black screen appeared, I pressed Alt+Ctrl+F2, then there were several commands that appeared on the screen after that, the system worked!

But when I tried to reboot, the same thing happened again.

I entered the recovery mode, and entered the code you told me, but I don't know what to do! 
here's what appeared
```
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
use `dselect' or `aptitude' for user friendly package management;
Type dpkg --Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing optionsp
Type dpkg-deb --help for help about manipulating *.db files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more'!
```

---

### Post by dgray_from_dc on 2008-01-15
> **Cypher said:**
> The first option is indeed the default GUI version of Ubuntu. There should be another "(recovery mode)" option in the menu as well, not sure about the third option.

It might be that the GUI is messed up, so choose the second option that drops you to a command line and type
```

dpkg -reconfigure -phigh xorg-server

```
This should allow you to reconfigure the XORG system and hopefully gets the video working again..

I think he meant

```
dpkg **[COLOR="Blue"][SIZE="4"]--reconfigure[/SIZE][/COLOR]** -phigh xorg-server
```

Two dashes instead of one.

---

