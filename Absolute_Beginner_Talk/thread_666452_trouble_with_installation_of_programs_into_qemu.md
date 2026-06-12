---
title: "trouble with installation of programs into qemu"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by lesrenai on 2008-01-13
I successfully loaded qemu and loaded windows xp media center edition on it. I am now having trouble loading programs in windows through qemu. It wont recognize my cd rom drive it just keeps saying insert disc.

---

### Post by aselya1 on 2008-01-14
Do you have a CD-ROM drive specified when you start Qemu? It doesn't automatically detect the one on your computer. You can use the switch '-cdrom /path/to/cdromdrive' where the path is probably /media/cdrom or /dev/cdrom if you're running qemu as a line command. I'd also like to recommend the package qemu-launcher (available from apt/Synaptic in the Universe repo) as it will handle all kinds of complex switched for you.

---

### Post by lesrenai on 2008-01-14
Thank you for answering my post!
I do have launcher and it launches windows well, Im trying to install a program into windows but having no luck. windows in qemu wont read cdrom

---

### Post by aselya1 on 2008-01-14
Do you have the "Use CD-ROM" box checked in qemu-launcher when you launch the qemu Windows window? Do you have the CD-ROM path pointing to your CD drive as well? If its not one of those things, I'm stumped as well...

---

### Post by ohhhchiahao on 2008-01-15
for me the cdrom was recognized by qemu windows xp when i checked the box for "Use CD-ROM" in the Qemu Launcher. the CD-ROM was linked to /dev/cdrom.

---

