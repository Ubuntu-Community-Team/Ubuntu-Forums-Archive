---
title: "Inspiron 1520 wireless and sound trouble"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by readingitsideways on 2007-12-11
Hi

I've just installed Gutsy on a new Dell Inspiron 1520 and can't get either the sound or wireless to work. For the wireless I've tried installing fwcutter, it doesn't appear in the restricted drivers manager (yes, I have updated apt).

My wireless is:
Broadcom Corporation BCM4328 

Audio:
 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


Any help appeaciated...

Duncan

---

### Post by linux23dragon on 2007-12-11
> **readingitsideways said:**
> Hi

I've just installed Gutsy on a new Dell Inspiron 1520 and can't get either the sound or wireless to work. For the wireless I've tried installing fwcutter, it doesn't appear in the restricted drivers manager (yes, I have updated apt).

My wireless is:
Broadcom Corporation BCM4328 

Audio:
 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


Any help appeaciated...

Duncan

Hi Duncan

This thread should help fix the [***_[COLOR="Blue"]Sound Card[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=636659&highlight=dell+1520&showpost=#2")


As For the Wifi, you might need to configure the driver or use the "ndiswrapper".

---

### Post by readingitsideways on 2007-12-11
Hi

Thanks, that solved the sound issue, now I just need to sort out teh wireless.... :(

I tried installing the broadcom firmware (bcm43xxfirmware.tar.gz) which has worked with other laptops on Feisty, but no luck.

Any ideas?

Duncan

---

### Post by readingitsideways on 2007-12-11
Solved by following [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

