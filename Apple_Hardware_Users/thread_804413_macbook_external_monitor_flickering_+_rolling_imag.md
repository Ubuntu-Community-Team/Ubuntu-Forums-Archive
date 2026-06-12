---
title: "macbook external monitor flickering + rolling image"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by kristof_v on 2008-05-23
Hi,

I followed some guides to get my external 22" screen working on my Macbook with Xrandr1.2.
I'm using the intel driver.

When I set the external screen image next to, above or below the macbook screen with xrandr everything works fine,
but when I only want to get an image on the external screen like so:

xrandr --output VGA --mode 1680x1050 --output LVDS --off,
it seems to work at first, but after a second the screen starts flickering and rolling pretty bad.
It's impossible to read anything on it.

Any ideas??

Gr

---

### Post by Joeb454 on 2008-05-23
I can't see why the guide wouldn't work. Can you post a link to the guide so we can see what you've done/tried already :)

---

### Post by kristof_v on 2008-05-23
This is the guide I followed:

[http://ubuntu-tutorials.com/2008/04/28/extended-display-on-the-macbook-with-xorg-conf-ubuntu-804/]("http://ubuntu-tutorials.com/2008/04/28/extended-display-on-the-macbook-with-xorg-conf-ubuntu-804/")

---

### Post by liquus on 2008-06-13
> **kristof_v said:**
> This is the guide I followed:

[http://ubuntu-tutorials.com/2008/04/28/extended-display-on-the-macbook-with-xorg-conf-ubuntu-804/]("http://ubuntu-tutorials.com/2008/04/28/extended-display-on-the-macbook-with-xorg-conf-ubuntu-804/")

this guide worked great for dual monitor but this prevents from using compiz.. 

also, if anyone else is using ubuntu on their macbook out there, and trying to use just the external monitor, you might have similar experience with flickering/rolling images where you can't see anything.

For me, i noticed that when i play a video file, it stops flickering.. 
so i added a random video file to play at start up (system -> preference -> sessions).. after few sec of video playing, you can close out of your video player and it should stop flickering.  This works for me, so I hope it works for you.

---

### Post by tobixyz on 2009-01-14
Hi,

I've the same problem here on my macbook 2,1. I'm using intrepid.
Does somebody have another solution to this than playing a video file?

Thanks a lot

tobixyz

---

### Post by stromdal on 2009-01-31
Bump

---

### Post by tobixyz on 2009-05-13
hi,
i can now use my external monitor. i found the following solution somewhere, but i don't remember where...
before i connect my dvi-monitor i have to turn off compiz, then plug in the monitor and with ```
xrandr --output TMDS-1 --mode 1680x1050 --output LVDS --off
``` i turn the internal screen off and the external on.
but when i turn compiz on again i get the flickering. then i execute the following commands in a terminal ```
xrandr --newmode dummy 75.00 1280 1301 1333 1408 800 804 808 816 -hsync -vsync
``` and ```
xrandr --output VGA --mode dummy
``` and the flickering is gone.

---

### Post by tiagobt on 2009-05-13
tobixyz,

The commands you posted gave me the following output:
```
$ xrandr --newmode dummy 75.00 1280 1301 1333 1408 800 804 808 816 -hsync -vsync
$ xrandr --output VGA --mode dummy
xrandr: cannot find mode dummy
```

Trying the first command again, the error changes:
```
$ xrandr --newmode dummy 75.00 1280 1301 1333 1408 800 804 808 816 -hsync -vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  27
  Current serial number in output stream:  27
```

What am I doing wrong?

I tried to turn the internal screen off with desktop effects enabled and disabled, but the flickering prevails.

Thanks,
Tiago

---

### Post by tobixyz on 2009-05-14
try ```
xrandr --addmode VGA dummy
```between the last two commands.
if the flickering remains try to execute again ```
xrandr --output VGA --mode dummy
```

---

### Post by tiagobt on 2009-05-15
I've now tried the following sequence of commands:

```
xrandr --newmode mymode 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
xrandr --addmode VGA mymode
xrandr --output VGA --output LVDS --off
```

But the flickering remains. Am I missing something?

The modeline I'm using was generated with the following command:

```
gtf 1680 1050 60
```
(1680x1050 @ 60.00 Hz)

Thanks again,
Tiago

---

### Post by tobixyz on 2009-05-17
hi,
are you using a vga screen? i'm using a dvi screen and then have to put this dummymode on the vga-output and the settings for the external screen on TMDS-1.

tobixyz

---

### Post by DwayneWayne on 2010-01-09
I have found the solution to this tiring problem. I am running the final Ubuntu 9.10 on a MacBook 2,1 and I can successfully fix this issue with a 100% success.

You need to do the following (remember to disable mirrored monitor first):
1. Plug in your external monitor
2. Start your MacBook and start boot into Ubuntu
3. Close the lid of your MacBook
4. You have now booted in and logged in (the flickering is now present)
5. Now, restart your machine and boot into Ubuntu (DO NOT OPEN MACBOOK LID!!)
6. Your now booted into Ubuntu again, the flickering is gone!

This I am able to do with success.

I have an SyncMaster 226BW and my MacBook is a revision 2,1.

I hope this helps others as well as it helped me!

I have also posted this in the original bug-thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377598](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377598)

---

### Post by linuxopjemac on 2010-01-10
question: how to you restart while having the lid closed ? Isn't your machine sleeping then ?

---

### Post by DwayneWayne on 2010-01-11
> **linuxopjemac said:**
> question: how to you restart while having the lid closed ? Isn't your machine sleeping then ?

No, if an external screen is connected it will not sleep, at least not on my system. The trick here is to restart the system while the lid is closed, it will restart with the main screen disabled and the external screen enabled.

I've found an even easier solution: You press the MacBook powerbutton and then instantly close the lid. It boots only with the external screen enabled and it will work the same way. You can do this if you already have the external monitor properly set up in Desktop settings in Ubuntu.

---

