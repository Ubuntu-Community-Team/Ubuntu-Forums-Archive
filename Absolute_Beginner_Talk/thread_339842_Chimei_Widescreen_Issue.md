---
title: "Chimei Widescreen Issue"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by thevenerablez on 2007-01-16
Hi,

I just installed Unbuntu yesterday and I'm having a widescreen issue. I have no Linux coding skills, and I do not know what a conf file is. If someone could help me out, I would appreciate it very much. 

I have a computer set up for dual boot with OS X Tiger ( 10.4.8 ) and Ubuntu Linux. As of now, I'm in OS X on my Chimei Widescreen 22" LCD Monitor. My resolution is 1440 x 900 and everything looks just fine. 

When I boot into Ubuntu, I have no widescreen options in the screen resolution section, so everything is stretched to fill the screen. Needless to say, everything looks silly and it is barely able to be used with the resolution. 

How do I change the resolution to 1440 x 900? I don't know if there is a graphical way to do it. If there is, I would prefer that method. But, beggers can't be choosers, so if I have to code I will. I can code HTML, CSS, ActionScript, and some simple UNIX commands, but not enough to get by on the Linux system. As I said before, I only installed Linux yesterday so I'm very new to all of this. 

Can someone just add a widescreen option in the screen resolution application? It seems like it would be the simplest way around this problem...

Thanks everyone in advance, I really appreciate it!

_zach

---

### Post by Lucardo Mamones on 2007-01-16
your best bet will be to use the "dpkg-reconfigure xserver-xorg" command from a console. in there it will detect your video card and will attempt to autodetect the screen. It´s fairly stright forward and doesnt need any coding skills.

Good luck.

---

### Post by thevenerablez on 2007-01-16
OK, this is what I did, tell me if I'm wrong.

1) Boot in Linux
2) Go to Applications>>Accessories>>Terminal
3) Enter this code: "dpkg-reconfigure xserver-xorg"

I did those three steps and got this as a result:

"zach@zach-desktop:~$ dpkg-reconfigure xserver-xorg
/usr/sbin/dpkg-reconfigure must be run as root"

Can someone please tell me what I'm doing wrong?

Thanks again,
_zach

---

### Post by docetes on 2007-01-16
you must type in 
sudo dpkg-reconfigure xserver-xorg

it will them prompt you for a password
and then it'll run the script

---

### Post by phr0ze on 2007-01-16
For anything that requires root, just preceed the command with Sudo. ie. 
Sudo <Command>

If your command has parameters you can wrap it in double quotes.

Sudo "<Command> <Parameters>"

You will then be asked for your password. Thats it.

---

### Post by thevenerablez on 2007-01-16
It didn't work. Are there any other ways?

---

### Post by Lucardo Mamones on 2007-01-17
did the screen resolution that you are looking even appear?

---

### Post by thevenerablez on 2007-01-17
Yes, I chose it as an option, but when I rebooted nothing happened.

---

### Post by Lucardo Mamones on 2007-01-17
can you post a copy of /etc/X11/xorg.conf

are you trying to set the resolution of the console or are you trying to set the conf of the graphical mode?

---

### Post by thevenerablez on 2007-01-17
I fooled around blindly in the console and now I'm alright. Thanks everyone for your help!

_zach

---

