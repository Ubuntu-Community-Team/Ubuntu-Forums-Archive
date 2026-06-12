---
title: "Need Urgent Help"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-08-12
Ok, so my Ubuntu was running fine. I installed some things from automatix; everything was running smoothly. I decided to reboot to see if the nVidia driver would allow me to use my video card. I went into the BIOS and changed "video adapter" to "AUTO" instead of "on-board." I booted up, and it froze at "Loading hardware drivers..." It's done this before, so I thought it wasn't a problem. I rebooted, re-entered the BIOS, and changed the video adapter back to "on-board." This time, when I booted up, my screen is all blue with random letters on the sides of the screen, and an error message in the middle that reads:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to see the X server output to diagnose the problem. <YES> <NO>?"

I clicked <YES> and this is the next screen:

> "X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol version 11, revision 0, release 7.0
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux kyle-desktop 2.6.15-26-386 #1 Preempt
Thu Aug 3 02:52:00 UTC 2006 i686
Build date: 16 March 2006
             Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
             to make sure that you have the latest version
Module loader present
Markers: (--)probed, (**)from config file, (==)default setting, (++)from command line, (!!)notice, (II)informational, (ww)warning, (EE)error, (NI)not implemented, (??)unknown.

(==)log file: "/var/log/xorg.0.log", Time: Sat Aug 12 20:29:55 2006
(==)using config file: "/etc/X11/xorg.conf"

                                         <OK>"

I click <OK> and this is the next screen:

"Would you like to view the detailed X server output as well? <YES> <NO>"

I click <YES> and it shows me the exact same screen as before ("X Window..."). I click <OK> at the bottom of it again, and this is the next screen:

"The X server is now disabled. Restart GDM when it's configured correctly <OK>"

I click <OK> once again, and now the screen goes black, and white letters appear:

"Ubuntu 6.06.1 LTS kyle-desktop tty1
kyle-desktop login: kyle
password: *******
/LINUX

[...]

The programs included with the Ubuntu system are free...

[...]

kyle@kyle-desktop:~$ "



Ok, this all really freaks me out because I've been working on my computer and setting up Ubuntu for the past few days. I believe it wants me to edit the xorg.conf file, but I don't know how to do it (basically, what to type here, because it seems like a terminal). If you have any advice, it would be extremely helpful! I will worship you forever if you help me fix this!!!

---

### Post by kebes on 2006-08-12
Things to try:

1. Set your BIOS settings back to the way they were when things were working (I know you already did this, but double-check). Do a complete system shutdown, count to ten, and boot up again. If the problem persists...

2. On the commandline (which is all you have access to right now!), try to force the graphic session to start anyway. Type:
$ startx
or:
$ gnome-session

If you boot into your desktop, then that's good. If not, check if the error messages have anything new/different to say.

3. Go to the X11 directory:
$ cd /etc/X11
and see if there are any backups of the "xorg.conf" file:
$ ls -laF
They might be named "xorg.conf.old" or "~xorg.conf" or something like that.

4. Look at the differences between the current xorg.conf and the older ones. There is a commandline program called "diff" that can help you do this. Use the program "nano" to open up the files. Copy the current file somewhere:
$ mv xorg.conf xorg.saved
and then try one of the other ones:
$ mv xorg.conf.old xorg.conf
and then reboot. An older copy might work!


If there are no older copies of "xorg.conf", then go into your current one and look at the settings. See if anything looks "strange" .. you can paste the contents of your xorg.conf here if you like.

Also go into the log file "/var/log/xorg.0.log" and see what it says. It should have some specific error messages. They may have to do with drivers being missing or options like that. Again paste pertinent info here.


You can also try editing the "xorg.conf" file. There are many online guides for how to do this. (But be careful!). Something simple to do is find the section "Screen" and see the display modes available. You can try changing the "DefaultDepth" to something simpler and reduce the available resolution in the corresponding Mode line. So instead of trying to boot into 1600x1200 at 24-bit, it will boot into 800x600 16-bit. This is just to get booted properly... you can re-configure your display later.


I know this isn't a "solution" yet... but hopefully it will get you closer to a solution.

---

### Post by confused57 on 2006-08-12
See this link, check out #9 near the bottom:

[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

To edit the xserver file:
```
sudo nano /etc/X11/xorg.conf
```

An interactive way to edit:
```
sudo dpkg-reconfigure xserver-xorg
```

You can get to a console command prompt by pressing Ctrl+Alt+F1.

If you need to stop or start gdm:
```
sudo /etc/init.d/gdm stop
sudo etc/init.d/gdm start
```

You might want to select the generic drive  "vesa" until you can get the correct drivers installed.

Edit: Yes, you might want to backup your xorg.conf file first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by kbsuperstar on 2006-08-12
Thank you SO MUCH! Sorry that I'm such a newb, ha. You guys are my saviors!

---

