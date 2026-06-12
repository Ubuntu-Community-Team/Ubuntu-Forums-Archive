---
title: "Fails to restart and wouldn't start up properly"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by l0l on 2007-01-30
Hello there,

I recently got a laptop (AMD 64, NVidia), and so decided to install Ubuntu 6.10. The Live CD worked perfectly, and the installation also went well; however, after I restarted my computer after the end of the install, it went to a black screen and would not restart. So I forced it to restart; however now it wouldn't power up. It goes through the loading part, but before it gets to the login part, the screen blanks with no actions going on. Thinking that this was a problem with the CD or Ubuntu, I decided to get a Kubuntu CD. Long story short, the same thing happened. I get the feeling that there is something wrong with the laptop, but I don't know what.

Could you at least point me in some direction to start with?

Thanks for your help beforehand.

---

### Post by taurus on 2007-01-30
I don't think there is anything wrong with your laptop.  I think it's X is having a little difficulty with your graphic card.  

Try to boot into recovery mode from GRUB and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just take the default.  And for a video driver, use vesa for now to get X working first.  Then, you can install nVidia driver for it later.

Reboot and see what happens.

---

### Post by l0l on 2007-01-30
Hmm, recovery mode seems not to be working correctly. When I first tried going into it (before posting here) it went just fine, but this time it stopped before getting to the user prompt. The last lines were :

ACPI: Assume boot ridge [\_SB_.PCI0] bus is 0
PCI: Ignoring BARO-3 of IDE controller 0000.00.0d.0

Then it just does nothing.

---

### Post by l0l on 2007-01-31
Ok, I just reinstalled Kubuntu, and at the first attempt it did get to the user prompt in recovery mode, which is when I ran dpkg-reconfigure; however, when I restarted, it did not get to the log in page again, and looking at the recovery mode, it still stops after the line 
PCI: Ignoring BARO-3 of IDE controller 0000.00.0d.0

Any help?

---

### Post by BrownieMan on 2007-02-01
> **l0l said:**
> Ok, I just reinstalled Kubuntu, and at the first attempt it did get to the user prompt in recovery mode, which is when I ran dpkg-reconfigure; however, when I restarted, it did not get to the log in page again, and looking at the recovery mode, it still stops after the line 
PCI: Ignoring BARO-3 of IDE controller 0000.00.0d.0

Any help?


[http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/66204/%3Fhighlight%3D&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3D%2522BARO-3%2522%2Bubuntu%26hl%3Den%26safe%3Doff%26sa%3DG](http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/66204/%3Fhighlight%3D&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3D%2522BARO-3%2522%2Bubuntu%26hl%3Den%26safe%3Doff%26sa%3DG)

Try this page, It's translated but might be of some use to you. Goodluck.

---

