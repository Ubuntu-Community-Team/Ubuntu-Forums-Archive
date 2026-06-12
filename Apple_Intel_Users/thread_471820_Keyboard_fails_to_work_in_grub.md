---
title: "Keyboard fails to work in grub"
date: 2007-06-12
forum: Apple Intel Users
---

### Post by erkker on 2007-06-12
hey,

I have managed to get a dual boot working Ubuntu Studio / OS X 10.4.9 with refit on MBP 2.33GHz, 15 ".   Most things are working pretty well.  I stil need to tweak sound and right click, but wireless is working.

This however is my problem.  After I choose ubuntu in rEFIt my keyboard stops working until the splash screen.  I cannot hit escape to get into the grub menu and if I modify menu.lst to default to the menu I still cannot use the keyboard to choose my kernel.

More about my setup:

installed refit then installed ubuntu studio went with all the defaults except manually partitioned my drive in OS X before I started.  And no Swap drive.

PS Sometimes the computer thinks I am running off ac power when the computer is unplugged.


oh well thats the shape of things around here.

Thanks

-E

---

### Post by ronocdh on 2007-06-12
This is a known problem and [has been documented]("http://refit.sourceforge.net/doc/c4s3_keyboard.html"). As yet, there is no fix, but I personally do a little keyboard voodoo in order to move the selection on the GRUB screen. As soon as I choose either Ubuntu or Windows XP on the rEFIt screen (both go to the same GRUB menu, as they share the MBR), I begin tapping rapidly on both the up and down arrows. Usually by the time the GRUB screen appears, the selection if dancing up and down. 

Of course, you can't use the left and right arrows here if you're triple booting, because that won't allow you to move down on the menu, and will just proceed with the first option. If you're dual booting and that's all you want to do, though, you could edit your GRUB menu.lst and change the countdown timer to 2 or 3 seconds.

---

