---
title: "Can't boot after installing kubuntu-desktop on iMac running Hardy Heron."
date: 2008-09-29
forum: Apple Hardware Users
---

### Post by wizzipopnfizz on 2008-09-29
Hey,

I am new to Ubuntu and recently installed Ubuntu Hairy Hardon on my $50 iMac PowerPC (yes, it worked fine). My mate showed me how to install packages so I got working what I needed to. Things were all going sweet until I decided to try a GUI instead of living on CLI, so I tried 'sudo apt-get install kdesktop' and it all installed fine but wouldn't run suggesting that it didn't recognise my display.

After reading some stuff on the net (thanks Google), a suggestion was to install kubuntu-desktop instead, which I did not realising the problem I was about to run into. It too spat back the error about not recognising the display and then it rebooted.

Since then, each time I boot, it turns itself off after a brief while. I get to the yaboot prompt (boot:) and if I either leave it or press <ENTER> it goes through a few lines of text:

> boot:
Please wait, loading kernel ...
   Elf32 kernel loaded.
Loading ramdisk ...

..then it flashes up some quick text but I miss it before going to a white screen with black text that says:

> done
copying OF devices tree ...
Building dt strings ...
Building dt structure ...
Device tree strings <some hex>
Device tree struct <some hex>
Calling quiesce
returning from prom_init

..then back to a black screen with the following text:

> Loading, please wait ...

.. and that's where the hard drive spins down and the machine turns off.

What do I need to do and/or type at the yaboot (boot:) screen to autoremove the kubuntu-desktop that I {shouldn't have} installed.

<edit>
Nevermind, I decided to blow it all away and start fresh.
</edit>

---

### Post by jenitta on 2008-09-30
I have recently installed Ubuntu Hairy Hardon my friend showed me how to install packages it is working fine

___________________________________

[Houston Best Florist](http://www.florist-flowers-roses-delivery.com/texas/houston_tx.html) [loans with no credit check](http://www.cheaponline-loans.co.uk/help/no-credit-check-loans.php) [pisos vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [download iPhone ringtones](http://www.myringtoneshub.com/specials/buy-cell-phone-ringtones.htm)

---

### Post by johndavid_9696 on 2008-10-11
CLI is the best one than the GUI. The step taken by you was wrong. Ubuntu Hairy Hardon on 50 iMac PowerPC was supported very fine by CLI, I felt very happy with it and did not tried any other to spoil my PC.


===============================================================


john


[vilafranca](http://www.vilafrancadelpenedes.com)

---

