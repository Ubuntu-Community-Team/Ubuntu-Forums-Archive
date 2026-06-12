---
title: "ATI driver 8.42 is now available!"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by prana on 2007-10-23
[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)


Can someone test this on the Macbook Pro with ATI cards and let us know if the suspend issue has been resolved?

---

### Post by Greywhind on 2007-10-23
Well, I can't say anything about suspend/resume, but I tried the new driver on my Intel iMac and it's a major improvement - everyone with an ATI card should upgrade, I'd say.

---

### Post by cyberdork33 on 2007-10-23
direct link:
[http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)

---

### Post by clayboy on 2007-10-24
how do i know if the right drivers were installed cause i cant access the Ati control panel but my fglrxinfo gives me the proper output

---

### Post by Levo75 on 2007-10-24
ati-driver-installer-**8.40.4**-x86.x86_64


ummm, am i missing something here?

---

### Post by Ubivetz on 2007-10-24
> **Levo75 said:**
> ati-driver-installer-**8.40.4**-x86.x86_64


ummm, am i missing something here?
Maybe AMD forgot to update this page.

---

### Post by Antman on 2007-10-24
AMD forgets a lot of things; like coming out with Linux updated drivers in a reasonable amount of time. :mad:

I'm sticking with Nvidia devices until ATI gets their act together.

---

### Post by dark_harmonics on 2007-10-24
Am I retarded!?!? I followed the instructions posted here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
and now my MBP has no display :( I can still get to the command line but i cant get the video to work . I swear i followed the directions exactly!


**Update: I walked through the instructions for the 9th time with no success. I know i doing the comands right and im not getting any errors **

---

### Post by mcdull2k on 2007-10-24
I have installed it with my MacBook Pro (of course the one with X1600).  Key findings.

1. Compiz Fusion works
2. Extremely Slow and bad performance on Compiz Fusion, a LOT worse than XGL.
3. CANNOT suspend.
4. Very difficult to install.
5. Regret.

---

### Post by dark_harmonics on 2007-10-24
Hey at least you got it to work... I got mine reverted back to the repo-downloaded version and im up and running good. I think for now, ill suffer xgl...

---

### Post by mcdull2k on 2007-10-24
I won't say XGL is a suffer.  Trust me, you don't want to use compiz fusion with 8.42 driver.
In what way your driver won't run?
white screen or what?

---

### Post by mikezila on 2007-10-24
Does anyone know if this makes Source games on Steam work?  They wouldn't work for me, and not being able to play TF2 on Linux is the only thing, **the only thing**, stopping me from blowing away my OSX and Windows installs for Ubuntu greattimes.

---

### Post by cyberdork33 on 2007-10-24
> **mcdull2k said:**
> I have installed it with my MacBook Pro (of course the one with X1600).  Key findings.

1. Compiz Fusion works
2. Extremely Slow and bad performance on Compiz Fusion, a LOT worse than XGL.
3. CANNOT suspend.
4. Very difficult to install.
5. Regret.

It is too bad that ATI finally got AIGLX working, and it is not very good...

Suspend will not change until ATI fixes memory allocation.

---

### Post by cyberdork33 on 2007-10-24
If anyone wants to test on Gutsy, there are debs here:
[http://people.ubuntu.com/~bryce/Testing/fglrx-8.42.3-Gutsy/]("http://people.ubuntu.com/%7Ebryce/Testing/fglrx-8.42.3-Gutsy/")

I am working on some 64bit debs (there are packaging errors for x86_64).

Ok, posted How To here:
[http://ubuntuforums.org/showthread.php?t=590679](http://ubuntuforums.org/showthread.php?t=590679)

---

### Post by dark_harmonics on 2007-10-25
> **mcdull2k said:**
> I won't say XGL is a suffer.  Trust me, you don't want to use compiz fusion with 8.42 driver.
In what way your driver won't run?
white screen or what?

I just get a black screen and then it switches to a blinking cursor. If i apt-get remove the xorg driver and then reinstall the one from the repos it works again. I worked on it for about 2 hours before giving up and trying to switch back. I tried a everything my meager linux knowledge and internet searches could provide... I followed that wiki to the letter the first time through (i scrolled up my commands to check) and then for posterity, i went through it 8 more times. I was really excited to have native aiglx support but i guess ill be waiting for ubuntu to incorporate it into one of their releases or updates.


EDIT: I was able to get installer working by doing this:

Download the .run file
chmod 755 the file
sudo ./ati...run

It still doesnt do AIGLX but I'm halfway there now :)


Edit: The only reason it wasnt working was that i needed to edit my xorg.conf to allow composite (commenting out the disable lines) and that i was trying to use dual-head which doesnt seem to be supported :(. It now works on my single monitor.

---

