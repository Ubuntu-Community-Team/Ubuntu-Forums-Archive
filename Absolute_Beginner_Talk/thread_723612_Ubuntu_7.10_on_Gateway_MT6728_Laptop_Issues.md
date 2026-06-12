---
title: "Ubuntu 7.10 on Gateway MT6728 Laptop Issues"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by AsWeAre2 on 2008-03-13
**Hi Everyone,**

I've been dual-booting XP/Ubuntu on a desktop for a year or two now - I've always used this forum and found the right answers right away. Even though I've been using it I can't say I've really explored into the guts of Linux itself because I'm basically a simple personal/light user. This is, however, the first laptop I've ever owned so I wasn't really familiar with how to shop for a linux compatible laptop. At this point I CAN switch to XP and be content, but I'd be way above content if I can get Ubuntu working, even for just the basics.

I've tried searching through google, digg, this forum, other forums, linuxlaptops, and every manufacturer I could find in association with this laptop and I just can't make sense of all of it but I think there has to be some kind of solution somewhere, so that said, forgive me if this has been answered before, but here goes:

I rebooted with LiveCD in drive, booted into LiveCD just to see what issues what come up, becuase I expected some. 

I can post whatever stats you need for now I can start with this:
**Model:** Gateway MT6728 Widescreen ACPI x86
**Processor:** Intel Pentium Dual CPU T2330
**Wireless Adapter:** RTL 8187B (Apparently the worst kind for Linux?)
**Display Adapter:** Mobile Intel 965 Express Chipset Family

**[COLOR="Lime"]WORKS:[/COLOR]** Sound, Basics (Keyboard, Touchpad, USB Mouse), Screen, Wired Ethernet Connection
[COLOR="Red"]**DOES NOT WORK: **[/COLOR]Wireless, Widescreen (I can get it to span but it stretches instead of adjusting)

I hope that's enough info, I apologize for the long post, any help would be appreciated - newbie lingo would really be appreciated. *Thanks in advance!*

---

### Post by jcwmoore on 2008-03-13
which version of ubuntu are you using, I guess both as a dual boot and the live cd?

---

### Post by AsWeAre2 on 2008-03-13
Gutsy on the laptop, was using Dapper on the desktop, but I no longer have the desktop.

EDIT:
These are the hardware [specs]("http://www.gateway.com/product_spec.php?product_recid=529667876") from Gateway if that helps:

---

### Post by jcwmoore on 2008-03-13
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-01/msg02519.html]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-01/msg02519.html")

looks like the exact same issues.
I suspect the resolution is probably just set to a none wide screen by default

---

### Post by AsWeAre2 on 2008-03-13
I will try the NDISwrapper thing. I did read that before but I found so many different instructions on how to do it, hopefully I can figure it out. Thanks!

I'm not sure what you mean about a "none wide screen by default" - sorry...

---

### Post by jcwmoore on 2008-03-13
i'm guessing that the live cd is defaulting the resolution to something like 1024 X 768 (a "none wide screen" ratio) rather than wide screen ratio like 1280 X 800.  I have a wide screen laptop and can change the resolution between these two.  the wide screen ratio look natural, but the 1024 X 768 looks stretched and weird...

---

### Post by AsWeAre2 on 2008-03-13
OK, as soon as I get out of class here I'll try it out, thanks for your help, hopefully I can get this working soon - I'm just not a fan of Vista.

---

### Post by WeAreMany on 2008-03-13
as for the wireless it will be easy,
 like they said the you need the  NDIS wrapper



Just go to the Applications>>Add/Remove>>search>" NDIS">>select "windows Wireless Drivers">>apply Changes
###
while its downloading go find the WINDOWS XP drivers for your wifi card.  
###
unzip your wifi drivers some where safe /home/mydrivers/yarg
 you will need the .sys and .ini from your drivers
###
Then SYSTEM>>Administration>Wireless (or something forgot to be honest...)
select the drivers that you want to install.  (the .ini)



#############################
As for the Monitor thing...



[http://ubuntuforums.org/archive/index.php/t-631526.html](http://ubuntuforums.org/archive/index.php/t-631526.html)

December 4th, 2007, 04:10 PM
You edit it in your xorg.conf file.

in /etc/X11/xorg.conf you will find resolutions for different color depths. So you can just change the ones that are there to something you want.

Say eg mine say:

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation G80 [Quadro NVS 135M]"
Monitor "Standard skjerm"
DefaultDepth 24
SubSection "Display"
Modes "1440x1050"
EndSubSection
EndSection


If I wanted eg 1920x1200 resolution I could just change it there..


If you are running a nvidia card the nvidia-settings configurations utility is pretty good.

To run it you type gksudo nvidia-settings

---

### Post by pvfjr on 2008-03-16
Hi, not to hijack, but I might be buying this same laptop used.  Did you have any other issues with it?  Card reader?  Multimedia keys?  Does this laptop have any multimedia outputs, if so do they work?

---

### Post by AsWeAre2 on 2008-03-16
Update:
OK, I got the driver installed via ndiswrapper. I had to install it command line to get it to work, but it did. It immediately recognized my home network, I entered in our WEP key, and then I got 0 bars. When I select the network it shows almost 70% strength, but when I log-in to the network I get 0 bars and therefore 0 connection. I tried refreshing, rebooting, the whole nine. I'm sitting next to the router so I know my signal strength is OK, and Vista was getting "excellent" strength.

I've been searching through the forums and I can't find anything about signal strength that seems to apply here, any help?

Also, I still can't get the widescreen to format properly, the background spans the screen, but the actual workspace is still the basic aspect ratio in the upper left corner of the screen, any help with that, maybe more detail on how to change that file because it doesn't seem to let me do that if I just open the file.

Thanks for any help, I'll be checking back shortly.



> **pvfjr said:**
> Hi, not to hijack, but I might be buying this same laptop used.  Did you have any other issues with it?  Card reader?  Multimedia keys?  Does this laptop have any multimedia outputs, if so do they work?
I'm only running on LiveCD and haven't really attempted anything multimedia wise in Ubuntu. I'm not a gamer at all so if you're wondering about that I don't think I can help, sorry!

---

### Post by pvfjr on 2008-03-17
Yeah, I hear you.  Games are evil, and the end of a good computer usually.  Deal fell through though, so it's a moot point. :( Thanks for the reply though.

---

### Post by lokasennasam on 2008-03-19
I have the same problem with the same laptop. I can connect to wireless networks without encryption. And my monitor still doesn't display the desired resolution after fiddling with the xorg.conf. [[COLOR="Red"]Xorg log[/COLOR]]("http://loki.sdf1.org/Xorg.0.log")

---

### Post by AsWeAre2 on 2008-03-27
Sorry, this is 1/2 a bump and 1/2 I still can't get this figured out.

I stopped trying for a little while but I would really like to be able to switch completely still.

Anyone know how I can configure Ubuntu to not just recognize my wireless but to be able to use it properly and receive signal?

Still can't get widescreen working either.

---

### Post by irregardlessly on 2008-06-04
Hey guys,

I have this same laptop and had the same 2 problems.  I never fixed the wireless, but I will try ndiswrapper shortly.  I was able to fix the screen resolution issue though with the help of this thread:

[http://ubuntuforums.org/showthread.php?t=610407]("http://ubuntuforums.org/showthread.php?t=610407")

Let me know if you are able to fix it with that.  If not I will upload my xorg.conf so you can see exactly what I did.  It was a long time ago but if I recall I just followed that thread.

---

