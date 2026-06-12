---
title: "Mac os x &amp; Ubuntu live CD.."
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by bienwold on 2008-03-21
hi all, 
i am in a sticky situation!  my mac os x mini was working fine.  i decided i would like to investigate ubuntu.  

so i downloaded the ubuntu live cd iso and burned it onto a disk.  next thing, i go to system preferences in mac os x and change the startup disk to be the ubuntu live cd.  then i restarted my mac.  the sytem booted straight into ubuntu via the live cd.  so now i would like to get rid of ubuntu and stay with mac os x.  i remove the ubuntu live cd and restart, hoping that it will boot directly back into mac os x... but it does'nt.  

now i have the predicament, where nothing else works on my mac except  the ubuntu live cd!  i tried all the usual apple cmd options... tried to get at the open firmware... tried to boot from the leopard disk... all with no success. it does'nt recognise anything else.

also, when i do boot from the ubuntu live cd, the ubuntu welcome screen starts with a number of options, however i can not select any...

unfortnately i have tried that. but it does not recognise any of the usual cmd+opt commands. infact it does'nt recognise anything except the ubuntu live cd. without the cd it says 'grub hard disk error'. i tried the os x disk without any look. i cant access the firewire at all.

even if i wanted too reinstall os x from scratch... i cant... because it does not recognise it!! when the mac boots i never see any sign of os x... no apple... no nothing... if i start using the cmd+opt+o+f it does nothing. like as if when i changed the startup disk initially in mac os x, after reboot, it continues to look for the ubuntu live cd, disregarding everything else

any Help greatly appreciated.

---

### Post by sumguy231 on 2008-03-21
> without the cd it says 'grub hard disk error'.
This implies that you installed it over Mac OS X, in which case just rebooting without the LiveCD won't return you to Mac OS, because it's not on your system anymore. You'll need to reinstall, but I can't really help you with that because I don't have a Mac.

---

### Post by bienwold on 2008-03-21
yes  i suppose your right.... but i know all the info is still there... seen using ubuntu.  if i installed a new hdd.... then i'd be able to save the info on the corrupt drive by running it as an external drive... right??

---

### Post by sumguy231 on 2008-03-21
Disregard my first advice. I'm guessing you just had it resize your Mac OS X partition rather than erase it, which is a very good thing. You should be able to restore without another hard drive if you can remove GRUB and reinstall whatever bootloader Mac OS uses. Someone who actually knows anything about Macs could probably help you with that.

---

### Post by nrcooled on 2008-03-21
> **sumguy231 said:**
> Disregard my first advice. I'm guessing you just had it resize your Mac OS X partition rather than erase it, which is a very good thing. You should be able to restore without another hard drive if you can remove GRUB and reinstall whatever bootloader Mac OS uses. Someone who actually knows anything about Macs could probably help you with that.
I agree.  The boot loader for OS X is gone and you will need to reinstall the boot loader.  Also, you didn't mention wether or not you changed your boot order back to the local HDD.

---

### Post by bienwold on 2008-03-21
how can i sort this out? i am an absolute beginner.

---

### Post by bienwold on 2008-03-21
i can see the os x system when i run ubuntu off the live cd.  how can i reinstall the os x boot loader?  i have no idea how to change the boot order on the local hdd... help???

---

