---
title: "Low Memory Install = small desktop?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by rkrakora on 2008-04-02
Good morning, 
I have just reanimated an old laptopToshiba Satellite 4090 [400MHZ Celeron, 6G Harddrive, 64MG RAM yikes!] with a fresh install of Xubuntu.  I utilized the text install disk, all was fine, though it did run in 'Low Memory Mode'.  

I also noticed that it didn't fully use all of the desktop space on the screen.  So 1/3 of the screen is a black frame around the desktop.  Is that because I'm so limited on memory, or am I missing a setting?  I've already ordered a 128MG stick to help the speed issue.  [that is the maximum]  I've attempted adjusting all of the display settings, 800X600 is where its set. 

Please let me know if there are any commands I could attempt so I can enjoy a full screen experience!

Thank you in advance!

Rich

---

### Post by wolfen69 on 2008-04-02
try adjusting the controls on your monitor. (horizontal and vertical size and position)

---

### Post by rkrakora on 2008-04-02
I tried using the function keys [F10] that should expand the desktop size but to no avail.  Where do I find those controls within Xubuntu?  Can I find in BIOS before booting up?

---

### Post by wolfen69 on 2008-04-02
you should have buttons on your monitor that control various things.

---

### Post by rkrakora on 2008-04-02
Thanks, its an older laptop, no additional buttons on the screen.

---

### Post by kerry_s on 2008-04-02
you need to adjust your xorg.conf.

but with 64mb of ram your using the wrong distro for those specs.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by rkrakora on 2008-04-02
Thank you kerry_s.  After I get the additional RAM, what is the step by step for adjusting the xorg.conf?

---

### Post by kerry_s on 2008-04-02
simple way:
in terminal run> **sudo dpkg-reconfigure -phigh xserver-xorg**

manual way:
press alt+f2
type> gksudo mousepad /etc/X11/xorg.conf

find the 800x600
change it to
1024x768

now if you got a non standard size display, you need to do the display size and the driver for your vid card. vesa only does standard sizes.

---

### Post by rkrakora on 2008-04-02
Interesting.... the terminal command yields a "md5sum: /etc/X11/xorg.conf: no such file or directory" message. [I'll need to redress this issue as well?]   However, running the alt-F2 command sent me to a screen, searched for 800X600, found 1024X768.  [hmm, no changes needed there?]

Perhaps its a driver issue, I will troubleshoot a bit tonight and respond again.

Thanks again, I really appreciate the help!

R.

---

### Post by kerry_s on 2008-04-02
> **rkrakora said:**
> Interesting.... the terminal command yields a "md5sum: /etc/X11/xorg.conf: no such file or directory" message. [I'll need to redress this issue as well?]   However, running the alt-F2 command sent me to a screen, searched for 800X600, found 1024X768.  [hmm, no changes needed there?]

Perhaps its a driver issue, I will troubleshoot a bit tonight and respond again.

Thanks again, I really appreciate the help!

R.

weird never seen that error before.
change the xorg so there's only 1 size, the size you want.
(my vid only does 16 colors, you can stay with 24 or what's there)

```
 Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection
```

---

### Post by rkrakora on 2008-04-05
Below is the results of running the first command line you posted above.  Im afraid I dont understand.

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080404225209

Any thoughts on this?

I am going to attempt the alt/f2 command after I updated my memory to the max [192MG] and also reinstalled Xubuntu.  

Rich

---

### Post by kerry_s on 2008-04-05
first tip, xubuntu is bloated! you might as well run the normal gnome install.

if you must use xfce4, use a different distro. i recommend debian->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

have you even tried a low resource distro yet?
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
the iso-> [ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso)

a good place to look->
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by N1N31NCHN41L5 on 2008-04-05
I went with puppy on the Older machine and found I had much more success than trying to run xubuntu. I am running Ubuntu 7.10 on 2 machines, xubuntu 7.10 on 1 , and puppy on the old machine. Again I found the best sucess on puppy for the old style comp.

---

### Post by rkrakora on 2008-04-05
Thanks, I did some research on Puppy and downloaded the .iso.  However, I'm not sure that will help my desktop issue.  What I need to determine is if its a driver/bios/hardware problem.  And/or is it the OS that is not configurable to my machine.  

R.

EDIT:  Honestly, the performance of Xubuntu isn't THAT bad @ 192K of RAM.  I just wish I could enjoy the pretty interface in all its glory.  Could my horizontal sync and Vertrefresh be a telling sign?

HorizSynch:  28-51
Vert Refresh: 43-60

Mode:  1024X768
Default depth: 24

---

### Post by kerry_s on 2008-04-05
> **rkrakora said:**
> Thanks, I did some research on Puppy and downloaded the .iso.  However, I'm not sure that will help my desktop issue.  What I need to determine is if its a driver/bios/hardware problem.  And/or is it the OS that is not configurable to my machine.  

R.

what?
is it more than just the screen and memory problem?

first just get a distro that runs well on 64mb ram, dsl is king, puppy needs at least 128mb. then just start getting your feet wet, learn the ropes, how linux works, yadyada...

your main problem is your trying to run stuff not made for your low specs, there's not enough room, sorta speak. things have requirements to function properly. just adding a new os is not magically going to turn your old laptop into a brand new speed demon, you need to face that a lot of things just won't work, things like flash in the browser, an up to date browser.

---

### Post by rkrakora on 2008-04-05
Sorry if that last post wasn't clear.  I now have 192K of memory [which should be marginal for xubuntu], so I'd prefer to keep Xubuntu, as its nice on the eyes.  My only problem at this point is the desktop not covering the laptop screen.  Its a small box in the middle.  

I've tried several of the suggestions above, but none have changed the desktop size.  I researched the Toshiba Satellite 4090XDVD model, it should be able to run 1024X768.  So hopefully I'll be able to resolve this problem.  

Thanks again.

---

### Post by kerry_s on 2008-04-05
> **rkrakora said:**
> Sorry if that last post wasn't clear.  I now have 192K of memory [which should be marginal for xubuntu], so I'd prefer to keep Xubuntu, as its nice on the eyes.  My only problem at this point is the desktop not covering the laptop screen.  Its a small box in the middle.  

I've tried several of the suggestions above, but none have changed the desktop size.  I researched the Toshiba Satellite 4090XDVD model, it should be able to run 1024X768.  So hopefully I'll be able to resolve this problem.  

Thanks again.

okay for that just edit the xorg.conf
you won't see no effect till you restart X, press ctrl+alt+backspace at the log in screen to restart X.

---

### Post by rkrakora on 2008-04-06
I ran the following again:

sudo dpkg-reconfigure xserver-xorg

in terminal.  What was ultimately successful was selecting the 'simple' configuration of the resolutions, selecting a LCD size [17"] and letting it figure out the rest.  So happy that things are working.  

kerry_s:  Thank you for responding several times.  I appreciate it very much.

Best, 
Rich

---

