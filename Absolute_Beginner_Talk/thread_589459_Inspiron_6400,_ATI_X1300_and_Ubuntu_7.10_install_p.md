---
title: "Inspiron 6400, ATI X1300 and Ubuntu 7.10 install problems"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by grawlybean on 2007-10-24
I am trying to set up a dual boot system but when I boot from the live CD the X system reports errors because, I believe, my card is unsupprted. I am unclear how to proceed.

Forgive me if this question has been answered before but I am a newbie and unable to find the issue relating to the X1300 card rather than the X1400 card.

Spec:
Inspiron 6400, Intel Core Duoprocessor T7200
1GB, DDR2, 533MHz 2 Dimm
ATI MOBILITY RADEON X1300
Microsoft Windows XP Professional, Service Pack 2, English
Integrated Broadcom 440x 10/100 Network Cardand Modem
Dell Wireless 1390 802.11b/g Mini Card (54Mbps)

Thanks for any help

---

### Post by renzokuken on 2007-10-24
that card should be supported......have you tried booting the livecd in safe (grafix) mode?

---

### Post by grawlybean on 2007-10-24
No booting into safe mode still produces the same problem, as the X windowing system fails.

---

### Post by Armadillo C on 2007-10-27
Hi, I just wanted to say that I am experiencing the same problem. I have an ATI X1300 graphics card and can not load the live CD desktop to install 7.10. 

My computer will boot from the cd, and after choosing to load the live desktop (in safe mode or not), it will display the ubuntu startup screen and progress bar. When it finishes loading and tries to start the graphical desktop it restarts this process several times (6) before displaying an error message that says it has:
"restarted the graphical display process 6 times in the last minute, something is going wrong"

I know it is not a problem with the CD, as a friend has used the same CD to install Ubuntu on his computer. It does sound like a problem with our graphics card not being supported. This is strange because i recently installed V6.04 without any problems (I did have to install GC drivers to get it to run smoothly, but this did not effect the installation)

I hope this issue is resolved soon, let me know if you find a solution!

---

### Post by djRob on 2007-10-27
Welcome to the club of ATI owners who must put up with this crap. The cause of your problem is the crappy open source driver provided by ATI. My solution was to download alternate CD and use text mode installation (I disabled Wi-Fi and Bluetooth in BIOS), after the installation I installed proprietary ATI driver - the procedure is described here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you want Compiz, here is another howto
[https://help.ubuntu.com/community/CompositeManager/CompizFusionATI](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI)

---

### Post by PcPixel on 2007-10-31
I tried that solution, as I have the same card. It doesn't work.

I used the alternate CD to install the OS. That works just fine & the GUI comes up. However, the moment I install the Restricted Driver, X hangs whether the XGL X server is installed or not.

---

### Post by Armadillo C on 2007-11-12
I used the alternate CD to install 7.10, but the x server still does not work. I have exactly the same problem that i experienced when trying to run Ubuntu 7.10 from the CD (see above post).

The only advantage is now i can boot into the command line interface. I thought I could install the proprietary drivers using the command line approach, but it seems that Ubuntu can't connect to the internet while booted into the shell.

Is there a way of enabling an internet connection from the shell? Is there a service that i need to start? 

Any help would be appreciated.

---

