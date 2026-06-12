---
title: "bcm43xx_microcode5.fw"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by |2eM!x on 2007-10-03
To start I am in the beginning process of installing ubuntu.  I have never worked with linux and I am trying hard to stay off the MS bandwagon.  Anyways, I am receiving the error above when I try to boot for the first time.  I have read this thread:[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) .  But I am unsure how to do any of the steps as I think they are not for beginners.  To start, how do I save to my home folder from windows?  Any steps that can be simplified I will be very happy! Thankyou!

---

### Post by master_kernel on 2007-10-03
I don't think Windows has ext* support, so you can't save to your home folder from Windows.

Specifically what error are you receiving?

To enable the Broadcom 43xx drivers in Feisty/Gutsy you can type in a terminal:
```
sudo modprobe bcm43xx
```

---

### Post by |2eM!x on 2007-10-03
The error reads "Bcm43xx: Error: Microcode 'bcm43xx_microcode5.fw' not available to load or failed"

I dont know if I am in feisty or gutsy?  I downloaded the alternate CD.  I will try and run that command you just typed, Ill edit this post with results.  Thanks

---

### Post by master_kernel on 2007-10-03
Before rebooting, run:
```
echo "bcm43xx" | sudo tee -a /etc/modules
```

You can find out your distribution by pressing ALT + F2 and typing gnome-system-monitor (like CTRL + ALT + DEL in Winblows)

---

### Post by |2eM!x on 2007-10-04
Im sorry, like I said, I am new.  I typed that all in and nothing happend.  I must have some mental defect or something?

---

### Post by kevdog on 2007-10-04
Did you download the bcm43xx firmware??  Although the driver is installed in kernel -- its not complete.  Its missing the user space utitlities that you need to download and install.  

Kind of off topic -- but Id recommend ndiswrapper anyway over bcm43xx.  You will get better connection speed and not be limited to 11 Mb/sec.  Just an FYI.

---

### Post by |2eM!x on 2007-10-04
Like I said, I dont know where to download or save that file to.  Im seriously 100% new, and the terms being used are ones I am unfamiliar with so I apoligize I sound silly.

---

### Post by kevdog on 2007-10-04
Not to mix instructions, but try these:

[http://ubuntuforums.org/showthread.php?t=475963&highlight=jamie+jackson](http://ubuntuforums.org/showthread.php?t=475963&highlight=jamie+jackson)

They are fairly straightforward and tested.

---

