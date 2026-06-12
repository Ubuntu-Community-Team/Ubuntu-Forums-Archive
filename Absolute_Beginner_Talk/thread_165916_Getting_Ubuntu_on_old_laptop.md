---
title: "Getting Ubuntu on old laptop"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by natman on 2006-04-25
Hi, I have an old laptop, 64mb ram, intel celeron 500 mhz win ME and am trying to put ubuntu on it. I have no internet connection. But installation always frezzes at the screen "Starting up the partitioner " at 52 % can anyone help? thanks

---

### Post by az on 2006-04-25
You probably need more ram.  You need 128 megs of ram to run the installer.

---

### Post by waldorf on 2006-04-25
This is probably not the answer you were looking for but I've found Zenwalk <http://www.zenwalk.org/> to be really wonderful for old and slow computers.

---

### Post by malavar on 2006-04-25
try debian it works well with old slow pcs hence, i have a oooold compaq laptop with no cdrom drive, 48 megs of ram and like 120 mhz, i did a net install tho and managed to get everything running including xfree86 with blackbox wm. or try to create partitions using another utility...

---

### Post by Rikostan on 2006-04-25
Puppylinux flies on older machines. I have a Compaq Armada 1750( I think) that has pretty close to the same system specs as yours and Puppylinux runs extremely well on it.

---

### Post by hentaidan on 2006-04-25
[QUOTE=azz]You probably need more ram.  You need 128 megs of ram to run the installer.[/QUOTE]

128MB for the installer? When Ubuntu only needs 32MB? :confused:

---

### Post by jason.b.c on 2006-04-25
[QUOTE=hentaidan]128MB for the installer? When Ubuntu only needs 32MB? :confused:[/QUOTE]

That dosen't sound unreasonable to me..!     How do you figure ubuntu only needs **32mb's** to run.. :confused:     I always thought it was **128mb** as well..;)

---

### Post by hentaidan on 2006-04-25
[QUOTE=natman]"Starting up the partitioner " at 52 % can anyone help? thanks[/QUOTE]

Looking through results on google brings up quite a few hits. Only thing I could find that solved it for some one was new hard drive cables and bending the pins back straight on his hard drive...

Perhaps you have a hardware problem?

You mention that you have no internet connection, but I'll say this anyway: It might be worth trying the [gparted live CD]("http://gparted.sourceforge.net/livecd.php") (30MB) to partiton your hard drive. If that fails, then you probably have a hardware problem.

---

### Post by hentaidan on 2006-04-25
[QUOTE=jason.b.c]How do you figure ubuntu only needs **32mb's** to run..[/QUOTE]

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch02s05.html]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch02s05.html") ?

---

### Post by jason.b.c on 2006-04-25
[QUOTE=hentaidan][http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch02s05.html]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch02s05.html") ?[/QUOTE]



> You must have at least 32MB of memory and 110MB of hard disk space. _For a minimal console-based system (all standard packages)_, **250MB** is required. If you want to install a reasonable amount of software, including the X Window System, and some development programs and libraries, you'll need at least 400MB. For a more or less complete desktop system, you'll need a few gigabytes.

:) ;)

---

### Post by hentaidan on 2006-04-25
[QUOTE=jason.b.c]:) ;)[/QUOTE]

I dont follow?

---

### Post by Jagot on 2006-04-25
The 250MB referred to is not RAM - it is space on the hard disk.

---

### Post by echo $USER on 2006-04-25
I always thought you needed 64mb of ram for server install and 128mb for gui install.

i have a IBMT21 800mhz Athlon, 128mb ram, 20gb hdd running fluxbox, no troubles whatsoever.

---

### Post by jason.b.c on 2006-04-25
> **echo $USER]I always thought you needed 64mb of ram for server install and 128mb for gui install.

i have a IBMT21 800mhz Athlon, 128mb ram, 20gb hdd running fluxbox, no troubles whatsoever.[/QUOTE]


Yea thats what i thought too:confused:  said:**
> I dont follow?

So then you don't follow your own *" link "* that you posted.???:-k

---

### Post by az on 2006-04-25
[QUOTE=echo $USER]I always thought you needed 64mb of ram for server install and 128mb for gui install.

i have a IBMT21 800mhz Athlon, 128mb ram, 20gb hdd running fluxbox, no troubles whatsoever.[/QUOTE]
That was for Warty.

I don't have a breezy install disk handy, but look in the F1 or F2 help screens and the minimum requirements are there.  You certainly cannot run Ubuntu with 32 megs of ram.

The installer used to be able to run with 64 megs of ram but now requires 128.  It may work with less ram on some systems, but is not guaranteed to work with less than 128 megs of ram.

---

### Post by echo $USER on 2006-04-25
[QUOTE=azz]I don't have a breezy install disk handy, but look in the F1 or F2 help screens and the minimum requirements are there. [/QUOTE]

Sweet, I didn't know about that.  If it were not for this forum, I wouldn't learn anything at work (or do anything lol).

---

### Post by hentaidan on 2006-04-26
[QUOTE=azz]I don't have a breezy install disk handy, but look in the F1 or F2 help screens and the minimum requirements are there.  You certainly cannot run Ubuntu with 32 megs of ram.

The installer used to be able to run with 64 megs of ram but now requires 128.  It may work with less ram on some systems, but is not guaranteed to work with less than 128 megs of ram.[/QUOTE]

According to my Breezy install disk it needs 64MB of RAM (see screenshot).

From: [https://wiki.ubuntu.com/Installation/LowMemorySystems]("https://wiki.ubuntu.com/Installation/LowMemorySystems")
> How to install an Ubuntu-Desktop on low memory systems (Pentium II and III Processor, **32**-256 MB RAM)

Does the documentation need updating?

---

### Post by tbrminsanity on 2006-08-24
I tried getting Ubuntu working on my Compaq Armada 1750 (64MB ram) but it was just too slow.  I got the latest version of Xubuntu and now it runs faster then when I had windows on the damn machine.  I think you should check out Xubuntu for your laptop.

---

### Post by Metacarpal on 2006-08-24
The basic Ubuntu (Gnome) install suggests having at least 256MB of RAM.  I think that's for the actual install itself, as I have a shade less than that and it runs fine.

However

With only 64MB, you're unlikely to get any good response out of Gnome.  Try [Xubuntu]("http://www.xubuntu.com/") instead. It uses the XFCE desktop environment, which is much lighter-weight.  I found the system requirements on their website:
> To use the installed system at least 64 megabytes of RAM is required but 128 is recommended. At least 1.4 gigabytes of disk space is required.
Now, keep in mind that you do NOT want to try to use the "desktop install CD", as it won't run on your machine.  Use the "alternate install CD", which will work fine.  Once it's done, you'll still have the desktop environment, no worries.

To download the Xubuntu alternate install CD .iso file, [go to this page]("http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/") and scroll about half-way down.

---

