---
title: "Installation of 6.10 hangs laptop HP DV9014EA"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by hans1970 on 2007-01-04
Hi,
I just made a CD with the 6.10 and tried to install it on my laptop

HP Pavilion DV9014.EA AMD Turion TL-50/17"/1GB/80+80GB/GF Go 7600 256Mt/DVD+/+RW DL

Every try to install this great Ubuntu hangs the laptop after about a minute...

I will try to explain when it happens, and hopefully some of you can give me som advice what to do.

After the usual start up phase I come to the silver colored Ubuntu logo and below that is a bar graph with a "blip" that runs back and forth, that works fine. After that the info on the screen turns into color, and after 6 runs( back and forth) everything hangs when the blip is returning from the left ( to be exact: about 1.3-1.5 parts from the left...) After that is impossible to do anything else take out the battery to kill it.

Any suggestions?

(I have also tried the 6.06.1 version with the same result.)

Thanks in advance
/
Hans

---

### Post by gilbertr on 2007-01-04
Which version of the Edgy CD are you using ? (i386/64bit/alternate ?)

As an aside, something similar happened to me a little while back and it turned out to be a bad CD.

---

### Post by hans1970 on 2007-01-04
Hi!
I believe I used the 64 bit version for both version.

here is a picture of when it hangs isself during the 6.06.1 version...

/
Hans

---

### Post by mxrten on 2007-01-04
It won't solve your problem but:

The silver colored ubuntu logo is a 64bit bug and can later be fixed by installing a modified usplash package: [http://www.ubuntuforums.org/showthread.php?t=304673](http://www.ubuntuforums.org/showthread.php?t=304673), provided that you solve your problem.

Holding down the power button for appr. 5 sec is an easier way of killing the computer, you shouldn't need to remove the battery.

---

### Post by gilbertr on 2007-01-04
Couple of things you could try :

When the initial splash screen comes up, press F6 and add 'noapic nolapic' at the end of the line (without the quotes')

Failing that, use the alternate CD instead of 64bit, it is less prone to installation issues.

---

### Post by gunksta on 2007-01-04
Someone has already mentioned checking the integrity of the CD you burned. Sometimes they burn funny. I would also recommend checking the MD5 sum value of the ISO file you downloaded.

--andy

---

### Post by hans1970 on 2007-01-04
Thanks for all replies! I will try the suggested things tomorrow.

/
Hans

---

