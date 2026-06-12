---
title: "Screen resolution keeps changing itself"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by kgeil on 2006-09-08
Hi, I've been working on this problem for a bit now:
I recently installed ubuntu and updated the nvidia graphics card drivers, following the directions given in the faq pages.  My problem is that if I go to system preferences/screen resolution, the only resolution option is 640X480.  So, I followed some instructions I found somewhere (I'll really have to start documenting better I know) to edit the xorg.conf file.  Under display, I replaced 640X480 with 1024X768.  I restarted, and voila! my screen resolution was what I wanted.  The funny thing is, on my next restart, the 640X480 res was back, and no way to change in system preferences.  So, having already backed xorg.conf, I went a bit crazy, and changed every instance of 640X480 to 1024X768.  This did change my resolution as I desired, until restarting a few times, and now, I can't change my screen res through system preferences, AND there is nothing left to change in xorg.conf, as far as I can tell.  This is a problem for me, by the way, because on many windows, the apply or ok buttons are not on the screen, and I have to guess on which one to tab to and hit enter.  

Once again, any info will be greatly appreciated!!!

Thanks,

Kevin

---

### Post by kgeil on 2006-09-08
So, as an update, I followed Halitech's instructions from a previous post, which I'll paste below.  I set screen res to 1024X768, but when I restarted, the resolution was 800X600, which is better, but not what I need.  By the way, what is the command to restart x?

Thanks,

Kevin

from a post here:

[http://www.ubuntuforums.org/showthre...ght=resolution](http://www.ubuntuforums.org/showthre...ght=resolution)

Open terminal and copy and paste command below:

sudo dpkg-reconfigure xserver-xorg

And select which res's you want
__________________
I reject your reality and substitute my own - Adam Savage
"Linux is just like an indian tent: no Gates, no Windows and an Apache inside..."
Registered Linux User #347519
Reply With Quote

---

### Post by Metacarpal on 2006-09-08
Hitting Ctrl+Alt+Backspace will restart your X session.  Make sure you save all data before hitting it, as that also logs you out.

---

### Post by wekebu on 2006-10-16
Kevin,
Did you ever find a solution?  I have the same problem. I've tried several steps to no avail.  For now, I have found that whenever this happens, if I reboot, it's okay. I turn off the computer every day.  Some days when I turn it on, it's okay, some days the resolution is at 640 x 480 with no other selections. After a reboot, when the settings are correct, I've gone into Screen Resolution and selected Make Default for This Computer.  Still doesn't keep the settings consistently. I've also selected Save Current Setup at Log Off/Shutdown.](*,) 

Wendy Kelly Budd

---

### Post by traverse on 2007-02-27
I too have the same problem. I'm using a Matrox G400/450 series card tho.

Any help on this would be great.

---

### Post by Malcolm on 2007-04-26
I have the same problem as well. I switch off my computer every night; when I turn it on in the morning, the resolution will sometimes be correct, more often it will be 640x480 with no other choice. After a reboot, it's back to normal.

---

### Post by lepz on 2007-04-26
> **Malcolm said:**
> I have the same problem as well. I switch off my computer every night; when I turn it on in the morning, the resolution will sometimes be correct, more often it will be 640x480 with no other choice. After a reboot, it's back to normal.

Do you have the restricted drivers manager enabled? are you using nvidia? have you set uo the nvidia settings?

---

### Post by u.b.u.n.t.u on 2007-04-26
The entire xorg automation system needs to be fixed and it is being looked into.

---

### Post by Malcolm on 2007-04-26
No, I don't use any restricted drivers, all of my hardware is recognised without problems or need to tweak anything (onboard graphics card is a VIA Technologies KM400/VT8378 ).

---

### Post by chrono13 on 2007-11-27
Ubuntu 7.10

I know this is an old thread, but I am having the same problem, and haven't been able to find a solution.

About a week ago I set my resolution down to 1024x768 to do a recording of my desktop. I set it back to 1440x900. I made the mistake of actually using Screens and Graphics (ugh).
Now it won't stick.

Here is part of my current xorg.conf

```

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

```

Upon startup, it removes all resolutions from Xorg other than 640x480. This is what you see above.

This is my** current** xorg, and I am running at 1440x900 with this xorg. Screens and Graphics shows many, many resolutions, many that my monitor can not support (320x240 through 2048x1536).

Yes, I have backed up my xorg, and performed a dpkg-reconfigure xserver-xorg

It is not sticking, and forces me to fix everything every single time I restart my computer.

Anyone else having this problem? Any idea's on how to set my resolution and get it to not rewrite xorg incorrectly every time I restart?

---

### Post by Hatchetfish on 2007-11-29
so, given that 'Screen and Graphics' seems to be an utter mess for the time being, anybody have any ideas on how to make it take a hike and leave my settings alone, at least until it's sorted out in 8.04 or so?  I can tweak xorg.conf to make X sit up and beg, but with this dastardly thing in the way, it seems to be largely ignored.  I'm not generally much for opposition to graphical 'friendly' config tools, but I really have to register my utter disdain for broken ones that (evidently) stand in the way of the canonical method to configure something, and have no way to tell them to bow out.

---

### Post by Hatchetfish on 2007-11-29
yep, same problem.  more or less.  mine will stick to the right res (2048x1536) but it picks a refresh rate randomly and usually wrongly, with the effect of both near siezure inducing flicker (it should be illegal to sell video cards that output 50Hz...)  and nice black borders around the screen.

my girlfriend's system can't stick to the right resolution though.  

i've seen no solution so far, but I've been hunting for a way to tell screen and graphics to get lost, so i can just set it in xorg.conf, like i always have.  i'll post anything i discover here.

---

### Post by chrono13 on 2007-12-04
Please, is there a bug number for this?

ls /etc/X11/
```

app-defaults             xorg.conf~                xorg.conf.8
cursors                  xorg.conf.1               Xresources
default-display-manager  xorg.conf.2               xserver
fonts                    xorg.conf.20071119064501  Xsession
rgb.txt                  xorg.conf.3               Xsession.d
X                        xorg.conf.4               Xsession.options
xinit                    xorg.conf.5               XvMCConfig
xkb                      xorg.conf.6               Xwrapper.config
xorg.conf                xorg.conf.7

```

It makes a convenient count of times that it hits. Among these auto-backups, it somehow failed to ever backup my original, good and working xorg. Logging out drops me to a GDM so low-res that what is being typed can't be seen. I avoid logging out, restarting or shutting down for almost any reason because of this bug.

Tonight when this hit, I reconfigured xorg to only have 1400x900 and no others.
This was promptly blown away and I was forced to use Screens and Graphics, which thankfully this time had 1400x900 (along with a dozen others). I can't seem to get it to this correct resolution without in some what using S&G, once I get S&G to list the correct resolution of course.

There are some parts of this that are not predictable (whether S&G will have 1400x900), while others are (log out/in and xorg.conf is hosed).

Is it S&G that is doing this? Xorg shooting itself? Any information, bug number, other threads to track, etc would be helpful. Thanks.

Very thankful for the info so far. Sad to see I'm not alone in this issue though.

---

### Post by Hatchetfish on 2007-12-04
If there is a bug#, i'm not aware of it.  I've been meaning to file one, but haven't, partly because I'm not sure what package it should be for.  

To get a relatively sane xorg.conf, you could try 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

without the -phigh option it leaves edits in, whether they came from you or S&G (or as i've started referring to it, The Evil Thing)

---

### Post by chrono13 on 2007-12-05
From my ls, you can see that I've done a dpkg-reconfigure and it didn't stick.

This issue however is FIXED for me.

How I fixed it (overly detailed for anyone else who may run into this)
System / Administration / Screens & Graphics.
1. Changed Plug & Play to LCD 1400x900
2. Checked Widescreen.
3. Changed to 1400x900.
4. Logged out. Resolution was 1400x900 for GDM.
5 Logged in, resolution was 1024x768 for Gnome.
6 System / Preferences / Screen Resolution - changed to 1400x900. Resolution was now 1400x900.
7. Logged out and back in - resolution remained at 1400x900

My hardware
lspci
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Monitor:
Hanns G HW191D 

Anyone having any monitor or resolution issues that the above does not fix should check [this]("https://help.ubuntu.com/community/FixVideoResolutionHowto") first. And then of course extensively search the forums.

Thanks everyone. I hope this solution helps someone else too.

---

### Post by Hatchetfish on 2007-12-05
Sorry, I realize you said you'd done the reconfigure, you just didn't mention whether you'd used the --phigh option, so thought i'd point it out, since it's easy to miss (advice on the forums here often as not leaves it out so that the menus are presented, whereas you mention having lost your default xorg.conf)

I also didn't mean to imply that it would stick, I know quite well it doesn't, just that it would restore a (relatively) sane xorg.conf, to be copied elsewhere or whatever, since yours was lost.

the only thing i've found so far for more than one session is pretty much exactly your process of 'change in s&g, logout, login, change in s.r.' but that still only works for three or four sessions and then has to be repeated.  hope it sticks for you, but it's not a permanent fix for me.

---

### Post by skyjacker on 2007-12-05
Same problem here. I use kubuntu, and every time I restart I have to reset mt resolution.

---

### Post by crispycritter911 on 2007-12-17
Mine did the same thing this morning. I'm using the Nvidia Legacy drivers with 7.10 for about 3 months now. I have Compiz enabled. As far as I know there no updates from last night. For some weird reason it went from 1024x768 back to 640x480. I tried dpkg-reconfigure xserver-xorg but made it worse.

I managed to get xorg working by copying the first back up of xorg.conf over the messed up one. I hope it doesn't keep doing this. This computer is a Xmas gift for my grandmother and she live about 2 hours away.](*,)

---

### Post by W3stinat0r on 2007-12-31
I'm having very much the same problem:

 - Old ECS KM400-M2 (Via VT8378 Northbridge chipset)
-  Ubuntu 7.10
 - Just bought an Acer 22" W and a Samsung 24" W.  

Both monitors revert to 1280x960 (what kind of res is that anyway!?!) after reboot.  

Setting the Samsung to 1920x1200 then logout-login freezes X - all i get is bckground color - have to reboot and back to 1280x960 it goes!

One odd thing that no one else has mentioned before is that when I do try to change the res in Screen Resolution Preferences, it changes, but the desktop blows up to bigger than the actual display.  Checking the display info on the monitor itself, it reads as 800x600...  

At this point I'd assume its the driver for the VIA chipset (maybe not WS compatable?)... Does anyone know of a more recent driver than what's available on the VIA site?  Is this the one Ubuntu installs automatically the most recent?

If I don't get this resolved I'm going shopping for a new graphics card - any suggestions?!?!?  I don't want to throw good money at bad, but at this point, I dropped $400 on the 24" monitor, I'd like to make full use of it!

Thanks,

---

### Post by Toadmund on 2008-01-30
I've been having this problem again as well.
My xorg.conf keeps resetting itself to a non-ATI driver version giving me something like a 600x480 resolution with no other res options.
I have to run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and go into 'restricted driver manager' and re-enable my driver.

I just want my xorg.conf to stay as it is, but it wont.

---

