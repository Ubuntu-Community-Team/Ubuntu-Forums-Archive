---
title: "Screen Resolution during boot"
date: 2012-03-26
forum: Any Other OS
---

### Post by stalkingwolf on 2012-03-26
The problem may be with grub im not sure.  Here is the problem I have 6 Os's
installed on this machine.  They are Win 7, Ultimate edition 3.0, Zorin 5.2,
Mint 12, and pinguy.
The machine is an HP 5713w with nvidia gforce on board graphics, 2.8 gz dual core processor and 3gb ram.  The Monitor is an HP w1907.

Once booted all systems work fine. They all set the resolution to the default 1440 x 900.

The problem comes at boot.  with just one os and win7 grub works fine. after the second is installed grub disappears, and i get the resolution out of range reset your resolution to 1440 x900 popup.  then it goes on and boots.

I said disappears, that is not exactly accurate.  It goes invisible and remains invisible even after the other os's are installed.  That is until i 
install pinguy then grub is visible again and all is well.

any ideas?

---

### Post by dandnsmith on 2012-03-26
pinguy is obviously installing some boot defaults which work for you.
I suggest you find the files, keep a record of them, and then make sure that any subsequent install which modifies the setup is corrected.

I don't know pinguy, but I'd try to ensure that other distros don't re-install the grub boot setup, and then do a grub-update (or is it update-grub) from pinguy to correct any changes in OSs available.

---

### Post by pqwoerituytrueiwoq on 2012-03-26
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
that guide should help

---

### Post by stalkingwolf on 2012-03-27
Thanks I will try both suggestions and let you know

---

### Post by stalkingwolf on 2012-04-27
it appears the solution is to change the resolution in the grub.confg file.

---

### Post by stalkingwolf on 2012-05-16
i have found a solution for this at least it has worked so far.

I use the grub boot repair disk.
Under advanced options , select grub options, then check uncomment
Grub_GFXmode.

You can also set a specific resolution in the grub.cfg file save it then update grub.

---

### Post by Perfect Storm on 2012-05-16
Moved to Other OS/Distro talk.

---

