---
title: "Unable to use wireless"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by akros on 2007-03-21
First off, I am an absolute Linux newbie. I just installed Ubuntu on my laptop today. It originally had Windows XP on it but I got rid of it. 

I can (obviously) connect to the internet just fine, but only by actually plugging in an ethernet cable. The wireless does not work (it is a Dell 1470). I have read the other threads regarding the 1470 but they've only confused me further. 

Thanks for the assistance.

---

### Post by crispy_420 on 2007-03-21
Do you know the chipset?

If you run dmesg from command line (applications -> accessories -> terminal). It will list all your hardware.

A little google search turned up that it is a Broadcom 43XX chipset. Not sure of linux support but search these forums. But I'll just throw in some other links too:

[http://www.linuxquestions.org/questions/showthread.php?p=2240477](http://www.linuxquestions.org/questions/showthread.php?p=2240477)

[http://mandrivausers.org/lofiversion/index.php/t34824.html](http://mandrivausers.org/lofiversion/index.php/t34824.html)

It looks to me as use ndiswrapper is your primary option. That basically uses the windows driver to allow connection. Don't worry this is actually pretty common as many chipsets have no native support.

---

### Post by them4504 on 2007-03-21
Had the same problem and fooled around for almost a week.  Set the ethn to the ethx that goes with your wlan. go to terminal and type "sudo pppoeconfig", answer yes on all questions after you put in your signin code and password. Turn off computer and re boot. I correct you will see a green block and some computers with
little orange marks about them.  The complete sequence is in a booklet you can download.Good luck

---

