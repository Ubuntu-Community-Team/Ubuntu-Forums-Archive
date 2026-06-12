---
title: "N53 startup display issue"
date: 2012-04-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nonoland on 2012-04-04
Hello,

I have many troubles with Ubuntu on my new N53S laptop. Thanks to this forum, I've already found solutions for some issues (sleep and hibernate issues - thank you), but I have difficulties to find help about the display issue I encounter at start up.

As a video is better to all textual description, please have a look at this :
[http://youtu.be/zFyKdWU6IeM](http://youtu.be/zFyKdWU6IeM)

So, I have a "frightening" display at start up. I hear the Ubuntu start up sound.
When I press [ctl] + [alt] + [F1], no ascii login is displayed.
The only way to get out of this situation is to make a long press on power button to restart the computer.
This display issue at start up occurs 1 time out of 2, approximately.

My computer has 2 GPUs:
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)

I think that this is the Intel one that is used, because:
~$ grep -i nvidia /var/log/Xorg.0.log
[    20.615] (II) Module glx: vendor="NVIDIA Corporation"
[    20.615] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[    20.946] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
.... Moreover I can see many "Intel" keywords in this Xorg log file.

Does someone have the same issue and do you have an idea how to solve it ?
For information, I am a software developer, so I'm used to work with computers, but I don't have so much skills in Linux administration.

Thanks in advance,

---

### Post by Paddy Landau on 2012-04-05
The last time I had an issue like this, it was a hardware error, something to do with the "matrix" in the screen. As with you, it happened (at first) sometimes, but it became more and more frequent. I had to get an external monitor.

If you can plug in an external monitor, that would give you more information.

---

### Post by nonoland on 2012-04-11
Thank you Paddy Landau for you answer... It's a good starting point for my investigation.
You're right, external display is working when I have this issue.

So, I analyze the /var/log/Xorg.0.log file and found differences with a one created on a successful startup, at the end of the log file.

Here is the end of a successful log file:

```
[    18.316] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    18.316] (II) No input driver/identifier specified (ignoring)
[    19.447] (II) intel(0): EDID vendor "SEC", prod id 12620
[    19.447] (II) intel(0): Printing DDC gathered Modelines:
[    19.447] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    20.061] (II) intel(0): EDID vendor "SEC", prod id 12620
[    20.061] (II) intel(0): Printing DDC gathered Modelines:
[    20.061] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    20.316] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    22.551] (II) intel(0): EDID vendor "SEC", prod id 12620
[    22.551] (II) intel(0): Printing DDC gathered Modelines:
[    22.551] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    35.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-598948634C34C8EA808C3E0E76E4114C06A24770.xkm
[    95.080] (II) XKB: reuse xkmfile /var/lib/xkb/server-598948634C34C8EA808C3E0E76E4114C06A24770.xkm
```
And here is the end of a failure log file:

```
[    18.408] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    18.408] (II) No input driver/identifier specified (ignoring)
[    25.609] (II) intel(0): EDID vendor "SEC", prod id 12620
[    25.609] (II) intel(0): Printing DDC gathered Modelines:
[    25.609] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    26.539] (II) intel(0): EDID vendor "SEC", prod id 12620
[    26.539] (II) intel(0): Printing DDC gathered Modelines:
[    26.539] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    26.818] (II) XKB: reuse xkmfile /var/lib/xkb/server-598948634C34C8EA808C3E0E76E4114C06A24770.xkm
[    29.283] (II) intel(0): EDID vendor "SEC", prod id 12620
[    29.283] (II) intel(0): Printing DDC gathered Modelines:
[    29.283] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    55.618] (II) intel(0): EDID vendor "SEC", prod id 12620
[    55.618] (II) intel(0): Printing DDC gathered Modelines:
[    55.618] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    55.865] (II) intel(0): Allocated new frame buffer 3200x1080 stride 12800, tiled
[    78.096] (II) XKB: reuse xkmfile /var/lib/xkb/server-598948634C34C8EA808C3E0E76E4114C06A24770.xkm
[    90.088] (II) Open ACPI successful (/var/run/acpid.socket)
[    90.088] (EE) intel(0): Couldn't create pixmap for fbcon
[    90.200] (II) intel(0): EDID vendor "SEC", prod id 12620
[    90.200] (II) intel(0): Printing DDC gathered Modelines:
[    90.200] (II) intel(0): Modeline "1920x1080"x0.0  138.65  1920 1944 1960 2080  1080 1082 1087 1111 -hsync -vsync (66.7 kHz)
[    90.333] (--) ETPS/2 Elantech Touchpad: touchpad found
[    90.619] (II) XKB: reuse xkmfile /var/lib/xkb/server-598948634C34C8EA808C3E0E76E4114C06A24770.xkm
```

I notice 2 things :
- time elapses differently
- more lines in the failure log file

But I'm afraid the lines added at the end are due to the external display plug... 

What kind of logs can I analyze to follow on my investigation ?

---

### Post by Paddy Landau on 2012-04-12
As far as I know, it's a hardware error. Error logs won't help you.

Your laptop is new, so you should be able to get it repaired under guarantee.

---

### Post by nonoland on 2012-04-12
Really !!!!
But, my laptop has been sold with Windows 7.... Do you think ASUS won't answer to me "You computer has not been made to run Linux, we don't care about your problem" ?????

How can I be 100% sure that this is an hardware issue ?

Thanks again for your help

---

### Post by Paddy Landau on 2012-04-13
Do you still have Windows to boot off? If you boot with Windows, do you still get the problem?

That will help narrow it down.

---

### Post by nonoland on 2012-04-13
Yes I have a double boot (Win7 / Ubuntu). But I never had the issue starting Windows... :-/

---

### Post by Paddy Landau on 2012-04-14
> **nonoland said:**
> Yes I have a double boot (Win7 / Ubuntu). But I never had the issue starting Windows... :-/
In that case, it is **not** a hardware problem. I am sorry to have misled you earlier.

The problem would most likely lie in the driver. The driver -- or, possibly, the settings -- that Linux has for your laptop screen is incorrect.

What happens if you run Ubuntu from a Live CD or USB? Download the 12.04 Beta to find out whether or not it works.

Unfortunately, this is not an area I am expert in, so I'm not sure how much help I'd be able to give you.

---

### Post by 23dornot23d on 2012-04-14
You have a Hybrid Graphics setup ....

> 
My computer has 2 GPUs:
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)


This means the computer will use the Intel graphics to save power and the Nvidia 555
card for more demanding applications .....

What is usually needed is a driver that supports this function.

The Ironhide driver was the one I used to sort my problem out .... this is a Blog
that explains a little about it .... but it is quite old now ....

[http://linux-hybrid-graphics.blogspot.fr/2011/08/ironhide-branch-first-release-including.html](http://linux-hybrid-graphics.blogspot.fr/2011/08/ironhide-branch-first-release-including.html)

The time I set mine up was in January 2012 ,,, some information is here as I
tend to keep a record of what I do - in case I need to go back and sore problems
out .....

[http://ubuntuforums.org/member.php?tab=visitor_messaging&u=953253&page=42#visitor_messaging](http://ubuntuforums.org/member.php?tab=visitor_messaging&u=953253&page=42#visitor_messaging)

The latest Ubuntu seems to pick my Graphics up better now - I am now using 12.04 development version ( the proper 12.04 is due out in 2 weeks time )

There is a Launchpad item set-up for people to join and help with problems - sometimes
there is some interesting information here as this is relatively new to Linux .....

May be worth joining it and letting them know the problems you encounter ....
as this will or should be more uptodate .....

[https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")

Best I can do for now ..... might be worth downloading the latest daily release 
and burn to CD and see if it works for you ..... 
( I use Kubuntu though as it seems better for me )

This is the Daily Build Link and is for Testing only ..... [[COLOR=Blue]_**LINK**_[/COLOR]]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/")

But if it works ok for you and your setup ...... it may be a solution ..... and as I
say ...... in 2 weeks time and the Official Release is due out .....

[http://www.kubuntuforums.net/showthread.php?57862-Kubuntu-12-04-LTS-release-date](http://www.kubuntuforums.net/showthread.php?57862-Kubuntu-12-04-LTS-release-date)

---

### Post by nonoland on 2012-05-18
Just to inform the community :
It's been few days I updated my Ubuntu version to 12.04 and I never encounter the issue again!!! :) I hope it is gone forever...
Thanks again for those who contribute to the resolution !!

---

### Post by BjornMolin on 2012-06-15
I have had exactly the same issue with 11.10 at my Asus N53. I am happy to hear that 12.04 will solve this. However, I have noticed two interesting things:

[LIST=1]
[*]Only the build in monitor is affected. An external monitor works fine.
[*]If you put the machine in stand by mode and after that wake it up, it will be normal again.
[/LIST]

---

