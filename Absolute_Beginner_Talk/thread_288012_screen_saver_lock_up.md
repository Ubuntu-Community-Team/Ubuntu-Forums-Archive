---
title: "screen saver lock up"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by paultru on 2006-10-29
From an first time absolute beginner. Just been upgraded to edgy elf and find that when the screen saver cuts in I cannot get back into the system - black screen. All I get is the pointer or the "I" symbol. All key strokes do nothing even ctrl/alt/del. I have to power down and re boot to get gack in. Any suggestions please?

---

### Post by maniacmusician on 2006-10-29
only thing I can think of is to disable the screensaver  until you find a solution. should save you a lot of reboots. 

also, ctrl+alt+delete wouldn't work, this isn't windows. secondly, it's "edgy eft" :)  

One thing you can try is: ctrl+alt+backspace. that should restart the xserver, and will plop you back at the login screen. This is to test how deep the problem goes. if this doesnt work, that means your kernel has crashed (another way to test this is press the caps lock key; if the A light on your keyboard doesn't light up, your kernel has crashed). If ctrl+alt+backspace works, then that means there's probably something wrong with the program that runs the screensavers.

---

### Post by paultru on 2006-10-29
Thanks for the reply, and sorry about the elf typo!! I assume this is a problem with the upgrade or is it just my system?

---

### Post by maniacmusician on 2006-10-29
upgrades are known to be...a bit difficult. There are ways to get an upgrade to work, but I havn't stumbled across them. I would assume it's the upgrade. Because it worked in dapper, right? anyways, have you done the kernel crash test?

---

### Post by paultru on 2006-10-29
Tried your suggestions. The caps light illuminates and the ctrl+alt+backspace takes me back to the login screen. Sooo, something wrong with the screensaver program!? I think I will turn the screen saver off. Thanks again.

---

### Post by maniacmusician on 2006-10-29
i think in gnome the screensaver program is called xscreensaver? could you please verify this? if that is the screensaver program, then uninstall it and reinstall it like this:

> sudo aptitude purge xscreensaver
sudo aptitude install xscreensaver

---

### Post by paultru on 2006-10-29
Hi, tried the fix and got the following after many lines of text

The following NEW packages will be installed:
  libavcodec0d libavformat0d libpostproc0d libsdl-image1.2 libvlc0
  libwxbase2.6-0 vlc-nox
The following packages will be REMOVED:
  xscreensaver{p}
The following packages will be upgraded:
  libdvdread3
1 packages upgraded, 7 newly installed, 1 to remove and 373 not upgraded.
Need to get 0B/7530kB of archives. After unpacking 20.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate file for the xorg-driver-fglrx package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

Any ideas?

---

### Post by eiraku on 2006-11-05
Well, after a few days using Edgy, I experianced this myself...Whenever I try to preview a screensaver it goes black, whenever i lock my screen it goes black as well... 

The thing is, when the screen is all black, try entering your password and then press enter... It works over here, which means that there's something wrong with the screen lock program (which is usually loaded with the screensaver).... It's working but its just not visible... T_T

A question to paultru, are you running Edgy with or without AIGLX + Beryl (the pretty-ish bling-bling 3d effects thingy)... I'm running Edgy with both installed, and if you are too, then it just might be AIGLX + Beryl going bonkers due to our system... 

Cause if this is a more general issue, I would've gotten more hits from google (especially from launchpad)... So I guess it's just a problem for a small set of people...

Maybe I (or someone) should post an entry into Launchpad later if this problem remains unsolvable... :|

My specs:

Fujitsu C2220 Laptop running Edgy 6.10, Pentium 4M (the old, un-centrino platform) 2.4GHz (speedstep turned off - running at 1.8GHz stable), 768MB RAM (128MB shared with onboard Radeon IGP 340M).

---

### Post by undertakingyou on 2006-11-23
just wondering if there has been any resolve to this.  I have been having the same issues.  When I hit lock screen I don't get the screen saver.  On rare occasions it does nothing.  Every once in a while it works right.  I have noticed that after using Azures it goes haywire.  But, I can not isolate it to Azures because it does it other times too.  Any thoughts?
Running on desktop x86 machine, no special "Bling Bling" 3d effects stuff, and using an Nvidia card with the Nvidia drivers.
Will Smith--

---

