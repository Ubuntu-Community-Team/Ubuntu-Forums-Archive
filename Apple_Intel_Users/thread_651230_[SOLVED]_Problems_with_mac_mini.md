---
title: "[SOLVED] Problems with mac mini"
date: 2007-12-27
forum: Apple Intel Users
---

### Post by el_baby on 2007-12-27
Hi,

I'm completely new to mac but have some experience with linux, debian and ubuntu.

After reading a bit, I installed [rEFIt]("http://refit.sourceforge.net/") 0.10 and could boot the gutsy dvd... but without keyboard access... and it only works with a DVI monitor... I tried 2 different VGA monitors that work perfectly fine with OS X on the same machine, but whenever I boot linux, they either go blank or freeze with the grey screen and the linux logo in the center (from rEFIt).

Did anyone else experienced this?

I also have a problem with the keyboard/mouse... I have an apple keyboard and a microsoft mouse that work OK in OS X and within rEFIt, but when I see the first text screen (either the ubuntu CD boot menu or the "press ESC" from grub after installing ubuntu to the hard disk), the keyboard is non-functional (and I notice the light from the mouse is off)... after the menu times out and linux starts booting, the mouse light blinks a couple of times and then is on and the keyboard is functional again... but [this seems to be an apple firmware problem]("http://refit.sourceforge.net/doc/c4s3_keyboard.html").

Eventually I did install gutsy from the DVD and it does work, but it ONLY works with my Dell DVI monitor... neither an old Compaq 1425 nor a new Samsung VA1903wb work with the VGA adaptor under ubuntu, but they both work OK under OS X in the very same machine... and I don't have any other DVI monitor...

Any help/hints will be very welcome.

---

### Post by el_baby on 2007-12-28
Well,

I finally solved my problem after reading [this post](http://ubuntuforums.org/showthread.php?t=522101&p=3177324).

What I did was to buy another (non-apple) DVI/VGA adaptor (I payed about 10 bucks) and voilá... everything worked... the VGA monitors under linux (yeah, even the old Compaq 14" CRT), **and** the mouse/keyboard in grub.
:-)

---

