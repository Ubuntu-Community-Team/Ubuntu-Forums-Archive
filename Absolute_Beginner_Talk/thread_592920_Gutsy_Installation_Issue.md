---
title: "Gutsy Installation Issue"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by oni5115 on 2007-10-26
When installing 7.04 I had an issue on my other box where normal install would have an extremely distored ranbow screen of death.  I still get this in 7.10 sadly.  However, in 7.04 using safe mode for installation worked perfectly fine...  Unfortunately, 7.10 does not do the same.  =/

Safe mode gives me a jumbled screwed up looking screen, better than the non-safe mode by far, at least I can see orange and a mouse cursor (albeit fuzzy, and repeated).  

To get 7.04 working with nvidia drivers and effects and all that good stufff, I remember having to look up and manually input my horizontal and vetical sync frequencies because the default monitor did not match my ancient NEC multisync 5fge.

I've had similar graphical glitches with the  Clonezilla/GParted live CD, but I had no issues with that loading it using VESA drivers.  Is there a way to manually force the ububtu installation to do the same?  Or to manually force it to a certain horizontal/vertical sync?  I don't know the commands to do it.  :confused:

The disk passes the sumcheck scan just fine.  It works in my laptop without any problems as well.  Both use nVidia cards too, so I doubt its the video card itself.  Any advice on how to set those options, or ideas of what else it could be are certainly appreciated.

---

### Post by molly_001 on 2007-10-26
> **oni5115 said:**
> oni5115 wrote . . . 
 
When installing 7.04 I had an issue on my other box where normal install would have an extremely distored ranbow screen of death. I still get this in 7.10 sadly. However, in 7.04 using safe mode for installation worked perfectly fine... Unfortunately, 7.10 does not do the same. =/
 

 
When you install 7.10, try adding the following to the line of text which is provided (just before install) when choosing the safe mode:
 
nosmp maxcpus=1
 
It's also highly recommended to use the Alternate Install CD for 7.10 if you do not now do so.
 
[quote=oni5115]oni5115 wrote . . .
 
Safe mode gives me a jumbled screwed up looking screen, better than the non-safe mode by far, at least I can see orange and a mouse cursor (albeit fuzzy, and repeated). 
 
To get 7.04 working with nvidia drivers and effects and all that good stufff, I remember having to look up and manually input my horizontal and vetical sync frequencies because the default monitor did not match my ancient NEC multisync 5fge.
 
I've had similar graphical glitches with the Clonezilla/GParted live CD, but I had no issues with that loading it using VESA drivers. Is there a way to manually force the ububtu installation to do the same? Or to manually force it to a certain horizontal/vertical sync? I don't know the commands to do it. :confused:
 
[/quote]
 
After Ubuntu has loaded (again, I recommend a fresh install using the Alternate Install CD, with safe mode, and with the extra commands above) ... you can always get a command line interface at root level.  Do do this, after Ubuntu appears to have loaded and you have an orange screen, press simultaneously ALT + CTRL + F1 .  This will take you to the text-based command line interface.  Now type:
 
```
 
sudo dpkg-reconfigure xserver-xorg

```
 
 
This will allow you to enter a dialogue with the xserver where you can control the refresh rates of the adapter as it speaks to your monitor, and color depth, resolution, etc.  I strongly suggest looking below before entering into the xxorg dialogue.
 
copied from [http://tinyurl.com/35v4zc](http://tinyurl.com/35v4zc)

Preparation
To use this tool you will need to do a little preparation to ensure you have the info needed by **[B]dpkg**-**reconfigure** **xserver**-**xorg**[/B] as you will be asked a series of questions about your setup and hardware - read carefully these questions - often it is ok to leave the answer box blank (where it is suggested) or choose auto. 
[LIST]
[*]Graphics Card - ensure you have the correct drivers installed for your hardware before using this tool. Generic vesa/nv type drivers have limited capabillities and cannot do openGL/3D graphics
[*]Your Keyboard type - often PC104
[*]Mouse port connection - commonly /dev/psaux
[*]Server Modules to load - when using the official nvidia driver "nvidia" it is important to not load the module/section "Dri"
[*]Monitor Display Resolutions to be used
[*]Horizontal and Vertical Resolutions (-if you select Advanced when prompted in monitor setup section) - search the web if you don't have the manual/spec of your monitor
[*]Colour Bit Depth to use - 24 bit for most newer hardware[/LIST]It can be a lot to assemble blindly, so I would suggest that you choose nv for driver/adapter type, 1024x768 for resolution, and 16-bit color.  There are many other choices along the way, and it's best to just hit enter/next.

---

### Post by oni5115 on 2007-12-24
Just wanted to post a thanks for the help.  I never did it on my desktop since I just used Feisty and upgraded and that worked. But I ran into the same exact issue when trying to fix up my aunt's computer and was able to do full install from the Gutsy disk.  =)

---

