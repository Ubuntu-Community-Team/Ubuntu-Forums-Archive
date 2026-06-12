---
title: "Trying to Install Ubunutu on iMac"
date: 2006-08-28
forum: Apple PPC Users
---

### Post by spikedupback529 on 2006-08-28
Hi,
I just picked up an old iMac for $2.00. When I got home, i slipped the Ubuntu 6.05 cd in it. When I turned it on, I got a message saying that i needed a system disk to repair the hard drive. I don't care about OS 8, i just want to install Ubuntu. I attached a Windows keyboard to it and I followed the instructions for booting from a CD (holding down c, right?) with no luck. I still get the error message. I also tried 5.10, with the same thing. 

Any suggestions? Am I going to have to buy an apple keyboard and mouse? If I do...will this be compatable with Ubuntu?

Thanks,
Dale

---

### Post by 3rdalbum on 2006-08-29
An ordinary PC keyboard will still work with the Mac. Try holding down Command-Option-O-F to boot into the Open Firmware prompt (I assume the Command key will be mapped to the Windows key if you have one), then type:

```
boot cd
```

Are you trying to use burnt discs, or ShipIt discs? What sounds play and what comes up on the screen before this error message? I don't think I've ever seen this particular one before.

---

### Post by spikedupback529 on 2006-08-29
Ok, I'm using ShipIt disks to start off with. Some sound comes on when I first turn the computer on (before this I was a Windows/Linux guy, I never touched a Mac). The only thing that comes up before the error message comes up is a happy mac with a progress bar - I guess indicating the loading. I followed your instructions with some luck. I held down windows+alt+o+f and got up the open firmware. I typed in boot cd, just as you said to, and got a message:
> LOAD-SIZE too small.
ok.

Any suggestions?
Thanks again,
Dale

---

### Post by linear on 2006-08-29
Bad CD? Can you download and burn the alternate install disk?

---

### Post by spikedupback529 on 2006-09-01
Sorry i didn't get back to you - I have it set for immediate notification by e - mail. I should've checked back. I am downloading the alternitive image now. I checked with 3 other CDs, from 5.10 and 6.06 with no luck. I'll let you know how the alt. one turns out.

Sorry for the delay,
Dale

---

### Post by spikedupback529 on 2006-09-02
I burned the image to cd, followed the same procedure - windows-alt-o-f

i typed in:
> boot cd

and it came back with:
> O> boot cd MAC-PARTS: LOAD-SIZE (noninterposed) not supportedload-size=0 adler 32=1

LOAD-SIZE is too small
ok

---

### Post by bas2e on 2006-09-06
hi, i've had this error for a few days now. Tried ubuntu, kubuntu, debian, live or normal install cd's, iso-file or all files separated; all result in the same error.

The normal apple boot cd does run like normal so my guess is that the commands with which we try to boot from cd are wrong.

Hope that anyone with experience reads this forum!

---

### Post by qwave on 2006-09-07
Try taking out the hard drive and formatting it on a PC. I was having a similar problem with my iMac not being able to boot from the CD, and I was using a Windows USB keyboard. I couldn't get the machine to boot to the CD, even using all the key combinations, and it would keep booting from the hard drive. So I formatted the hard drive and tried it again, and it worked!
Hope this helps!

---

### Post by spikedupback529 on 2006-09-07
how would i go about formatting the hard drive?

---

### Post by kulath on 2006-09-08
I would try resetting the open firmware PRAM. You can do this from within OF, but I can't remember the command - the obvious one just resets what is reset by a power-on, so does not fix any problems in the PRAM. To reset, I think it would be windows-alt-P-R on your keyboard - you hold this chord while the machine starts, keep it held after the first BONG, then keep holding it for two or three more BONGs (witchcraft varies as to how many are needed). Then release the chord and let the machine boot as normal.

If you think formatting the disc would help (I don't see why that would cause the fault) then you can do this after booting into the Mac boot CD, and choosing disc setup (or something similar) from one of the menus, instead of installing the OS

---

### Post by spikedupback529 on 2006-09-08
I tried Windows-Alt-P-R and I heard the 3 bongs...then I went into the open firmware, but still no luck - Same message (Load size too small)

Thanks to everyone for the help so far
Dale

p.s. i don't have a mac boot cd...which had caused the initial error. can i download a boot cd from the web?

---

