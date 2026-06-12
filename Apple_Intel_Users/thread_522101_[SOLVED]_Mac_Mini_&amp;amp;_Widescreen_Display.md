---
title: "[SOLVED] Mac Mini &amp;amp; Widescreen Display"
date: 2007-08-10
forum: Apple Intel Users
---

### Post by koboldx on 2007-08-10
Hi there

I own a Mac Mini with a 1.83 GHz CPU and a Intel GMA 950 graphics processor.running Ubuntu Gutsy. Initially I had an Acer 20" 4:3 Display and everything was working like a charm. Recently I got a new Display (ACER AL2216W - 1680x1050 Widescreen) and the problems started. When I press the "on" button, this usual white screen shows up, after that: nothing. My display just sais: "No Signal". However if I plug in my old screen it works.

My standard boot process now looks like this:(  ::
Boot having the old screen attached, as soon as i see "Grub loading" I switch the screen to the new one, when i reach the login manager I start fumbling around with "dpkg-reconfigure xserver-xorg", editing xorg.xonf and 915resolution... Usually I manage to get a good looking login screen (My display tells me its 1680x105[COLOR="Red"]3[/COLOR]), however after entering my password the display goes blank (Input out of range)...after 30 more minutes of fumbling around I usually manage to log in and take care to not turnoff the computer until the evening ;) .

So basically for me it's like having a difficult display configuration and having to redo everything everytime I boot because in order to boot I need to reattach an old screen...



Does anyone have an Idea? Thanks in advance.

Cheers, Kobold

---

### Post by ivesjd on 2007-08-10
so is your xorg setup just not being saved across boots?

---

### Post by cyberdork33 on 2007-08-10
sounds like the timings are not correct.

Need to lookup the appropriate VertRefresh and HorizSync values for your monitor (just google), and probably comment out the DPMS line.

Also, make sure you are using the 'intel' driver, as opposed to the i810 driver. The intel driver, i think, does not need 915resolution to work correctly.

---

### Post by koboldx on 2007-08-12
Hello
Thank you for the fast replys.

ivesjd: The xorg configuration is being saved across boot, but since I need to attach the old (smaller) monitor in order to get the mac mini to boot, it seems to mix everything up... Allthough I have no idea why.

cyberdork33: Ill try the config this evening, thank you. 
But the boot issue (which seems to be the source of my problems) cannot really be resolved by editting the xorg.conf, right? The xserver doesent come into play until I see the login manager I think?

---

### Post by koboldx on 2007-08-12
I was able to resolve the issue. 
It seems that the macmini + dvi cable + "weird" display wont work. 

Solution: DVI->VGA adapter, then a VGA cable. Now everything works fine.


Thanks for you efforts guys. 
Cheers, Koboldx

---

### Post by ivesjd on 2007-08-12
What was your setup before? As in what cables were you using?

---

### Post by koboldx on 2007-08-13
I tried two different DVI cables (one bought, on delivered with the monitor I was trying to use).

Cheers

---

### Post by weezel on 2007-08-14
> **koboldx said:**
> Hi there

I own a Mac Mini with a 1.83 GHz CPU and a Intel GMA 950 graphics processor.running Ubuntu Gutsy. Initially I had an Acer 20" 4:3 Display and everything was working like a charm. Recently I got a new Display (ACER AL2216W - 1680x1050 Widescreen) and the problems started. When I press the "on" button, this usual white screen shows up, after that: nothing. My display just sais: "No Signal". However if I plug in my old screen it works.

My standard boot process now looks like this:(  ::
Boot having the old screen attached, as soon as i see "Grub loading" I switch the screen to the new one, when i reach the login manager I start fumbling around with "dpkg-reconfigure xserver-xorg", editing xorg.xonf and 915resolution... Usually I manage to get a good looking login screen (My display tells me its 1680x105[COLOR="Red"]3[/COLOR]), however after entering my password the display goes blank (Input out of range)...after 30 more minutes of fumbling around I usually manage to log in and take care to not turnoff the computer until the evening ;) .

So basically for me it's like having a difficult display configuration and having to redo everything everytime I boot because in order to boot I need to reattach an old screen...



Does anyone have an Idea? Thanks in advance.

Cheers, Kobold

Try this one: install 915resolution (apt-get install 915resolution) 
Then run it: sudo 915resolution -c 5c 1680x1050
and edit your /etc/X11/xorg.conf video driver section.
Change the driver to i810. Now try again.

---

### Post by cyberdork33 on 2007-08-14
> **weezel said:**
> Try this one: install 915resolution (apt-get install 915resolution) 
Then run it: sudo 915resolution -c 5c 1680x1050
and edit your /etc/X11/xorg.conf video driver section.
Change the driver to i810. Now try again.

This is old... the Intel driver now works on Mac hardware. 915 resolution was a workaround.

---

### Post by weezel on 2007-08-15
> **cyberdork33 said:**
> This is old... the Intel driver now works on Mac hardware. 915 resolution was a workaround.

When they've fixed it? At least few time ago it didn't work. It went out of sync. I think I'll give a shot for intel again..

---

### Post by cyberdork33 on 2007-08-15
> **weezel said:**
> When they've fixed it? At least few time ago it didn't work. It went out of sync. I think I'll give a shot for intel again..

I am not saying it will fix your sync problems as that might be another issue... i.e. vertrefresh / horizsync values

915resolution was a workaround to get proper resolutions, the intel driver now allows the resolutions.

---

### Post by el_baby on 2007-12-28
> **koboldx said:**
> I was able to resolve the issue. 
It seems that the macmini + dvi cable + "weird" display wont work. 

Solution: DVI->VGA adapter, then a VGA cable. Now everything works fine.

Hi, I'm having what I think is the [same problem](http://ubuntuforums.org/showthread.php?t=651230)...

I'm using the original DVI->VGA adaptor that comes bundled with the mini. My monitor has a VGA cable. Do you think that a different DVI->VGA adapter will work?

Which one are you using?

TIA

---

### Post by el_baby on 2007-12-28
FWIW, a $10 DVI/VGA brandless adaptor replacing the original one from Apple solved this problem (and another one regarding non being able to use the mouse when grub bootstraped).

---

