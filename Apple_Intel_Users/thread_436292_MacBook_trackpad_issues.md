---
title: "MacBook trackpad issues"
date: 2007-05-07
forum: Apple Intel Users
---

### Post by thully on 2007-05-07
After a long hiatus from the Linux world and exclusively using OS X for 2+ years, I just took the plunge and installed Ubuntu 7.04 (Feisty) on my MacBook.  The install, for the most part, went well - it worked with Boot Camp with no special MBR/GPT hacking/bootloaders required!  However, I have run into a few MacBook-specific issues - mostly with the trackpad (and power management/suspend, but that's another post).

First of all, my trackpad is quite sluggish when compared to OS X.  Attempts to change acceleration in the GNOME Mouse control panel and in gsynaptics have had no effect whatsoever - I end up with the same trackpad speed/acceleration regardless.

Also, right-click has been a problem - I know F12 will right-click, but that's just irritating.  I'd like to change it such that I can right-click by Ctrl-clicking or Command-clicking (and something similar for middle-click) - or preferably by holding two fingers on the trackpad and clicking as I can on OS X.  I saw mouseemu, but I can't figure out how to set it up to my liking (showkeys won't tell me they keycodes on a MacBook).

Finally, trackpad scrolling is also an annoyance under Ubuntu.  OS X allows me to hold two fingers on the trackpad and move up and down to scroll.  However, on Ubuntu I have to hold my finger precisely on the side and swipe it to scroll.  Is there any way to get the OS X behavior - or at least set scroll up for a key+movement combination (mouseemu appears to do that, but it doesn't work out of the box).

Yes, I know all this may simply seem to demonstrate why Apple's one-button trackpad idea is stupid.  However, with the special gestures (two-finger right click and two-finger scroll), I found it to work as good as any two-button wheel mouse in OS X, and actually PREFERRED it over the three-button Trackpad+TrackPoint on my old ThinkPad (that I used back when I used Ubuntu 2-3 years ago) or an external mouse.

---

### Post by ronocdh on 2007-05-07
Try installing Qsynaptics or Gsynaptics. You'll have to edit your xorg.conf, but the error message the program throws on first one will tell you the specific option that must be added. This should resolve the poor tracking and scrolling issues, but as for mapping another right-click key, you may have to find an additional solution.

---

### Post by thully on 2007-05-07
I have Gsynaptics installed with the appropriate option in xorg.conf enabled. Tweaking the options for responsiveness had no effect whatsoever, and I'm still stuck with edge-of-trackpad scrolling...  I do know that Gsynaptics does work, though - I did turn off tapping successfully in there.

---

### Post by ronocdh on 2007-05-07
I don't recall specifically why, but at one point I removed Gsynaptics and switched to Qsynaptics. See whether that helps you and please post back with results.

---

### Post by ronocdh on 2007-05-07
Please check out [this thread]("http://ubuntuforums.org/showthread.php?t=434998") for more info on mapping right-click.

---

### Post by thully on 2007-05-07
I tried doing some tweaks to get two-finger scrolling et al working.
While I did get it to work, the erratic mouse behavior (browser mysteriously going back/forward, mouse focus mysteriously moving) made it not worth it, and I'm back to the default side-scroll, which is more reliable in Ubuntu.

Regarding right-click - I'd prefer it to be Command+click or Ctrl+click (like in OSX) instead of a key...

---

### Post by Chrisj303 on 2007-05-08
You know what? - i've been battling with the trackpad for a LONG time. I have only been able to get the qsyanptics driver up and running since feisty, and TBH have found it horrid. It feels "sticky" and unresponsive - nothing like OSX, i have tried a handful of different xorg.conf configurations to no avail.

My soloution? - By your self a nice mouse. Honestly, i picked up a small Belkin USB mouse, with retractable cord for less than £10, it easily fits into a side pocket of my carry-bag, and can even fit into my trouser pocket with no problems! Right/Middle -click is no longer an issue either

I know it sounds like giving up - but it's not, as soon as a better soloution to the trackpad becomes available - i'm all ears. But for know this definitely seem to be the best work-around.


cheers,

chrisj303

---

### Post by ronocdh on 2007-05-08
> **Chrisj303 said:**
> You know what? - i've been battling with the trackpad for a LONG time. I have only been able to get the qsyanptics driver up and running since feisty, and TBH have found it horrid. It feels "sticky" and unresponsive - nothing like OSX, i have tried a handful of different xorg.conf configurations to no avail.

My soloution? - By your self a nice mouse. Honestly, i picked up a small Belkin USB mouse, with retractable cord for less than £10, it easily fits into a side pocket of my carry-bag, and can even fit into my trouser pocket with no problems! Right/Middle -click is no longer an issue either

I know it sounds like giving up - but it's not, as soon as a better soloution to the trackpad becomes available - i'm all ears. But for know this definitely seem to be the best work-around.


cheers,

chrisj303
With my frequent reinstalls and continual wireless troubles, I'm definitely still relegated to using a mouse, because I can't stray very far from my router. =) I've yet to try bsantos's recommendation on widemos's thread, which I saw worked for your, Chrisj....

---

### Post by tgalati4 on 2007-05-08
I had the same issues on a powerbook G4.  The scrolling and trackpad functions are not as smooth as in Tiger.  An external mouse won't work when you are outside sitting under a tree (where mac users like to "work").  

Pehaps Apple will open up their hardware specs for the trackpad to improve this situation.

My compromise is to run Tiger with XDarwin and ssh into a remote Ubuntu machine and gnome-panel to get an Ubuntu Desktop on one of my virtual desktops (using Desktop Manager).  You get 90% of the Ubuntu goodness with the smooth hardware behavior that you have grown acustom to in Tiger.

---

### Post by ronocdh on 2007-05-08
> **tgalati4 said:**
> An external mouse won't work when you are outside sitting under a tree (where mac users like to "work").This generalization made me grin like crazy. What a great prejudice!

> Pehaps Apple will open up their hardware specs for the trackpad to improve this situation.Not gonna happen--at least, not anytime soon, IMO. I do think we'll have a delightful little hacker have a breakthrough sometime in the near future, though, and when I hear of it I shall PayPal him much monies.

> My compromise is to run Tiger with XDarwin and ssh into a remote Ubuntu machine and gnome-panel to get an Ubuntu Desktop on one of my virtual desktops (using Desktop Manager).  You get 90% of the Ubuntu goodness with the smooth hardware behavior that you have grown acustom to in Tiger.90% of the Ubuntu goodness to me is snappy response times; I love how thin it feels. Even with sick bandwidth, I would still think this method would be lacking.

---

### Post by tgalati4 on 2007-05-08
Well, it is a trade off.  You are running gnome applications (don't know about KDE) in a semi-native Cocoa environment, so they actually seem to run faster in XDarwin than booting into Ubuntu.

In addition, you can use Fink Commander to install many open source,  ported-to-ppc applications that run even faster because they are using the Cocoa environment instead of XDarwin over Cocoa.

The BSD foundation allows many of our favorite apps to run happily inside Tiger.

You fell into the Apple hardware hole that I dug.  I was just seeing if you were paying attention.

I need to move now, I have lost my shade.

---

### Post by thully on 2007-05-08
Yes, I knew "get a mouse" would be one of the suggestions, but I do use my MacBook on my lap extensively so this really isn't an option.  As far as compromises, I was thinking of running Ubuntu in Parallels or VMware Fusion on OS X...  In my experience, it is quite fast on both - though I've had better experience on Parallels (VMware Fusion still is quite glitchy - though it is a BETA, so this should be expected).  I may just stick with native Ubuntu, though - I did just get suspend-to-RAM to work...

---

### Post by ronocdh on 2007-05-08
Congratulations on the suspend to RAM! I personally support VMFusion over Parallels just because it acknowledges the existence of Ubuntu. ;) Although I've heard Parallels installations work fine if you just set it to "Solaris" or something.

Sorry for being discouraging in promoting the mouse option. I think that given the progress from Edgy to Feisty in Mactel compatibility, we'll see even greater support in Gutsy. It's commonplace here that we criticize the devs for marginalizing us, discriminating against us because we are a minuscule  slice of the market they're aiming for, but really we're getting a lot of help. Wireless is a bitch this time around, yes, but things are looking up overall.

That said, please make sure to post even incremental progress towards better trackpad performance. ;)

---

### Post by thully on 2007-05-08
OK - I'm still unsure whether I will go VM or native.
For VM, Parallels does seem to work better as of now - VMware has some annoying quirks, such as:

* OS X menu pops up every time my mouse pointer is at the top of the screen
* no way to default to full screen for a session
* "eject" key is completely nonfunctional
* tends to get sluggish for no reason at all

VMware will probably be better in the end, though, since it has VMware Tools for Linux...
It is a beta, though...  I am curious what they will charge for the final.  I'd hate to buy Parallels and find out there is a free VMware Server/Vmware Player for OSX after the beta.  Then again, they could just sell it at VMware Workstation prices and not compete with Parallels (just targeting those standardized on VMware or those who need more advanced features than Parallels)

---

### Post by thully on 2007-05-08
I did tweak things a little and came up with something that may be a tad better.
Still slow movement, but it may be less erratic.  I disabled all tapping and edge scrolling, and enabled vertical two-finger scrolling only.  Of course, this should be combined with a good keyboard mapping for right-click and middle-click.

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "VertScrollDelta"       "25"
        Option          "HorizScrollDelta"      "0"
        Option          "VertEdgeScroll"        "false"
        Option          "HorizEdgeScroll"       "false"
        Option          "VertTwoFingerScroll"   "true"
        Option          "HorizTwoFingerScroll"  "false"
        Option          "TapButton1"            "0"
        Option          "TapButton2"            "0"
        Option          "TapButton3"            "0"
        Option          "MinSpeed"              "0.79"
        Option          "MaxSpeed"              "0.88"
        Option          "AccelFactor"           "0.015"
EndSection

Also, If anyone knows how to make Command-click or Ctrl-click right-click, please post it here (I specifically want to do ctrl+click rather than just ctrl or command because this is how OS X does it).

---

### Post by ry4nolson on 2007-05-08
Option		"SHMConfig"		"true"

i'm pretty sure you need to have this in there for any of (g or q)synaptics settings to work.

---

### Post by thully on 2007-05-08
I'm not using either right now...  They seemed to do nothing of significance.

---

### Post by zurgutt on 2007-05-09
I got a brand new white 1G Macbook and installed Feisty on it - no much problems, bootcamp, install, widescreen graphics fix, madwifi drivers, done.

The trackpad action feels nice and responsive, EXCEPT one very annoying issue: sometimes when you put a finger on pad and move it, cursor wont move.  Doesnt move at all - this is not issue of touching too lightly or somesuch.  To make it move again I have to lift off finger and try again (sometimes 2-3 times) OR I can use quick wiggling movement without lifting finger, which seems to work too, mostly.  In contrast, long smooth strokes without lifting finger does not seem to work.

This seems to happen at random times, at average several times per minute.  Extremely annoying.

Trackpad works fine in osx and knoppix livecd.  Feisty livecd has same issue though.

I have installed gsynaptics, however it does not seem to help, or do anything in fact - speed/acceleration controls have no effect.  Checkbox options do, however..

Anyone got a idea whats going on?

---

### Post by gus6464 on 2007-05-25
I have two finger scrolling and right click by tapping with 3 fingers enabled and it works perfectly on my macbook. Install qsynaptics and here is my xorg.conf trackpad section:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
	Option		"VertTwoFingerScroll"	"true"
	Option		"HorizTwoFingerScroll"	"true"
EndSection

---

