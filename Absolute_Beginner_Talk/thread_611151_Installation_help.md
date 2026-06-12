---
title: "Installation help"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Kratosaurion7 on 2007-11-12
Ok im trying to install Ubuntu in my virtual machine. So when i put the cd in the drive and boot my machine up, after a few second of initialization(I guess) it gives me this screen. 
[IMG]http://img232.imageshack.us/img232/9291/imageyo7.png[/IMG]
What does that mean?

---

### Post by chamberlain2006 on 2007-11-12
Are you sure that you downloaded Ubuntu Linux and not Caldera Linux?  Did you download it from [http://www.ubuntu.com?](http://www.ubuntu.com?)

---

### Post by ubnewbie2 on 2007-11-12
or the virtual machine might have it's "cdrom" pointed at an iso file on his hard disk, so it's not seeing the real CD in the drive.

btw: that screen shows he has booted into DR-DOS.

---

### Post by Kratosaurion7 on 2007-11-12
I downloaded from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and its the version 7.10.

---

### Post by Kratosaurion7 on 2007-11-12
Something else i discovered when i boot up the first line says Caldera

Starting Caldera DR-DOS

Means anything?

Edit: Or maybe I burned my CD wrong?

---

### Post by ubnewbie2 on 2007-11-12
See my reply

---

### Post by Kratosaurion7 on 2007-11-12
It even says that when im booting my physical PC, and im pretty sure it does regognize my CD. Whats DR-DOS anyway?

---

### Post by Maestro23 on 2007-11-12
> **Kratosaurion7 said:**
> It even says that when im booting my physical PC, and im pretty sure it does regognize my CD. Whats DR-DOS anyway?

I believe this is what is on your system: [http://www.drdos.com/](http://www.drdos.com/)

---

### Post by Frak on 2007-11-12
> **Kratosaurion7 said:**
> It even says that when im booting my physical PC, and im pretty sure it does regognize my CD. Whats DR-DOS anyway?
> DR-DOS is a PC DOS-compatible operating system for IBM PC-compatible personal computers, originally developed by Gary Kildall's Digital Research and derived from CP/M-86.
- Wikipedia
It was later bought by Novel

As for your installation, try using an iso file instead of a physical medium.

---

### Post by Kratosaurion7 on 2007-11-12
Dunno,I never heard of DR-DOS and im pretty sure I don't have than thing.

---

### Post by Kratosaurion7 on 2007-11-12
By the way, when I downloaded Ubuntu was it supposed to give a .iso file? Because it gave me a .rar file which I burned in my cd.

Edit : Ha ha! Got it. Worked things a little bit and it worked(I think, i got a different result, im hoping for the best)

---

### Post by Maestro23 on 2007-11-12
> **Kratosaurion7 said:**
> By the way, when I downloaded Ubuntu was it supposed to give a .iso file? Because it gave me a .rar file which I burned in my cd.

You need to burn it as an **image.**  Whatever burning program you use, make sure you burn as image.

---

### Post by Kratosaurion7 on 2007-11-12
Still, thanks for all the help.

---

### Post by Frak on 2007-11-12
> **Kratosaurion7 said:**
> By the way, when I downloaded Ubuntu was it supposed to give a .iso file? Because it gave me a .rar file which I burned in my cd.

Edit : Ha ha! Got it. Worked things a little bit and it worked(I think, i got a different result, im hoping for the best)
.rar?

---

### Post by ubnewbie2 on 2007-11-12
.rar files are compressed.  Maybe there's an iso file inside?

---

### Post by Kratosaurion7 on 2007-11-12
Actually my error was that my WinRar program (for an unknown reason) regognize .iso files as a .rar or .zip files and try to extract them.

---

### Post by Frak on 2007-11-12
> **Kratosaurion7 said:**
> Actually my error was that my WinRar program (for an unknown reason) regognize .iso files as a .rar or .zip files and try to extract them.
That's what I was wondering, since Ubuntu.com doesn't distribute .rar files.

---

### Post by ubnewbie2 on 2007-11-12
> **Kratosaurion7 said:**
> Actually my error was that my WinRar program (for an unknown reason) regognize .iso files as a .rar or .zip files and try to extract them.

Yes, as iso files contain a complete filesystem, some archiving programs can "unpack" them and let you deal with the contents.

I'll bet the boot image contained in the iso from ubuntu, is DR-DOS based. That must be why you ended up at a DOS prompt.

---

### Post by Frak on 2007-11-12
> **ubnewbie2 said:**
> Yes, as iso files contain a complete filesystem, some archiving programs can "unpack" them and let you deal with the contents.

I'll bet the boot image contained in the iso from ubuntu, is DR-DOS based. That must be why you ended up at a DOS prompt.
Some VM's use DR-DOS OSS components for booting.

The boot image for Ubuntu is a squashfs Linux Busybox system.

---

