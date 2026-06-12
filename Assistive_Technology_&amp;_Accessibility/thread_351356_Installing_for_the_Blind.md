---
title: "Installing for the Blind?"
date: 2007-02-01
forum: Assistive Technology &amp; Accessibility
---

### Post by deadowl on 2007-02-01
I believe this actually belongs in both the installation and accessibility forums, but has more to do with accessibility in installation.

Is there any way for a member of the blind community to install Ubuntu with a screenreader already set to run? This would allow users who are blind to independently set up an Ubuntu distribution on their computers.

---

### Post by dlehman on 2007-02-01
I have not tried it but if you use the alternate cd there are accessibility options I think it is F5. you would have to boot the Cd up and take a look

---

### Post by frafu on 2007-02-02
It is better to use the LiveCD, because I think it has a screenreader as a boot option:

[https://wiki.ubuntu.com/Accessibility/doc/LiveCDsettings?highlight=%28accessibility%29](https://wiki.ubuntu.com/Accessibility/doc/LiveCDsettings?highlight=%28accessibility%29)

Once in the LiveCD environment, it is possible to start the installation from there. However, I don't know whether every step in the installation process already is accessible. 

Have a nice day. 

Francesco

---

### Post by Henrik on 2007-02-02
There is a fairly detailed step-by-step guide here: [http://www.ubuntu.com/access/livecd](http://www.ubuntu.com/access/livecd)

But clearly it's not discoverable enough.

---

### Post by Pipistrelle on 2007-02-02
Thank you, Henrich. I was just looking for this, and couldn't remember for the life of me where I'd seen it before.

Teresa

---

### Post by zcat on 2007-04-23
I've just been playing with feisty and orca and I don't think it's quite good enough yet. If orca and gksudo can get along nicely, we might have something..

  With the screen on I figured out the magic sequence of keys I need; F5, down three times, enter twice. This will start feisty with the orca screenreader enabled. I guess there's no way grub can provide any audio feedback so we're just going to have to tell our blind user the magic key sequence to get him started.

I managed to repeat this with the screen off and get feisty live CD to boot.

I also managed to navigate the orca configuration (the defaults seem sensible enough), minimise it and navigate the livecd desktop, with the screen still off. Looking good so far.

Next I launched the installer program and everything went quiet, so after giving it a few minutes I turned the screen back on to see what had happened. It's sitting in the installer waiting for me to choose install language and not uttering a word.


I have the same problem with using orca on a preinstalled system. As soon as I run any administrative commands the screen reader stops working. 

This is going to seriously limit what a blind user can do with their computer, they'll have to phone me for help every time they want to install a program, add a peripheral, change a network setting..

---

