---
title: "NEWBIE mistake, please help!!!"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by nixie21 on 2007-10-02
I have a ATI 9600 video card... For some reason I thought i was supposed to do this:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

But now when Ubuntu tries to start, I have NO VIDEO...what do I do?

Thanks,

Once i get it fixed, how do I install the right driver for my card?

Thanks so much

---

### Post by phidia on 2007-10-02
To get your graphical desktop (gui) back type > sudo dpkg-reconfigure xserver-xorg press the enter key and enter your password. Be prepared to answer some questions about your keyboard, mouse, gpu and monitor. 
Doing that should get you an xserver that works-if you answer the questions correctly (you can run through it/do it over as many times as you need to)
After you've done that read [this]("http://ubuntuforums.org/showthread.php?t=515573") on installing the proprietary ATI driver.

---

### Post by SpiritIsReality on 2007-10-02
howdy
once ubuntu is running and you have no video, you could try hoding down the Ctrl and Alt key, and press F2 key, then let all up. Then you should have a login prompt. Log in, and type $sudo dpkg-reconfigure xserver-xorg
and press enter. Once you have answered the questions, you should have a working /etc/X11/xorg.conf file with the fglrx xorg.conf file as a backup.
Then you can press Ctrl and F7 to get back to gui.
It will help to know your monitor's vertical and horizontal refresh rates before. Either from the manual, or the manufacturer's web page. Then when it asks you to choose between simple, medium , choose the last one. If in doubt, choose the default answers that it has already highlighted and this should work. If not, post back here for some REAL directions. haha!
buds
edit : thanks phidia

---

### Post by nixie21 on 2007-10-02
Maybe I am missing something... I got back my display, worked perfectly, thanks.

I tried to install the drivers, 

1st - Install from Ubuntu repositories (easier)

Had no display

then tried the edgy way, same result???

This is what I have now

nixie21@Main:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

nixie21@Main:~$ 


01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

Any ideas?  Thanks...

---

### Post by SpiritIsReality on 2007-10-03
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) ?
from [http://ubuntuforums.org/showthread.php?t=564893](http://ubuntuforums.org/showthread.php?t=564893)

---

