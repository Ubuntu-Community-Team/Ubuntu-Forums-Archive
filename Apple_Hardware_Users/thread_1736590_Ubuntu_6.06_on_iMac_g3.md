---
title: "Ubuntu 6.06 on iMac g3"
date: 2011-04-22
forum: Apple Hardware Users
---

### Post by Blasphemous on 2011-04-22
I've got an old **iMac g3** on which I'd like to install **Ubuntu Dapper Drake.**

Here's the problem:
I insert the disk in the computer.
Keep pressing "C" till this comes out:
> "The default option is "live" bla bla bla but in case of problems use "Live video=ofonly"
I write "**Live**".
The orange progress bar appears, but the the **screen becomes bla**ck.
I still **can hear sound**s: the classic ubuntu log-in music, but I can not see anything: **I guess the live has started, but the screen is just black.**
By pressing CTRL-ALT-BACKSPACE I'm able to come back to shell.

Once rebooted, I try "**Live video=ofonly**".
Again the orange progress bar, but then this message comes out
> "Failed to start the X Server, It is likely that is not set up correctly. Would you like to view the server output to diagnose the problem?"
Even if I dont select anything, some random words appear in the screen, too fast for me to read them.
Then I'm back to shell.
 

I read here ([http://ubuntuforums.org/showthread.php?t=405934]("http://ubuntuforums.org/showthread.php?t=405934"))that the problem is caused by Xorg and that the solution can but editing his configuration by using 
> sudo nano /etc/X11/xorg.conf
But I just don't know **when** to do that: **Ubuntu is not installed yet** and there is only **MacOS 9.2 **on that machine.

Any suggestions?

---

### Post by Blasphemous on 2011-04-22
Solved!

Start the live-CD
Type: "live-powerpc"
Wait untill the system is loaded
Type CTRL-ALR-BACKSPACE
Follow the instructions listed below.

> Got it working with a quick text edit:

 drop to console (ctrl - option F1)

 and edit the X config file as follows:

sudo pico /etc/X11/xorg.conf
 or if you prefer:
sudo vi /etc/X11/xorg.conf
 (or your favorite editor)

 change the frequencies in monitor section as follows:

Section "Monitor"
 Identifier "Generic Monitor"
 Option "DPMS"
 HorizSync 60-60
 VertRefresh 43-117
EndSection

 restart X

Seen here [http://ubuntuforums.org/showthread.php?t=75604]("http://ubuntuforums.org/showthread.php?t=75604")

---

### Post by mondo2k on 2011-04-22
Yeah I stepped on that landmine earlier today. I had to use these specs in xorg.conf to get things going:

HorizSync 58-62
VertRefresh 75-117

---

