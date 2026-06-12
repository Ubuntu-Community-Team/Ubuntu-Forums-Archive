---
title: "Are the DPI settings for my monitor imported from Windows?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-19
UPDATE: I reposted with new info. Please go to the following thread: [http://ubuntuforums.org/showthread.php?t=478525](http://ubuntuforums.org/showthread.php?t=478525)


Hey, everyone, I have to make this quick, but I'd like some input. Here's the story: I have a brand new hard drive in one of the computers at home. Last night, I installed XP and all its stupid service packs and crap. Then, I rebooted with my Fiesty liveCD, clicked the Install icon, and the Install window came up. Strangely, I could not view the bottom of the window, and I could not resize it to get at the buttons. I also could not change the screen resolution from the GNOME desktop. I finally aborted the install and went to bed.

Can anyone tell me why this would happen? I have a hunch: Despite the fact that my ViewSonic VG150 is supposed to be set at 1024x768 with 96dpi, when I installed Windows I set it at 800x600 with 96dpi. Is it possible that Ubuntu imported this weird setup, and is not displaying the GNOME or Install window correctly as a result?

If not, what can I do to fix this problem?

Thanks!

---

### Post by dannyboy79 on 2007-06-19
no, it's not possible at all. You monitor will communicate with the graphics card. sometimes the ubuntu installer doesn't chose the correct driver for the gfx card and then you'll have problems. if you can't adjust the monitor itself (you can almost always widen, shrink both vertically and horizontally within the front buttons of any monitor) then I would suggest using the alternate install cd as it's text based. OR, there are instructions for editing the driver that the install will use by envoking the break=bottom kernel boot option found here: [http://ubuntuforums.org/showthread.php?t=389980](http://ubuntuforums.org/showthread.php?t=389980)

this is especially if you have an ATI card as in my example, I couldn't get the livecd to launch any video output.

---

### Post by reset3x on 2007-06-19
When I have this problem I go to the properties on each of the panels and choose autohide... That way I can at least get it installed... Then I reconfigure xorg with the monitor settings for vertical and horizontal refresh I get from the manufacturers website.... Just a thought :)

---

### Post by wonk-o-matic on 2007-06-19
No, the Windows setup is independent.  

Here's another link:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

If you don't get it working, get back to us with more specifics: graphics card or chipset, in particular.

---

### Post by samuraiCat on 2007-06-19
> **dannyboy79 said:**
> (you can almost always widen, shrink both vertically and horizontally within the front buttons of any monitor) [http://ubuntuforums.org/showthread.php?t=389980](http://ubuntuforums.org/showthread.php?t=389980)



That's the weird thing: I can see the bottom toolbar on the GNOME desktop, but the Install window dips beneath it and I can't move it up. Resizing the monitor via the buttons on the front of the monitor would not help.

---

### Post by samuraiCat on 2007-06-19
> **wonk-o-matic said:**
> No, the Windows setup is independent.  

Here's another link:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

If you don't get it working, get back to us with more specifics: graphics card or chipset, in particular.

Okay, the card in an nVidia GeForce FX5200 PCI card.

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> When I have this problem I go to the properties on each of the panels and choose autohide... That way I can at least get it installed... Then I reconfigure xorg with the monitor settings for vertical and horizontal refresh I get from the manufacturers website.... Just a thought :)

I'm sorry, but could you clarify? I'm not in front of that machine right now, and I don't know which "panels" you're talking about or how to access them. Thanks!

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> When I have this problem I go to the properties on each of the panels and choose autohide... That way I can at least get it installed... Then I reconfigure xorg with the monitor settings for vertical and horizontal refresh I get from the manufacturers website.... Just a thought :)

Can I reconfigure xorg from the liveCD so that I can continue the install?

---

### Post by arsenic23 on 2007-06-19
I don't think this is a software issue.  More then likely just hitting whatever button or function auto adjusts on the monitor will fix the issue.  On at least one of my machines if I boot into windows my *NEC AccuSync LCD72v* will auto adjust the screen to a perfect fit.  When I boot back into Ubuntu it fails to do this, and I end up with the bottom and the left of my screen hanging off the edge.  All I have to do to correct this is hit auto-adjust under the monitor's main menu.

This might not have anything to do with your problem (not being able to see your screen I can only guess ), but then again, it wouldn't hurt to try.

---

### Post by samuraiCat on 2007-06-19
> **arsenic23 said:**
> I don't think this is a software issue.  More then likely just hitting whatever button or function auto adjusts on the monitor will fix the issue.  On at least one of my machines if I boot into windows my *NEC AccuSync LCD72v* will auto adjust the screen to a perfect fit.  When I boot back into Ubuntu it fails to do this, and I end up with the bottom and the left of my screen hanging off the edge.  All I have to do to correct this is hit auto-adjust under the monitor's main menu.

This might not have anything to do with your problem (not being able to see your screen I can only guess ), but then again, it wouldn't hurt to try.

The strange thing is that I can see both the top and bottom GNOME desktop toolbars.

---

### Post by wonk-o-matic on 2007-06-19
I use that same gfx card with a generic monitor.  

You can set up xorg by doing a ctrl-alt-f1, logging in (root has no password, i think, you might want to google it), and doing: 

sudo dpkg-reconfigure xserver-xorg

---

### Post by wonk-o-matic on 2007-06-19
Oh, and there's the alternate install CD, which starts out in text mode.  And the usual install cd has the f6 key for boot options.

---

### Post by samuraiCat on 2007-06-19
> **wonk-o-matic said:**
> I use that same gfx card with a generic monitor.  

You can set up xorg by doing a ctrl-alt-f1, logging in (root has no password, i think, you might want to google it), and doing: 

sudo dpkg-reconfigure xserver-xorg

Cool! Can I do that from the liveCD via the terminal?

---

### Post by reset3x on 2007-06-19
> **samuraiCat said:**
> Can I reconfigure xorg from the liveCD so that I can continue the install?

He can adjust the vertical and horizontal settings all he wants with the buttons on is monitor and he will still have 800x600........

The panels are the two bars on the top and bottom of your screen... You can right click on them and choose properties... then choose auto hide.... When you get your sysem installed you may want to consider downloading Envy here: [http://albertomilone.com/](http://albertomilone.com/) and use Envy to get your nVidia drivers installed.... Envy will configure x for you automatically.... I have have good success this way... If there's an easier, softer way please clue me in.....

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> He can adjust the vertical and horizontal settings all he wants with the buttons on is monitor and he will still have 800x600........

The panels are the two bars on the top and bottom of your screen... You can right click on them and choose properties... then choose auto hide.... When you get your sysem installed you may want to consider downloading Envy here: [http://albertomilone.com/](http://albertomilone.com/) and use Envy to get your nVidia drivers installed.... Envy will configure x for you automatically.... I have have good success this way... If there's an easier, softer way please clue me in.....

Yeah, I'm going to try to set the monitor in Windows to 1024x768 and then reloading, just on the off chance that it works. Then I'll do the xorg.conf thing from the liveCD and hope it works.

---

### Post by reset3x on 2007-06-19
> **samuraiCat said:**
> Yeah, I'm going to try to set the monitor in Windows to 1024x768 and then reloading, just on the off chance that it works. Then I'll do the xorg.conf thing from the liveCD and hope it works.

Sorry but that will not help you... What you get in Win has nothing to do with it... Try what I suggest and see if that works...If not we'll go from there... I subscribed to this thread to keep an eye out for ya......

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> Sorry but that will not help you... What you get in Win has nothing to do with it... Try what I suggest and see if that works...If not we'll go from there... I subscribed to this thread to keep an eye out for ya......

Thanks! Okay, so scratch the Windows crap. Can I edit the xorg.conf file from the liveCD? Do I simply delete the resolutions from the "modes" lines below, as I read elswhere?
> Section "Monitor"
# HorizSync source: edid, VertRefresh source: edid
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Samsung SyncMaster" 
HorizSync 30.0 - 71.0
VertRefresh 50.0 - 160.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia" 
VendorName "NVIDIA Corporation"
BoardName "GeForce2 MX/MX 400"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0" 
Monitor "Monitor0"
DefaultDepth 24
Option "metamodes" "1024x768 +0+0; 1024x768_85 +0+0; 1280x1024 +0+0; 832x624 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0; 1024x768_70 +0+0" 
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection 

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> Sorry but that will not help you... What you get in Win has nothing to do with it... Try what I suggest and see if that works...If not we'll go from there... I subscribed to this thread to keep an eye out for ya......

Or would this work for me:
> Are you using a Nvidia card? If so, open a terminal (Applications --> Accessories --> Terminal) and type:

Code:
sudo nvidia-settingsChange your default resolution in there, and then click "save to xorg.conf file" to write the changes. Now your computer should be OK betweeen boots. 



---

### Post by reset3x on 2007-06-19
Are you trying to do an install or just check out the Live CD? I thought you we're trying to install.... I never tried fiddling with x running a Live CD.....

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> Are you trying to do an install or just check out the Live CD? I thought you we're trying to install.... I never tried fiddling with x running a Live CD.....

Yes, I am trying to install. The problem is that I can't get to those bottom buttons. The panels are not so large that autohiding them would make the buttons visible. I want to avoid the alternate install method, if possible.

---

### Post by reset3x on 2007-06-19
> **samuraiCat said:**
> Yes, I am trying to install. The problem is that I can't get to those bottom buttons. The panels are not so large that autohiding them would make the buttons visible. I'll try that anyway when I get home. However, do you think I can do the xorg.conf thing from the liveCD prior to the install? I'd have to, if I want to avoid the alternate install method.


I'd be doing you a disservice helping you config x from the Live CD.... And it's really not necessary to get Ubuntu installed.... Try playing with "autohide" and "show hide buttons" in the panel properties and you can move the panels off of the screen if you have to..... Then do your install... After you have your system up try the Envy thing...... This is an easier alternative.... But that's just me....

Also the xorg config is showing has MX400  listed and You're telling us you have a FX5200... So that may be whats screwing you up....

Good Luck!!!

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> 

Also the xorg config is showing has MX400  listed and You're telling us you have a FX5200... So that may be whats screwing you up....

Good Luck!!!

Thanks! Actually, that xorg snippet of text was the advice given to a different poster on a similar issue. I'll definitely try to move the panels.

---

### Post by reset3x on 2007-06-19
Is it your intention to dual boot Linux and XP? Or are you dropping XP?

---

### Post by reset3x on 2007-06-19
Just saw you found a solution on your other thread....

Good Luck!!! Enjoy Ubuntu!!! :)

---

### Post by samuraiCat on 2007-06-19
> **reset3x said:**
> Is it your intention to dual boot Linux and XP? Or are you dropping XP?

Well, I'm going to dual-boot, but I'm only going to use XP if I absolutely need to. Eventually, I will delete it.

---

