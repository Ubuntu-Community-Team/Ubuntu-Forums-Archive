---
title: "Macbook Pro 2009 Battery issues"
date: 2013-05-24
forum: Apple Hardware Users
---

### Post by wammeze on 2013-05-24
Hi guys!!

Let me explain my situation first:
 I received a friends 2009 macbook pro earlier this year with a broken screen, so I promptly fixed the screen, deleted Mac OS X off the hard drive, then put ubuntu onto the HDD. I was satisfied with the computer for about 2 months, until I got my hands on 2 pieces of 4GB RAM, to which I quickly put into the computer. I did my research, and first checked whether or not the 2009 model could take the 8 GB of RAM, which apple advertises as being possible. The moment I turn the computer on, I get the deadly beeps no one wants to hear come from a mac. I take one 4GB stick out of the computer and replace it with a 1GB stick, now putting the computer to 5GB of RAM. Only when the 4GB stick was removed did the computer properly start up. This is where my problems started occurring:

I turned the computer on, with no problem. Everything was working, except the battery. I already tried _hundreds of times_ to reset the SMC (the controller on the macbooks motherboard that monitors battery level, power button pressing, etc.), and I even reset the PRAM on the macbook, to no avail. I even went so far as to replace the old battery with a new one (70 dollars down the drain :-(  ), and the macbook still doesn't start without the charger plugged in, and the indicator lights on the side of the unit do not light up. 

What i'm asking is if there were lines or scripts of code I could run to help reset the macbooks SMC properly, or atleast a script that helps diagnose the actual issue with the motherboard? I don't think buying a new motherboard is practical, as i'm a poor motherlicker.

*_**THANK YOU TO ANYONE THAT CAN HELP!!!!**_* I've been SOL for the past 2 months with this computer, it sucks that it's been reduced to a highly portable desktop computer.

**TL;DR**: I screwed up something, so now my 2009 macbook pro does not detect the battery in the computer, indicator on the side also does not work. i'm guessing it's the motherboard, I just want to make sure. Any help? :-D

_Unit Information_
Computer: Macbook pro 2009
 Model #: A1278
HDD: 160 GB SATA HDD, fs=NTFS
RAM: 5GB
Linux Version: stock Ubuntu 12.04
Battery: Li-ion 10.95V 60Wh Standard internal MBP Battery (replaced once already)

---

### Post by Bucky Ball on 2013-05-24
*Thread moved to **Apple Users**.*

That machine sounds ill. ;(

---

### Post by GhettoMrBob on 2013-05-25
You mentioned that you tried to reset the SMC. Were you successful in doing that? If not, the procedure is:

Shutdown the computer. Connect the power adapter. Hold down shift+control+alt/option and press the power button. Release all keys.

If that went as planned the LED on the MagSafe adapter should change color, indicating that the SMC was reset.

Have you tried removing that additional 4GB stick of RAM and seeing if the battery problem is replicated? If not, I'd try that and replace the stock RAM that came with the unit (if you still have it).

---

### Post by wammeze on 2013-05-25
the SMC was reset at-least 25 times on that computer, it's not the SMC. I've also tried what you've mentioned with replacing the old RAM back into the computer, to no avail :(. What i'm mainly looked for is some diagnostic tests I can run in ubuntu to see the state of the battery, otherboard, or SMC in the macbook. :)

---

### Post by GhettoMrBob on 2013-05-26
There aren't any diags that you can run within Ubuntu that I know of. Do you happen to have the disk that came with the computer? If so, one option would be to install OS X on another partition and see what it has to say about the battery..the battery may be DOA and it will tell you if it needs to be replaced.

Other option, insert the disk that came in the box and hold down 'D' at boot. That should bring you to a hardware diagnostic that you can run or even loop if you'd like.
**Note:**
The disk must be the original disk that came with the computer and **not** just a retail OS X disk.

---

### Post by wammeze on 2013-05-29
yeah I forgot to mention the battery was already replaced once, so it's not the battery (unless i've had the misfortune to encounter 2 batteries with the same issue). I'm almost certain the problem is with the SMC or the motherboard, but I can't really confirm that without any diagnostic tools. And I don't have the original CD either :/ is there any other options?

---

### Post by GhettoMrBob on 2013-05-30
Unfortunately Apple is very proprietary in nature with their software and hardware. That being said, the install disks are the only option I know of for diagnostics such as that. They may be others out there but I know that their hardware test (Apple Hardware Test, AHT) and their service diagnostic (Apple Service Diagnostic, ASD) are pretty much spot on with what they find.

If you can I'd try to contact Apple and see if they can't hook you up with a set.

---

