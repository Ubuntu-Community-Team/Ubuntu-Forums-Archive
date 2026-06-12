---
title: "ubuntu 7.10 not booting up on my HP"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by immranderson on 2007-10-19
hi, my ubuntu live CD isn't even booting up on my computer, and I don't know why? Is there any way to fix it? I'd REALLY like to have it on my laptop, but yea :-\

my laptop is an HP compaq nw8440
intel core 2 duo CPU T5600 @1.83 Ghz, 2gb ram
ATI mobility FireGL V5200 display adapter

upon trying to boot up the disk, it got up to "running local boot scripts (/etc/rc.local)" and kept flickering to a mish mashed colored screen for a couple of seconds before reverting back to that message in the comand prompt esque format

any help would be greatly appreciated! Thanks!!

---

### Post by mlentink on 2007-10-19
- Have you checked the MD5sums to make sure you do not have a faulty disk?
- Did you burn it at a slow speed?

I'd try another disk and see whether that works. If not, please try and post exactly what error messages you are getting.

btw, Most of us will not be familiar with your machine, so try to list as many specs as you cab find, especially concerning the video-chip/card

---

### Post by immranderson on 2007-10-19
ok, well -- i'm running windows XP professional

and...
my specs

ACPI multiprocessor PC
ST980825AS disk drive
ATI MOBILITY FireGL V5200 display adaptor

Intel(r) 8280 1g (ICH7 family) ultra ata storage controllers, intel (r) 8280 1gbm sata AHCI controller, Texas Instruments OHCI compliant IEEE 1394 host controller

intel PRO/wireless 3945ABG network connection

Texas instruments PCIxx12 cardbus controller

Texas instruments PCIxx12 integrated flashmedia controller

Intel Core2 CPU T5600 @ 1.83 Ghz

....reading the rest of the stuff -- i don't think you guys would exactly need it... thought on my device manager, that's what I found...

I'm reburning a disc at low speeds now to see if that fixes the problem (I burnt it at 24x before)

---

### Post by mlentink on 2007-10-19
Except for the ATI, no outlandish things. Your kit should work. So first approximation is that the disk was flakey.

---

### Post by immranderson on 2007-10-19
ok, I burnt the disc at 4x and I get the same error of it getting to the prompt of

"running local boot scripts (/etc/rc.local)"

then it goes back and forth between that command prompt and going to a colored screen with distorted ubunto logos along the top...

---

### Post by immranderson on 2007-10-19
I also get an error message 


 The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.

---

### Post by molly_001 on 2007-10-19
Newer HP Pavilion "Media" machines have always been problematic for the initial install.  You can click [here]("http://tinyurl.com/3aa95c") for more:
[**http://tinyurl.com/3aa95c**]("http://tinyurl.com/3aa95c")

I did manage to install Ubuntu 6.06 on an HP Pavilion a1210n, but not without significant grief.  I can't remember the tricks I used, and I would have thought I made some digital notes for it!  My hunch is that if you were to try installing Ubuntu 6.06, it would work.

---

### Post by Arthur Archnix on 2007-10-19
I use the alternate cd to install in text mode. You might have more luck with that.

---

