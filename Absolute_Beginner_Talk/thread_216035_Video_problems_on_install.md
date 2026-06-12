---
title: "Video problems on install"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-07-14
Hi all,

I am a complete beginner so please keep all replies very simple.

I have installed 6.06 i386 on an AMD64 (heard i386 installed easier and was better than AMD64 bit version) with a Radeon ATI integrated video card and a sony (DVI) flat panel monitor. 

The screen resolution is set at 640 x 480. (this also make the installation difficult since all the windows are larger than the screen and have to be moved around)

I have tried to install the video driver according to 
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
however on reboot I have no signal to my monitor at all.

I'm sorry I can't offer more details but I don't know what details are important. 

Thanks

---

### Post by Herman on 2006-07-14
> **Revert to Xorg driver**  If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing 
 ```
sudo dpkg-reconfigure xserver-xorg
``` and selecting the "ati" driver, or simply restoring the previous /etc/X11/xorg.conf file, if you made a backup.


Here's a link I'm working on to help guide people through the sudo dpkg-reconfigure xserver-xorg process. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p7.html")
If you decide to look at it, any suggestions for improvements will be welcome. I'm working on it this weekend. 
Regards, Herman :D

---

