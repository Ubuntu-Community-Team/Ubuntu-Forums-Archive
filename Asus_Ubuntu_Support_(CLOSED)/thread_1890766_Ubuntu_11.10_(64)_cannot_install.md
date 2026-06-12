---
title: "Ubuntu 11.10 (64) cannot install"
date: 2011-12-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by iondoarion on 2011-12-04
Hi,

I am trying to install Ubuntu 11.10 and it won't work and I don't know what else to try. :confused:
 
I've tried from USB and from CD without any success; when I try to install from USB I get a black screen and when I try to install from CD it either gets blocked on Ubuntu logo or I get an graphic error (I get something like a TV snow image)

My system looks like this:

ASUS K72JT-TY165D

Intel Core i5-480m, 2,66 Ghz
ATI Radeon 6370M
4 GB RAM

I've read that it might be a problem with ATI driver. It could be that? How could I fix it?

Any help would be appreciated :) 

TY

---

### Post by sanderd17 on 2011-12-04
Check out my signature about boot options. And try the nomodeset option.

---

### Post by iondoarion on 2011-12-04
> **sanderd17 said:**
> Check out my signature about boot options. And try the nomodeset option.

Hey,

TY for your swift answer. I've tried nomodeset option an finally I got to see some images. After some error messages about SQUASH I've got the following error message
______________________________________________________________________
ubi-language crashed
--------------------------------------------------------------------------------------------------
ubi-language failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try running this again before continuing? If you do not, your installation may fail entirely or may be broken.
______________________________________________________________________

I've tryed again and this message kept showing up.

Any suggestion?

---

### Post by sanderd17 on 2011-12-04
> **iondoarion said:**
> Hey,

TY for your swift answer. I've tried nomodeset option an finally I got to see some images. After some error messages about SQUASH I've got the following error message
______________________________________________________________________
ubi-language crashed
--------------------------------------------------------------------------------------------------
ubi-language failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try running this again before continuing? If you do not, your installation may fail entirely or may be broken.
______________________________________________________________________

I've tryed again and this message kept showing up.

Any suggestion?

Crashing because of language files? This is not right. Can you check the md5sum of your CD (I don't know exactly how to do this on Windows, but it should be found somewhere near the installation instructions on the site).

---

### Post by iondoarion on 2011-12-04
> **sanderd17 said:**
> Crashing because of language files? This is not right. Can you check the md5sum of your CD (I don't know exactly how to do this on Windows, but it should be found somewhere near the installation instructions on the site).

Right now I am on my brand new Ubuntu 11.10  :guitar:

How did I do it? Well, I have used as a last (crazy, noobish) mesure both ways of installing (USB + CD). I have selected just like you thought me (TY again for that) **nomodeset **option and before installing I've made the *check*. After an instalation process (install+updates+mp3 soft) that lasted for ~50 min (is it ok?) I have finally did it.

I am very excited and I can wait to explore it and learn everything. :)

I hope that my post and your answers will help others in need that will have the same problems.

TY very much!

---

### Post by iondoarion on 2011-12-04
Should I activate ATI drivers?

---

### Post by sanderd17 on 2011-12-04
Great to hear this, for the ATI drivers, if it works as smooth as you want without the proprietary drivers, you can leave it this way.

By default open-source drivers are used, and it depends on your graphical card which are better.

Maybe using the proprietary ones will make it unnecessary of using the nomodeset option.

But I would really need to google the type of your graphical card to know these things for sure.

---

### Post by collisionystm on 2011-12-04
> **iondoarion said:**
> Should I activate ATI drivers?

yes. I would.

---

