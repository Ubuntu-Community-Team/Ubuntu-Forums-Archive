---
title: "M-audio jamlab"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Forko on 2006-08-08
Can anyone tell me if it is possible to get my M-audio jamlab working on Ubuntu? It is the only thing that is stopping me from installing Ubuntu the fact that i can't find a way to do it. It is a USB audio interface for plugging a guitar into my computer. Can i use a Windows of Mac OS driver for it on Ubuntu? CHeers

---

### Post by gn2 on 2006-08-08
Check this out first: [http://www.m-audio.ca/index.php?do=support.faq&ID=cf6f53946a5d2cfa3792487b2af97e61](http://www.m-audio.ca/index.php?do=support.faq&ID=cf6f53946a5d2cfa3792487b2af97e61)

Then try here: [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

Hope that's useful

---

### Post by Forko on 2006-08-09
I checked both of the links and i can't get a driver from either.

---

### Post by Forko on 2006-08-09
I plugged my Jamlab in today, and it is detecting it as a Jamlba, but is not giving out any sound. The Jamlab is automatically set and the output when i plug it in in windows, will it be the same in Linux? I have my speakers plugged into it, and i have it set as the soundcard, so what should i try now? I ahve tryed executing the install on the CD that cae with it, but it won't work. How do i install a .exe with Linux anyway? Cheers.

Edit: I have now got it working!

---

### Post by shanike on 2007-05-07
> **Forko said:**
> 
Edit: I have now got it working!


maybe you could share your solution with us?! ;)

---

### Post by kyriacos on 2008-02-07
I'm interested in one of these devices but can't source the drivers either. What did you do to make it work?

:guitar:

---

### Post by stingx on 2008-05-22
strange things... I've installed OSS driver, that makes ALSA stop working. After removing OSS package and rebooting, ALSA works fine and jamlab device working, but with OSS driver. 

Thats because package has compiled it's kernel modules, but forgot to remove them.

There is still one problem: only guitar input volume control is displayed, no headset output volume sliders...

---

