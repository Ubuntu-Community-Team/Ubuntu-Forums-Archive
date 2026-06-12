---
title: "X Server Error: video card won't display graphics"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by gordonsowner on 2007-11-11
Hi,

I'm putting Ubuntu on an older computer (2001 Gateway vintage).  Anyway, it's been in storage for a while, so I hauled it out and dusted it off.  Well, the install went ok, but I think my default video card has some issues, as I get some vertical lines that look like white noise on my display.

No problem I thought... I had a video card laying around from another computer.  I snapped it in and booted.  Well, I saw the bootup graphics ok (the Ubuntu symbol and the orange progress bar), but then I got an error and it gave me some output (with some messed up characters around the border)

```
Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly.
Would you like to see the X server output to diagnose the problem?

```
When I select 'Yes', this is first screen's worth of the diagnostic here:

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: 2.6.15.7 i686
Current Operating System: Linux pettis-linux 2.6.17-10-generic SMP #2
Friday Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 Jul 2006
  Before reporting problems, check http://wiki.x.org
  to make sure that you have the latest version.
Module loader present
Markers: (--) probed, (**) from config file, (==) default setting,
  (++) the command line, (!!) notice, (II) nformational
  (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) log file: "/var/log/Xorg.0.log" Time: Sunday Nov 11, 13:15:24 2007
(==) using config file: "/etc/X11/xorg.conf"
```

It then kicks me to a text only logon console.

Anybody have any idea if this is an Ubuntu issue that I can fix with some updated drivers?

---

### Post by Partyboi2 on 2007-11-11
you could try reconfiguring X.org
Back up your current one:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```then to reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```
:)

---

### Post by gordonsowner on 2007-11-12
Thanks!

followed your instructions so far... as i am scuttling a server i got, i have no idea what kind of video driver i have, nor what to select after executing the 'dpkg' command... the info i can read off of the card is:

64mb agp
e-geforce2 mx-400

can you tell me what this translates to in the drop-down list ubuntu is asking me to choose from (list too long to give full set of options)...

thanks,
matt

---

### Post by Partyboi2 on 2007-11-12
> **gordonsowner said:**
> Thanks!

followed your instructions so far... as i am scuttling a server i got, i have no idea what kind of video driver i have, nor what to select after executing the 'dpkg' command... the info i can read off of the card is:

64mb agp
e-geforce2 mx-400

can you tell me what this translates to in the drop-down list ubuntu is asking me to choose from (list too long to give full set of options)...

thanks,
matt

Its a [SIZE=-1]NVIDIA geforce2 mx-400
So choose NV,  if you have enabled restricted drivers then choose Nvidia
then work your way through the rest of the questions. After that restart X
Ctrl+Alt+Backspace
or
[/SIZE]```
sudo /etc/init.d/gdm start
```

---

### Post by gordonsowner on 2007-11-12
Worked, Thanks!

---

### Post by Partyboi2 on 2007-11-12
Happy to help
:)

---

