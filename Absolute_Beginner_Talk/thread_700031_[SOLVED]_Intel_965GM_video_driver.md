---
title: "[SOLVED] Intel 965GM video driver?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-02-17
I have a Dell Inspiron 1420 (that came with Ubuntu pre-installed) and it has an Intel 965GM graphics card. I was wondering what version of x-org Gutsy has and also should I install the drivers from [http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")? would it work? As in will it work and give me full support?

---

### Post by peabody on 2008-02-18
> **slughappy1 said:**
> I have a Dell Inspiron 1420 (that came with Ubuntu pre-installed) and it has an Intel 965GM graphics card. I was wondering what version of x-org Gutsy has and also should I install the drivers from [http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")? would it work? As in will it work and give me full support?

Well, a relevant question is, what doesn't work currently?  Is there a reason you need to futs with the drivers?

---

### Post by jan quark on 2008-02-18
_**[COLOR="DarkOrange"]if ain't broken, don't fix it[/COLOR]**_

---

### Post by Golem XIV on 2008-02-18
Here's a resource for your system:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")

Hopefully it'll help.

---

### Post by slughappy1 on 2008-02-19
well I bought a laptop from Dell an expected it to have full hardware support. Then when I try and enable Compiz I got an error and had to tell it to not check for support to get it to work (but it messes with my Network Manager somehow I think, and crashes when used too much). When I tried to play a 3D game, it couldn't. I want to have full 3D functionality like I did with my previous laptop.

After looking at your link Golem XIV, I found 
But when reading it says "This driver provides low-performance 3-D graphics acceleration capabilities." When I looked on the Intel website it said that the 965GM was a newer/NextGen video card. If that is true then would I be right in assuming it is a linux driver thing? Would the other site (above in first post) be a better driver or is it the same?

My current xorg.conf looks like:```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```
If I were to change Driver "intel" to Driver "i810" would that work?

---

### Post by Golem XIV on 2008-02-19
> **slughappy1 said:**
> well I bought a laptop from Dell an expected it to have full hardware support. Then when I try and enable Compiz I got an error and had to tell it to not check for support to get it to work (but it messes with my Network Manager somehow I think, and crashes when used too much). When I tried to play a 3D game, it couldn't. I want to have full 3D functionality like I did with my previous laptop.

After looking at your link Golem XIV, I found 
But when reading it says "This driver provides low-performance 3-D graphics acceleration capabilities." When I looked on the Intel website it said that the 965GM was a newer/NextGen video card. If that is true then would I be right in assuming it is a linux driver thing? Would the other site (above in first post) be a better driver or is it the same?

My current xorg.conf looks like:```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```
If I were to change Driver "intel" to Driver "i810" would that work?

The "newer/NextGen video card" is marketspeak.  IMO all Intel graphic chips are <diplomatic mode> underwhelming </diplomatic mode>.  They are nice for general office work, browsing, e-mail and such but are utter crap for games.  The 3D games I tried work for a few minutes and then they lock up the system hard.  I am pretty certain that you would have the same problems in Windows with them.  Just grab any newer game and check the supported chipsets - if you find any mention of Intel graphics I will be honestly surprised.

I have recently pointed someone to a reply I made on [this thread]("http://ubuntuforums.org/showthread.php?t=695195") where you can find how to set your system up so that the X3100 will give you both desktop effects and video playback.  Hopefully it can help you, too.

I don't think that changing the driver will help.  If anything, the i810 driver appears to be even worse than the i965 one.

---

### Post by peabody on 2008-02-19
I have a i950 (945GM chipset).  I've got no trouble running compiz or with video playback.  I even managed to half life 2 running under wine (though I'll admit, it wasn't very playable).  I use the intel driver.

You SHOULD be able to get 3D with that card, though the other posters are right in that it isn't a gaming adapter (you can probably get Warcraft III and maybe even WoW to work however).

Did you buy this from Dell?  They should be able to provide support for it.  Have you run all of the system updates?  The xserver-xorg-video-intel package was updated very recently.

---

### Post by parmdeep on 2008-02-19
to get compiz working u need to uncomment the the intel driver from the compiz file somewhere, google it, once you have done this you also need to change the setting in your movie players to be able to play movies while compiz is active.

---

### Post by slughappy1 on 2008-02-19
Well see Compiz blacklisted the 965 Intel series. You can see it on [URL="http://wiki.compiz-fusion.org/Hardware/Blacklist"]http://wiki.compiz-fusion.org/Hardware/Blacklist[
/URL]. I posted another thread asking about it [here]("http://ubuntuforums.org/showthread.php?t=701567") but as of yet no one has responded to it

---

### Post by Golem XIV on 2008-02-19
> **slughappy1 said:**
> Well see Compiz blacklisted the 965 Intel series. You can see it on [URL="http://wiki.compiz-fusion.org/Hardware/Blacklist"]http://wiki.compiz-fusion.org/Hardware/Blacklist[
/URL]. I posted another thread asking about it [here]("http://ubuntuforums.org/showthread.php?t=701567") but as of yet no one has responded to it

Have you looked at the link I provided?  I'll quote it here:

> **Golem XIV said:**
> The Intel chipsets are blacklisted in Compiz because they don't play nice.  

To enable Compiz effects, you can edit the file /etc/xdg/compiz/compiz-manager and add the line:

```
SKIP_CHECKS="yes"
```

This will allow you to enable the desktop effects.  However, there is a cost: it will break video playback.

the video problem can also be worked around, though.  Run the Multimedia System Selector that is on the System -> Preferences menu (but it is hidden by default, run the menu editor first to show it) or through the terminal 
```
gstreamer-properties
```

Make a note of the configuration so you can reset it back in case something gets screwed up.  Now go to the Video tab and under Default Output change the Plugin to "X Window System (No Xv)".
This will give you back video playback by using a slower and more resource-intensive renderer (but at lkeast it'll work).  Use the Test button to make sure it works.

The downside is that some apps will not like this new renderer and will not work with it (Skype 2.0 beta will not show you video, for example).

---

### Post by slughappy1 on 2008-02-19
Yes I did. I haven't had time to follow the last part of it. I previously found on the Compiz Community Forums (Which I was pointed to in [this post I made]("http://ubuntuforums.org/showthread.php?t=683929"). When you follow the link there it says to ```
mkdir ~/.config/compiz
echo "SKIP_CHECKS=yes" >> ~/.config/compiz/compiz-manager
```
I did that and it worked. So I guess it is the same as yours just yours has that extra step I think I need to do. Thank you for you help, it was just that I haven't had the time to use it and see how it works yet.

---

