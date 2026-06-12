---
title: "asus maximus iv extreme + HD 6990 problems"
date: 2011-08-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by masuch on 2011-08-22
Hi,

I would like to ask if anybody else has some similar problems or if anybody was successfully solved those thing/s ?

--------configuration:
--asus maximus iv extreme rev 3 motherboard 
--bios revision 1850
--asus HD 6990 graphic card. 
--running on 64 bit ubuntu 11.04 with kernel natty 3.0.0.9 
--or running on kernel 3.0.3 taken from "http://duopetalflower.blogspot.com/2011/08/superfast-i7-optimized-303-kernel-for.html"
--catalyst 11.8


1) software problems:
--previous versions of oneric kernels did not work at all - really freeze.
  only cold reset helped :-(
--no rendering at all. catalyst from 11.6 up to 11.8 versions. 
  Many attempts to re-install in console did not help.
  Errors:
  partly result of this command
LIBGL_DEBUG=verbose glxinfo |grep rendering
dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)

  tried to create links for swrast_dri.so library according to this:
$ locate swrast_dri.so
/usr/lib/debug/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
/usr/lib/debug/usr/lib/x86_64-linux-gnu/dri-alternates/swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri-alternates/swrast_dri.so
/usr/lib32/dri/swrast_dri.so

did not help.

-- I cannot use open source ati driver because temperature has been increased within couple of minutes to 60 degrees Celsius on air cooler output ! and went to freeze.

-- comparing the glxgears perfomance: open source vs. proprietary catalyst driver:
open source ~ 4000 fps big fluctuation, proprietary over 14.000,- fps on older kernel 2.6.39.3 (catalyst 11.6 patched). 
   From kernel versions > 3.0 (catalyst 11.7,11.8)  I have got max 12.200,- fps. 
   Comparing to my very old nvidia geforce 7920 GTX Go (laptop) graphic card where proprietary nvidia driver version 280 got ~ 2500,- fps (kernel 2.6.39.3).
   Quite funny. I would expect from HD6990 quite better performance.
Proprietary catalyst drivers from version 11.3 to 11.8 have always some problems. Installation or something does not work.
   So, concerning the graphic performance I have experienced similar thing to: "http://ubuntuforums.org/showthread.php?t=1827117"

If anybody has experience with nvidia 590 please do not hesitate to share experience ?

-- sometimes I have noticed the small choking even if processor and graphic card is almost idle.


2) hardware problems with motherboard:
-- randomly disconnected SATA II or SATA III hard drives. Running on ACPI. approximately monthly period. Does not matter if hot-plug is on/off.
-- BIOS from 1309 to 1850 versions does not detect any firewire PCI-E card . Does not matter if it is connected to x1, x4 or x8/16 PCI-E slot. Advice from ASUS technical support - buy more and more firewire card/s until some is going to work. Oh yes, they have such sense of humor. Firewire cards definitely works in another motherboard without problems.
-- BIOS does not reliably detects all connected devices in seeing in boot menu. Sometimes is missing flash card, sometimes usb disk.
-- ubs 3.0 sometimes is going to disconnect device (no matter if hd or flashdrive or something else). Sometimes I have got message of "low power".
-- clear CMOS switch on motherboard works sporadically (according to manual I would expect better reliability).
-- debug 2 digit display on motherboard: When something went wrong - usually shows debug code: "reserved for future error codes" or something similar - not much useful.


Thanks for any comments, advice or experience.

---

### Post by masuch on 2011-09-06
Any experience / suggestions with maximus iv extreme motherboard or/and hd6990 graphic card in linux / hardware / software / overclock ?

---

### Post by masuch on 2011-10-17
Does anybody has working firewire on this motherboard like PCI-E internal card or cardbus with firewire ?

---

