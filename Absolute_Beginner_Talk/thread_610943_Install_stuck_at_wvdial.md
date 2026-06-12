---
title: "Install stuck at wvdial"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by m.p. on 2007-11-12
Hi, 

I'm having trouble installing Ubuntu. 

The installation gets stuck at the point "wvdial 80% install". 

I've tried both the LiveCD and alternate version with the same problem. 
I tried the CD's on a different computer with no problems. 
The checksum on the CD's are OK. 

The computer I'm having trouble with has a WinModem PCI card and 
ethernet on the motherboard. 

(The computer that has no problems has an NIC PCI card and 
a modem on the motherboard.) 

The other posts on this forum regarding wvdial either didn't work 
(such as killing the wvdial process) or are over my head. 

Can anyone help? Thanks!

---

### Post by jfinkels on 2007-11-12
When the install process gets to this point, check to see if there is any error output or warning messages in the virtual terminals. To go to the virtual terminals, type <Ctrl>+<Alt>+<F1> (or <F2>, <F3>, through <F6>...you can even try <F8> if you're adventurous). Get back to the graphical system by pressing <Ctrl>+<Alt>+<F7>.

For example, when using the alternate install disc, when the install freezes, press <Ctrl>+<Alt>+<F2> and see if there's any messages. Report back with more info.

---

### Post by m.p. on 2007-11-14
Hi, 

Thanks for the tips. I tried it out, but not much luck. 

With the LiveCD install, there are no messages when it gets stuck. 

With the alternate install, there are messages only when I press <Ctrl><Alt><F4>. 
The last message displayed when it gets stuck (and the only one mentioning wvdial) is: 

"Obsolete command TITLE Configuring wvdial called" 

I have no idea what this means. Any clues? 

Thanks again!

---

### Post by ntu on 2007-11-14
Sorry i can't offer any help, but I would try taking the pci modem out and then try reinstalling. Do you use dialup? I am on dialup and use a external serial modem (gave up on pci ones) they are recognised as easier to setup.

---

### Post by jfinkels on 2007-11-14
Searching for that error string using Google turns up only a few results, but it seems that some other people have experienced this problem:

[https://bugs.launchpad.net/ubuntu/+source/wvdial/+bug/39983/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/wvdial/+bug/39983/+viewstatus)

Try removing the modem card if possible.

---

