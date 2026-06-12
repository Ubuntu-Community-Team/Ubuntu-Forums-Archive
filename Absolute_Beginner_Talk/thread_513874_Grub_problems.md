---
title: "Grub problems"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-07-31
Hi, I have an hp notebook and its been giving me problems like crazy in getting ubuntu working. Ive done nearly everything to get it working, but no matter what the system is never working properly, or even working in general. I have an hp dv 6000z, amd64 x2 2.0 ghz, 2 gb ram, nvidia geforce go 7200 256 mb.
The problem at hand right now is the error 15 I am getting from grub. I installed ubuntu 7.04 amd 64 ver from the live CD and it froze at 90 percent. I restarted and nothing worked, not even my recovery cds for microsoft. I installed ubuntu studio over the ubuntu partitiion and now I can get on windows. Is there a way to uninstall ubuntu and the grub menu so its back to how it was originally before I even set foot in ubuntu? plus, does anyone know if using wubi would help with the process, for instance if the problem was windows messing with the installation 

[http://www.softpedia.com/get/System/Boot-Manager-Disk/Wubi.shtml](http://www.softpedia.com/get/System/Boot-Manager-Disk/Wubi.shtml)

thanks for reading and helping
if anymore info is needed ill gladly provide

---

### Post by aquavitae on 2007-07-31
I've never used wubi, but super grub disk should sort it out.  It should also sort out the error 15 problem: [http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/).  It will be able to reinstall the windows boot loader, and should be able to sort out the linux boot loader too (grub) if you still have ubuntu installed.

---

### Post by kevinlyfellow on 2007-07-31
Here is a howto to remove ubuntu

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

