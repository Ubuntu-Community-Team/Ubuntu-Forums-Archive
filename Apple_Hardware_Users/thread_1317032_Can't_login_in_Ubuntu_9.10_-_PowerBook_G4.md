---
title: "Can't login in Ubuntu 9.10 - PowerBook G4"
date: 2009-11-06
forum: Apple Hardware Users
---

### Post by nickyboom on 2009-11-06
Hi everyone,

I've downloaded the new release of Ubuntu 9.10 PowerPC  (*both* the 'desktop' and the 'alternate' version, since with 9.04 I had some problems....) using BitTorrent, as suggested in the forum's sticky posts, getting the .torrent files from the webpage found at

[http://cdimage.ubuntu.com/ports/releases/9.10/release/](http://cdimage.ubuntu.com/ports/releases/9.10/release/)

I booted the 'desktop'  variant on my Powerbook G4: the system seems to boot fine, if it wasn't for the fact that, at the moment of automatically logging in, it says "authorization failed", and there is no combination of "user:ubuntu/password:[name one]" that works...
During the boot process an error message stating something like "can't add ubuntu user" flashes on the screen... then disappears when the X server starts.

So, I tried the the 'alternate' variant: the install starts, it seems to go fine (I'm doing a fresh install on the notebook hd, using the whole disk -- no dual boot -- and ext3 as filesystem), except for an error when it comes to the "install software" option in the install menu...although  choosing the option manually seems to do the trick.
I rebooted the system and.... same story, but this time doesn't allow me to log in using the username/password that I just created... 

I've burnt both images on dvd, at low speed, on two different kind of medium (DVDRW and DVD-R)... I repeated the 'alternate install' three times... but it doesn't work.

Any suggestion is _extremely_ welcome...


Cheers,

Nicky

---

### Post by linuxopjemac on 2009-11-06
Nicky, seems related to your PRAM battery which takes care of the time (dead)

[http://ubuntuforums.org/showthread.php?t=1241259](http://ubuntuforums.org/showthread.php?t=1241259)

---

### Post by Dennis- on 2009-11-07
you can try going into osx first and setting the time correct, then reboot with the powercord connected and the cd in the laptop.

hope thad helps,

Dennis-

---

### Post by nickyboom on 2009-11-08
@linuxopjemac : yes, you're right, the PRAM is completely dead; thank you for pointing me in the right direction. 

@Dennis- : thanks for the hint, but unfonrtunately there is no dual boot option, as I completely erased the content of the hard disk. Is there any option that you know of that can be passed to system during boot (or installation) to set date and time?

Cheers,

Nicky

---

### Post by linuxopjemac on 2009-11-08
To do this access open firmware by booting the computer while holding down the O, F, Apple and Option keys. The command to set the date and time is:

```
decimal dev rtc sec min hour day month year set-time
```

So to set the clock to 10 seconds past 11:15PM on December 31st, 2005, the command would be:

```
decimal dev rtc 10 15 23 31 12 2005 set-time
```

The Open Firmware prompt should type ok after this. You can then reboot and do an install and it should not fail at the "select and install software" step.

The option to boot in open firmware is 
```
mac-boot
``` 
I think

---

### Post by nickyboom on 2009-11-08
Hi linuxopjemac, 

thank you very much, setting the date and time from the Open Firmware solved the problem; after that the system installed without problems, and now it runs smoothly.

Nicky

---

### Post by linuxopjemac on 2009-11-08
I would go for a new PRAM battery. You can find them at [http://www.ifixit.com/](http://www.ifixit.com/)

Good luck

---

