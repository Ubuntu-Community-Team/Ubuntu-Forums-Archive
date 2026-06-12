---
title: "where is software installed?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by liquidus219 on 2007-10-29
Is there a folder in the filesystem (Gutsy Gibbon) where software is installed, like the "Program Files" folder in Windows?

Where can I find the executables for my software?

---

### Post by overdrank on 2007-10-29
> **liquidus219 said:**
> Is there a folder in the filesystem (Gutsy Gibbon) where software is installed, like the "Program Files" folder in Windows?

Where can I find the executables for my software?

Hi and welcome, maybe this link will shed some light
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

:KS

---

### Post by taurus on 2007-10-29
_Usually_ in /usr/bin.

---

### Post by macogw on 2007-10-29
And if you compile it yourself, /usr/local/bin is the default place, but you can tell it where you want it to go if you want it somewhere else (like in your home drive)

---

### Post by reza81 on 2007-10-29
/bin >> programs that are booted

/sbin >> it's a bit like system32 ... here you can find programs like fdisk, shutdown, lilo etc...
* remember ... this is a different OS... is not like Windows... you can better try to understand it instead of comparing it. *

/etc >> here you can find the configuration files 

/lib >> hier you can find the library files. compare it with *.DLL in windows

/dev >> Here you can find the devices HDD/USB/CD-/DVD.... etc..
/dev/hd >> IDE-HDD
/dev/sd >> scsi
/dev/fd >> floppy
/dev/st >> SCSI-tape
/dev/scd >> SCSI-CD-DVD-Devices
/dev/tty >> virtual controles Ctrl+Alt+F1,F2, F3... F6
/dev/pty >> Pseudo-terminals to log on the network 
/dev/ttys >> serial interface
/dev/null >> "The black hole " for devices... with this e.g. your output wont appear on the screan
/dev/usb >> usb devices

/usr >> user files 

/var >> files that change size ... like log files...

/opt >> doesn't always get used by all Linux distro's... big programs use this ( like KDE environment or openoffice)

/proc >> kernel uses this directory as interface... Here you can see whats loaded in your memory ... It's a pointer! each process that you run got a subdirectory here 

/home ... wel guess it's a bit like my documents... ( & more)

---

### Post by 3rdalbum on 2007-10-29
I assume you want to know so you can put the programs into your Applications menu?

You don't actually need to know where the programs are. All you need to know is what their name is. Just putting the name into the "command" field (or into the terminal) is enough; Linux will find the program if it's in one of those standard directories that the others speak of above.

Have a look at the HOWTO and the screencast in my signature for a little bit more of a grounding.

---

### Post by liquidus219 on 2007-10-29
Thanks everyone, especially reza81 - guess I should do some bg reading before I do any tinkering.

---

### Post by reza81 on 2007-10-30
> **liquidus219 said:**
> Thanks everyone, especially reza81 - guess I should do some bg reading before I do any tinkering.

No problem. If you need any help... just ask!

---

