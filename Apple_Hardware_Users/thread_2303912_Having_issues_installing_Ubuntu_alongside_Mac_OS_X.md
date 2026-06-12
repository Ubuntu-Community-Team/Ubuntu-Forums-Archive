---
title: "Having issues installing Ubuntu alongside Mac OS X El Capitan."
date: 2015-11-22
forum: Apple Hardware Users
---

### Post by alex473 on 2015-11-22
[FONT=verdana]Im trying to install Ubuntu alongside Mac OS X El Capitan but when I go to install it, it doesn't have the option for "Install alongside Mac OS X", all it says is "this computer currently has no detected operating system." I want to be able to dual boot not lose my Mac OS completely.

[/FONT]
[FONT=verdana]Does anyone know what may be causing this?

[/FONT]
[FONT=verdana](*more info*) 
--I am using an iMac with OSX El Capitan. 
--I downloaded rEFInd and installed successfully. 
--I disabled (SIP) system integrity protection on the computer. 
--I created a OS X bootable Ubuntu usb stick using this tutorial[https://www.youtube.com/watch?v=T2nDMgTMctg](https://www.youtube.com/watch?v=T2nDMgTMctg). 
--I partitioned my hard drive giving 469.55GB to "Macintosh HD" and 29.56GB to "UBUNTU".[/FONT]

---

### Post by __PG__ on 2015-11-23
Are you able to actually boot of the USB?  Have you managed to proceed past the Grub2.0 menu?
I'm having similar issues as well. See [this thread](http://ubuntuforums.org/showthread.php?t=2303621).

---

### Post by luciano.x on 2015-11-25
> **alex473 said:**
> [FONT=verdana]I want to be able to dual boot not lose my Mac OS completely.
[/font]

You must go 'somewhere else' (advanced). DO NOT choose the first option.

> **alex473 said:**
> [FONT=verdana]
Does anyone know what may be causing this?
[/font]

I had that issue too. Don't know what the cause is. It seems that sometimes the installer just doesn't detect the presence of OS X.

PS: I had to install rEFInd again because it would boot directly onto Linux after installed. It shouldn't be a problem for you I think.

---

