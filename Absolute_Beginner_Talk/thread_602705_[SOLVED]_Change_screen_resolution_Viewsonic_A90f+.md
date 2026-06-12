---
title: "[SOLVED] Change screen resolution Viewsonic A90f+ ??"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bobafifi on 2007-11-04
I've got a Viewsonic UltraBright A90f+ monitor ( [http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/](http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/) ) showing at a resolution of 800x600 (only other option in drop down menu is 640x480):

[[IMG]http://img99.imageshack.us/img99/4273/screenshotscreenresolutvt5.png[/IMG]](http://imageshack.us)


02:09.0 VGA compatible controller: S3 Inc. Savage 4 (rev 04) (prog-if 00 [VGA])
        Subsystem: CardExpert Technology Unknown device 8888
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e7000000 (32-bit, non-prefetchable) [size=512K]
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at e7ff0000 [disabled] [size=64K]
        Capabilities: [dc] Power Management version 1



//

Anybody know how/where to change this to get 1280x1024?

Many thanks in advance,

-Bob

---

### Post by linuxwizard on 2007-11-05
I have the same monitor and what I had to do each time on an install with Ubuntu Dapper.Edgy & Feisty is open terminal > sudo nano /etc/X11/xorg.conf > scroll down to Section Monitor > HorizSync 28-51 change to 30-86 > VertRefresh 43-68 change to 50-150 > now save and close. These setting I got from ViewSonic manual. Now you should have more resolution settings and more refresh rate settings.

---

### Post by bobafifi on 2007-11-05
After much Googling and terminal attempts - I got it to work.  The end of this thread was particularly helpful.
[http://ubuntuforums.org/archive/index.php/t-2287.html]("http://ubuntuforums.org/archive/index.php/t-2287.html")
Thanks!

-Bob

---

