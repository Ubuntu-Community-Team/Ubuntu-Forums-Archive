---
title: "Linux apps in windows? (not the contrary!)"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by hito1 on 2007-02-01
Silly problem alert. :) 

Can I install/run a ubuntu app in windows? I can't seem to find a decent (simple, lightweighted and complete like the one in ubuntu) mahjongg game for windows, is there a way to install the one that comes with ubuntu in windows xp?

Thanks!

(I know it's a silly question, but I'm hoping someone has enough free time :) )

---

### Post by annda on 2007-02-01
as far as i know you will have to run a virtual machine, like VMWare (player).

---

### Post by tkjacobsen on 2007-02-01
This sourceforge project seems to have made a cygwin port of mahjongg:
[http://sourceforge.net/project/showfiles.php?group_id=67909](http://sourceforge.net/project/showfiles.php?group_id=67909)

Cygwin is a Linux-like environment for Windows
[http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by mikewhatever on 2007-02-01
There are Firefox and Open Office for Windows. You might wanna do a search and make sure, before installing something else.

---

### Post by gh0st on 2007-02-01
> **annda said:**
> as far as i know you will have to run a virtual machine, like VMWare (player).

Yeah a virtual machine with Ubuntu installed running on your Windows PC is the only way I know of doing this. You can get VMware server for free off the website and it allows you create virtual machines, install an OS and use it in a window on your host machine.

You do have to sign up to get a serial number for VMware server but it wasn't much hassle when I did it and they don't hammer me with spam or anything. I get the odd email about a VMware conference or something. VMware Player is also free and you don't need a serial for that I don't think. I can only only run virtual machine that have already been created though, it won't create them. You can download pre-built Appliances from VMware website, you could get one with Ubuntu and just use the Mahjongg (can't spell that sorry :D ) game.

Have a look here - [http://www.vmware.com/download/](http://www.vmware.com/download/)

You have to scroll down a bit the free products are at the bottom. There are other VM platforms available as well but I don't know much about them, you might wanna look around.

Unless someone more knowledgeable can tell you a way to run the program on Windows natively of course. Good luck

---

### Post by igknighted on 2007-02-01
I heard KDE is going to make a port fo their libraries for Mac OS X and maybe windows too (something about QT4 being usable cross-platform) so in the future KDE apps may have this ability.

---

### Post by gh0st on 2007-02-01
> **igknighted said:**
> I heard KDE is going to make a port fo their libraries for Mac OS X and maybe windows too (something about QT4 being usable cross-platform) so in the future KDE apps may have this ability.

That would be cool 8-)

---

### Post by hito1 on 2007-02-01
> **tkjacobsen said:**
> This sourceforge project seems to have made a cygwin port of mahjongg:
[http://sourceforge.net/project/showfiles.php?group_id=67909](http://sourceforge.net/project/showfiles.php?group_id=67909)

Cygwin is a Linux-like environment for Windows
[http://www.cygwin.com/](http://www.cygwin.com/)
Thanks for the quick answer, guys.

Could you please explain more how this cygwin works, tkjacobsen?

---

### Post by tkjacobsen on 2007-02-01
actually i have never tried it myself -- Have no windows installation to use it on... But i know several people who uses it to run linux apps on windows.

---

### Post by igknighted on 2007-02-01
> **gh0st said:**
> That would be cool 8-)

Heres a link to what they're planning:
[http://dot.kde.org/1168899755/](http://dot.kde.org/1168899755/)

---

### Post by irish_flu on 2007-02-01
Cygwin is a tool (installed on Windows boxes) that makes it easy for developers to port Linux apps to Windows.  You can't just install "any" Linux app, they have to be recompiled from source in order to take advantage of Cygwin.

There is also a tool called MinGW )and a sister app called MSYS) that helps you to generate and configure "make" files to help Linux apps work in Windows.

I didn't find MinGW very easy to use (in fact, I found it quite difficult to use) but I might have felt differently if I were the sort of dude who regularly recompiles Linux applications.

There is also "GTK+ for Windows", which installs the same toolkit as is used for creating GUI apps in Gnome.  Applications utilizing this include GIMP and GAIM for Windows.

[http://www.gimp.org/~tml/gimp/win32/](http://www.gimp.org/~tml/gimp/win32/)

Still, I am pretty sure that apps have to be built from source to use GTK+ in Windows (I'm not really clear on that).

---

### Post by hito1 on 2007-02-01
I realize my safest chance is to get one of those horrible-clunky-buggy-sluggish-with-unnecessary-3d-and-undistinguable-untasteful-tiles flash/java based mahjong then. :(

But thanks anyway, guys. :D

(I'll whine at gnomemahjong .com: "we windows users are people too! we're a significant part of computer users! make a port of your game to windows! :p)

---

### Post by kn000bie on 2008-07-10
colinux

andLinux?

---

### Post by carolus on 2008-07-11
To see what you can do with Cygwin, look at the package list on the Cygwin website.  

Roughly, Cygwin gives you nearly all of the command-line tools, compilers, and scripting tools of linux right out of the box.  If a command-line tool is not in the package list, it can often be built from source exactly as on linux. If you want those to be handy without having to reboot, and to use the linux tools on a Windows NTFS file system with no risk, Cygwin is great.

There is an x-windows emulator, but the choice of GUI stuff is limited. Of course, popular Linux programs are sometimes available as Windows ports, often built with the help of Cygwin.

---

