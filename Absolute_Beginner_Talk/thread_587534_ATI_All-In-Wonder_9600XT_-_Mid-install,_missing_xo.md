---
title: "ATI All-In-Wonder 9600XT - Mid-install, missing xorg.conf?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by BCoon on 2007-10-22
I haven't been heavily using Ubuntu like I thought I would.  New to Linux, plus I've been slammed in school lately (case study due tomorrow, haven't started, typing this up while I'm waiting for the Adderall to kick in - yes I have a prescription).  ANYWAY, since I didn't have much invested in Feisty, I decided to try an upgrade to 7.10 Gutsy.. 

Trying to get this card working correctly - ATI All-in-Wonder 9600XT.  I was going to use the guide for Linux on the ATI website specific to this card, but I figured the Gutsy specific guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") would work better.

So on a fresh install (haven't updated anything through the update manager), I started from the top.  After getting through the "method 1" section, I got confused on what steps I should follow in "method 2".  I figured "Method 2: Install the 8.40.4 Driver Manually" would be more accurate than 1, so I followed that from the beginning.  Everything worked out fine, I rebooted where it said to at the beginning of the "Configure the Driver" section.  I get to the part: ```
sudo aticonfig --initial
``` and I get this ```
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

```  Obviously something is wrong.  So, I go look at it in gedit, and it's blank.  No idea how this happened, but I followed the guide step by step.  I could edit it in the beginning of the guide as it says, but I can't now.

Can I generate a default one somehow and start this guide from the top or would doing it over mess with settings or config files somehow?

FYI, I looked around to see if I was missing anything, here is my terminal after the above: ```
brandon@hpubuntu:~$ cd /etc/X11
brandon@hpubuntu:/etc/X11$ ls
app-defaults             rgb.txt  xorg.conf~            Xsession
cursors                  X        xorg.conf.original-0  Xsession.d
default-display-manager  xinit    Xresources            Xsession.options
fonts                    xkb      xserver               Xwrapper.config
brandon@hpubuntu:/etc/X11$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
brandon@hpubuntu:/etc/X11$ $fglrxinfo
brandon@hpubuntu:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

```

---

### Post by BCoon on 2007-10-22
I went into the file browser, opened up xorg.conf.original-0, and it has the lines added I followed at the beginning of that guide I linked to above.

Why would my xorg.conf be deleted while this was labeled original?

Thank you for your help, sorry for my ignorance.

---

### Post by Luis_vxd on 2007-10-23
Open a terminal window an type in
'sudo dpkg-reconfigure -phigh xserver-xorg'
this will rebuild your xorg.conf file and take it from there. Reboot and see.

---

