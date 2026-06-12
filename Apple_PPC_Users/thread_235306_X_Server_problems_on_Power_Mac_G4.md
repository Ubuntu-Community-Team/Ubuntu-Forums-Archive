---
title: "X Server problems on Power Mac G4"
date: 2006-08-12
forum: Apple PPC Users
---

### Post by meshica7 on 2006-08-12
Hello all,

 I recently tried to get XGL/Compiz going on my dual boot (Dapper/OS X) Mac G4. I followed some of the commande line how to's on the forums here and now I get a warning/message when I try to boot into Ubuntu.This is the message:

**[COLOR="Red"]Failed to start the X Server.It is likely that it is not set correctly.[/COLOR]**

Here are the instructions that I used:

[COLOR="Red"][COLOR="Red"][COLOR="RoyalBlue"]Configure GDM

Code:

sudo gedit /etc/gdm/gdm.conf-custom


And complete the servers section

Code:

[servers] 0=Xgl [server-Xgl] name=Xgl server command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx: pbuffer -accel xv: pbuffer flexible=true


4. Create startup script

Code:

sudo gedit /usr/local/bin/compiz-start


And paste the following code:

Code:

#!/bin/sh killall gnome-window-decorator wait gnome-window-decorator & compiz --replace gconf & cgwd --replace &


Make it exécutable :

Code:

sudo chmod +x /usr/local/bin/compiz-start[/COLOR][/COLOR][/COLOR]

 I then retarted my Mac.
By the way,I got this code from the following thread posted [here.]("http://www.ubuntuforums.org/showthread.php?t=225141")


Well, I suppose that I must have really screwed something up in the term somewhere! How do I remedy this as now I am only seeing a command line interface for mu Linux boot? Please keep in mind that I am a newbie to Linux and not very adept at the command line.I know very basic commands (cd,whoami,reboot,etc.).Will I have to reinstall Ubuntu from the CD? I hope not! I just got my DVD,MP3,and internet going in Ubuntu (plus a lot of apps and custome themes,icons,etc) and hopefully will not need to configure this again.
 Here is the type of video card my Mac uses according to my Apple System Profiler:

 ATY Rage Pro 128

 I have found all the answers here for other problems I have had and hope that you all can help this time as well! I really want to remain in my Linux environment (which I have been using for almost a month untill today). Till then,I will have to keep using my OS X dektop.

 thanx in advance!]

Juan

---

### Post by 3rdalbum on 2006-08-14
Type:
```
sudo dpkg-reconfigure xserver-xorg
```

And reconfigure your X server. If the Ubuntu installer detected your video hardware flawlessly, then it's safe to hit "Ok" when asked if you want to use autodetection. Then get rid of all the stuff that you added to the gdm.conf file.

Reboot, and you should be fine.

For all intents and purposes, XGL and Compiz won't work on a PowerPC.

---

### Post by meshica7 on 2006-08-14
Thanx for the tip!
I did the code and the video card was detected properly.No more compiz for me!I will wait till I get an Intel laptop.For now,Desktop 3D is pretty cool.Thanx for the help.:D 
juan

BTW Your blog states that you have XGL and Compiz working.Are you on a Mac?:shock:

---

### Post by stmiller on 2006-08-14
Errr. I have a Radeon 9600 128MB and can't get 3D working. I'd love to try out XGL.

---

### Post by Black Mage on 2007-09-20
Ok, now I have the same problem and on an intel lab, MacBook Pro(one of the newest ones bought August 2007) with a NVIDIA GeForce 8600M GT graphics with 128MB SDRA. It detects it NVDIA but it comes up at a generic brand only and then when I restart it, it the same problem of "Failed to start xServer."

Anyone have this problem before or any possible solutions?

---

