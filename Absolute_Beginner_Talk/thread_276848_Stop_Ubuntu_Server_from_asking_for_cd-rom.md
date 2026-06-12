---
title: "Stop Ubuntu Server from asking for cd-rom"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-13
Hello,

I have a Ubuntu Server (non-GUI) installed; love it!  However, if I ever try to install a package via apt-get or aptitude it requires that I have the original install cd-rom in the CD drive.  This is a bit of a hassle since my server is accessed remotely and I have to trudge my way over to load the cd-rom.

How can I stop it from asking for the CD ?  Do I need to copy the CD on the system or ... ?  

Idea ?  Thanks.

---

### Post by JonahRowley on 2006-10-13
Open up **/etc/apt/sources.list** in your favorite editor.  There will be a line in there for the Ubuntu cdrom, either delete it or comment it out (put a # at the beginning of the line).  Run **apt-get update** afterwards and it won't ask for your cdrom while installing packages anymore.

---

### Post by thornomad on 2006-10-13
Ah!  Yes!  I see it now ... thank you!

Is there a particular reason that Ubuntu-Server (and not plain-jane Ubuntu) includes the call to the CD-ROM drive ?  Interesting!

---

### Post by JonahRowley on 2006-10-13
It's left in there by default for all installs (except beta installs, I think).  It lessens the load on their servers and your bandwidth for installing packages you already have I guess.

---

