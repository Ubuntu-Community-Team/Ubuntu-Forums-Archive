---
title: "Unable to wake after suspend (gutsy)"
date: 2007-10-16
forum: Apple Intel Users
---

### Post by xIke on 2007-10-16
MacBook Pro, Core 2 Duo.
I had this problem in feisty too:

I can't wake my machine after I suspend, either by closing the lid, or manually suspending.  When I try to wake it back up, my external mouse will light up, but the built-in keyboard is unresponsive, and the screen is black.  I've looked at the screen from different angles and it isn't on and missing backlight, it's totally off.

I've searched the forums and looked at the wiki, but a lot of the advice is for feisty people to try gutsy.  I'm using gutsy, so what next?

Thanks,

---

### Post by xIke on 2007-10-19
Well, gutsy's officially out now.  Do other mac intel users have luck suspending their systems?  If so, did you do anything to get it working?

---

### Post by phonky on 2007-10-19
Same here,
no wake up after suspend on macbook pro.

what about hibernate? has this disappeared in gutsy? don't see the button
when the shut down dialog appears.

---

### Post by xIke on 2007-10-19
I have hibernate.  I haven't tried it because suspend is scary enough. :P

---

### Post by vloris on 2007-10-19
My laptop (IBM Thinkpad X23) used to suspend perfectly when I was using feisty. But now, after I upgraded to gutsy, after suspend, the backlight stays on, when I try to resume it, the screen turns off completely and my whole computer hangs.
No, it is not just the screen, network doesn't work (can't ping it from other pc), keyboard doesn't work (can't Ctrl-Alt-F1, Ctrl-Alt-Del to reboot).

---

### Post by entangled on 2007-10-19
I have a Intel Mac Mini. Using Feisty it would not suspend at all, just said not possible.
Gutsy does suspend but I can't revive it afterwards (unless I power cycle). It's a step forward but it would be nice if supend was conditional on being able to resume.

---

### Post by freakyfelt on 2007-10-19
I cannot resume from suspend or hibernate either (MBP Santa Rosa), the only major thing keeping me on Mac OS X.

---

### Post by theltemes on 2007-10-19
Suspend/Resume and Hibernate/Resume worked fine in Fiesty with my Rev 1 MacBook Pro, but both are now broken (it's locking up in the suspend/hibernate, so all I can do is rebot) with Gutsy. Very disappointing to say the least.

---

### Post by Mega_slayer on 2007-10-20
I am having the same problem as you guys have noted. I am using Gutsy with a "Intel 945GM" video card. What cards are you guys using? Should we file a bug? I think that I may search them.

---

### Post by xIke on 2007-10-20
Okay, supposedly it's a bug with fglrx.  I've quite a few ideas, thanks to the guys in #ubuntu.  I'll post back soon once I look into it a bit more.

---

### Post by lyndaj70 on 2007-10-20
I'm on Feisty, with a Toshiba laptop.  Have the exact same problem.  I can hibernate okay, but suspend is definitely broken...

I'm downloading the new gutsy now, but don't know if it will help....

---

### Post by rd42 on 2007-10-20
Same problem here, with a Core Solo Mac Mini. I'd love to get this fixed, as I am used to putting my computer to sleep.

---

### Post by xIke on 2007-10-20
Okay, here's what I've found, though none of it is working for me so far.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#If_suspend_is_not_working]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#If_suspend_is_not_working")
[Black Screen since resuming](http://ubuntuforums.org/showthread.php?t=539540)

I haven't tried the grub fix yet from that second link.  Going to do so now.

---

### Post by xIke on 2007-10-20
Still no luck.  I found a bug report in launchpad that sounds similar.  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/50031/comments/71]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/50031/comments/71")

---

### Post by [woodstock] on 2007-10-21
> **xIke said:**
> Okay, here's what I've found, though none of it is working for me so far.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#If_suspend_is_not_working]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#If_suspend_is_not_working")
[Black Screen since resuming](http://ubuntuforums.org/showthread.php?t=539540)

I haven't tried the grub fix yet from that second link.  Going to do so now.


Just to keep record:
The solution mentioned [here](http://ubuntuforums.org/showthread.php?t=539540) is working for a* MacBook Pro C2D with nvidia graphics card* (driver version 100.14.19)

_First, check if compiz is the cause!_

Press ALT+F2 and enter *metacity --replace*
Wait till the changes are applied.
Try to suspend the computer. If it resumes correctly then compiz is the cause of our problem.

This is the solution from the other post mentioned above:
> install via apt-get CompizConfig (if it isn't already)
then in **General Options** go to **Display Settings** and **disable Sync to VBlank**

This works with the following settings in xorg.conf
```
[...]

Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#additional settings
	Option		"NoTwinViewXineramaInfo"	"false"

	Option		"NoLogo"		"true"
	Option		"RandRRotation"		"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"OnDemandVBlankInterrupts"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"NvAGP"			"0"
	Option		"DamageEvents"		"true"
	Option		"UseEvents"		"true"
	Option		"TripleBuffer"		"true"

EndSection

[...]

Section "Extensions"
	Option	"DAMAGE"	"Enable"
	Option	"Composite"	"Enable"
	Option	"RENDER"	"Enable"
EndSection
```

---

### Post by Mega_slayer on 2007-10-21
I have my suspend working now. I followed this thread: [COLOR="Blue"][http://ubuntuforums.org/showthread.php?p=3523957#post3523957](http://ubuntuforums.org/showthread.php?p=3523957#post3523957)[/COLOR]

Quoting aldeby > ... also try changing some values in /etc/default/acpi-support most notable change should be changing POST_VIDEO=true to POST_VIDEO=false

The method [woodstock] used didn't work for me. I changed acpi-support, from POST_VIDEO=true to POST_VIDEO=false and now it is working. Hibernate is still giving me problems, however I do not use it.

---

### Post by madscientist032 on 2007-10-21
When I first used feisty, I remember being able to successfully suspend Ubuntu and then un-suspend it without any issues. I'm thinking that the issue here is a bug from a feisty update that made its way to Gusty. I suspend almost constantly, and hibernating is useless, as I dual-boot OSX and 7.10. I haven't tried any of the methods listed in this thread but when I do I'll post my results.

iMac 17 inch (Early 2006)
Intel Core Duo 1.83 Ghz
1 Gig memory (1 x 1 Gig)
ATI Radeon x1600 w/ 128 mb vram

---

### Post by theltemes on 2007-10-21
> **Mega_slayer said:**
> I have my suspend working now. I followed this thread: [COLOR="Blue"][http://ubuntuforums.org/showthread.php?p=3523957#post3523957](http://ubuntuforums.org/showthread.php?p=3523957#post3523957)[/COLOR]

Quoting aldeby 

The method [woodstock] used didn't work for me. I changed acpi-support, from POST_VIDEO=true to POST_VIDEO=false and now it is working. Hibernate is still giving me problems, however I do not use it.

POST_VIDEO=false didn't help out my suspend/hibernate issue.

---

### Post by Sunnz on 2007-10-22
> **theltemes said:**
> POST_VIDEO=false didn't help out my suspend/hibernate issue.
Same here, a nVidia card with Compiz enabled, Gutsy, whenever I tried to resume it during the time I have "POST_VIDEO=false" it just simply reboots.

---

### Post by theltemes on 2007-10-22
> **theltemes said:**
> POST_VIDEO=false didn't help out my suspend/hibernate issue.

Oh yeah, I forgot to mention: fglrx drivers, no Compiz stuff installed.

---

### Post by [woodstock] on 2007-10-23
> **Sunnz said:**
> Same here, a nVidia card with Compiz enabled, Gutsy, whenever I tried to resume it during the time I have "POST_VIDEO=false" it just simply reboots.

With a nvidia card, i.e. MBP rev.3, and compiz running try to disable sync to vblank in compiz settings as described above. This works in my case, however the tradeoff are tearing windows etc.

---

### Post by cyberdork33 on 2007-10-23
> **madscientist032 said:**
> When I first used feisty, I remember being able to successfully suspend Ubuntu and then un-suspend it without any issues. I'm thinking that the issue here is a bug from a feisty update that made its way to Gusty. I suspend almost constantly, and hibernating is useless, as I dual-boot OSX and 7.10. I haven't tried any of the methods listed in this thread but when I do I'll post my results.

iMac 17 inch (Early 2006)
Intel Core Duo 1.83 Ghz
1 Gig memory (1 x 1 Gig)
ATI Radeon x1600 w/ 128 mb vramIt is not a bug.
> **"Gutsy Gibbon Release Notes"]
**Suspend to RAM with fglrx**

 [LIST]
[*]  Attempting to suspend to RAM using the proprietary fglrx ATI video driver from the restricted component will hard-lock the system due to changes in the kernel's memory allocator (which will be the default in Linux 2.6.23) that have not been followed by ATI in a timely fashion said:**
> Bug #121653[/URL] 
[/LIST]

---

### Post by xIke on 2007-10-25
Wow.  By free ATI driver, I assume you're referring to the open source one?  The one that doesn't work for recent cards, like the x1600?

---

### Post by cyberdork33 on 2007-10-25
> **xIke said:**
> Wow.  By free ATI driver, I assume you're referring to the open source one?  The one that doesn't work for recent cards, like the x1600?
They are getting there, but yea.

I think if you get the older kernel from feisty (that does work) you can then suspend. You can also recompile the current kernel changing the SLUB option back to SLAB (I think, or maybe the other way around) which changes the memory allocation method.

---

### Post by madscientist032 on 2007-10-25
yeah, suspending did work in Feisty, but that was when the restricted drivers were off. I suppose turning them off in Gusty would have the same effect. 
Any idea how to completely turn off Compiz in Gusty?

---

### Post by cyberdork33 on 2007-10-26
> **madscientist032 said:**
> yeah, suspending did work in Feisty, but that was when the restricted drivers were off. I suppose turning them off in Gusty would have the same effect. 
Any idea how to completely turn off Compiz in Gusty?
Turn it off in System > Preferences > Appearance

---

### Post by kaiguy57 on 2007-10-27
I'm suffering from the same problem. Suspend and hibernate both do the same thing: the screen turns off completely and the keyboard stays backlit, and it's stuck until I manually power off the computer and do a cold reboot (by holding power button). I downgraded to the feisty kernel and turned off compiz fusion and it still stays :-(

---

### Post by dimeotane on 2007-10-27
So for now, we don't get to have the lovely visual effects? :(
I hope this gets fixed soon.  I need to be able to suspend my laptop reliably without having to reboot each time.  I loved showing off the cool visual effects to people.... "ooh it looks like a mac!"

---

### Post by bluetoad on 2007-11-01
> **lyndaj70 said:**
> I'm on Feisty, with a Toshiba laptop.  Have the exact same problem.  I can hibernate okay, but suspend is definitely broken...

I'm downloading the new gutsy now, but don't know if it will help....

What model of Toshiba do you have?  If you leave it for over 5 minutes does it suspend and resume?  If that is the case see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139045](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139045)

---

### Post by xIke on 2007-11-01
> **cyberdork33 said:**
> They are getting there, but yea.

I think if you get the older kernel from feisty (that does work) you can then suspend. You can also recompile the current kernel changing the SLUB option back to SLAB (I think, or maybe the other way around) which changes the memory allocation method.

Do you know of a good page that explains how to do this?  I know I could google or search this forum, but I've had some bad advice really make my life miserable before ("Envy is totally the best way to install video card drivers!!!")

---

### Post by cyberdork33 on 2007-11-01
> **xIke said:**
> Do you know of a good page that explains how to do this?  I know I could google or search this forum, but I've had some bad advice really make my life miserable before ("Envy is totally the best way to install video card drivers!!!")

Not really... The kernel compiling tutorial is in the FAQ.

---

