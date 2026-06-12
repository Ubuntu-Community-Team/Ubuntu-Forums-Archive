---
title: "Blinking question-mark folder of doom (post-borked-install blues)"
date: 2009-03-09
forum: Apple Hardware Users
---

### Post by Dynaflow on 2009-03-09
Some friends and I came into possession of a second-hand Power Mac G4, with the intention of wiping it clean and using it as an exclusively Ubuntu box (preferably with an encrypted filesystem).  I've converted a lot of x86 and 64-bit systems to Ubuntu over the last few years, so I volunteered to do this machine's makeover as well.  I downloaded the latest PowerPC alternate installer, worked myself past the ["Installer cannot detect CD-ROM" bug]("https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu 8.10 PowerPc alternate install"), and started installing.

Seven hours later, this is the first computer I have ever seriously considered shooting.

I had picked guided partitioning, using the full disk to test out what a normal installation would do.  However, the installation media turned out to be corrupted, and the installation needed to be aborted.  When I rebooted to try another installation with a better-burned CD, everything was utterly borked.  

The hard drive won't boot because, of course, there is presumably nothing but jibberish on it, but the CD-ROM drive won't boot either.  I just find myself staring at this taunting little smiley-faced folder with a question mark blinking on it over and over again.  I tried all the hotkey methods I know of the get the sucker to boot from CD.  I've gone into OpenFirmware and and tried this: ```
0 > boot cd:,\install\yaboot
```  But to no avail.

My question: How can I best go about stuffing Ubuntu down this evil, truculent beast's throat?

---

### Post by tiresia on 2009-03-09
I guess you downloaded the right alternate iso image for your Mac here:
[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)

Burn it at low speed, because old drive are very picky on mac.
At boot up, press C to start from the CD and, when you get the yaboot prompt (do you get it?) press TAB to see different options.

Your Mac is a 32 bit. Type install adding following arguments for the kernel:```
install nosplash
```
or
```
install video=ofonly
```
or ```
install video=ofonly nosplash
```

Are you trying to install Intrepid? Please, tell us more about your hardware (grafic card, extra pci card, processor?)

---

### Post by Dynaflow on 2009-03-09
There's no yaboot prompt.  Just black screen, and then the blinking question-mark folder.  The drive doesn't even whir.

I would chalk it up to a bad optical drive, but the thing worked immediately prior to the ill-fated installation attempt.  I can get into OpenFirmware if I hold down the hotkeys, but my attempts there to get the system (or what's left of it) to boot from CD uniformly fail.

---

### Post by tiresia on 2009-03-09
Optical Drives in such machines are quite problematic. And it is advisable to use the Apple Disk Utility (if you have MacOS) to burn a disk, at _very slow speed_.

My suggestions:
1. Reset PRAM (cmd-opt-P-R)
[http://support.apple.com/kb/HT1379](http://support.apple.com/kb/HT1379)
2. Be sure to use supported CD (most probably cd-r)
3. Try different version (Ubuntu Hardy, or Intrepid or Debian)
4. If everything fails, we can try to check via OpenFirmware (but it can be annoying and not easy)
5. Try a USB Install - it is the most efficient way to install 
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

