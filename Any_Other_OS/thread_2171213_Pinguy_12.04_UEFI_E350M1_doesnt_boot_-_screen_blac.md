---
title: "Pinguy 12.04 UEFI E350M1 doesnt boot - screen black"
date: 2013-08-29
forum: Any Other OS
---

### Post by andreazzz on 2013-08-29
Hi everyone!
Yesterday I assembled a nice mini pc based on a ASROCK [E350M1]("http://www.asrock.com/mb/AMD/E350M1/?cat=Download&os=BIOS") for my granny. She is typical Dutch and wants to spend as little as possible. Therefore I used (in a demo-pc) an old IDE HDD with i686 Pinguy 12.04 (after troubles with 3 other OS's). Unfortunately, the hdd did not fit in the case, so I decided to buy a cheap 8GB USB key. On another key drive I placed a X86_64 image and placed in the pc. After fixing some settings in the BIOS, it still did (and does) not boot (i.e. after BIOS picture screen turns black, but backlight stays on). I disabled "SATA IDE Combined" and set SATA on "AHCI". Also settings for Serial port are all disabled and Safe Boot is disabled, just as Fast Boot.
The boot sequence has two options for "Generic USB flash": normal and UEFI. Changing the sequence does not matter.
Image has been downloaded with Transmission, burned (~) with Imagewriter as well as Unetbootin. The live-usb works with another pc (Phenom X4 930, 8GB, AM3, ATI 4850).

System specs:
ASRock E350M1 with ATI graphics
2GB DDR3 1333MHz, Kingston
Verbatim 8GB Flash disk (Benchmarked at: Write 2,5MB/s; read 20MB/s)

Might it change something to connect the pc with VGA i.o. HDMI? Edit: no.
What might worth noticing: First I saw a blinking cursor in a black screen, then the screen goes black/gray. (At the very first the blinking cursor was as far as I could get, but after that I made the Live-usb with Unetbootin.)

---

### Post by oldfred on 2013-08-29
I do not know AMD, but have you tried nomodeset.
The other system had older verison and may be why it worked.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

      
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by andreazzz on 2013-08-30
The problem is that I can't even use a live OS. When booting from live usb, I first see a blinking cursor and after that the screen goes black (with backlight turned on). Nothing happens, no matter how long I wait. I cannot get boot-repair (on another pc) to make the stick UEFI ready. Can it be that Pinguy 12.04 does not support UEFI?
Next I am gonna try a 13.04 dvd-rw disk with an external player.

---

### Post by Frogs Hair on 2013-08-30
***&#8203;Moved to Other OS/Disto Support***

---

### Post by andreazzz on 2013-09-01
I finally solved the problem!
For some reason booting a USB key does not work, but when I made a live DVD with 12.04 and attached a external DVD-drive I was able to boot into the live environment! The only problem was that Pinguy 12.04 requires 8,7GB, so I installed 10.04. Somehow 10.04 is a little slow (any idea why? Or is 2GB RAM to few for XFCE?), but it works and my granny is happy now(:

---

### Post by oldfred on 2013-09-01
I run full Ubuntu in my laptop with 1.5GB with 12.04, but changed from Unity to fallback or gnome panel.

And 12.04 seemed a bit faster than my previous 10.10, and I had 10.04 before that but do not have a comparison.

---

### Post by andreazzz on 2013-09-01
Ah, I have not tried that. I try it when I'll be there next month.

---

