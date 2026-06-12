---
title: "So maybey ill keep 7.10 (HAL/Wifi fixed) ATI/restricted drivers problem"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by USFMD82 on 2008-01-11
Well I had a few problems when first upgraded to the 7.10 but now I finally have my WIFI back, and my computer no longer says Failed to initialize HAL.

However still a few kinks to workout.

I have nothing that is USB at the moment to test it out, however my card reader is not working. It used to be i could plug in my SD whatever card and a SD icon would pop up on the desktop, now it doesnt do that however in the File browser it does pop up SD/MMC bowever clicking on it does nothing.


Also, I still have some problems with Restricted Drivers.
Driver
ATI Accelerated Graphics Driver
Software Modem Driver
Firmware
Firmware for Broadcom 43xx shipset family

All have no checkbox in the one for enabled, and all say status not in use when  I try to enable the box comes up asking me to cancel or enable driver, I click enable and then it pops up with the error

"The software source for the package 
sl-modem-daemon
is not enabled"

I have already tried changing the sources from US to Main and back (did this while trying to fix HAL problem as well.

Thanks in advance for any assistance.

---

### Post by mikeyphi on 2008-01-12
Just a suggestion:
Open System/Administration/Software sources
Make sure the 'Propriety drivers for devices (restricted) is checked

---

### Post by USFMD82 on 2008-01-12
WORKED!!

Still having problems with the SD reader thouhg.

And now I am having trouble with my DVD

---

### Post by CCNA_student on 2008-01-12
This is what I had to type in to play DVD's:

*sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot*

Then use this to get past the encryption in DVD's:

*sudo /usr/share/doc/libdvdread3/install-css.sh*

That works on the x86 version of Ubuntu anyway. Here is how playing a DVD looks like on Xubuntu with Totem.

---

