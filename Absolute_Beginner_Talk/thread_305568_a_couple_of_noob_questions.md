---
title: "a couple of noob questions"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by dude420 on 2006-11-23
I'm a linux noob w/ only a couple of days experience.  Lovin it so far.  I just have a couple of stupid questions though.
1. First - I know how to change directories in linux - cd whatever - but how do you go back a directory?  I know in dos it is either cd.. or cd\ but these don't work in linux.  
2.  Second - I have gotten ubuntu to work on my desktop, but when i tried installing on laptop I get error message "Failed to start the x server(your graphical interface)
It is likely it is not set up correctly. Would you like to view the x server output to diagnose the problem?"
I have ran xserver config a couple of times using different settings with same results.  I have even tried alternate cd and dapper, still same thing. ](*,)  Running dimension 2600 laptop w/ Intel 830MG integrated graphics.  Had somewhat similar problems when I installed xp pro, had to install driver for integrated graphics before things looked right. When I was playing with alternate cd i got ubuntu to install and xserver would not run, but it did get me to a log on prompt and let me login.  My question is - Is there an intel driver in .deb format that I can use and where is it?  And also will this solve my problems.  I have spent a couple of hours on google looking, but can't seem to find.  Only finding .rpm.  Would use alien to convert, but it says not to do with system specific programs or something. Please help and thx.

---

### Post by eeGhoong0ais on 2006-11-23
```
cd ..
``` (note the space) will take you up one level in the directory tree. ```
cd -
``` will take you back to the last directory you visited, but repeating it will bring you back, so it doesn't act like a browser's "back" button.

No idea about drivers, sorry ...

---

### Post by fishpie on 2006-11-23
Hi,
I might be able eo help you with your graphics problem. Please post the contents of your /etc/X11/xorg.conf and /var/log/Xorg.0.log files

---

### Post by jon419 on 2006-11-23
> **fishpie said:**
> Hi,
I might be able eo help you with your graphics problem. Please post the contents of your /etc/X11/xorg.conf and /var/log/Xorg.0.log files

Not sure how much you know about editing files in Linux from the command line, but whenever I install Ubuntu on my computer I get the same basic error as you do.  The problem is (for me) the default driver that is selected by Ubuntu never works.

I have to go to the command line and edit my /etc/X11/xorg.conf file.

I then look for the following section:
```
Section "Device"
     Identifier "Name Of Card"
     Driver "bad bad driver"
EndSection
```

I change that bad bad driver to a very basic driver such as vesa.  Then I save the file and run the command startx (not as super user).  That will allow me to start X with a basic driver and then I can use apt (Synaptic, whatever) to download the correct drivers.

I am new to this whole Ubuntu thing, but that is what I have to do anytime I install Ubuntu on my computer.  The bad driver Ubuntu tries to use is ati (not fglrx).

So anyway, if you have any questions about my post, ask away.

---

### Post by dude420 on 2006-11-24
Actually like I said earlier I am really new to linux.  Been hardcore windows fan for years until I saw the light.  So honestly I know little to nothing about linux except its pretty cool and some basic dos commands don't work like dos.  If you could please walk me through how to list contents of xorg.conf/xorg.0.log so I can post them I would be very greatfull.  I figured out how to get to file but I don't know what to do with it or how to open it.  And by the way thx for taking the time to help a stranger. :D

---

### Post by compwiz18 on 2006-11-24
Ok.  I can't help you more then to tell you how to edit files and stuff.

To edit a file in the terminal, run **nano /name/of/file**.  I'm not sure how much you know about permissions, but in order to edit /etc/X11/xorg.conf, you will need to be the superuser, which you can do by **sudo nano /name/of/file**.  So to edit /etc/X11/xorg.conf, use **sudo nano /etc/X11/xorg.conf**.  Find the line specified in the earlier post, switch the name, then use Ctrl+X to exit nano.  Make sure you save the file.  Then type startx and press enter.  Tada! You *should* have a working display.  If you need more terminal help, just ask :D

edit: for reference, some other basic commands:
[LIST]
[*]**cd** - change directory (you already know that)
[*]**ls** - list all the files in a directory
[*]**cat a_file** - output the contents of a file to the terminal
[*]**top** - display the top CPU using programs
[*]**mv old_file new_file** - move a file
[*]**cp old_file new_file** - copies files
[/LIST]

---

### Post by Voxxi on 2006-11-24
> **dude420 said:**
> Actually like I said earlier I am really new to linux.  Been hardcore windows fan for years until I saw the light.  So honestly I know little to nothing about linux except its pretty cool and some basic dos commands don't work like dos.  If you could please walk me through how to list contents of xorg.conf/xorg.0.log so I can post them I would be very greatfull.  I figured out how to get to file but I don't know what to do with it or how to open it.  And by the way thx for taking the time to help a stranger. :D

Heres a way to do it in the graphical interface, slightly easier than nano. ;) 

To post your /etc/X11/xorg.conf:

Get into a terminal (Applications -> Accessories -> Terminal)

1. Type in:
```
gedit /etc/X11/xorg.conf
```

Remember, the case is important.

2. Select all the text and copy/paste it into your forum message.

To post your xorg.log:

1. Type in:
```
gedit /var/log/Xorg.0.log
```

Remember, the case is important.

2. Select all the text and copy/paste it into your forum message.


If you want to edit your xorg.conf, you need to be root.

To edit the files using Gedit :

1. Type in:
```
**sudo** gedit /etc/X11/xorg.conf
```

It will ask you for a password, the password is the password you use to logon.

What sudo does is run the command as the user "root". Root is like Administrator in Windows XP. But be VERY careful when you're root, its easy to mess up your system if you don't know what you're doing, but with some help from all of us, you'll be a command-line pro before long. ;)

---

### Post by compwiz18 on 2006-11-24
I thought the idea was that the X server wasn't working, but maybe I read something wrong...anyhow, nice explanation of how root works.  Mine was horrible.

---

### Post by Voxxi on 2006-11-24
> **compwiz18 said:**
> I thought the idea was that the X server wasn't working, but maybe I read something wrong...anyhow, nice explanation of how root works.  Mine was horrible.

WHOOPS! You're right I didn't read it properly. I had a moronic moment.](*,)  Still, its useful information to know when you're using the graphical interface and you don't feel comfortable with editing files on the command line.

By the way dude420, how are you posting on the forum?

EDIT: Just thought of something that might be useful to you, Linux equivalents of DOS command line programs.

Anyone know any? I'm not familiar with DOS.

---

### Post by compwiz18 on 2006-11-24
Yeah, that info would've been useful when I first started Linux...

And I don't know DOS either...

---

### Post by dude420 on 2006-11-24
O.K. I did what you said earlier with the nano but versa is already the driver selected.  I have run sudo dpkg-reconfigure xserver-xorg several times and played w/ most of the settings hoping for a better result.  Keep getting same result.  I would post the contents of xorg.conf and xorg.0.log, but I dont know how to do that from the command line and that is all I have to work with.  Right now I am typing on windows desktop (have multi comp setup) and my problems are on my laptop so thats how i am able to post at all and I would type out files but man that would take forever.  Is there a couple of lines in general you would like to see that I could write down and type out?  Like I said earlier I got ubuntu to work on desktop and thought it was great, I just was hoping i could  make it mobile.  Is there a .deb intel 830mg driver out there that I am just not finding that I might be able to download and install from the command line?  Thx again for help you guys are awesome.

---

### Post by dude420 on 2006-11-24
If I download the .rpm intel driver and use alien to make .deb would this work safely?  The .rpm file says for use with these releases
 

SuSE Linux Professional 9.0 w/Kernel 2.4.21-144-default

SuSE Linux Professional 9.1 w/Kernel 2.6.4-54-default

SuSE Linux Professional 9.1 w/Kernel 2.6.4-54-smp

SuSE Linux Professional 9.2 w/Kernel 2.6.8-24-default

SuSE Linux Professional 9.2 w/Kernel 2.6.8-24-smp

Mandrake 10.0 w/Kernel 2.6.3-7mdk

Mandrake 10.0 w/Kernel 2.6.3-7mdksmp

RedFlag Linux Desktop 4.0 w/Kernel 2.4.20-8

RedFlag Linux Desktop 4.0 w/Kernel 2.4.20-8smp

TurboLinux Desktop 10.0 w/Kernel 2.6.0-6

TurboLinux Desktop 10.0 w/Kernel 2.6.0-6smp

RedHat Enterprise Linux Workstation v.3 w/Kernel 2.4.21-4.EL

RedHat Enterprise Linux Workstation v.3 w/Kernel 2.4.21-4.ELsmp

and with these graphics chips
    *

      Intel® 830M Chipset
    *

      Intel® 830MG Chipset
    *

      Intel® 845G Chipset
    *

      Intel® 845GE Chipset
    *

      Intel® 845GL Chipset
    *

      Intel® 845GV Chipset
    *

      Intel® 852GM Chipset
    *

      Intel® 852GME Chipset
    *

      Intel® 855GM Chipset
    *

      Intel® 855GME Chipset
    *

      Intel® 865G Chipset
    *

      Intel® 910GL Express Chipset
    *

      Intel® 915GV Express Chipset
    *

      Intel® 915GM Chipset
this is about all I could find for drivers for linux and intel.

---

### Post by dude420 on 2006-11-24
Also found something about xfree86.  Is it possible this might help?

---

### Post by dude420 on 2006-11-24
Well I have gotten xserver to work in agp with 8 bit color.  It's a start but still not very usefull.  Begining to think this is more trouble than it is worth.  With 8 bit I can only really use the terminal.  All other boxes open up so big you can only see menu options.  :confused: When I went to synaptic package manager to try to get updates it said I had no internet connection.  I'm hoping mabey, just mabey if I can get net connection to work and update that it might dl a fix for me.  So my next question is how do I get linux to detect my dsl.   thx again for help

---

### Post by maxxis on 2008-06-17
hi there, i have a similar problem as dude, ive a sony vaio r505gl and since 3 days i play around with the graphic, its the same chip set from intel, 830gm , always i just can use 800*600 (what is set when i made the installation), when i turn it to the real 1024*768 it shows me only blackwhite screen,what looks like a hubble picture.ive no idear please could you help me? could i past the xorg,config file and the log file here?

---

