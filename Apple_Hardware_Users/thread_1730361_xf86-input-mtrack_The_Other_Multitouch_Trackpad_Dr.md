---
title: "xf86-input-mtrack: The Other Multitouch Trackpad Driver"
date: 2011-04-15
forum: Apple Hardware Users
---

### Post by BlueDragonX on 2011-04-15
[CENTER][SIZE="5"]xf86-input-mtrack v0.2.0[/SIZE]
[SIZE="3"]Xorg Multitouch Trackpad Driver[/SIZE][/CENTER]

This is the official release of xf86-input-mtrack, a multitouch trackpad driver for X.  It has been tested again Xorg versions 1.7, 1.8, 1.9, and now 1.10.

Click [here](https://github.com/BlueDragonX/xf86-input-mtrack) to visit the GitHub project page.

To download the latest stable source code:```
git clone git://github.com/BlueDragonX/xf86-input-mtrack.git
```

This project started life as a fork of xf86-input-multitouch and was originally announced [in this thread](http://ubuntuforums.org/showthread.php?t=1334696).  It has come a long way and I believe it's finally worthy of a version number.

The README on Github gives a configuration example and an overview of all the available options.

Support for disabling the trackpad while typing is included as of v0.2.0. This requires an external daemon. I have created dispad for this purpose:
[LIST]
[*][Dispad Ubuntu Packages](http://www.dev.fatalmachine.org/packages/dispad/ubuntu/)
[*][Dispad Source at Github](https://github.com/BlueDragonX/dispad)
[/LIST]

Please post any issues to the project's [issues tracker](https://github.com/BlueDragonX/xf86-input-mtrack/issues) on Github.  You can check the last few pages of the original thread for some example configs that other people are using.

**Downloads**
[LIST]
[*][Ubuntu mtrack Binaries (Lucid, Maverick, Natty, Oneiric)](http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/)
[*][Lucid mtdev Binaries (mtrack dependency)](http://www.dev.fatalmachine.org/packages/mtdev/ubuntu/)
[*][Gentoo mtrack Ebuilds](http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/gentoo/)
[*]Gentoo - Ebuilds in Portage
[*][Arch Linux](http://aur.archlinux.org/packages.php?ID=48505) - supplied by mikezackles! Thanks!
[/LIST]

**Changelog for v0.2.0**
[LIST]
[*]Now built via autoconf/automake.
[*]Fully configurable via XInput.
[*]Sensitivify now configurable.
[*]Trackpad can now be disabled on keystroke via an external daemon.
[*]Four finger tapping/swiping added.
[*]Button zones added, a new button emulation method.
[*]Tap-to-drag fixed.
[*]Three finger tapping responsiveness fixed.
[/LIST]
**Changelog for v0.1.1**
[LIST]
[*]Bugfix release.
[*]Disabling tapping no longer (wrongly) disables pointer movement.
[*]Button emulation set to ignore "old" touches. What consitutes an old touch can be adjusted with the ButtonTouchExpire option.
[/LIST]
**Changelog for v0.1.0**
[LIST]
[*]Initial release.
[/LIST]

---

### Post by eelcoh on 2011-04-16
Thanks! Finally my macbook is linux-ready. I've got it running on Fedora 15 (Gnome3).
One thing i would really love is to bind a 3 or 4 finger down swipe to an expose kind of view (show all running windows), and one to show all workspaces. Is that possible?

---

### Post by labaom on 2011-04-16
May I ask how this is different than the main one?

---

### Post by c3n on 2011-04-17
great, thanks! it's already working a lot better than the original one. a few comments:
- scrolling up and down is too slow in firefox (was faster with the original driver)
- my girlfriend has rather small fingers which sometimes arent recognized properly, especially with gestures
- sometimes scrolling up doesnt work, while scrolling down does (strange...)

---

### Post by eelcoh on 2011-04-17
> - scrolling up and down is too slow in firefox (was faster with the original driver)

Same here. On the other hand, tapping is much better.

---

### Post by BlueDragonX on 2011-04-17
> **labaom said:**
> May I ask how this is different than the main one?

The mtrack driver is fully configurable.  See the [README](https://github.com/BlueDragonX/xf86-input-mtrack/raw/master/README).  Also, I've fixed a few of the quirks that the original had.

> **c3n said:**
> great, thanks! it's already working a lot better than the original one. a few comments:
- scrolling up and down is too slow in firefox (was faster with the original driver)
- my girlfriend has rather small fingers which sometimes arent recognized properly, especially with gestures

This can be taken care of by adjusting the configuration.  For scrolling you'll want to adjust ScrollDistance and for touching you'll want to adjust FingerHigh and FingerLow.  See the [README](https://github.com/BlueDragonX/xf86-input-mtrack/raw/master/README) for all of the configuration options, their descriptions, and their defaults.

> **c3n said:**
> - sometimes scrolling up doesnt work, while scrolling down does (strange...)

This I haven't seen happen.  Are you lifting your fingers from the trackpad between scrolling, or are you attempting to scroll down then back up without lifting your fingers?  How are you situating your fingers when you scroll and which fingers are you using?

---

### Post by NiñoScript on 2011-04-17
rafwes claims that his configuration works closer to the default behavior of the Mac OS X driver:
```
Section "InputClass"
	MatchIsTouchpad "on"
	Identifier      "Touchpads"
	Driver          "multitouch"
	Option		"ThumbSize"      "35"
	Option		"PalmSize"       "55"
	Option		"ClickTime"      "25"
	Option		"ScrollDistance" "300"
EndSection
```

You can read his original post [SIZE="3"][over here]("http://ubuntuforums.org/showthread.php?p=10557093#post10557093")[/SIZE], he commented a bit on the rationale behind those numbers. :)

---

### Post by eelcoh on 2011-04-20
I've changed the ScrollDistance to 120. Feels much better.

---

### Post by Helios747 on 2011-04-23
Triple edit: after some fiddling around I got it working, but I did some really weird stuff. I'll update this post once I work out all the kinks.

Just one question, which option would change overall sensitivity of the trackpad?

The sensitivity on my MacBook 5,1 is a TINY bit too sensitive, would like to turn that down, then I'll have near perfect trackpad settings to reflect OS X

---

### Post by mstratman on 2011-04-24
I added some rudimentary support for the MT protocol to part of the elantech kernel driver (among other changes) ( [https://bugzilla.kernel.org/show_bug.cgi?id=27442](https://bugzilla.kernel.org/show_bug.cgi?id=27442) ). It affects the newer Samsung laptops.

Your Xorg driver appears to work with it. :) Cheers.
Well, at a glance anyway. I haven't yet done extensive testing.

A couple of questions:
* These newer Samsungs (the ones for which the MT-capable part of elantech) have a single touchpad with no clickable buttons... does this mean I want your has_integrated_button() in capabilities.c to return 1?  And more importantly, what's this for and what will it affect? (sorry if that's a dumb question - i'm kind of new to this touchpad stuff).

* Is two-finger click and drag (i.e. click with one finger, move other finger to drag) supposed to work with your Xorg driver? And if not, is this outside of the scope of what it should be doing; or simply not (yet) implemented?
If it is supposed to work, any ideas why it might not be working?

Thanks, and let me know if you need any more info from me.

---

### Post by BlueDragonX on 2011-04-24
> **mstratman said:**
> I added some rudimentary support for the MT protocol to part of the elantech kernel driver (among other changes) ( [https://bugzilla.kernel.org/show_bug.cgi?id=27442](https://bugzilla.kernel.org/show_bug.cgi?id=27442) ). It affects the newer Samsung laptops.

Your Xorg driver appears to work with it. :) Cheers.
Well, at a glance anyway. I haven't yet done extensive testing.

Sweet, nice work!

> **mstratman said:**
> A couple of questions:
* These newer Samsungs (the ones for which the MT-capable part of elantech) have a single touchpad with no clickable buttons... does this mean I want your has_integrated_button() in capabilities.c to return 1?  And more importantly, what's this for and what will it affect? (sorry if that's a dumb question - i'm kind of new to this touchpad stuff).

From what I understand, yes.  However, I do not check that value,  the driver depends on the user to configure that.

> **mstratman said:**
> * Is two-finger click and drag (i.e. click with one finger, move other finger to drag) supposed to work with your Xorg driver? And if not, is this outside of the scope of what it should be doing; or simply not (yet) implemented?
If it is supposed to work, any ideas why it might not be working?

Yes, this functionality works with this driver.  I use it all the time.  I'll have to give it some thought when it's not 2 AM.  Compiling the driver with debugging output would help to pinpoint it, though.

---

### Post by BlueDragonX on 2011-04-24
> **Helios747 said:**
> Just one question, which option would change overall sensitivity of the trackpad?

There's no sensitivity adjustment in the driver. That's something I intend to add in the next. I find the acceleration controls work well enough for the moment, though.

---

### Post by Helios747 on 2011-04-24
Ah. well let us know when that happens! I would love that option in my xorg file.

In the mean time, is there some variable I can tweak in the source code and recompile? Or do I just have to wait? I think I remember some multitouch driver (that I tried recently) where I could modify the sensitivity in some .c file and recompile.

---

### Post by BlueDragonX on 2011-04-24
> **Helios747 said:**
> Ah. well let us know when that happens! I would love that option in my xorg file.

In the mean time, is there some variable I can tweak in the source code and recompile? Or do I just have to wait? I think I remember some multitouch driver (that I tried recently) where I could modify the sensitivity in some .c file and recompile.

I merged support for sensitivity into the dev branch today. The xorg.conf option is "Sensitivity" and it's a double value.  It's been tested but there are no builds yet.  There will be a collection of new features - this one of them - that will be released in the 0.2.0 release.

---

### Post by Helios747 on 2011-04-24
Does that mean I can download it from the git and compile?

When you say it's a double value what does that mean? Like a decimal?

Sorry, I'm not much of a programmer, most I do is a few bash scripts or a python script.

EDIT: Also whenever I try to disable tap to click it simply breaks the touchpad until I comment out the options. This is what the entry looks like with the tap to click "disabled", am I doing something wrong?

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "TapButton1" "0"
    Option          "TapButton2" "0"
    Option          "TapButton3" "0"
EndSection


```If I comment out those options, tap to click is still enabled (and bugs me), but the touchpad works.

---

### Post by BlueDragonX on 2011-04-24
> **Helios747 said:**
> Does that mean I can download it from the git and compile?

Yes, but you need to get the source from the development branch.  The master branch has the latest stable release which does not include features from the next version.

> **Helios747 said:**
> When you say it's a double value what does that mean? Like a decimal?

Correct.

> **Helios747 said:**
> EDIT: Also whenever I try to disable tap to click it simply breaks the touchpad until I comment out the options. This is what the entry looks like with the tap to click "disabled", am I doing something wrong?

What do you mean "simply breaks"?  I need to know exactly what happens and will need to see your Xorg logs.

Your configuration is correct, however.  The same configuration on my system yields the desired results without any issues.

---

### Post by Helios747 on 2011-04-24
Here is a pastebin of a fresh log after an X restart with the TapButton options enabled.

[http://pastebin.com/d0kMbAvn](http://pastebin.com/d0kMbAvn)

what happens visually when I enable those options is that after I restart X, touchpad movement does not move the mouse, but button clicks are still detected (Taps aren't though! haha!)

Here is my full xorg.conf

```
Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "TapButton1" "0"
    Option          "TapButton2" "0"
    Option          "TapButton3" "0"
    Option          "ThumbSize"  "35"
    Option          "PalmSize"   "55"
    Option          "ClickTime"  "25"
    Option          "ScrollDistance" "300"
EndSection

```Things work again whenever I comment out the tapbutton options. The other options I have in there work fine.

I'm running a MacBook 5,1 with Ubuntu Natty Beta 2.

---

### Post by mstratman on 2011-04-24
Re: click+drag
> **BlueDragonX said:**
> 
Yes, this functionality works with this driver.  I use it all the time.  I'll have to give it some thought when it's not 2 AM.  Compiling the driver with debugging output would help to pinpoint it, though.

Good to know, thanks.

I spent a little time trying to debug it, to no avail though. I'll have to sit down and really figure out how these various drag routines are supposed to work (so far, all I've figured out is trigger_drag_ready() only gets called when i double tap).

It should be seeing both fingers, as it reports swipes just fine.  Haven't yet gotten it to report scrolls though.

I'll dig into this more this week, I hope.

If it's a quick/simple answer (I don't want to take up any of your time unnecessarily, especially before I do my due-diligence)... Could the fact that I'm only implementing the bare-bones MT protocol be the issue?
i.e. I'm only reporting ABS_MT_POSITION_[X|Y] and ABS_MT_PRESSURE.  No widths, or any of the other options.
I'm wondering if that might be preventing the Xorg driver from properly detecting a thumb click, or any other checks it might be doing.

---

### Post by scoddy on 2011-04-25
Mtrack driver is working for me on a MacBook Air 3,1 11" under gentoo as well as Ubunty natty b2. Tapping is much better than with multitouch, thanks for all the efforts!

As mentioned by Helios747 I can confirm that
```
Option          "TapButton1" "0"     
Option          "TapButton2" "0"     
Option          "TapButton3" "0"
```does not work for me either.  Another thing came up with the bcm5794 I'm using:

```
Xorg.log
(EE) mtrack: cannot configure device
(EE) Couldn't init device "bcm5974"
```It seems that the xorg.conf.d evdev-hooks try to initialize the device twice, as touchpad and mouse - however it's working though. A little odd is the touch behavior, which seems to be correct with the multitouch driver, but not in mtrack: I'm scrolling with my right hand pointer finger, leave it on the touchpad whilst the mouse pointer is over the button I wanna click (e.g. firefox). Now clicking with the left hand pointing finger results in a two finger tap (right click). Any way to get rid of this behavior or is it related to the TapButton Option?

---

### Post by buzzboy on 2011-04-27
Any work towards this working for Lucid?

---

### Post by BlueDragonX on 2011-04-27
> **mstratman said:**
> I spent a little time trying to debug it, to no avail though. I'll have to sit down and really figure out how these various drag routines are supposed to work (so far, all I've figured out is trigger_drag_ready() only gets called when i double tap).

That's expected and is used by the tap-and-drag functionality.  It doesn't have anything to do with click and drag.

> **mstratman said:**
> Could the fact that I'm only implementing the bare-bones MT protocol be the issue?
i.e. I'm only reporting ABS_MT_POSITION_[X|Y] and ABS_MT_PRESSURE.  No widths, or any of the other options.
I'm wondering if that might be preventing the Xorg driver from properly detecting a thumb click, or any other checks it might be doing.

Without widths, etc, thumb and palm detection shouldn't even be operable. While I'd like to say that not implementing those features should have no effect, I don't have a pressure based multitouch device to test against. It may be that the default values, and even some of the logic, needs to be adjusted for such devices. Hit me up with a PM and we can talk further. I'd like to get this resolved.

> **scoddy said:**
> Tapping is much better than with multitouch, thanks for all the efforts!

You're welcome!

> **scoddy said:**
> As mentioned by Helios747 I can confirm that (snip) does not work for me either.

Glad you were able to confirm this. I'm going to take a more indepth look at the code tonight and see if I can't figure out what's causing it. Hopefully I'll have progress to report in an hour or a few.

> **scoddy said:**
> Another thing came up with the bcm5794 I'm using:

```
Xorg.log
(EE) mtrack: cannot configure device
(EE) Couldn't init device "bcm5974"
```It seems that the xorg.conf.d evdev-hooks try to initialize the device twice, as touchpad and mouse - however it's working though.

Happens for me as well. Some adjustment to the xorg.conf config would prevent this, but it works just fine either way.

> **scoddy said:**
> A little odd is the touch behavior, which seems to be correct with the multitouch driver, but not in mtrack: I'm scrolling with my right hand pointer finger, leave it on the touchpad whilst the mouse pointer is over the button I wanna click (e.g. firefox). Now clicking with the left hand pointing finger results in a two finger tap (right click). Any way to get rid of this behavior or is it related to the TapButton Option?

Based on how I read this, this is what you're doing:

1) You successfully execute two finger scrolling.
2) You lift one finger from the trackpad, leaving exactly one finger touching.
3) With a single finger you click the physical button on the trackpad.
4) This causes a right click.

If I am correct and did not misread, then yes, it's working as I built it. That doesn't mean it *should* work that way, though. I definitely see your point, and agree with it, so I'll call it a bug. It is likely I will fix this by only counting fingers which have touched down inside a certain timeframe. So scrolling or moving fingers won't cause this.

> **buzzboy said:**
> Any work towards this working for Lucid?

I don't have a package for Lucid, but that doesn't mean it won't work. Try compiling it yourself if your're up for it.

I don't have a build environment set up for Lucid yet, it's on my "to do" list.

---

### Post by BlueDragonX on 2011-04-28
The issues and milestones on Github are now updated.  If you're interested in seeing what's to come in the next feature version check out the open milestones.

---

### Post by BlueDragonX on 2011-04-28
I've got a bugfix in place for the no movement problem when disabling tapping.  It's in master on github.

I'm going to get the clicking issue fixed up before rolling out a new release with these fixes in it.

---

### Post by BlueDragonX on 2011-04-28
Good news, nobody! Version 0.1.1 is here!

**Changelog for v0.1.1**
[LIST]
[*]Bugfix release.
[*]Disabling tapping no longer (wrongly) disables pointer movement.
[*]Button emulation set to ignore "old" touches. What consitutes an old touch can be adjusted with the ButtonTouchExpire option.
[/LIST]

All bug fixes have also been (and will continue to be) merged into the dev branch.

---

### Post by BlueDragonX on 2011-04-28
I'm looking for people to post up their configs they're using. I want to work a set of reasonable defaults based on what everyone is using now.

---

### Post by pbhedlund on 2011-04-28
> **BlueDragonX said:**
> I'm looking for people to post up their configs they're using. I want to work a set of reasonable defaults based on what everyone is using now.

Thanks for your great progress. I am fairly happy with (haven't tested sensitivity extensively yet) on my MacBook Air 3,2.

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    MatchDevicePath "/dev/input/event*"
    Option          "Sensitivity" "0.75"
    Option          "ClickTime" "50"
    Option          "IgnoreThumb" "False"
    Option          "IgnorePalm" "False"
    Option          "TapDragEnable" "False"
    Option          "ScrollDistance" "150"
    Option          "TapButton1" "0"
    Option          "TapButton2" "0"
    Option          "TapButton3" "0"
EndSection
```In my .xbindkeysrc I have this to enable pinch to zoom in Dolphin, Okular, Firefox and other programs

```
"xvkbd -xsendevent -text "\C\[plus]""
  b:12

"xvkbd -xsendevent -text "\C\[minus]""
  b:13
```

---

### Post by roydrager on 2011-04-28
Macbook Pro 6,1  Ubuntu 11.04 Natty
```

Section "InputClass"
    MatchIsTouchpad "on"
        Identifier "Touchpads"
        Driver "mtrack"
    Option "PalmSize" "45"
    Option "IgnoreThumb" "0"
    Option "ClickTime" "25"
    Option "ScrollDistance" "300"
    Option "Sensitivity" "1.1"
    #Option "TapDragTime" "1000"
EndSection

```This is with the code compiled from the latest master branch on your github 4/28.

I haven't heard anybody else mention this issue, but tap-to-drag does not work at all for me.  (Holding the physical integrated button and dragging works fine.)  It is like tap to drag is not executing.  I tried increasing TapDragTime but it has no effect.  

Also, I am looking forward to Disable Pad While Typing.   I saw in your github notes that it should work but I don't know how to enable it.

Thanks for your terrific work!

---

### Post by Helios747 on 2011-04-28
> **BlueDragonX said:**
> Good news, nobody! Version 0.1.1 is here!

**Changelog for v0.1.1**
[LIST]
[*]Bugfix release.
[*]Disabling tapping no longer (wrongly) disables pointer movement.
[*]Button emulation set to ignore "old" touches. What consitutes an old touch can be adjusted with the ButtonTouchExpire option.
[/LIST]

All bug fixes have also been (and will continue to be) merged into the dev branch.

You sir, are my savior. I will try this and report my results and configs ASAP.

---

### Post by BlueDragonX on 2011-04-29
> **Helios747 said:**
> You sir, are my savior. I will try this and report my results and configs ASAP.

That's some high praise, not sure if I'm worthy :P

Thanks for the help so far, guys. I'll be updating the default config for the next release.

Somehow while I was screwing around with two different remotes (my private gitolite server and github) I managed to merge changes from dev into master. No clue how. So sensitivity support is in master now. Not what I intended, but at least I've already tested it. It's just simple multiplication, anyways...

I'm going to go ahead and do a real merge from dev to master just so everything else is in sync and I don't shoot myself in the foot, here.

EDIT: Merge is done, new features coming your way!

---

### Post by Helios747 on 2011-04-29
Updated. This is awesome. Everything works just as I like it in OS X, more or less. I'm using this config right now but I plan on tweaking it as I use this driver.

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "TapButton1" "0"
    Option          "TapButton2" "0"
    Option          "TapButton3" "0"
    Option          "ThumbSize"  "26"
    Option          "Sensitivity" "0.85"
    Option          "ScrollDistance" "175"
    Option          "FingerHigh" "10"
    Option          "FingerLow"  "10"
EndSection


```I'll update this post with my settings as I tweak them for anybody who likes this.

---

### Post by eelcoh on 2011-04-29
Section "InputClass"
        MatchIsTouchpad "true"
        Identifier      "Multitouch Touchpad"
        MatchProduct    "bcm5974"
        Driver          "mtrack"
        MatchDevicePath "/dev/input/event*"
        Option          "ThumbSize" "35"
        Option          "PalmSize" "55"
        Option          "ClickTime" "25"
        Option          "ScrollDistance" "70"
        Option          "TapDragEnable" "False"
EndSection

---

### Post by buzzboy on 2011-04-30
Sorry to be a bit of a noob here but I've not done much compiling of code
So I download the tar file and extract it. Where does it need to go and do I need to "install" it or something?

---

### Post by ckisgen on 2011-04-30
> **roydrager said:**
> Macbook Pro 6,1  Ubuntu 11.04 Natty

<<snip>>
I haven't heard anybody else mention this issue, but tap-to-drag does not work at all for me.  (Holding the physical integrated button and dragging works fine.)  It is like tap to drag is not executing.  I tried increasing TapDragTime but it has no effect.  

Also, I am looking forward to Disable Pad While Typing.   I saw in your github notes that it should work but I don't know how to enable it.

Thanks for your terrific work!

+1 .. my tap to drag doesn't work for me either.  didn't work on 0.1.0 or 0.1.1 

i love this driver but the lack of tap to drag is a real drag (el oh el) .. this is a function i need/use almost constantly

dragon?  help please?

thanks for the great work

(macbook 5,1 / ubuntu 11.04)

---

### Post by Helios747 on 2011-04-30
> **buzzboy said:**
> Sorry to be a bit of a noob here but I've not done much compiling of code
So I download the tar file and extract it. Where does it need to go and do I need to "install" it or something?


Forget the tar file.


Follow these instructions.


Install git if you don't have it already

```
sudo apt-get install git
```Get a copy of the stable code for the driver

```
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
```cd into the directory

```
cd xf86-input-mtrack
```Install the required dev libs for compiling

```
sudo apt-get install xorg-dev libmtdev-dev
```compile

```
make
```Install the driver

```
sudo make install
```edit your /etc/X11/xorg.conf (if this does not exist, create it.)

```
sudo nano /etc/X11/xorg.conf
```Put this code into it to activate the driver

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
 EndSection

```Reboot your computer, or restart X to activate the driver.

To tweak the options for the driver (sensitivity, pressure sensing, tap to click enable/disable, thumb width, etc) follow the list of options in the configuration section of the readme here:

[https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md](https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md)

You insert the options you want to tweak in your xorg.conf file in between "Driver "mtrack"" and "EndSection"

Have fun. :)

---

### Post by buzzboy on 2011-04-30
Thanks for the how-to.
So if I do all that and the trackpad no longer works I take it I'm out of luck?

---

### Post by Helios747 on 2011-04-30
Not at all!

If your trackpad stops working, you have two options on how to fix this.

Plug in a USB mouse, login, and do

```
sudo nano /etc/X11/xorg.conf
```Comment out all lines that you pasted in from the previous post (comment is a # sign before each line)

Save, and restart X (or reboot)

Or, use the keyboard to log in. once you're logged in, hit the Super key (Win key on PCs, Apple key on Macs)

type "terminal", hit enter.

then edit the xorg file and do the same thing.

---

### Post by buzzboy on 2011-04-30
Yeah, I can do that, and I have. What I mean though is that most likely this driver won't work for me.

---

### Post by Helios747 on 2011-04-30
Can you post what happens when you activate the driver to help BlueDragonX fix it?

---

### Post by BlueDragonX on 2011-05-01
Thanks for helping out, Helios!

> **buzzboy said:**
> Sorry to be a bit of a noob here but I've not done much compiling of code
So I download the tar file and extract it. Where does it need to go and do I need to "install" it or something?

If you're running Ubuntu Maverick or Natty you can install the appropriate deb and not worry about compiling: [http://www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/](http://www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/)

However, you'll be missing the ability to adjust sensitivity, as that's in the latest stable code at github. If you want that then follow Helios' instructions.

> **buzzboy said:**
> Yeah, I can do that, and I have. What I mean though is that most likely this driver won't work for me.

What hardware are you running? If you do an 'lsmod | grep bcm5974' at the console, do you see anything? The bcm5974 is the kernel driver used for the MacBook and Apple Magic trackpads. This driver is only compatible with true multitouch devices, so if you don't have one you're out of luck.

If you know you've got an actual multitouch trackpad, then post your xorg config and log files and we'll see what's up.

> **roydrager said:**
> I haven't heard anybody else mention this issue, but tap-to-drag does not work at all for me.
(snip)
Also, I am looking forward to Disable Pad While Typing.   I saw in your github notes that it should work but I don't know how to enable it.

Tap-to-drag is a known failure. I re-implemented it wrong, and in a similar manner to how xf86-input-multitouch does it, which is not how it works in other drivers. It will work as is but you have to be damned fast. I've done it, but it's not what I'd call usable. Version 0.2.0 will have new tap-to-drag code. I've got a milestone for this.

Disable-on-typing isn't implemented yet. I've gotten the first piece completed, which is properties support, but I've got to have a separate process to monitor the keyboard (like syndaemon in the Synaptics driver). I will roll the daemon as a separate package once it's ready to go. I've got a milestone for this as well.

---

### Post by joskapista on 2011-05-01
My favorite setups are:

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "ThumbSize"  "26"
    Option        "PalmSize" "35"
    Option          "Sensitivity" "0.75"
    Option          "ScrollDistance" "100"
    Option          "FingerHigh" "7"
    Option          "FingerLow"  "7"
EndSection

Could someone please help me, how can I enable click and move with one finger (or this is the tap to drag which is not works yet?)?

This driver is almost perfect, thanks!

---

### Post by buzzboy on 2011-05-01
I am running a MacBook 5,5 with a true multitouch trackpad using the bcm5974 driver. For my xorg file I copy pasta this

Section "InputClass"     
MatchIsTouchpad "on"     
Identifier      "Touchpads"     
Driver          "mtrack"
EndSection

---

### Post by BlueDragonX on 2011-05-01
> **joskapista said:**
> Could someone please help me, how can I enable click and move with one finger (or this is the tap to drag which is not works yet?)?

That's tap-to-drag. See post #39.

---

### Post by scoddy on 2011-05-02
Wow, just got back to the forum after a few days of absence and such a progress, impressive.

> Glad you were able to confirm this. I'm going to take a more indepth look at the code tonight and see if I can't figure out what's causing it. Hopefully I'll have progress to report in an hour or a few.
Great, can report that this is now working as expected:
```

  Option          "TapButton1" "0"
    Option          "TapButton2" "0"
    Option          "TapButton3" "0"

```> 
1) You successfully execute two finger scrolling.
2) You lift one finger from the trackpad, leaving exactly one finger touching.
3) With a single finger you click the physical button on the trackpad.
4) This causes a right click.With your new code, the ButtonTouchExpire Setting is doing the trick, the default value of 100ms is a perfect value. Thanks much for doing all this great work!

---

### Post by joskapista on 2011-05-02
OK, thanks

---

### Post by BlueDragonX on 2011-05-02
> **buzzboy said:**
> I am running a MacBook 5,5 with a true multitouch trackpad using the bcm5974 driver. For my xorg file I copy pasta this

Section "InputClass"     
MatchIsTouchpad "on"     
Identifier      "Touchpads"     
Driver          "mtrack"
EndSection

That's not enoigh.  I need to see the entire contents of that file as well as the Xorg log file.  Please use a service like pastebin to upload them.

---

### Post by buzzboy on 2011-05-02
Here's the log file
[http://pastebin.com/x2w4Cf31](http://pastebin.com/x2w4Cf31)

And here's my Xorg.conf
[http://pastebin.com/UYa7WkeE](http://pastebin.com/UYa7WkeE)

---

### Post by BlueDragonX on 2011-05-02
> **buzzboy said:**
> Here's the log file
[http://pastebin.com/x2w4Cf31](http://pastebin.com/x2w4Cf31)

And here's my Xorg.conf
[http://pastebin.com/UYa7WkeE](http://pastebin.com/UYa7WkeE)

The mtrack driver is never loaded by Xorg. Your config is correct, though.

Make sure this file exists: ```
/usr/lib/xorg/modules/input/mtrack.so
```

If it does not then the driver was not installed.

Are you using Ubuntu? If yes, what version? If not, what *are* you using?

As I've said, if you're using Ubuntu, the easiest way is to install the deb from [my website](www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/):

```

# wget http://www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.1.1_VERSION_ARCH.deb
# sudo dpkg -i xserver-xorg-input-mtrack_0.1.1_VERSION_ARCH.deb

```

Where VERSION is either maverick or natty and ARCH is i386 or amd64 (both depending on what flavor of Ubuntu you have installed). I don't have Lucid packages yet.

---

### Post by buzzboy on 2011-05-02
I had attempted to install this for 10.04 just to try it. However th[FONT=monospace]is [/FONT]/usr/lib/xorg/modules/input/mtrack.so   does not exist. Not sure why. I had followed the steps posted on a previous page to install and received no errors.

---

### Post by BlueDragonX on 2011-05-02
You're using Lucid, which I have not tested against. The packages will not even build as-is in my Lucid build environment so I'd be surprised if you didn't get any errors, especially if that file is missing, since at the very least it indicates the install step failed or wasn't run.

You will need to wait till I've got packages built for Lucid unless you want to upgrade to Maverick or Natty.  Or you can attempt to solve the issue yourself in Lucid.

I intend to have packages for Lucid by the next feature release.

---

### Post by Helios747 on 2011-05-02
My bet is that the build is failing somewhere for lucid lynx. Can you upgrade to Natty? I can verify that the code is working on Natty.

Just so you know, that small how to I wrote was for Natty, sorry. I thought you were running it. Did you get any errors while following that?

Damn, dragon beat me to it.

---

### Post by eelcoh on 2011-05-02
I managed to bind the three finger down swipe to show activities by using xvkbd and xbindkeys.
```

"xvkbd  -text "\[Alt_L]\[F1]""
       m:0x0 + b:9

```

However, it seems that the swipe down is directly followed by a swipe up, unless the swipe is really fast and short. Is there anyway to make that less sensitive?

---

### Post by buzzboy on 2011-05-02
Yeah, I knew it was a crap shoot. I'll just wait till you have a lucid release because this is something I'm really needing in my Ubuntu Life

---

### Post by BlueDragonX on 2011-05-03
> **eelcoh said:**
> I managed to bind the three finger down swipe to show activities by using xvkbd and xbindkeys.
```

"xvkbd  -text "\[Alt_L]\[F1]""
       m:0x0 + b:9

```

However, it seems that the swipe down is directly followed by a swipe up, unless the swipe is really fast and short. Is there anyway to make that less sensitive?

You could increase the SwipeDist value. The default value is pretty sensitive.

> **buzzboy said:**
> Yeah, I knew it was a crap shoot. I'll just wait till you have a lucid release because this is something I'm really needing in my Ubuntu Life

I've put together some experimental Lucid packages. Try them out. [www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/](www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/)

---

### Post by BlueDragonX on 2011-05-04
> **BlueDragonX said:**
> I've put together some experimental Lucid packages. Try them out. [www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/](www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu/)

Anyone have an update on how the Lucid packages are working?  I know at least two people out there have downloaded them...

---

### Post by v41 on 2011-05-05
> **BlueDragonX said:**
> Anyone have an update on how the Lucid packages are working?  I know at least two people out there have downloaded them...

The lucid packages depend upon libmtdev1 which does not seem to be available for lucid.

---

### Post by v41 on 2011-05-05
Using the appletouch driver on a macbook-4.1, I get 2-finger scrolling and 2/3-finger tapping.  So it seems that this trackpad has some multi-touch functionality.  But it is not supported by the bcm5974 driver, so presumably it cannot be used with xf86-input-mtrack?

---

### Post by BlueDragonX on 2011-05-05
> **v41 said:**
> The lucid packages depend upon libmtdev1 which does not seem to be available for lucid.

I'll have the Lucid packages for mtdev uploaded in a bit.

> **v41 said:**
> Using the appletouch driver on a macbook-4.1, I get 2-finger scrolling and 2/3-finger tapping.  So it seems that this trackpad has some multi-touch functionality.  But it is not supported by the bcm5974 driver, so presumably it cannot be used with xf86-input-mtrack?

The Synaptics driver may support some multitouch-like features but that does not indicate whether or not the underlying driver implements the slotted multitouch protocol which is required for full multitouch support (see the [readme](https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md) for more info).

Do an lsusb -v and see what model of trackpad you have and what driver it's using. However, I don't believe the 4,1 hardware or earlier supports multitouch (I've got an early 2008 Black MacBook which I'll can take a look at though, it's a 4,1).

---

### Post by v41 on 2011-05-05
To satisfy my curiosity, I found an explanation [here]("http://voices.canonical.com/chase.douglas/2010/08/16/decoding-apples-magic-trackpad/") for why older trackpads are not truly multi-touch,

> 
 most Synaptics touchpads are not truly multitouch. They can provide  information on how many fingers are touching the touchpad, but they  can't provide the locations of each of the individual fingers. Thus, you  can do two-finger scroll and three-finger tapping because you only need  one set of coordinates to perform those functions. But you can't do  pinch to zoom or rotate because the device doesn't give you the  locations of all the fingers.		


I'm pretty sure the Macbook-4.1 falls into this category.  FWIW, lsusb shows that the trackpad product ID is 0x0229, version 0x111.

---

### Post by Nopstnz8 on 2011-05-06
So I've been using the driver from post 39, and it works pretty well, but I know tap-drag isn't fully working yet, dev confirmed v2 will be more stable, but I've been noticing a bug when typing that is really bothering me. When I am typing in say an address bar, facebook comment, or something similar, if the mouse pointer isn't in the box at the same time, or I think when the box scrolls down to show more space, it won't allow me to type anymore, or I will end up continuing to type, but on the completely wrong line. Is anyone aware of this? Is there an even better driver out yet?

---

### Post by BlueDragonX on 2011-05-06
> **Nopstnz8 said:**
> So I've been using the driver from post 39, and it works pretty well, but I know tap-drag isn't fully working yet, dev confirmed v2 will be more stable, but I've been noticing a bug when typing that is really bothering me. When I am typing in say an address bar, facebook comment, or something similar, if the mouse pointer isn't in the box at the same time, or I think when the box scrolls down to show more space, it won't allow me to type anymore, or I will end up continuing to type, but on the completely wrong line. Is anyone aware of this? Is there an even better driver out yet?

That happens at times, and it's quite annoying, but it's not a bug. You're accidentally tapping the trackpad as you type. You may want to increase the pressure requires to trigger a tap and/or decrease the palm detection size (or turn it on if you have it disabled).

The next feature release, v0.2.0, will include support for disabling the touchpad while typing.

---

### Post by Helios747 on 2011-05-06
I simply disable tapping all together. Pressing to click doesn't bother me.


I was wondering if there will be a feature planned to do kind of the smooth scrolling like OS X does, when you scroll and let go it still kind of glides based on how fast you scrolled or until you use your fingers to stop it.

---

### Post by BlueDragonX on 2011-05-06
> **Helios747 said:**
> I was wondering if there will be a feature planned to do kind of the smooth scrolling like OS X does, when you scroll and let go it still kind of glides based on how fast you scrolled or until you use your fingers to stop it.

It's not in the roadmap, but it's not a bad idea. I'll probably make it part of v0.3.0.

---

### Post by dogtooth on 2011-05-07
Hi, I'm on Arch. The driver isn't working for me (two-finger tapping, scrolling etc. doesn't work). Here's my xorg.conf: [http://pastebin.com/40cw0MpD](http://pastebin.com/40cw0MpD).

If I understand the Xorg log correctly, the mtrack driver never gets loaded. What am I doing wrong?

---

### Post by BlueDragonX on 2011-05-07
> **dogtooth said:**
> Hi, I'm on Arch. The driver isn't working for me (two-finger tapping, scrolling etc. doesn't work). Here's my xorg.conf: [http://pastebin.com/40cw0MpD](http://pastebin.com/40cw0MpD).

If I understand the Xorg log correctly, the mtrack driver never gets loaded. What am I doing wrong?

Your xorg.conf is correct. Please post your xorg logs.

---

### Post by dogtooth on 2011-05-07
> **BlueDragonX said:**
> Your xorg.conf is correct. Please post your xorg logs.

[http://pastebin.com/qDg5tkTK](http://pastebin.com/qDg5tkTK)

BTW, the .so file you asked buzzyboy about *does* exist on my system.

---

### Post by BlueDragonX on 2011-05-08
> **dogtooth said:**
> [http://pastebin.com/qDg5tkTK](http://pastebin.com/qDg5tkTK)

BTW, the .so file you asked buzzyboy about *does* exist on my system.

I was wrong, there is a problem with your xorg.conf:
```

Section "ServerFlags"
	Option "AutoAddDevices" "False"
EndSection

```

That is preventing the devices from being loaded by X on load. Either remove that section from your xorg.conf or create an explicit InputDevice section for your trackpad instead of using the InputClass.

---

### Post by Psychotron45 on 2011-05-08
I just tried the mtrack driver and found some issues with it.

- I trigger button clicks a lot during typing...

- Even though I'm using the 0.1.1 deb disabling tapping (TapButton1 = 0) breaks pointer movement. After the release notes this should have been fixed?

- Pointer movement is broken for me. This might be just a config issue, but: What happens is, when moving the pointer it always gets stuck (during a single move). I think what happens is, that I change the position and orientation of the finger during the move. And as the touch area gets bigger at some point mtrack mistakes it for a thumb, which stops the movement of the pointer. So the solution might be to change ThumbSize/ThumbRatio. However: a finger usually can't transform into a thumb :) So it would make mtrack more robust, if it would take that into account. OTOH my ThumbSize is 26, which is a quarter of this big trackpad (says the doc). However, movement stops way before this size...

- The docs are a little confusing. The README says:
 
**ClickFinger1** - ... Defaults to 3.
**ClickFinger2** - ... Defaults to 2.

However 1-finger click produces button 1 and 2-finger click produces button 3. As one would expect, btw.

- A wish: I would like to have a 3-finger click, simulating the middle mouse button.

- Is there an interface which a configuration app could use to adjust the settings? Restarting X all the time is a bit annoying :)

- Can I somehow enable debug output to see how mtrack interprets the touches?

- Could mtrack emit X key symbols instead of countless mouse buttons? This would make usage of the actions easier.

Ok, thats it for now...

---

### Post by BlueDragonX on 2011-05-08
> **Psychotron45 said:**
> I trigger button clicks a lot during typing...

This is expected. You can adjust your settings to mitigate this - thumb/palm detection and min tap pressure, or just disable tapping. Or you can be more aware of what you're doing. As frequently stated, support for disabling the touchpad while typing is coming in the next version.

> **Psychotron45 said:**
> Even though I'm using the 0.1.1 deb disabling tapping (TapButton1 = 0) breaks pointer movement. After the release notes this should have been fixed?

It is fixed. Please re-install, try again, and if it's not working post your xorg.conf and X logs.

> **Psychotron45 said:**
> Pointer movement is broken for me. This might be just a config issue (snip) So the solution might be to change ThumbSize/ThumbRatio. However: a finger usually can't transform into a thumb :) So it would make mtrack more robust, if it would take that into account. OTOH my ThumbSize is 26, which is a quarter of this big trackpad (says the doc). However, movement stops way before this size...

Your are mistaken on a couple of points here.

Firstly, a finger *must* transform from a regular touch to a thumb. When you first apply pressure to the trackpad it's not large enough to consider a thumb. Once the finger settles onto the trackpad then the driver can see its full size and shape, at which point it decides that the touch is a thumb.

Secondly, the ThumbSize is measures in trackpad pixels, not percentages. The MacBook trackpads are over 1000 pixels wide. Check the logs, the driver will indicate the size of the trackpad on start.

You just need to adjust your thumb size as you suspected.

> **Psychotron45 said:**
> The docs are a little confusing. The README says:
 
**ClickFinger1** - ... Defaults to 3.
**ClickFinger2** - ... Defaults to 2.

However 1-finger click produces button 1 and 2-finger click produces button 3. As one would expect, btw.

This is consistent with X. In X the left mouse button is button 1, right is button 2, middle is button 3. Generally the scroll wheel triggers buttons 4 and 5.

> **Psychotron45 said:**
> A wish: I would like to have a 3-finger click, simulating the middle mouse button.

See the issues list. Three finger tapping works but it is inconsistent.

> **Psychotron45 said:**
> Is there an interface which a configuration app could use to adjust the settings? Restarting X all the time is a bit annoying :)

See the issues list. Xinput properties support exists in dev.

> **Psychotron45 said:**
> Can I somehow enable debug output to see how mtrack interprets the touches?

You'll have to get the source code and compile it yourself. There is an excessive amount of debugging output available. You'll need to enable what you want via the CFLAGS. See the source code.

> **Psychotron45 said:**
> Could mtrack emit X key symbols instead of countless mouse buttons? This would make usage of the actions easier.

Mice in X emit mouse button clicks. Thusly the mtrack driver emits mouse button clicks. You have the ability to assign any mouse button you want to any of the functions. There are other ways emit key events off of mouse clicks, they do not belong in the driver.

---

### Post by dogtooth on 2011-05-08
> **BlueDragonX said:**
> I was wrong, there is a problem with your xorg.conf:
```

Section "ServerFlags"
	Option "AutoAddDevices" "False"
EndSection

```

That is preventing the devices from being loaded by X on load. Either remove that section from your xorg.conf or create an explicit InputDevice section for your trackpad instead of using the InputClass.

Thanks, works now! Thanks for the great driver & support!

---

### Post by marciallus on 2011-05-09
Hi,

I've just put ubuntu on my macbookpro 13', unibody, with big trackPad with One button
And just wanted to say that your driver r0x !!

I've use the tree finger swip up and down to run the scale or expo compiz plugin, like in mac OS

and the 3 finger Taps for copy the clipboard. no problem for me all is good.

the only thing which could be pretty cool would be a graphical GUI for params, but i will try xinput this evening.

and perhaps a four finger management ? 

thanx a lot for your work

--
MarCo

---

### Post by BlueDragonX on 2011-05-09
> **marciallus said:**
> And just wanted to say that your driver r0x !!

Awesome!

> **marciallus said:**
> the only thing which could be pretty cool would be a graphical GUI for params, but i will try xinput this evening.

I've considered doing something like that, but it would be a separate project and I'm focusing all of my effort on the driver.

The Xinput properties support is in the dev branch, so if you installed one of the debs you won't be able to use it. It will be part of the next feature release, though. You can either wait till then or build the dev branch on your system.

> **marciallus said:**
> and perhaps a four finger management ? 

Four finger tap and swipe support is coming with the next feature release as well.

---

### Post by dukes on 2011-05-09
> **marciallus said:**
> Hi,

I've just put ubuntu on my macbookpro 13', unibody, with big trackPad with One button
And just wanted to say that your driver r0x !!

I've use the tree finger swip up and down to run the scale or expo compiz plugin, like in mac OS

and the 3 finger Taps for copy the clipboard. no problem for me all is good.

the only thing which could be pretty cool would be a graphical GUI for params, but i will try xinput this evening.

and perhaps a four finger management ? 

thanx a lot for your work

--
MarCo


MarCo, post your configs!  :)

---

### Post by unagimiyagi on 2011-05-13
Hi there,

How do you install this?  I downloaded the .deb from the ftp site, and Ubuntu software center installed it.  
I rebooted.  But now what?

I looked in the readme, but I don't see anything about how to activate / use this cool program.

I don't need to compile it and install it, right?  (meaning that make install command is not necessary because I have downloaded the .deb)

Thanks

---

### Post by BlueDragonX on 2011-05-13
> **unagimiyagi said:**
> I looked in the readme, but I don't see anything about how to activate / use this cool program.


Look again. There's a section called "Configuration" which takes up 90% of the readme.

---

### Post by unagimiyagi on 2011-05-13
> **BlueDragonX said:**
> Look again. There's a section called "Configuration" which takes up 90% of the readme.


This is what I see.  It's in a file called Readme.md
I clicked on it and got what's below.

Xorg Multitouch Trackpad Driver
* Install the Debian package
* Configure xorg.conf
* Restart X

When I am saying that I (and likely other newbies) do not understand how to install this, is that I would like more info about each of these three steps.

In case you are interested in the points that a newbie used to the windows world would find unclear, it's:

Where is the debian package?  I assume that it's the binary for Ubuntu that I installed already from the ftp site dated April 28, 2011.

How do I configure xorg.conf?  Do I search for it somewhere in my file system and then add some lines to it?

I assume I restart X (I think that's the windowing system name in Ubuntu) by rebooting the computer?


Here is some additional detail for total newbies that I added to another post made earlier from Helios (thanks, Helios!)


If you have ubuntu, go to this link and download the file that applies to your version of linux that you are running:

[http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/)

I grabbed this one:  
[xserver-xorg-input-mtrack_0.1.1_natty_i386.deb]("http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.1.1_natty_i386.deb")  because I have Ubuntu 11.04 natty, the 32-bit version.

double click on this and Ubuntu software center will open.  Install it by following the onscreen directions. FYI: You do not need to download the tar file and extract it, compile it with "make install" or anything like that. 
If the right .deb is not in the link to the ftp site above, you'll have to compile this yourself before proceeding to any further steps.  No directions are being included for that.

OK, now you've just installed the new driver, but it's not activated yet.

To do that, you need to find and edit a file called xorg.conf.

The place (path) where this file is located on your computer is: /etc/X11/xorg.conf

You need to open this file.  If you use Nautilus, the windows explorer-type graphical file browser, you can navigate to and open this file.
Or you can use nano or vim or gedit (all text editors) to open this file.  To open this file, you need to become the superuser with the command sudo.
So, to use the built-in text editor to modify xorg.conf, type in the following at the command line (open a terminal window):
     
     ```

     sudo nano /etc/X11/xorg.conf 

``` Type in the following bit of code at the end of the file
```

Section "InputClass"
        MatchIsTouchpad "on"
        Identifier "Touchpads"
        Driver "mtrack"
EndSection


```When you are done, your xorg.conf should look like this:

```

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
        MatchIsTouchpad "on"
        Identifier "Touchpads"
        Driver "mtrack"
EndSection




```Bookmark this page and Reboot your computer. (yes, you must do this or the new driver won't work).  If you don't wish to reboot, you can just restart the X windowing system if you know how to do that.

To tweak the options for the driver (sensitivity, pressure sensing, tap  to click enable/disable, thumb width, etc) follow the list of options in  the configuration section of the readme here:

[https://github.com/BlueDragonX/xf86-...ster/README.md]("https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md")

You insert the options you want to tweak in your xorg.conf file in between "Driver "mtrack"" and "EndSection"


Thanks for the great program!

---

### Post by clakes on 2011-05-14
You would forgive my apparently stupid question, I hope...

Is on supposed to remove every multitouch-related driver and tweak prior to installing *mtrack*?
(xserver-xorg-input-mtrack_0.1.1_maverick_amd64.deb - in my own case)

I've been messing with the xf86-, bcm-, and gpointing- thingies before...
Thank you for your help.

---

### Post by BlueDragonX on 2011-05-16
> **clakes said:**
> You would forgive my apparently stupid question, I hope...

Is on supposed to remove every multitouch-related driver and tweak prior to installing *mtrack*?
(xserver-xorg-input-mtrack_0.1.1_maverick_amd64.deb - in my own case)

I've been messing with the xf86-, bcm-, and gpointing- thingies before...
Thank you for your help.

Not a stupid question, but a difficult one for my to answer since I don't know specifically what else you have installed. I would just try it and see if it works. If not, then blacklist any kernel drivers that are not bcm5974, remove (or comment) any xorg.conf configuration that is not mtrack, and stop any services that may interfere associated with those blacklisted/removed kernel/xorg drivers.

---

### Post by BlueDragonX on 2011-05-16
> **unagimiyagi said:**
> Thanks for the great program!

Glad you figured it out! 

A bit of Googling is often all it takes to find a few examples and howtos. There's also loads of documentation both on the Ubuntu sites and the project pages for the software in question (xorg in this case). Ubuntu's docs are always a great place to start.

---

### Post by god7i11a on 2011-05-17
just trying out mtrack (i couldnt handle the default trackpad, no click-n-drag), and see this in the Xorg.0.log even though it seems mtrack is working:

> 
[    48.022] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
[    48.022] (II) device control: init
[    48.022] (**) Option "Device" "/dev/input/mouse0"
[    48.022] (EE) mtrack: cannot configure device
[    48.022] (EE) Couldn't init device "bcm5974"
[    48.022] (II) UnloadModule: "mtrack"
[    48.022] (II) Unloading mtrack
there are lots of other entries for mtrack and bcm5974, but this is the last.

is this a problem? BTW, is kernel module bcm5974 still supposed to be loaded? mtrack depends on it?

next up is to fine-tune the settings; two-finger drag in Firefox is not nice yet.

---

### Post by BlueDragonX on 2011-05-17
> **god7i11a said:**
> just trying out mtrack (i couldnt handle the default trackpad, no click-n-drag), and see this in the Xorg.0.log even though it seems mtrack is working:

there are lots of other entries for mtrack and bcm5974, but this is the last.

is this a problem? BTW, is kernel module bcm5974 still supposed to be loaded? mtrack depends on it?

next up is to fine-tune the settings; two-finger drag in Firefox is not nice yet.

That's not a problem. You should see the mtrack driver loaded for a /dev/input/event* device.

The kernel driver provides access to the hardware, so yes.

---

### Post by pbhedlund on 2011-05-17
> **god7i11a said:**
> 

is this a problem? BTW, is kernel module bcm5974 still supposed to be loaded? mtrack depends on it?


I add
```
MatchDevicePath "/dev/input/event*"
```to xorg.conf to remove that kind of errors.

---

### Post by god7i11a on 2011-05-17
> **BlueDragonX said:**
> That's not a problem. You should see the mtrack driver loaded for a /dev/input/event* device.

The kernel driver provides access to the hardware, so yes.

ok, BTW your "run" program points to /dev/input/event6 but i get 
```

godzilla@gyro:~/install/xf86-input-mtrack$ ./run 
mtrack: devname: applesmc
mtrack: devid: 0 0 0
mtrack: caps:
Touchpad has minimal capabilities. Some features will be unavailable.
width:  0
height: 0
^C

```i get correct results when i do sudo bin/src/test /dev/input/event5 instead (i see same in Xorg.0.log).  i think multitouch handled this differently. 

is there a way to play with the settings  without restarting the Xserver each time? it would make it easier to test.

also, i looked around but could not find a description of the differences between your module and multitouch. a diff would help when testing and comparing the two.

---

### Post by god7i11a on 2011-05-18
ok, xinput works for some of the properties. here is what i could do:

```

sudo xinput set-prop 11 "Trackpad Thumb Size" 25 70
sudo xinput set-prop 11 "Trackpad Sensitivity" 0.85

```etc

where 11 is the device number found like so:

```

godzilla@gyro:~/install/xf86-input-mtrack$ xinput list
&#9121; Virtual core pointer                         id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer               id=4    [slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                  id=11   [slave  pointer  (2)]
...

```here is a list of properties that is availble as of the latest dev branch of git:

```

godzilla@gyro:~/install/xf86-input-mtrack$ xinput list-props 11
Device 'bcm5974':
    Device Enabled (137):    1
    Coordinate Transformation Matrix (139):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (262):    0
    Device Accel Constant Deceleration (263):    1.000000
    Device Accel Adaptive Deceleration (264):    1.000000
    Device Accel Velocity Scaling (265):    10.000000
    Trackpad Disable Input (266):    0
    Trackpad Sensitivity (267):    0.850000
    Trackpad Button Settings (268):    1, 1, 100
    Trackpad Button Emulation (269):    3, 2
    Trackpad Tap Settings (270):    100, 120, 400
    Trackpad Tap Button Emulation (271):    1, 3, 2
    Trackpad Thumb Detection (272):    1, 0
    Trackpad Thumb Size (273):    26, 70
    Trackpad Palm Detection (274):    1, 1
    Trackpad Palm Size (275):    40
    Trackpad Gesture Settings (276):    10, 100
    Trackpad Scroll Distance (277):    175
    Trackpad Scroll Buttons (278):    4, 5, 6, 7
    Trackpad Swipe Distance (279):    700
    Trackpad Swipe Buttons (280):    8, 9, 10, 11
    Trackpad Scale Distance (281):    150
    Trackpad Scale Buttons (282):    14, 15
    Trackpad Rotate Distance (283):    150
    Trackpad Drag Settings (284):    1, 350, 40, 200
    Synaptics Off (447):    1

```i assume other parameters from the README will join the list eventually.

---

### Post by jamesjenner on 2011-05-18
Well I've played around with this for a few hours this night and am very impressed with the results. I've got a 5,1 MacBook running 11.10 and I didn't have a problem (I did build from source, not really sure if I needed to or not). Fantastic job on the drivers, a big thank you for your effort in getting this working.

The only problem I have is trying to do the three finger click is problematic. Sometimes it works, sometimes it doesn't. I'm going to go through the settings tomorrow night and see what I can tweak to get it going (not a major issue, only really used for a couple of things so I have work arounds that don't bother me).

Would be nice to have the pad disable when typing, but after experimenting with thumb and palm size related settings I suspect it's not going to be an issue anyway. 

Not sure where pinching and expanding apply, I thought it may work in firefox to change the size of text, but nope. Oh btw, two finger drag is brillant for scrolling :)

Again thanks mate, brilliant work.

Cheers,

James.

---

### Post by BlueDragonX on 2011-05-19
Experimental disable-on-keystroke functionality is now available using the dispad tool I've created. It will only work with the code in the dev (since it uses xinput) and some functionality is not or partially implemented - the config file, for example, is ignored at the moment, and I intend to allow creation of a PID file when forking to the background. On the other side of the fence, the driver itself does not behave exactly as I want it when it's disabled.

> **god7i11a said:**
> ok, BTW your "run" program points to /dev/input/event6...

I know this. It's just a shortcut for my personal use.

> **god7i11a said:**
> also, i looked around but could not find a description of the differences between your module and multitouch. a diff would help when testing and comparing the two.

What are you testing? I don't see any benefit to comparing the mtrack codebase to multitouch. mtrack is a fork of multitouch, but the first alpha releases were a result of two major rewrites of the original code. The added features since then make this even less useful.

> **god7i11a said:**
> ok, xinput works for some of the properties. here is what i could do:
<snip>
i assume other parameters from the README will join the list eventually.

All of them are available, but none of them are documented (yet).

> **jamesjenner said:**
> Well I've played around with this for a few hours this night and am very impressed with the results.

Thanks :)

> **jamesjenner said:**
> The only problem I have is trying to do the three finger click is problematic.

I am aware of this. See the issues list on github.

> **jamesjenner said:**
> Would be nice to have the pad disable when typing

Experimental support is now available, but again, take a look at github for new features, etc. Most of the stuff people are looking for is on the roadmap.

> **jamesjenner said:**
> Not sure where pinching and expanding apply, I thought it may work in firefox to change the size of text, but nope. Oh btw, two finger drag is brillant for scrolling :)

You'll have to bind those functions in the application to the applicable mouse clicks for those functions. There are ways, but I've not really looked into it.

---

### Post by god7i11a on 2011-05-19
> **BlueDragonX said:**
> 
What are you testing? I don't see any benefit to comparing the mtrack codebase to multitouch. mtrack is a fork of multitouch, but the first alpha releases were a result of two major rewrites of the original code. The added features since then make this even less useful.


there are two trackpad codebases out there, one the fork of the other, and at least one user would like to know what is the difference. i guess its the "added features" to mtrack, but it would be nice to know what the diffs are w/o reading through the source code.

my one headache is that while either two-finger scrolling or one finger mouse moving, as often as not the movement "jams". as best as i can tell this is happening because the finger pressure on the pad is increasing past some cutoff level, causing a full "stop". the only way to resume movement is to release the fingers from the pad completely and then remake contact. decreasing pressure is not enough to release the jam.

the other headache is that scrolling up does not work as smoothly as scrolling down, and i think its a pressure cutoff thing again. as one swipes downwards the pressure stays the same or lessens. as one pushes up, the pressure increases. i *think*.

---

### Post by jamesjenner on 2011-05-19
> **god7i11a said:**
> the other headache is that scrolling up does not work as smoothly as scrolling down, and i think its a pressure cutoff thing again. as one swipes downwards the pressure stays the same or lessens. as one pushes up, the pressure increases. i *think*.

I've not found problems with scrolling up at all. I have to say though my MacBook isn't my main computer so I haven't used it that extensively, but when I have the scrolling hasn't been a problem, in my experience that is.

---

### Post by BlueDragonX on 2011-05-19
> **god7i11a said:**
> there are two trackpad codebases out there, one the fork of the other, and at least one user would like to know what is the difference. i guess its the "added features" to mtrack, but it would be nice to know what the diffs are w/o reading through the source code.

Thanks, specific questions are much more helpful.

The main feature mtrack has over multitouch is that it's fully configurable, both via xorg.conf and xinput. The second is that it's more consistent and less quirky - tapping, movement, and dragging all interfere with each other in multitouch. Not so in mtrack. Lastly, there are additional features in the roadmap, such as disable-on-keystroke, button emulation zones, and more. Take a look at the github milestones to see what's been completed and what's coming up in the next release.

> **god7i11a said:**
> my one headache is that while either two-finger scrolling or one finger mouse moving, as often as not the movement "jams". as best as i can tell this is happening because the finger pressure on the pad is increasing past some cutoff level, causing a full "stop". the only way to resume movement is to release the fingers from the pad completely and then remake contact. decreasing pressure is not enough to release the jam.

You're triggering the thumb detection. Adjust the thumb detection settings or disable it.

> **god7i11a said:**
> the other headache is that scrolling up does not work as smoothly as scrolling down, and i think its a pressure cutoff thing again. as one swipes downwards the pressure stays the same or lessens. as one pushes up, the pressure increases. i *think*.

If it seems like it's the same thing then the above suggestion should fix it.

---

### Post by god7i11a on 2011-05-20
> **BlueDragonX said:**
> 
The main feature mtrack has over multitouch is that it's fully configurable,

a very nice feature indeed. any chance of getting FingerHigh and Finger Low configurable via xinput?

> 
You're triggering the thumb detection. Adjust the thumb detection settings or disable it.
ok. it definitely seems like if i stay "up on my fingertips" as i scroll up and don't press too hard (keeping contact size small), there is less jamming. 


anther problem i ran into was click-and-drag, for example, to move a window or drag a scrollbar. i found the drag wasnt going anywhere. it seemed the easiest way to fix it was to adjust the PalmSize upwards from the default 40 to 60 (!!??) ... even though no way the thumb is taking up even 40% of the trackpad height (if i read your docs correctly). and this is with thumb touches ignored. if i take the whole side of my thumb (horizontally) and click the pad at bottom, dragging goes nowhere even at PalmSize 60, and i gauge my thumb is only taking up -- what -- 10% of the trackpad height. it might be taking up 30% of the trackpad width, OTOH. if i turn thumb ignore back on, dragging stiilll works ok so long as PalmSize is large enough, even though ThumbSize is 25. i gather its a palm that can stop a drag, but not a thumb. what is thumb detection supposed to affect, out of curiosity?

---

### Post by BlueDragonX on 2011-05-23
> **god7i11a said:**
> a very nice feature indeed. any chance of getting FingerHigh and Finger Low configurable via xinput?

I'll have those added for v0.2.0. Should be released a few days from now.

> **god7i11a said:**
> if i turn thumb ignore back on, dragging stiilll works ok so long as PalmSize is large enough, even though ThumbSize is 25. i gather its a palm that can stop a drag, but not a thumb. what is thumb detection supposed to affect, out of curiosity?

In this case the documentation is incorrect. Both the ThumbSize and PalmSize values are calculated as a percentage of the maximum touch values. Meaning, there's an upper limit to the size of a touch, and these values are a percentage of that. This method is portable to trackpads which report pressure instead of the size of touches. As such it's fairly arbitrary, but will at least be consistent among the same types of devices.

What's done with touches reported as thumbs or palms is dictated by the config. If you have IgnoreThumb set to true, then the driver will ignore touches which are reported as thumbs. If that touch was participating in a gesture, then it's treated as if it were removed from the trackpad. From that point on the touch is ignored, regardless of what it looks like. The exact same rules apply to palms. The only difference is how they're detected.

If you enable DisableOnThumb or DisableOnPalm then all trackpad input will be disabled until the touch is removed from the trackpad.

I will be setting the default values for IgnoreThumb, IgnorePalm, DisableOnThumb, and DisableOnPalm all to false for v0.2.0 since that release supports disabling the trackpad while typing.

---

### Post by BlueDragonX on 2011-05-26
mtrack v0.2.0 is now available!

Support for disabling the trackpad while typing is included in this release. This feature requires an external daemon. I have created dispad for this purpose:
[LIST]
[*][Dispad Ubuntu Packages](http://www.dev.fatalmachine.org/packages/dispad/ubuntu/)
[*][Dispad Source at Github](https://github.com/BlueDragonX/dispad)
[/LIST]

**Changelog for v0.2.0**
[LIST]
[*]Now built via autoconf/automake.
[*]Fully configurable via XInput.
[*]Sensitivify now configurable.
[*]Trackpad can now be disabled on keystroke via an external daemon.
[*]Four finger tapping/swiping added.
[*]Button zones added, a new button emulation method.
[*]Tap-to-drag fixed.
[*]Three finger tapping responsiveness fixed.
[/LIST]

---

### Post by joskapista on 2011-05-27
Hello
after I've installed mtrack 2.0 the touchpad stopped working. I attached my xorg.0.log
Could you please help me, what is the problem?

---

### Post by BlueDragonX on 2011-05-27
Please post the output of:

# sudo updatedb
# locate mtrack_drv.so

EDIT: Nevermind, I need to make a change to the modules.

---

### Post by joskapista on 2011-05-27
:~$ locate mtrack_drv.so
/usr/local/lib/xorg/modules/input/mtrack_drv.so

---

### Post by BlueDragonX on 2011-05-27
> **joskapista said:**
> :~$ locate mtrack_drv.so
/usr/local/lib/xorg/modules/input/mtrack_drv.so

Yes, it's being installed into the wrong location, which your previous post made me aware of. My server's down right now, but when it comes back up I'll have new debs available.

---

### Post by eelcoh on 2011-05-27
> **BlueDragonX said:**
> mtrack v0.2.0 is now available!

**Changelog for v0.2.0**
[LIST]
[*]Now built via autoconf/automake.
[*]Fully configurable via XInput.
[/LIST]

Hmm. Unfortunately, on Fedora it now says:
```

configure.ac:21: error: must install xorg-macros 1.8 or later before running autoconf/autogen

```

Not sure how to fix that, given that i already have got package xorg-x11-util-macros-1.13.0-1.fc15.noarch installed.

---

### Post by BlueDragonX on 2011-05-27
> **eelcoh said:**
> Hmm. Unfortunately, on Fedora it now says:
```

configure.ac:21: error: must install xorg-macros 1.8 or later before running autoconf/autogen

```

Not sure how to fix that, given that i already have got package xorg-x11-util-macros-1.13.0-1.fc15.noarch installed.

Don't know. I've not tested against Fedora. You might try installing an earlier version of xorg-x11-util-macros.

---

### Post by johnmurrayvi on 2011-05-28
> **eelcoh said:**
> Hmm. Unfortunately, on Fedora it now says:
```

configure.ac:21: error: must install xorg-macros 1.8 or later before running autoconf/autogen

```

Not sure how to fix that, given that i already have got package xorg-x11-util-macros-1.13.0-1.fc15.noarch installed.

Same here on Natty. I have xutils-dev installed but still receiving the error.
Gonna keep trying to figure out more.

---

### Post by jamesjenner on 2011-05-29
> **johnmurrayvi said:**
> Same here on Natty. I have xutils-dev installed but still receiving the error.
Gonna keep trying to figure out more.

I've got the same problem. I've downloaded the latest but it still gives the error that I must install version 1.8 or later.

I got my version from [http://mirrors.kernel.org/ubuntu/pool/main/x/xutils-dev/](http://mirrors.kernel.org/ubuntu/pool/main/x/xutils-dev/), it's xutils-dev_7.6+3_amd64.deb, which appears to be the latest. Not sure how to fix this and I sooo much want the three finger goodness. O.o


:edit:

I'm on 11.04 64bit, if that helps.

---

### Post by BlueDragonX on 2011-05-29
It works fine for me on Natty with xutils-dev 1:7.6+1 intalled.

How did ya'll run autotools? If you only do an autoconf && automake it will break every time. You need to do an autoreconf -i

---

### Post by BlueDragonX on 2011-05-29
My server is back up and the mtrack debs have been rebuilt with the correct install paths. Please try them again.

---

### Post by unagimiyagi on 2011-05-29
> **BlueDragonX said:**
> My server is back up and the mtrack debs have been rebuilt with the correct install paths. Please try them again.

Any documentation on how to compile using autoconf and automake for those who are not familiar with these tools?

---

### Post by ckisgen on 2011-05-29
> **BlueDragonX said:**
> My server is back up and the mtrack debs have been rebuilt with the correct install paths. Please try them again.

i haven't been able to get onto fatalmachine.org for a couple of days now .. including the last couple of hours since it was supposed to be back up ..  been holding my breath for trackpad disable on type and click to drag  ..

---

### Post by johnmurrayvi on 2011-05-30
> **jamesjenner said:**
> I've got the same problem. I've downloaded the latest but it still gives the error that I must install version 1.8 or later.

I got my version from [http://mirrors.kernel.org/ubuntu/pool/main/x/xutils-dev/](http://mirrors.kernel.org/ubuntu/pool/main/x/xutils-dev/), it's xutils-dev_7.6+3_amd64.deb, which appears to be the latest. Not sure how to fix this and I sooo much want the three finger goodness. O.o


:edit:

I'm on 11.04 64bit, if that helps.

Also on 64bit as well. 

> **BlueDragonX said:**
> It works fine for me on Natty with xutils-dev 1:7.6+1 intalled.

How did ya'll run autotools? If you only do an autoconf && automake it will break every time. You need to do an autoreconf -i

I tried autoreconf -i and got:
```
jmurray@jjmvi-mbp-ubuntu:~/projects/mtrack$ autoreconf -i
configure.ac:3: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
/usr/share/aclocal/xorg-macros.m4:1124: XORG_INSTALL is expanded from...
/usr/share/aclocal/xorg-macros.m4:1105: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:3: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
aclocal.m4:1145: XORG_INSTALL is expanded from...
aclocal.m4:1126: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:3: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
aclocal.m4:1145: XORG_INSTALL is expanded from...
aclocal.m4:1126: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:17: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:18: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

---

### Post by BlueDragonX on 2011-05-30
Then execute the full toolchain:

libtoolize && aclocal && autoconf && automake -c --add-missing

---

### Post by BlueDragonX on 2011-05-30
The server really is back up now. Had some DNS configuration that got overlooked.

---

### Post by joskapista on 2011-05-30
Now I could download the new driver, and it looks perfect! I'm testing it now, but my first impression was that it works like the original apple driver. Thanks again for your work!
I've installed the dispad too but I'm able write and move the cursor simultaneously.
Thanks

---

### Post by unagimiyagi on 2011-05-30
> **joskapista said:**
> Now I could download the new driver, and it looks perfect! I'm testing it now, but my first impression was that it works like the original apple driver. Thanks again for your work!
I've installed the dispad too but I'm able write and move the cursor simultaneously.
Thanks

Ah, server is working again and I downloaded 0.2 deb files. 

My impressions are that all is well except for two issues out of the box:

--up scrolling is not smooth and doesn't work as nicely as scrolling down

--pressing the button with your thumb makes the cursor jump around.  As in, hover over a link, and double tab the trackpad with your thumb makes the cursor jump around, so it's not precise.  This is an issue that I had using the original ubuntu trackpad driver as well.

--it seems that the click and drag (like selecting icons in nautius is better now)

All in all, a tough project indeed to tackle as in my experience, Apple has somehow finely tuned their driver to work exceptionally well.  Other one-button trackpads, including a newer one from lenovo's x220, indeed are not smooth at all.  I would recommend your trackpad driver as the best of the bunch for ubuntu.


Feature request:  a horizontal zone to emulate the "old" macbook pro trackpad.  This trackpad is the one right before the current buttonless trackpads.  I am thinking that dedicating say, the bottom horizontal 25% of the mbp's trackpad to being exclusively a button will go a long way to enable the trackpad to work properly a la the native apple driver.  I suspect that many people rest their thumbs on the bottom edge of the trackpad, and this tends to mess things up when two-finger scrolling and when clicking on links, etc.

---

### Post by Jannish on 2011-05-31
Thanks for a really great driver! :p
However, is it possible to include the Option "BottomEdge" setting, so when you use click and drag, your thumb doesn't move the pointer?

---

### Post by BlueDragonX on 2011-06-01
> **unagimiyagi said:**
> 
--up scrolling is not smooth and doesn't work as nicely as scrolling down

--pressing the button with your thumb makes the cursor jump around.  As in, hover over a link, and double tab the trackpad with your thumb makes the cursor jump around, so it's not precise.  This is an issue that I had using the original ubuntu trackpad driver as well.


I've not been able to reproduce either of these issues. How are you holding your fingers? I need to know how much pressure (roughly) you're putting on the pad, how close your fingers are together, and at what angle you're touching.

> **unagimiyagi said:**
> 
--it seems that the click and drag (like selecting icons in nautius is better now)


The tap-to-drag settings are adjustable. Check out the readme and tweak them till you like them.

> **unagimiyagi said:**
> 
Feature request:  a horizontal zone to emulate the "old" macbook pro trackpad.  This trackpad is the one right before the current buttonless trackpads.  I am thinking that dedicating say, the bottom horizontal 25% of the mbp's trackpad to being exclusively a button will go a long way to enable the trackpad to work properly a la the native apple driver.  I suspect that many people rest their thumbs on the bottom edge of the trackpad, and this tends to mess things up when two-finger scrolling and when clicking on links, etc.

It would go well with the button zones feature, yes. I may implement this in the next feature release. I'm considering implementing edge scrolling and coasting as well.

---

### Post by unagimiyagi on 2011-06-03
[COLOR=Red][QUOTE=[COLOR=Red]**BlueDragonX;10889524]I've not been able to reproduce either of these issues. How are you holding your fingers? I need to know how much pressure (roughly) you're putting on the pad, how close your fingers are together, and at what angle you're touching.**[/COLOR][/COLOR]

Upscrolling definitely seems a bit harder for me.  The stock driver in 11.04 did not have such issues.  But boy, changing my xorg.conf file to post #30's settings really improved things alot. 

Resting the thumb along the bottom edge of the trackpad and moving the cursor with your index finger no longer confuses the trackpad.  But regarding upscrolling, i use my right hand.  My thumb is resting on the bottom edge of the trackpad (so a thumb touch should be registered), and then with my index and middle finger, I scroll up and down. So while scrolling up and down, I've got 3 fingers touching the trackpad.  For upscrolling, my index and middle finger are 1 cm apart, and the middle fingertip is above the index finger's fingertip.  Not directly above, but above and to the right a bit.  I scroll up with "\" motion (starting from the bottom of the aforementioned slash, and moving say from the 5 o'clock to the 10 o'clock position.  I tend to use light pressure when scrolling.

But interestingly, upscrolling in an almost purely vertical motion doesn't seem to improve things.  But all in all, the settings do make a difference.



I also added an IgnorePalm "True" to the xorg.conf file.

Section "InputClass"     MatchIsTouchpad "on" 
    Identifier      "Touchpads"
 Driver          "mtrack"
 Option          "TapButton1" "0" 
    Option          "TapButton2" "0"
 Option          "TapButton3" "0"
 Option          "ThumbSize"  "26"     
Option          "Sensitivity" "0.85"     
Option          "ScrollDistance" "175" 
    Option          "FingerHigh" "10"     
Option          "FingerLow"  "10" 
EndSection

---

### Post by ehuds on 2011-06-07
Can't reach the server to download the deb.
Can someone please post a mirror for the natty 64 bit version?

Thanks.

---

### Post by geofroi on 2011-06-08
> **ehuds said:**
> Can't reach the server to download the deb.
Can someone please post a mirror for the natty 64 bit version?

Thanks.
I have the same problem, impossible to acces to [http://www.dev.fatalmachine.org/packages/dispad/ubuntu/](http://www.dev.fatalmachine.org/packages/dispad/ubuntu/) and [http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/). 
moreover i'm quite a begginer with ubuntu and impossible to deal with the xf86-input-mtrack file I get.

Ubuntu 11.04 on MacBookPro 5,5.

---

### Post by johnmurrayvi on 2011-06-08
> **ehuds said:**
> Can't reach the server to download the deb.
Can someone please post a mirror for the natty 64 bit version?

Thanks.

Here is the 64 bit ubuntu v0.2 deb.
[http://db.tt/Pufpziv](http://db.tt/Pufpziv)


> **geofroi said:**
> 
moreover i'm quite a begginer with ubuntu and impossible to deal with the xf86-input-mtrack file I get.


This should install it:
```

cd <download>/<directory>/
sudo dpkg -i xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb

```

---

### Post by geofroi on 2011-06-09
> **johnmurrayvi said:**
> Here is the 64 bit ubuntu v0.2 deb.
[http://db.tt/Pufpziv](http://db.tt/Pufpziv)




This should install it:
```

cd <download>/<directory>/
sudo dpkg -i xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb

```

Thanks a lot,
here is a tip for beginner (others can correct me if Im false): 
creating an input class section in xorg means that you have to create a 99-multitouch.conf in /usr/share/X11/xorg.conf.d (as well as the former xf86-input-multitouch driver) with a $ sudo gedit /usr/share/X11/xorg.conf.d/99-multitouch.conf and copy : 
Section "InputClass"     MatchIsTouchpad "on"     Identifier      "Touchpads"     Driver          "mtrack" EndSection

[FONT=Verdana]in it. Then you can add options as explain all along this thread...
[/FONT]

---

### Post by muammarelkhatib on 2011-06-09
Hi, 

I have a Macbook pro 8.1 I have installed the mtrack driver, but I haven't found how I can do for making right click. I am using Debian unstable. 

I'd appreciate if somebody could tell me which configuration I have to use in xorg.conf in order of getting right click.

---

### Post by johnmurrayvi on 2011-06-09
> **geofroi said:**
> Thanks a lot,
here is a tip for beginner (others can correct me if Im false): 
creating an input class section in xorg means that you have to create a 99-multitouch.conf in /usr/share/X11/xorg.conf.d (as well as the former xf86-input-multitouch driver) with a $ sudo gedit /usr/share/X11/xorg.conf.d/99-multitouch.conf and copy : 
Section "InputClass"     MatchIsTouchpad "on"     Identifier      "Touchpads"     Driver          "mtrack" EndSection

[FONT=Verdana]in it. Then you can add options as explain all along this thread...
[/FONT]

I just put the InputClass in /etc/X11/xorg.conf and didn't bother with the xorg.conf.d directory. It's working well for me, plus it might be easier to set up than creating a file in xorg.conf.d.

Here's the relevant part of my xorg.conf

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "TrackpadDisable" "0"
    Option          "Sensitivity" "0.77"
    Option          "FingerHigh" "10"
    Option          "FingerLow" "7"
    Option          "IgnorePalm" "true"
    Option          "ThumbRatio" "60"
    Option          "ThumbSize"  "20"
    Option          "ButtonEnable" "true"
    Option          "ButtonIntegrated" "true"
    Option          "ButtonZonesEnable" "false"
    Option          "ClickFinger1" "3"
    Option          "ClickFinger2" "2"
    Option          "ClickFinger3" "0"
    Option          "TapButton1" "1"
    Option          "TapButton2" "3"
    Option          "TapButton3" "2"
    Option          "ClickTime"    "40"
    Option          "SwipeUpButton" "0"
    Option          "SwipeDownButton" "0"
    Option          "Swipe4Distance" "600"
    Option          "Swipe4UpButton" "8"
    Option          "Swipe4DownButton" "9"
    Option          "Swipe4LeftButton" "0"
    Option          "Swipe4RightButton" "0"
    Option          "TapDragWait" "50"
EndSection
```

> **muammarelkhatib said:**
> Hi, 

I have a Macbook pro 8.1 I have installed the mtrack driver, but I haven't found how I can do for making right click. I am using Debian unstable. 

I'd appreciate if somebody could tell me which configuration I have to use in xorg.conf in order of getting right click.

Did you want to 'click' the trackpad, i.e. press the button, or 'tap' the trackpad?
And are you wanting to use two fingers to trigger the right click?

---

### Post by geofroi on 2011-06-10
> **johnmurrayvi said:**
> I just put the InputClass in /etc/X11/xorg.conf and didn't bother with the xorg.conf.d directory. It's working well for me, plus it might be easier to set up than creating a file in xorg.conf.d.

Thanks for the information, I will try when my settngs will be fixed, it is quite confortable to modify like that, and I can turn back easily to the former driver in case of pb.

here is mine  :

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
Option "IgnorePalm" "True"
Option "IgnoreThumb" "True"
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "ThumbSize" "26"
Option "ThumbRatio" "60"
Option "PalmSize""55"
Option "ScrollDistance" "150"
Option "Swipe4Distance" "600"
Option "Swipe4UpButton" "8"
Option "Swipe4DownButton" "9"
Option "TapDragEnable" "False"
Option "FingerHigh" "10"
Option "FingerLow"  "10"
EndSection

I have still some pb with the "thumb down" using of the touchpad. I 'm used move the pointer with my left hand fingers, and to click with my right one... sometime it mix up finger and thumb. It was more comfortable with xf86-input-multitouch.

other thing, impossible to use the 4 fingers swipe (up or down) to expose all the windows (as configured with compiz...)

---

### Post by tobyk100 on 2011-06-10
Hey All,
I am have some noob problems, thank you for being patient and helpful.

I call:

```
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
``````
Receiving objects: 100% (550/550), 106.14 KiB | 111 KiB/s, done.
Resolving deltas: 100% (329/329), done.
```Then:

```
sudo apt-get install xorg-dev libmtdev-dev
``````
libmtdev-dev is already the newest version.
xorg-dev is already the newest version.
```Then:

```
pwd && ls && make
``````
/home/tobyk100/Drivers/xf86-input-mtrack
config.h.in   COPYING  debian  include      README.md  tools
configure.ac  CREDITS  driver  Makefile.am  src
make: *** No targets specified and no makefile found.  Stop.
``````
make -f Makefile.am
``````
make: Nothing to be done for `INSTALL'.
```I guess I'm having trouble making the package? 
Thank you in advance.

EDIT:I got the multitouch driver working, so I'll go with that for now. Thanks.

---

### Post by geofroi on 2011-06-11
Ok, so, here I am:

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
Option "IgnorePalm" "false"
Option "IgnoreThumb" "false"
Option "ButtonIntegrated" "true" #allow the click and drag with two fingers, one for the click the other to move
Option "ButtonEnable" "true" #if false no way to click with a buttton
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "ScrollDistance" "150" #defaut 150
Option "Swipe4Distance" "600" #defaut 700
Option "Swipe4UpButton" "8"
Option "Swipe4DownButton" "9"
Option "Swipe4RightButton" "10"
Option "Swipe4LeftButton" "11"
Option "TapDragEnable" "False"
Option "FingerHigh" "10" #defaut 5
Option "FingerLow"  "10" #defaut 5
EndSection
```I add comments on my xorg.conf, it makes my mind clearer.

I remind that I use ubuntu 11.04 on a MacBookPro 5,5.

I discover the option ButtonIntegrated which fit quite well with my use. But, when I click, as I explain before was used on mac to have to finger on the touchpad and use an other to click. here it doesn't work very well, making ramdomly right left or middle click. Actually you can  use one of your fingers to navigate, and when you want to do a right click, you can let this finger on the touch pad but two other will have to execute a click. In my case I use a left hand finger to move the pointer which stay on the touchpad, when I want to left-click I use a finger of my right hand and press on the button, when I want to right-click I have to, touch the touchpad with another of my left finger and click with one of my right finger at the same time. The same principle for the middle click but with 3 fingers. I hope I was clear. I guess that is for my particular way to use it, but it may help people. 

I still have problem with the 4 finger swap to have and expose, I have the current xorg.conf and in compiz, scale mode, I have button9 in showing all the windows (I use ubuntu in french so I'am not sure of the names).

EDIT: I got it, you have to tick the the button_binding_toggle (second box in the top), because you cannot keep swaping!

---

### Post by Baughn on 2011-06-12
> **tobyk100 said:**
> Hey All,
I am have some noob problems, thank you for being patient and helpful.

Noob problems my ***. This one took me five minutes to solve, and I program for a living. :P

The package isn't fully configured on github. This is normal, but normally there'd also be a script to fix this and instructions explaining how to do it. Really, I'm surprised no-one else had trouble.

Anyway, you need to run "autoreconf -f -i", then ./configure, and only then make. Or dpkg-buildpackage, if you like; that's what I did.

---

### Post by Baughn on 2011-06-12
Sadly, second- and third-button clicks (using the physical, integrated button but with multiple fingers) seem not to work.

At this rate I'm starting to think I should write my own. It's, what, 2000 lines... seems doable, especially as a... but that would be telling. :P

(Yeah, okay, I'll tell. I'm going to write a "shim" driver that integrates with X but delegates all actual computation to a daemon process. Since I'll be able to restart the daemon without restarting X, and for that matter not use C, that should speed things up a bit. :))

---

### Post by *Legion* on 2011-06-13
> **Baughn said:**
> Sadly, second- and third-button clicks (using the physical, integrated button but with multiple fingers) seem not to work.

I have right-click working with a three finger click on my 13" MBP.

But here's the weird part: to achieve this, I have to use the following seemingly incorrect setting:

```
Option  "ClickFinger2"  "3"
```

If I understand right, that setting is *supposed* to mean that a two-finger click is supposed to register as mouse button 3. But for me, it makes a three-finger click register as mouse button 2 (right-click).

Complete config:
```
Section "InputClass"
  MatchIsTouchpad "on"
  Identifier "Touchpads"
  Driver  "mtrack"
  Option  "ButtonIntegrated"  "true"
  Option  "Sensitivity"       "1.10"
  Option  "ClickFinger1"      "1"
  Option  "ClickFinger2"      "3"
  Option  "TapButton1"        "0"
  Option  "TapButton2"        "0"
  Option  "TapButton3"        "0"
  Option  "TapDragEnable"     "false"
  Option  "ThumbSize"         "35"
  Option  "PalmSize"          "55"
  Option  "ScrollDistance"    "100"
EndSection

```

---

### Post by geofroi on 2011-06-13
Hi, 
> If I understand right, that setting is *supposed* to mean that a  two-finger click is supposed to register as mouse button 3. But for me,  it makes a three-finger click register as mouse button 2 (right-click).I think the mouse button 3 is the right click.
As I tried to explain in the [ post #120]("http://ubuntuforums.org/showpost.php?p=10927488&postcount=120"), the right click is a bit tricky, the driver seems to only consider the two fingers which are hitting the touchpad at the moment of the click. if you already have a finger on the touchpad (or not) you will have to click with two others. 
Moreover, by default, if you click in pressing with three fingers at the same time on the integrated button of your touchpad it will make a middle click (tested with firefox, open in a new tab...).

---

### Post by ckisgen on 2011-06-14
does anyone have tap to drag working to their satisfaction?

i do a lot of dragging when i'm in ubuntu-land and ANXIOUSLY awaited 0.2's arrival so i could get this back.  i have messed with all the tap to drag settings i can find (TapDragTime, TapDragWait, GestureWaitTime) and i just can't find the right balance

either it accidentally enables way too often (like when i'm double clicking thru a tree of folders .. inevitably whichever folder has just opened up is already highlighted/selected and when i go to move my finger to select another folder to open, it starts dragging the initial folder that was highlighted by default) OR when i tune the over-detection out, i can't seem to make it enable/drag for anything.

can anyone help?  i've basically got this wonderful driver working almost to os x standards but this is one glaring issue that i just can't seem to get around and would make a huge difference in my virtual world.

thanks

here are my current settings:

```
Section "InputClass"
	MatchIsTouchpad "on"
	Identifier "Touchpads"
	Driver "mtrack"
	MatchProduct "bcm5974"
	MatchDevicePath "/dev/input/event*"
	#Option "PalmSize" "40"
	Option "IgnorePalm" "true"
	Option "ThumbRatio" "60"
	Option "ThumbSize" "20"
	Option "ClickTime" "40"
	Option "ScrollDistance" "175"
	Option "Sensitivity" "1.00"
	Option "TapButton1" "1"
	Option "TapButton2" "3"
	Option "TapButton3" "2"
	Option "FingerHigh" "10"
	Option "FingerLow" "7"
	Option "SwipeLeftButton" "8"
	Option "SwipeRightButton" "9"
	Option "SwipeUpButton" "10"
	Option "SwipeDownButton" "11"
	#Option "ScaleUpButton" "0"
	#Option "ScaleDownButton" "0"
	#Option "TapDragTime" "900"
	Option "TapDragWait" "50"
	#Option "GestureWaitTime" "300"
EndSection
```

---

### Post by BlueDragonX on 2011-06-15
Anyone using v0.1.x needs to upgrade to v0.2.0. Many issues are fixed in the new version. The server is back up now and should remain up. I've fixed the issues that were causing it to go down.

> **geofroi said:**
> I have still some pb with the "thumb down" using of the touchpad. I 'm used move the pointer with my left hand fingers, and to click with my right one... sometime it mix up finger and thumb. It was more comfortable with xf86-input-multitouch.

You should still be able to move the pointer with one hand and click with the other. It is a completely separate action, so only the fingers you use to click/tap will be counted towards that click/tap. Meaning, if you have one finger down for movement and you tap with a single finger, it will be a left click, not a right click.

> **Baughn said:**
> The package isn't fully configured on github. This is normal, but normally there'd also be a script to fix this and instructions explaining how to do it. Really, I'm surprised no-one else had trouble.

Anyway, you need to run "autoreconf -f -i", then ./configure, and only then make. Or dpkg-buildpackage, if you like; that's what I did.

This is correct. I have not checked into github any generated code, so autoreconf must be run before you can ./configure && make && make install. I've stated this before in this thread.

> **Baughn said:**
> Sadly, second- and third-button clicks (using the physical, integrated button but with multiple fingers) seem not to work.

At this rate I'm starting to think I should write my own. It's, what, 2000 lines... seems doable, especially as a... but that would be telling. :P

How about telling me what the problem is and providing your config and log files? That would be quicker than writing your own. I know, I did...

> **geofroi said:**
> Hi, 
I think the mouse button 3 is the right click.
As I tried to explain in the [ post #120]("http://ubuntuforums.org/showpost.php?p=10927488&postcount=120"), the right click is a bit tricky, the driver seems to only consider the two fingers which are hitting the touchpad at the moment of the click. if you already have a finger on the touchpad (or not) you will have to click with two others. 
Moreover, by default, if you click in pressing with three fingers at the same time on the integrated button of your touchpad it will make a middle click (tested with firefox, open in a new tab...).

This is 100% true. In Xorg button 1 is the left button, button 2 is the middle button, and button 3 is the right button. I repeat: this is **not** specific to the mtrack driver, **all of Xorg behaves this way**.

As to the second part, this is not the synaptics driver, and so will not behave exactly as the synaptics driver does. This is true multitouch. In fact, the way the synaptics driver behaves is a side-effect of the way non-multitouch trackpads report touches on the pad.

Since it is true multitouch you can do multiple things on the trackpad at the same time. This means you can move and click separately. As such, fingers you're using for movement will not count towards tapping/clicking.

> **ckisgen said:**
> does anyone have tap to drag working to their satisfaction?

i do a lot of dragging when i'm in ubuntu-land and ANXIOUSLY awaited 0.2's arrival so i could get this back.  i have messed with all the tap to drag settings i can find (TapDragTime, TapDragWait, GestureWaitTime) and i just can't find the right balance

You'll never get this to work in v0.1.x. It is completely broken. You need to upgrade to v0.2.0. The server is back up so you can get to the debs. [http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/)

---

### Post by ckisgen on 2011-06-16
> **BlueDragonX said:**
> 
You'll never get this to work in v0.1.x. It is completely broken. You need to upgrade to v0.2.0. The server is back up so you can get to the debs. [http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/)

i should have been more clear in my post and not assumed it appears but i'm ON v0.2.0

and still am unable to get tap to drag working properly.  see my original post, i can either get it working 'too well'  where it constantly picks up times when i'm only trying to move the mouse within a couple seconds after double clicking to open a folder or i can't get it to work at all (if i dial up the 'offset / error correcting params' like TapDragWait, TapDragTime, even tried tweaking GestureWaitTime not knowing 100% if it was tied in to the accidental detections or not ..

---

### Post by BlueDragonX on 2011-06-16
> **ckisgen said:**
> and still am unable to get tap to drag working properly.  see my original post, i can either get it working 'too well'  where it constantly picks up times when i'm only trying to move the mouse within a couple seconds after double clicking to open a folder or i can't get it to work at all (if i dial up the 'offset / error correcting params' like TapDragWait, TapDragTime, even tried tweaking GestureWaitTime not knowing 100% if it was tied in to the accidental detections or not ..

Have you read the README?

The three parameters you need to adjust are TapDragTime, TapDragWait, and TapDragDist. GestureWaitTime is not used in tap-to-drag. As per the docs:

> 
TapDragTime - The tap-to-drag timeout. This is how long the driver will wait after a single tap for a movement event before sending the click. Integer value representing milliseconds. Defaults to 350.

TapDragWait How long after detecting movement to trigger a button down event. During this time pointer movement will be disabled. Increase this value if you find you're draggin when you don't wish it. Integer value representing milliseconds. Defaults to 40.

TapDragDist How far the finger is allowed to move during drag wait time. If the finger moves farther than this distance during the wait time then dragging will be canceled and pointer movement will resume. Integer value. Defaults to 200.


In order to activate tap-to-drag, you must (with one finger) tap the trackpad, release, then tap and hold. The second tap must occur within the TapDragTime time. If the finger of the second tap moves farther than TapDragDist within TapDragWait after touching, then dragging is not activated.

Start by increasing your TapDragDist or reducing TapDragWait.

---

### Post by tobyk100 on 2011-06-16
> **Baughn said:**
> Noob problems my ***. This one took me five minutes to solve, and I program for a living. :P

The package isn't fully configured on github. This is normal, but normally there'd also be a script to fix this and instructions explaining how to do it. Really, I'm surprised no-one else had trouble.

Anyway, you need to run "autoreconf -f -i", then ./configure, and only then make. Or dpkg-buildpackage, if you like; that's what I did.

Thank you Baughn for your help, but I need more.

Autoreconf builds a configure script which when I run outputs:

```
configure: error: cannot find install-sh, install.sh, or shtool in . "."/.
```

Running dpkg-buildpackage outputs:


```
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package xserver-xorg-input-mtrack
dpkg-buildpackage: source version 0.2.0
dpkg-buildpackage: source changed by Ryan Bourgeois <bluedragonx@gmail.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build xf86-input-mtrack
 fakeroot debian/rules clean
dh_testdir
dh_testroot
/usr/bin/make clean
make[1]: Entering directory `/home/tobyk100/Drivers/xf86-input-mtrack'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/tobyk100/Drivers/xf86-input-mtrack'
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2

```

Thank you for any help!

---

### Post by BlueDragonX on 2011-06-16
Do a:

libtoolize && aclocal && autoconf && automake --add-missing --copy

---

### Post by muammarelkhatib on 2011-06-18
> 

Did you want to 'click' the trackpad, i.e. press the button, or 'tap' the trackpad?
And are you wanting to use two fingers to trigger the right click?

Either of those ones is fine for me. So, if you can share it, I'd appreciate it. :)

---

### Post by johnmurrayvi on 2011-06-21
> **muammarelkhatib said:**
> Either of those ones is fine for me. So, if you can share it, I'd appreciate it. :)

Add this to your xorg.conf for both "tap" and "click" using two fingers:

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "ClickFinger1" "3"
    Option          "TapButton2" "3"
EndSection
```

---

### Post by muammarelkhatib on 2011-06-25
> **johnmurrayvi said:**
> Add this to your xorg.conf for both "tap" and "click" using two fingers:

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    Option          "ClickFinger1" "3"
    Option          "TapButton2" "3"
EndSection
```

Thanks. The Option TapButton2 worked pretty fine. But regarding the option ClickFinger, it didn't. Anyways, I can live with it right now. The only thing remaining at least for me, is to make the keymap to fit correctly with the US intl. 

Cheers,

---

### Post by BlueDragonX on 2011-06-25
> **muammarelkhatib said:**
> Thanks. The Option TapButton2 worked pretty fine. But regarding the option ClickFinger, it didn't. Anyways, I can live with it right now. The only thing remaining at least for me, is to make the keymap to fit correctly with the US intl. 

Cheers,

Please read the docs, there's a full explanation for each configuration parameter:
[https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md](https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md)

---

### Post by muammarelkhatib on 2011-06-30
> **BlueDragonX said:**
> Please read the docs, there's a full explanation for each configuration parameter:
[https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md](https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md)

Thanks for the suggestion. I had done partially (I didn't have time for reading it completely when I requested the help...). That's why I asked for one configuration that worked.

Now that I have more time, I will try to configure this in other way to see if I get what I need. I'll post back.

---

### Post by Quicksand on 2011-07-07
I like this driver -- the customizability is terrific!  I enjoy being able to use three- and four-finger gestures to trigger Expo, Scale, etc.  Good stuff.

But I'm stumped on one thing.  I'm using the mtrack driver (0.2, installed via the prebuilt .deb on Natty x64) with an Apple Magic Trackpad, and tap-to-drag is causing me problems.

When I tap to drag, I get a button1 double-click FOLLOWED by a drag.  So if I try to tap-and-drag a window by its titlebar, it maximizes and won't drag.  If I tap-and-drag to select text in a window, I get the first full word selected (the double-click) then, as I keep my finger down, dragging works as expected.

How can I avoid that double-click?  I just want to drag!

(And yeah, just to avoid all doubt -- I'm sure I'm executing the tap-to-drag maneuver correctly.  It works with the Synaptics driver, and it has worked on every Windows laptop I have ever used.)

This is with mtrack default settings.  I have played around with alternative settings, but I can't seem to make this problem go away.

Anyone have any thoughts?

---

### Post by lyapunov on 2011-07-08
Hi, 
I get 

```
(EE) mtrack: cannot configure device
(EE) Couldn't init device "bcm5974"
```

The problem is that the trackpad seems not working, since the right click doesn't work for me.

Any ideas?

Thank you,

---

### Post by rafwes on 2011-07-11
Hi!

I am having troubles setting up the driver. I installed the deb package for maverick, edited the xorg.conf but the trackpad will not work. Here are the logs for xorg:

```
[    15.373] (II) LoadModule: "mtrack"
[    15.373] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[    15.373] (II) Module mtrack: vendor="X.Org Foundation"
[    15.373] 	compiled for 1.10.1, module version = 0.1.0
[    15.373] 	Module class: X.Org XInput Driver
[    15.373] 	ABI class: X.Org XInput driver, version 12.3
[    15.373] (EE) module ABI major version (12) doesn't match the server's version (11)
[    15.373] (II) UnloadModule: "mtrack"
[    15.373] (II) Unloading /usr/lib/xorg/modules/input/mtrack_drv.so
[    15.373] (EE) Failed to load module "mtrack" (module requirement mismatch, 0)
[    15.373] (EE) No input driver matching `mtrack'

```

Any ideas what is going on?

Thanks!

---

### Post by BELzEBUB on 2011-07-11
Hi,

I am currently working on get ubuntu on my asus eee pad transformer.
One of the problems i am working on is the Touchpad. Evdev and Synaptics are not working. So I cam along this driver. Compiled it for ARM and setup the xorg.conf. First I thought that it does not work but when trying to scroll with to fingers the course was moving :confused:

So my question is: how can I change the behavior to move the courser when only one finger is on the touchpad? I cant find any reasonable option to do so.

Oh, and thanks for your work :)

---

### Post by flyingtabmow on 2011-07-20
Thanks so much for developing this! It's light years ahead of multitouch as far as reliable trackpadding on Linux is concerned (and this is by far the single biggest source of frustration for me when switching back and forth between Linux and OS X).

I want to add another vote towards the "BottomEdge" feature mentioned earlier... I tend to keep just the tip of my thumb on the bottom edge of the trackpad, and frequently pointer input stops working completely if my thumb isn't detected as big enough.

I've played around in OS X to see what the behavior is... it looks like any touch originating along a sliver at the bottom of the trackpad is ignored until it moves upwards sufficiently (at which point the cursor jumps a bit, presumably to make up for the amount of movement it missed). Furthermore, touches traveling into the bottom region from above don't get "lost" to the bottom region, instead they keep moving the cursor. I think this is the most transparent way of implementing this kind of feature, since it doesn't really take away any trackpad area.

---

### Post by agestrada on 2011-07-22
Hi all, 

Any updates on the **libmtdev1** for Lucid?. I still can't find it and I'm really willing to try this driver.

Thanks,

Edit: I actually found them in the first post under Downloads. Don't know how I did not see them before.... Now I will try it.

---

### Post by agestrada on 2011-07-24
The same problem here. I'm under Lucid with a MacbookPro 5.5.

> **rafwes said:**
> Hi!

I am having troubles setting up the driver. I installed the deb package for maverick, edited the xorg.conf but the trackpad will not work. Here are the logs for xorg:

```
[    15.373] (II) LoadModule: "mtrack"
[    15.373] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[    15.373] (II) Module mtrack: vendor="X.Org Foundation"
[    15.373]     compiled for 1.10.1, module version = 0.1.0
[    15.373]     Module class: X.Org XInput Driver
[    15.373]     ABI class: X.Org XInput driver, version 12.3
[    15.373] (EE) module ABI major version (12) doesn't match the server's version (11)
[    15.373] (II) UnloadModule: "mtrack"
[    15.373] (II) Unloading /usr/lib/xorg/modules/input/mtrack_drv.so
[    15.373] (EE) Failed to load module "mtrack" (module requirement mismatch, 0)
[    15.373] (EE) No input driver matching `mtrack'

```Any ideas what is going on?

Thanks!

---

### Post by dfacto on 2011-07-27
Hey all.  Does anyone know if this driver is supposed to support the new MacBookAir4,2?  I installed xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb and don't seem to get any notice of mtrack in Xorg.0.log (attached).

Thanks!

**Update:** I modified the bcm5974 driver and posted about it [here]("http://ubuntuforums.org/showpost.php?p=11106203&postcount=59").

---

### Post by neopium on 2011-07-29
Hi everyone,

I installed xf86-input-mtrack on Fedora 15 64 bits (I had to compile it manually with the autotools) and everything seemed to went fine... until I tried to load it. It then failed to load and the trackpad was not recognized anymore.

Here is what I have in the log file:
```

[   981.184] (II) config/udev: Adding input device bcm5974 (/dev/input/event10)
[   981.184] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[   981.184] (**) bcm5974: Applying InputClass "touchpad catchall"
[   981.184] (**) bcm5974: Applying InputClass "Touchpads"
[   981.184] (II) LoadModule: "mtrack"
[   981.186] (WW) Warning, couldn't open module mtrack
[   981.186] (II) UnloadModule: "mtrack"
[   981.186] (II) Unloading mtrack
[   981.186] (EE) Failed to load module "mtrack" (module does not exist, 0)
[   981.186] (EE) No input driver matching `mtrack'
[   981.187] (II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)
[   981.187] (**) bcm5974: Applying InputClass "Touchpads"
[   981.187] (II) LoadModule: "mtrack"
[   981.188] (WW) Warning, couldn't open module mtrack
[   981.188] (II) UnloadModule: "mtrack"
[   981.188] (II) Unloading mtrack
[   981.188] (EE) Failed to load module "mtrack" (module does not exist, 0)
[   981.188] (EE) No input driver matching `mtrack'

```

Upon installation, it says the libraries were installed in "/usr/local/lib/xorg/modules/input" and I indeed found the mtrack_drv.la and mtrack_drv.so files there.

As indicated in the reademe, I have created an xorg.conf file (with the "Xorg :1 -configure" command, as in Fedora, there is no xorg.conf file by default) and added the basic section:

```

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
EndSection

```

I know this is an Ubuntu forum, but this thread seems to be the only official forum for the mtrack driver. I hope someone will be able to help.

Kind regards,

Ben

---

### Post by Quicksand on 2011-07-29
> **neopium said:**
>  It then failed to load and the trackpad was not recognized anymore.

I'm not familiar with Fedora, but try copying the mtrack_drv.so file to /usr/lib/xorg/modules/input (i.e. /usr/lib instead of /usr/local/lib). That's where Ubuntu expects to find it.

---

### Post by neopium on 2011-07-29
> **Quicksand said:**
> I'm not familiar with Fedora, but try copying the mtrack_drv.so file to /usr/lib/xorg/modules/input (i.e. /usr/lib instead of /usr/local/lib). That's where Ubuntu expects to find it.

Thanks. I tried that and it did not work unfortunately. I will try and ask on Fedora forums and keep you in touch.

---

### Post by ryanclancy000 on 2011-07-30
I am running Ubuntu 11.04 on my Macbook Pro. The only option I want is to be able to click and drag windows like I can in OSX (ex. click down with one finger and use the other to move the window) After looking through the option, I can't seem to figure out which option I need to configure to what value. Also, being very new at Ubuntu, I am having troubles figuring out how to install it. Any insight?

~Ryan

---

### Post by lycoch on 2011-08-02
hi
no reference to touchegg here
this linux soft is really great for improve the multitouch trackpad capatibility

the project's home: [https://code.google.com/p/touchegg/](https://code.google.com/p/touchegg/)

actually it only work with synaptics and evdev but not mtrack :( 

Do you think it will be complicated to fix that issue ?
 mtrack is the best driver for me and i really want the best of the two

any help greatly appreciate

for information, the best way to test it is to compile it from source SVN

 svn checkout ***http***://touchegg.googlecode.com/svn/touchegg/ touchegg-read-only  

sudo apt-get install build-essential libqt4-dev utouch libx11-6 libxtst-dev
cd touchegg-read-only
qmake
make
make install

here is an example of config file


mkdir -p .config/touchegg/ && gedit .config/touchegg/touchegg.conf 

<touchégg>
   <settings>
       <property name="composed_gestures_time">0</property>
   </settings>
   <application name="All">
       <gesture type="TAP" fingers="2" direction="">
           <action type="MOUSE_CLICK">BUTTON=3</action>
       </gesture>
    <gesture type="TAP" fingers="3" direction="">
           <action type="MOUSE_CLICK">BUTTON=2</action>
       </gesture>
       <gesture type="DRAG" fingers="2" direction="ALL">
           <action type="SCROLL">SPEED=7:INVERTED=false</action>
       </gesture>
       <gesture type="DRAG" fingers="3" direction="UP">
           <action type="MAXIMIZE_RESTORE_WINDOW"></action>
       </gesture>
       <gesture type="DRAG" fingers="3" direction="DOWN">
           <action type="MINIMIZE_WINDOW"></action>
       </gesture>
    <gesture type="DRAG" fingers="3" direction="LEFT">
           <action type="SEND_KEYS">Control+Alt+Left</action>
       </gesture>
       <gesture type="DRAG" fingers="3" direction="RIGHT">
           <action type="SEND_KEYS">Control+Alt+Right</action>
       </gesture>
       <gesture type="DRAG" fingers="2" direction="LEFT">
           <action type="SEND_KEYS">Control+Alt+Left</action>
       </gesture>
       <gesture type="DRAG" fingers="2" direction="RIGHT">
           <action type="SEND_KEYS">Control+Alt+Right</action>
       </gesture>
       <gesture type="DRAG" fingers="4" direction="UP">
           <action type="SEND_KEYS">Super+W</action>
       </gesture>
       <gesture type="DRAG" fingers="4" direction="DOWN">
           <action type="SHOW_DESKTOP"></action>
       </gesture>
   </application>
   <application name="Chromium-browser, Firefox">
       <gesture type="PINCH" fingers="2" direction="IN">
           <action type="SEND_KEYS">Control+KP_Add</action>
       </gesture>
       <gesture type="PINCH" fingers="2" direction="OUT">
           <action type="SEND_KEYS">Control+KP_Subtract</action>
       </gesture>
   </application>
</touchégg>

---

### Post by ckisgen on 2011-08-22
> **agestrada said:**
> The same problem here. I'm under Lucid with a MacbookPro 5.5.

for anyone having the module requirement mismatch ...

```
sudo apt-add-repository ppa:xorg-edgers
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```


this updated xorg and fixed it for me.  thanks to bluedragon for the idea via PM.

---

### Post by smoothlarryhughes on 2011-08-22
Is using the "ignorethumb" feature the only way I can click the botto left corner of the touchpad while still using my right finger to move the mouse?

---

### Post by agestrada on 2011-08-30
To neopium #146. 

I tried this and broke my system. I cannot longer boot Lucid, any ideas on how to go back this steps?. I checked the repository after updating and it is only for natty and oneiric :S, I think I made quite a mess.

Thanks,

Solved: I used a Live-CD and ppa-purge to remove the repository and fix the system.

---

### Post by scisteffan on 2011-09-07
When I run "make" I get errors (running Debian Squeeze). Any help how to fix this would be much appreciated.
I used autoconf -f -i and ./configure before running make.

> :80: error: ‘ABS_MAX’ undeclared (first use in this function)
./src/capabilities.c:81: error: ‘KEY_MAX’ undeclared (first use in this function)
./src/capabilities.c:86: error: ‘EVIOCGID’ undeclared (first use in this function)
./src/capabilities.c:92: error: ‘EV_SYN’ undeclared (first use in this function)
./src/capabilities.c:95: error: ‘EV_KEY’ undeclared (first use in this function)
./src/capabilities.c:98: error: ‘EV_ABS’ undeclared (first use in this function)
./src/capabilities.c:102: error: ‘BTN_LEFT’ undeclared (first use in this function)
./src/capabilities.c:103: error: ‘BTN_MIDDLE’ undeclared (first use in this function)
./src/capabilities.c:104: error: ‘BTN_RIGHT’ undeclared (first use in this function)
./src/capabilities.c:106: error: ‘ABS_MT_SLOT’ undeclared (first use in this function)
./src/capabilities.c:113: error: ‘ABS_MT_POSITION_X’ undeclared (first use in this function)
./src/capabilities.c:114: error: ‘ABS_MT_POSITION_Y’ undeclared (first use in this function)
./src/capabilities.c:115: error: ‘ABS_MT_TOUCH_MAJOR’ undeclared (first use in this function)
./src/capabilities.c:116: error: ‘ABS_MT_TOUCH_MINOR’ undeclared (first use in this function)
./src/capabilities.c:117: error: ‘ABS_MT_WIDTH_MAJOR’ undeclared (first use in this function)
./src/capabilities.c:118: error: ‘ABS_MT_WIDTH_MINOR’ undeclared (first use in this function)
./src/capabilities.c:119: error: ‘ABS_MT_ORIENTATION’ undeclared (first use in this function)
./src/capabilities.c: In function ‘get_cap_xsize’:
./src/capabilities.c:126: error: ‘MTDEV_POSITION_X’ undeclared (first use in this function)
./src/capabilities.c:127: error: dereferencing pointer to incomplete type
./src/capabilities.c:127: error: dereferencing pointer to incomplete type
./src/capabilities.c: In function ‘get_cap_ysize’:
./src/capabilities.c:132: error: ‘MTDEV_POSITION_Y’ undeclared (first use in this function)
./src/capabilities.c:133: error: dereferencing pointer to incomplete type
./src/capabilities.c:133: error: dereferencing pointer to incomplete type
./src/capabilities.c: In function ‘get_cap_wsize’:
./src/capabilities.c:138: error: ‘MTDEV_TOUCH_MAJOR’ undeclared (first use in this function)
./src/capabilities.c:139: error: dereferencing pointer to incomplete type
./src/capabilities.c:139: error: dereferencing pointer to incomplete type
./src/capabilities.c: In function ‘get_cap_xmid’:
./src/capabilities.c:144: error: ‘MTDEV_POSITION_X’ undeclared (first use in this function)
./src/capabilities.c:145: error: dereferencing pointer to incomplete type
./src/capabilities.c:145: error: dereferencing pointer to incomplete type
./src/capabilities.c: In function ‘get_cap_ymid’:
./src/capabilities.c:150: error: ‘MTDEV_POSITION_Y’ undeclared (first use in this function)
./src/capabilities.c:151: error: dereferencing pointer to incomplete type
./src/capabilities.c:151: error: dereferencing pointer to incomplete type
make[1]: *** [capabilities.lo] Error 1
make[1]: Leaving directory `/home/steffan/installers/xf86-input-mtrack'
make: *** [all] Error 2


---

### Post by BlueDragonX on 2011-09-08
Looks like you forgot to install the mtdev library.

---

### Post by dfacto on 2011-09-08
There seems to be a lot of confusion on building this from git (which is understandable given the lack of build readme).  Anyway, if you're curious, here is my recipe for installing it on Ubuntu:
```

sudo apt-get install autoconf dpkg-dev git libmtdev-dev libtool xserver-xorg-dev xutils-dev
mkdir xf86-input-mtrack
cd xf86-input-mtrack
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack
# http://ubuntuforums.org/showpost.php?p=10881280&postcount=130
# libtoolize && aclocal && autoconf && automake --add-missing --copy
autoreconf --install --force
# should install to: /usr/lib/xorg/modules/input/
./configure --prefix=/usr
dpkg-buildpackage
cd ..
sudo dpkg -i xserver-xorg-input-mtrack*.deb

```

I'm not sure about the libtoolize sequence...autoreconf worked for me.

---

### Post by scisteffan on 2011-09-09
Sure, you need to download mdev from the unstable repository in Debian Squeeze.

I'm wondering, how do I fix the Xorg error:
> module ABI major version (7) doesn't match the server's version (13).
Recompile the package from source? (I have since upgraded to 'unstable')

---

### Post by scisteffan on 2011-09-09
^ Ive just answered my own question! The answer was to recompile from source. Sorry about that.

---

### Post by Zookalicious on 2011-09-12
First of all, great work on the driver, it really does help with several issues on the Macbook 5,1. Interestingly enough though, one of the helpful features is also one of my last problems :)

It seems that there is a restriction on taping to click after a gesture or movement has been performed. For example, if I move the cursor, tap clicks will not register for about half a second after I'm done moving. Likewise, if I scroll, I cannot tap to click for about 1.5 seconds afterwards. 

I really like this behaviour, but I can't find an option in the source code to reduce the amount of time that this restriction lasts for, because it feels a bit too long for me. Also I read through the thread, and I can't seem to figure out what the button numbers (0, 1, 2, 3, 4, 5 etc) that I am mapping gestures to actually do~

So if someone doesn't mind enlightening me on either (or both) of those items I would greatly appreciate it!

EDIT: Also, if I try and double click anything in Nautilus by double tapping it doesn't work, I have to tap about 5 times before it registers, although the sensitivity everywhere else seems fine.

EDIT EDIT: Turns out, In order to double click an icon (nautilus icons / the double click timeout tester under mouse settings in ubuntu) I need to tap three times? but if i want to double clictk to select an area of text, or a selection area on the desktop, that only requires two clicks...

---

### Post by BlueDragonX on 2011-09-12
Are you running dispad? You may try adjusting reducing the GestureWaitTime value, but I don't think that will help you any. I left mine to the defaults I chose and I don't have that issue.

For the buttons, those are the mouse button clicks those gestures will trigger. If you want them to do something other than a mouse click you'll need to use an external program to convert mouse click events into other actions.

---

### Post by Zookalicious on 2011-09-13
(First of all, thank you for the very swift reply!) Nope, not running dispad (I can't figure out how to build it, and the website hosting the .deb's seems to be down) I'll try tweaking that and seeing where I can get. The biggest problem I'd say though is trying to double click through tapping. It seems I tap too fast, and if I don't leave a good 0.6 seconds in between taps, it won't register the second tap (that's why I thought three clicks did it).

I have a sneaking suspicion that this is related to the timeout after movement :P and that it's timing out on the second tap. 

Thanks again for the great driver! Despite the above, it really is a great driver and solved a lot of my problems :)

And I figured the button mapping was something like that. I'll sort it out after I'm done tweaking.

---

### Post by dfacto on 2011-09-13
Great driver!  Really making my new MBA hum!  Would it make sense to request that mtrack support "inertia scrolling" like in smart phones or is this better suited for the window manager?

---

### Post by joskapista on 2011-09-14
I installed dispad. But nothing changed. Could you please help me, how can I find the problem?

---

### Post by Zookalicious on 2011-09-14
> **joskapista said:**
> I installed dispad. But nothing changed. Could you please help me, how can I find the problem?

Sorry for all the questions, but same issue. How can I start dispad? Running the command says that it's using the config file (which does exist) but it doesn't do anything. Running "ps aux" doesn't show anything either under dispad.

---

### Post by bakie on 2011-09-28
I seem to be having problems installing this on my debian wheezy.

If I try autoconf I get the following error:
configure.ac:21: error: 
must install xorg-macros 1.8 or later before running autoconf/autogen

I then tried autoreconf configure.ac ACLOAL="aclocal -I/usr/share/aclocal" because that is where my xorg-macros.m4 file is located. But this gives me the following error: 
configure.ac:17: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:18: error: possibly undefined macro: AC_PROG_LIBTOOL

Next I can do autoconf and automake --add-missing without errors. But when I do ./configure afterwards I get the following error:
......
checking dependency style of gcc... (cached) gcc3
configure: creating ./config.status
config.status: error: cannot find input file: `Makefile.in'


Can anyone help me trying to compile this on debian wheezy :)

Thx in advance

---

### Post by Zookalicious on 2011-09-28
> **bakie said:**
> 
If I try autoconf I get the following error:
configure.ac:21: error: 
must install xorg-macros 1.8 or later before running autoconf/autogen


You might want to consider installing xorg-macros ;P

I don't run debian, but I think it should just be "sudo apt-get install xorg-macros" or "util-macros". I can't seem to find it on Ubuntu though, so I might be wrong.

---

### Post by bakie on 2011-09-29
> **Zookalicious said:**
> You might want to consider installing xorg-macros ;P

I don't run debian, but I think it should just be "sudo apt-get install xorg-macros" or "util-macros". I can't seem to find it on Ubuntu though, so I might be wrong.

I did install the xorg-macros, it is under the xutils-dev package afaik :). So I don't get why I get these problems :).

---

### Post by mattmueller on 2011-10-01
So I've gone through quite a bit of headache getting natty using gnome 3 installed on my Macbook Pro (8,2).

The last blocking item I have for using it on a daily basis is trackpad support.  According to the wiki this should work out of the box with minimal effort, but had no luck there.  Came across this thread through the debian wiki and installed the driver, updated xorg.conf and so forth but the trackpad still doesn't seem to be working (and touchpad settings won't even show up for me in basic system menus).

Any ideas on how I can better troubleshoot this?

---

### Post by nikflewlow on 2011-10-05
hello there fellow ubuntu-users!

i wanted to install this driver onto my natty ubuntu, but it seems there are some problems.
i compiled the driver as described in this post: [http://ubuntuforums.org/showpost.php?p=11230727&postcount=154](http://ubuntuforums.org/showpost.php?p=11230727&postcount=154) (including the libtoolize command).
everything seemed to work fine. the only thing which was strange - there was no xorg.conf file - i had to create one (i chose [http://ubuntuforums.org/showpost.php?p=10811441&postcount=75](http://ubuntuforums.org/showpost.php?p=10811441&postcount=75) as a template)
so i rebooted the system, and now the trackpad isnt working at all...
why?

i attached a  my xorg log and the xorg conf.

i have a macbook 4,1 with ubuntu natty narwhal

thanks for the help :)

---

### Post by nikflewlow on 2011-10-07
anyone? plllease? :(

---

### Post by pbhedlund on 2011-10-07
Try adding
```
MatchDevicePath "/dev/input/event*"
```to the xorg.conf section to prevent the driver from being loaded twice (see earlier posts in this thread).

I also don't have anything about ''appletouch" in my log. Is that another competing driver?

---

### Post by nikflewlow on 2011-10-07
thanks for the help! :)
unfortunately it didnt change much...here is the log:

```
[   298.450] (II) config/udev: Adding input device appletouch (/dev/input/event5)
[   298.450] (**) appletouch: Applying InputClass "evdev touchpad catchall"
[   298.450] (**) appletouch: Applying InputClass "touchpad catchall"
[   298.450] (**) appletouch: Applying InputClass "Touchpads"
[   298.450] (II) LoadModule: "mtrack"
[   298.451] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[   298.451] (II) Module mtrack: vendor="X.Org Foundation"
[   298.451]     compiled for 1.10.1, module version = 0.1.0
[   298.451]     Module class: X.Org XInput Driver
[   298.451]     ABI class: X.Org XInput driver, version 12.3
[   298.451] (II) Using input driver 'mtrack' for 'appletouch'
[   298.451] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[   298.451] (**) appletouch: always reports core events
[   298.451] (**) appletouch: always reports core events
[   298.451] (**) Option "FingerHigh" "10"
[   298.452] (**) Option "FingerLow" "10"
[   298.452] (**) Option "ThumbSize" "26"
[   298.452] (**) Option "TapButton1" "0"
[   298.452] (**) Option "TapButton2" "0"
[   298.452] (**) Option "TapButton3" "0"
[   298.452] (**) Option "ScrollDistance" "175"
[   298.452] (**) Option "Sensitivity" "0.85"
[   298.452] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input5/event5"
[   298.452] (II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
[   298.452] (II) device control: init
[   298.452] (**) Option "Device" "/dev/input/event5"
[   298.453] (II) mtrack: devname: appletouch
[   298.453] (II) mtrack: devid: 5ac 22a 7
[   298.453] (II) mtrack: caps: left
[   298.456] (**) appletouch: (accel) keeping acceleration scheme 1
[   298.456] (**) appletouch: (accel) acceleration profile 0
[   298.456] (**) appletouch: (accel) acceleration factor: 2.000
[   298.456] (**) appletouch: (accel) acceleration threshold: 4
[   298.456] (II) device control: on
[   298.456] (WW) Touchpad has minimal capabilities. Some features will be unavailable.
[   298.457] (II) config/udev: Adding input device appletouch (/dev/input/mouse0)
[   298.457] (II) No input driver/identifier specified (ignoring)
```

regarding  "appletouch" - I didnt install any other driver before, I guess this is  the default one? Sorry, I am not that experienced with ubuntu...
so what else could it be?

regards,

nik

---

### Post by nikflewlow on 2011-10-07
thanks for the help! :)
unfortunately it didnt change much...here is the log:

```
[   298.450] (II) config/udev: Adding input device appletouch (/dev/input/event5)
[   298.450] (**) appletouch: Applying InputClass "evdev touchpad catchall"
[   298.450] (**) appletouch: Applying InputClass "touchpad catchall"
[   298.450] (**) appletouch: Applying InputClass "Touchpads"
[   298.450] (II) LoadModule: "mtrack"
[   298.451] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[   298.451] (II) Module mtrack: vendor="X.Org Foundation"
[   298.451]     compiled for 1.10.1, module version = 0.1.0
[   298.451]     Module class: X.Org XInput Driver
[   298.451]     ABI class: X.Org XInput driver, version 12.3
[   298.451] (II) Using input driver 'mtrack' for 'appletouch'
[   298.451] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[   298.451] (**) appletouch: always reports core events
[   298.451] (**) appletouch: always reports core events
[   298.451] (**) Option "FingerHigh" "10"
[   298.452] (**) Option "FingerLow" "10"
[   298.452] (**) Option "ThumbSize" "26"
[   298.452] (**) Option "TapButton1" "0"
[   298.452] (**) Option "TapButton2" "0"
[   298.452] (**) Option "TapButton3" "0"
[   298.452] (**) Option "ScrollDistance" "175"
[   298.452] (**) Option "Sensitivity" "0.85"
[   298.452] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input5/event5"
[   298.452] (II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
[   298.452] (II) device control: init
[   298.452] (**) Option "Device" "/dev/input/event5"
[   298.453] (II) mtrack: devname: appletouch
[   298.453] (II) mtrack: devid: 5ac 22a 7
[   298.453] (II) mtrack: caps: left
[   298.456] (**) appletouch: (accel) keeping acceleration scheme 1
[   298.456] (**) appletouch: (accel) acceleration profile 0
[   298.456] (**) appletouch: (accel) acceleration factor: 2.000
[   298.456] (**) appletouch: (accel) acceleration threshold: 4
[   298.456] (II) device control: on
[   298.456] (WW) Touchpad has minimal capabilities. Some features will be unavailable.
[   298.457] (II) config/udev: Adding input device appletouch (/dev/input/mouse0)
[   298.457] (II) No input driver/identifier specified (ignoring)
```

regarding  "appletouch" - I didnt install any other driver before, I guess this is  the default one? Sorry, I am not that experienced with ubuntu...
so what else could it be?

regards,

nik

---

### Post by nikflewlow on 2011-10-07
--

---

### Post by nikflewlow on 2011-10-11
anyone?

---

### Post by sickanimations on 2011-10-28
Can't get this working on 11.10 with 3.0.0-12 kernel. I've gone through all the suggestions in here, even tried editing mtrack.c, no good. Here are the details:

**Conditions**

New install of Ubuntu 11.10

Ran "http://almostsure.com/mba42/post-install-oneiric.sh", a post-install script for MacBook Air running Ubuntu 11.10 which reports to have mtrack working fine. The script failed to download and install mtrack. However, it did succeed with the other things it claims to get working.

**Installation Method**

```
dpkg-buildpackage
cd ..
sudo dpkg --install xserver-xorg-input-mtrack_0.2.0_amd64.deb
```

Added the following to xorg.conf:

```

    Section "InputClass"
        MatchIsTouchpad "on"
        Identifier      "Touchpads"
        Driver          "mtrack"
    EndSection

```


**Issues**

[LIST]
[*] Touchpad didn't work after restarting X. 
[*] Xorg log can't find "mtrack" driver.
[*] Module files in /usr/lib/xorg/modules/input/ are named "mtrack_drv.so" and "mtrack_drv.la". Rename
   these and Xorg now finds the driver.
[*] Xorg failes to completely load the module: "(EE) module ABI major version (13) doesn't match the 
   server's version (12)" I tried to edit the field in mtrack.c (yes, hackish)  but I can't understand CARD8 
   data type, nor can I find a definition for it.
 [*] Can't progress further.
[/LIST]

**Additional Information**
[LIST]
 [*] /var/log/Xorg.0.log: [http://pastebin.com/078jhiDa](http://pastebin.com/078jhiDa)
 [*] /etc/X11/xorg.conf: [http://pastebin.com/PKYkcVEg](http://pastebin.com/PKYkcVEg)
[/LIST]

I'm willing to put in time and effort to get this going. Thanks :)

---

### Post by BlueDragonX on 2011-10-28
I find it odd that the server has an older ABI version than the module. I'll have to look into that.

I've not tested against 11.10 yet, so of course there are no packages available. I'll see what I can do.

---

### Post by dfacto on 2011-10-28
I've happily been using mtrack for oneiric for several months now.
[http://almostsure.com/mba42/mba4-tmp/xserver-xorg-input-mtrack_0.2.0_amd64.deb](http://almostsure.com/mba42/mba4-tmp/xserver-xorg-input-mtrack_0.2.0_amd64.deb)

Built via:
```

echo "Building xf86-input-mtrack (trackpad driver)."
sudo aptitude install autoconf libtool libmtdev-dev xserver-xorg-dev xutils-dev
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack/
# http://ubuntuforums.org/showpost.php?p=10881280&postcount=105
# libtoolize && aclocal && autoconf && automake --add-missing --copy
autoreconf --install --force
# should install to: /usr/lib/xorg/modules/input/
./configure --prefix=/usr
dpkg-buildpackage

```

---

### Post by sickanimations on 2011-10-28
> **BlueDragonX said:**
> I find it odd that the server has an older ABI version than the module. I'll have to look into that.


I'm confused by it. Given that I build it and the code specifically uses the system's current ABI version.


> **dfacto said:**
> 
I've happily been using mtrack for oneiric for several months now.
[http://almostsure.com/mba42/mba4-tmp....2.0_amd64.deb](http://almostsure.com/mba42/mba4-tmp....2.0_amd64.deb)


Will have to give this a go, thanks.

---

### Post by joskapista on 2011-11-09
Hello, I tried to install the driver to  Debian 6, but I failed. I attached my xorg.log maybe somebody knows what is the problem. thanks

---

### Post by BlueDragonX on 2011-11-10
Did you use one of the deb package? It looks like you did - the driver was built against a much newer Xorg version than you're running. I don't have packages built for Debian. Try building it from source.

---

### Post by Moystard on 2011-11-11
> **dfacto said:**
> I've happily been using mtrack for oneiric for several months now.
[http://almostsure.com/mba42/mba4-tmp/xserver-xorg-input-mtrack_0.2.0_amd64.deb](http://almostsure.com/mba42/mba4-tmp/xserver-xorg-input-mtrack_0.2.0_amd64.deb)

Built via:
```

echo "Building xf86-input-mtrack (trackpad driver)."
sudo aptitude install autoconf libtool libmtdev-dev xserver-xorg-dev xutils-dev
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack/
# http://ubuntuforums.org/showpost.php?p=10881280&postcount=105
# libtoolize && aclocal && autoconf && automake --add-missing --copy
autoreconf --install --force
# should install to: /usr/lib/xorg/modules/input/
./configure --prefix=/usr
dpkg-buildpackage

```

Used your method to build a package from the last version of the sources and installed it. It works perfectly and it is a huge improvement over the default mouse driver.

Thank you very much :)

---

### Post by joskapista on 2011-11-12
thank you for your answer. I tried it but unfortunately it wasn't so simple, it looks too complicated for me.

---

### Post by BlueDragonX on 2011-11-12
> **joskapista said:**
> thank you for your answer. I tried it but unfortunately it wasn't so simple, it looks too complicated for me.

So you're giving up?

---

### Post by joskapista on 2011-11-12
No I never give up! :D I think I will try to install a newer xorg from backports. I know it would be better to learn how to build a .deb package but is seems to be a longer project, and I am just after the first steps.
(We usually say: if you know only the hammer, you will think that everything is an iron nail :))

---

### Post by BlueDragonX on 2011-11-12
Building the deb isn't hard. I've already got the deb package build directory in there since I build packages for Ubuntu. You may have to tweak it a bit for Debian but you shouldn't need to change much.

---

### Post by BlueDragonX on 2011-11-13
I'm trying to fix the issue where two finger scrolling in the up direction is hesitant. I can't seem to reproduce the issue. Can anyone who has run into the issue tell me how to reproduce? Otherwise I'm going to move on to the other outstanding issue.

---

### Post by BlueDragonX on 2011-11-14
Oneiric packages are now available: [http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/)

---

### Post by Quicksand on 2011-11-16
> **BlueDragonX said:**
> I'm trying to fix the issue where two finger scrolling in the up direction is hesitant. I can't seem to reproduce the issue. Can anyone who has run into the issue tell me how to reproduce? Otherwise I'm going to move on to the other outstanding issue.

I have experienced this -- here's my take on the situation.

Moving the wrist and hand downward is a natural, fluid motion, so it's easy to keep the two fingers' relative position the same while dragging them down together.

But going upward is less natural, and there's a tendency (at least in my case) for the fingers to drift together or apart, or for one finger to move a little faster than the other, or for the fingers to rotate with respect to each other, subtly.  And this seems to be the problem.  It stops scrolling when the fingers do something else -- even if it's not enough of that "something else" to trigger a zoom or whatever I have pinch or rotate set to.

If I lift my arm off the desk, and concentrate on keeping the two fingers identically spaced, I can scroll up and down smoothly.  When I don't think about it, it gets a little sloppy, and scrolling up doesn't work as well.  And if I intentionally make a very narrow "V" shape while scrolling up or down -- even if the angles are minimal, and the two tracks are almost parallel -- scrolling doesn't occur.

So that's my guess.

(And incidentally, I'm the guy who submitted issue #19 on your github project site, about extraneous pre-drag clicks showing up.  Here's hoping you can take a look at that one too!)

---

### Post by BlueDragonX on 2011-11-17
Nice description! That'll help out a lot. I'm determining movement direction using some bastardized trigonometry that's "close enough". I may have to upgrade to the real thing, but we'll see.

As for the tap-to-drag, I've played with it a bit and I think you might benefit from adjusting some of the configuration parameters for it. It's entirely adjustable. It works just fine for me using the defaults, but I know if I don't do it right it exhibits the behavior you're talking about. Give it a shot and see if you come up with anything. In the meantime I'm going to look into the upscrolling issue.

Also, I'm working on getting coasting implemented. So that's a feature to look forward to. I'm pushing for releasing v0.3.0 which will include a couple of new features.

---

### Post by quickk on 2011-11-24
> Oneiric packages are now available: [http://www.dev.fatedmariner.org/pack...mtrack/ubuntu/](http://www.dev.fatedmariner.org/pack...mtrack/ubuntu/) 

I tried installing the package from here, and upon rebooting my laptop, my trackpad is completely disabled.  What exactly are the installation steps?

I am using Kubuntu 11.10 on an original macbook air (1,1) and here is what I did:

- removed anything to do with synaptic (which I think were the following packages: xserver-xorg-input-synaptic-d, xserver-xorg-input-synaptics, xserver-xorg-input-synaptics:i3, kde-config-touchpad)

- installed the amd64 package from [http://www.dev.fatedmariner.org/pack...mtrack/ubuntu/](http://www.dev.fatedmariner.org/pack...mtrack/ubuntu/) (post 356)

- created a file /ect/X11/xorg.conf (I didn't have one before) and added the following lines, based on what I read in [this thread]("http://ubuntuforums.org/showthread.php?t=1334696&page=36").

```
Section "InputClass"
	MatchIsTouchpad "on"
	Identifier      "Touchpads"
	Driver          "multitouch"
	Option		"ThumbSize" "35"
	Option		"PalmSize" "55"
	Option		"ClickTime" "25"
	Option		"ScrollDistance" "300"
	Option		"TapDragEnable" "False"
EndSection

```

- rebooted.   Now my trackpad does not work at all!

Is there anything that I missed?   Should I have kept some of those packages that I removed?

---

### Post by BlueDragonX on 2011-11-24
Post your xorg log. I can't help you (or anyone else) if I don't have the logs.

---

### Post by BlueDragonX on 2011-11-24
> **quickk said:**
> 
```
Section "InputClass"
	MatchIsTouchpad "on"
	Identifier      "Touchpads"
	Driver          "multitouch"
	Option		"ThumbSize" "35"
	Option		"PalmSize" "55"
	Option		"ClickTime" "25"
	Option		"ScrollDistance" "300"
	Option		"TapDragEnable" "False"
EndSection

```


This is wrong. Driver should be mtrack. Fix that and post your xorg logs.

---

### Post by quickk on 2011-11-25
Thanks BlueDragonX!   I changed the name of the driver to mtrack and now the touchpad works (although it's a bit wonky).   All that I need to figure out now is how to make the three finger swipe work for forward and back, and to prevent the cursor to jump around when I accidentally brush the touchpad with my palms.   Two finger scrolling is not very smooth or responsive either, but I'm confident that these problems can be solved based on the large number of configuration options.

---

### Post by artik1024 on 2011-12-10
BlueDragonX, you made an amazing job. After getting a xorg.conf close to the macOs one, I wanted to know if I can set a 2 or 3 fingers left or right scrolling to a special fonction ?

Example :

2 fingers left / right : back button
3 fingers move : move windows
4 fingers left / right : switch desktops

Thank !

---

### Post by Zookalicious on 2011-12-10
> **artik1024 said:**
> BlueDragonX, you made an amazing job. After getting a xorg.conf close to the macOs one, I wanted to know if I can set a 2 or 3 fingers left or right scrolling to a special fonction ?

Example :

2 fingers left / right : back button
3 fingers move : move windows
4 fingers left / right : switch desktops

Thank !

Try using touchegg for that. I have a conf for it I can upload later.

---

### Post by BlueDragonX on 2011-12-10
> **artik1024 said:**
> BlueDragonX, you made an amazing job. After getting a xorg.conf close to the macOs one, I wanted to know if I can set a 2 or 3 fingers left or right scrolling to a special fonction ?

Example :

2 fingers left / right : back button
3 fingers move : move windows
4 fingers left / right : switch desktops

Thank !

Yes, a third party app is required to convert mouse clicks to something else.

I use Compiz and it does all that for me.

---

### Post by artik1024 on 2011-12-10
Thanks Zookalicious and Bluedrag'.

@Zookalicious : with pleasure ! going to try ;) waiting for your upload

---

### Post by Zookalicious on 2011-12-11
> **artik1024 said:**
> Thanks Zookalicious and Bluedrag'.

@Zookalicious : with pleasure ! going to try ;) waiting for your upload

I should have it up by either the end of today or tomorrow morning, I just need to get to the computer that has the file saved on it. Currently it has a bunch of extra options that I find usefull, but I will upload both a feature-rich version, and one that just matches OS X actions (a bit more simple).

Normal OS X version has:
3 finger swipe left and right to go back and forward.
3 finger swipe up and down to go to the top of the page or bottom of a page ("home" and "end" key simulation)
3 finger tap for middle click
4 finger swipe up / 4 finger swipe down triggers the "Scale" compiz plugin which is similar to Expose in OS X. I think this still works, the config file I use doesn't have this in it although I used it in the past.

Optionally, my "feature-rich" config file has the following added in:
4 finger tap to refresh a page ("F5" simulation)
4 finger drag to move a window (I don't use Unity, so this replaces the grab handles) (REPLACES 4 FINGER SWIPE UP/DOWN)
5 finger tap to close a window. 
5 finger swipe to change workspaces (Ex: Swipe left to change to the workspace to the left, etc)

Depending on what version of Ubuntu you have, installing touchegg is pretty simple. 11.10 just has it in the software center.

---

### Post by Zookalicious on 2011-12-12
For some reason Ubuntu forums won't let me attach a .conf file. So after installing touchegg, navigate to your /home/USERNAME/.config folder and make a new folder called "touchegg". In that new folder make a blank text file in geddit called "touchegg.conf". Copy and paste the following into that file, and then run the command "touchegg" in a terminal to get it started. 

```
<touchégg>
    
    <settings>
        <property name="composed_gestures_time">0</property>
    </settings>
    

    <application name="All">
        
        <gesture type="DRAG" fingers="3" direction="UP">
        <action type="SEND_KEYS">Home</action>
        </gesture>
        
        <gesture type="DRAG" fingers="3" direction="DOWN">
        <action type="SEND_KEYS">End</action>
        </gesture>

        <gesture type="DRAG" fingers="3" direction="LEFT">
            <action type="MOUSE_CLICK">BUTTON=8</action>
        </gesture>
 
        <gesture type="DRAG" fingers="3" direction="RIGHT">
            <action type="MOUSE_CLICK">BUTTON=9</action>
        </gesture>
       
    </application>


    <application name="Okular, Gwenview">

        <gesture type="PINCH" fingers="2" direction="IN">
            <action type="SEND_KEYS">Control+KP_Add</action>
        </gesture>

        <gesture type="PINCH" fingers="2" direction="OUT">
            <action type="SEND_KEYS">Control+KP_Subtract</action>
        </gesture>

        <gesture type="ROTATE" fingers="2" direction="LEFT">
            <action type="SEND_KEYS">Control+L</action>
        </gesture>

        <gesture type="ROTATE" fingers="2" direction="RIGHT">
            <action type="SEND_KEYS">Control+R</action>
        </gesture>

    </application>


    <application name="Chromium-browser, Dolphin">

        <gesture type="DRAG" fingers="2" direction="LEFT">
            <action type="SEND_KEYS">Alt+Left</action>
        </gesture>

        <gesture type="DRAG" fingers="2" direction="RIGHT">
            <action type="SEND_KEYS">Alt+Right</action>
        </gesture>
        
    </application>


</touchégg>
```


This is the basic one so all it does is add the three finger swipes for "home" "end" "back" and "forwards". I left the Scale plugin out because I forgot my key combinations are customized and it won't work for your install (and I don't remember the defaults)

If you want me to post the extra trackpad functions that's no problem as well, just let me know.

---

### Post by agestrada on 2012-01-08
Thanks a lot for the driver. Currently using it with Natty and a Macbook Pro 5,5, no problems so far.  I will try more compiz effects during the next days ...

---

### Post by fgmart on 2012-01-18
I've installed Ubuntu 11.10 on a MacBook Pro 13" model 8,1.

The trackpad only responds to physical clicks.  In the System Settings "Mouse and Touchpad" panel, only Mouse shows up -- no Trackpad.

I've tried installing the xf86-input-mtrack -- I downloaded the git source, installed xutils-dev, xserver-xorg-dev, did the "autoreconf -i", ./configure, make, and make-install.  It seemed to complete without complaining.

I added a basic /etc/X11/xorg.conf file; it says:

<hr>
Section "InputClass"
        MatchIsTouchpad "true"
        Identifier "touchpad"
        Driver "multitouch"
EndSection
</hr>

But none of this seems to work.  

lsusb gives this identifier for the trackpad:

Bus 001 Device 005: ID 05ac:0252 Apple, Inc. 

Does anyone have any suggestions?  

Thanks all.

p.s. This person over here seems to have the exact situation as do I -- [https://bbs.archlinux.org/viewtopic.php?id=131412](https://bbs.archlinux.org/viewtopic.php?id=131412) -- his case is unresolved.

---

### Post by BlueDragonX on 2012-01-18
I've built official debs for Oneiric. Did you try installing them?

[http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/)

---

### Post by jonas_t on 2012-01-21
First of all, thanks a lot for your effort, BlueDragonX!

After using the multitouch driver for a day, I've been trying to get mtrack working on Kubuntu 11.10. No luck so far. :(

What i've done: installed your offical mtrack ubuntu build (x64, version 0.2.0), removed the multitouch-driver. That removing actually didn't change anything. The logs with/without multitouch driver installed looked the same. Then I adjusted my xorg.conf for the touch-/trackpad -- taken from your github readme:

```
Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Touchpads"
     Driver "mtrack"
EndSection
```


According to the xserver logs (attached), it recognizes **two** devices, with mtrack failing on the second. Mtrack is then unloaded. As far as I understand the logs, the devices are:

[LIST]
[*]/dev/input/event7
[*]/dev/input/mouse1
[/LIST]
Is that normal behavior? Or is there some device filter required?

Model here is a MBP 6,2.

Btw: any plans to put your builds online as a ppa? That would really simplify updating!

I would much appreciate any help in getting this to run. The multitouch-driver is a little crappy. :)

---

### Post by jonas_t on 2012-01-21
> **jonas_t said:**
> 
After using the multitouch driver for a day, I've been trying to get mtrack working on Kubuntu 11.10. No luck so far. :(

Update - to be more precise: 
I found a reply in this thread, that loading the two devices should be ok. Still, I only see a mouse cursor. It does not move, nor do clicks work via tapping or the built-in button.

---

### Post by BlueDragonX on 2012-01-21
Well, everything looks good in the logs. Post up the output of xinput list-props for the driver.

Do an "xinput list" and find the bcm5974 device. Get the id number from it and do "xinput list-props ID" where the ID is the id= you found next to the bcm driver.

---

### Post by jonas_t on 2012-01-21
> **BlueDragonX said:**
> Well, everything looks good in the logs. Post up the output of xinput list-props for the driver.

Here you go:

```

jonas@jonas-mbp:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                   id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; Apple Inc. Apple Internal Keyboard / Trackpad     id=9    [slave  keyboard (3)]
    &#8627; Built-in iSight                           id=11   [slave  keyboard (3)]
jonas@jonas-mbp:~$ xinput list-props 10
Device 'bcm5974':
        Device Enabled (121):   1
        Coordinate Transformation Matrix (123): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (249):     0
        Device Accel Constant Deceleration (250):       1.000000
        Device Accel Adaptive Deceleration (251):       1.000000
        Device Accel Velocity Scaling (252):    10.000000
jonas@jonas-mbp:~$ 

```

---

### Post by BlueDragonX on 2012-01-21
mtrack is not associated with that device for some reason.

Show us the output of "dmesg | grep bcm"

Thanks.

---

### Post by jonas_t on 2012-01-21
> **BlueDragonX said:**
> mtrack is not associated with that device for some reason.

Show us the output of "dmesg | grep bcm"

Oh, ok. In the meantime, I restored the multitouch-driver and posted the output with it enabled. I didn't expect that to make a difference, since both drivers build upon bcm.

Anyway, here is the correct xinput-output with mtrack loaded:

```

Device 'bcm5974':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Trackpad Disable Input (253):    0
    Trackpad Sensitivity (254):    1.000000
    Trackpad Touch Pressure (255):    70, 5
    Trackpad Button Settings (256):    1, 1, 100, 0
    Trackpad Button Emulation (257):    3, 2, 0
    Trackpad Tap Settings (258):    50, 120, 400
    Trackpad Tap Button Emulation (259):    1, 3, 2, 0
    Trackpad Thumb Detection (260):    0, 0
    Trackpad Thumb Size (261):    25, 70
    Trackpad Palm Detection (262):    0, 0
    Trackpad Palm Size (263):    40
    Trackpad Gesture Settings (264):    10, 100
    Trackpad Scroll Distance (265):    150
    Trackpad Scroll Buttons (266):    4, 5, 6, 7
    Trackpad Swipe Distance (267):    700
    Trackpad Swipe Buttons (268):    8, 9, 10, 11
    Trackpad Swipe4 Distance (269):    700
    Trackpad Swipe4 Buttons (270):    0, 0, 0, 0
    Trackpad Scale Distance (271):    150
    Trackpad Scale Buttons (272):    14, 15
    Trackpad Rotate Distance (273):    150
    Trackpad Drag Settings (274):    1, 350, 40, 200

```

And dmesg output as well:
```

[   19.741683] input: bcm5974 as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input8
[   19.741791] usbcore: registered new interface driver bcm5974
[  440.196886] bcm5974: bad trackpad package, length: 8
[  440.208892] bcm5974: bad trackpad package, length: 8
[  440.209883] bcm5974: bad trackpad package, length: 8
[  440.210877] bcm5974: bad trackpad package, length: 8
[  440.212882] bcm5974: bad trackpad package, length: 8

```

---

### Post by BlueDragonX on 2012-01-21
X is using the wrong device. It's using /dev/input/event7 while dmesg reports it's on /dev/input/event8. Try changing you Xorg config to this:


Section "InputClass"
    MatchDevicePath "/dev/input/event8"
    Identifier      "Touchpads"
    Driver          "mtrack"
EndSection


Then restart X.

---

### Post by jonas_t on 2012-01-21
> **BlueDragonX said:**
> X is using the wrong device. It's using /dev/input/event7 while dmesg reports it's on /dev/input/event8. Try changing you Xorg config to this:


Well, the good news is: clicking works (at least via the built-in button). The bad news is: cursor movement does not. I checked with the multitouch-driver: it also hooks to event8, so that should be correct now.

Attaching Xorg log.

xinput list-props:
```
Device 'bcm5974':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Trackpad Disable Input (253):    0
    Trackpad Sensitivity (254):    1.000000
    Trackpad Touch Pressure (255):    70, 5
    Trackpad Button Settings (256):    1, 1, 100, 0
    Trackpad Button Emulation (257):    3, 2, 0
    Trackpad Tap Settings (258):    50, 120, 400
    Trackpad Tap Button Emulation (259):    1, 3, 2, 0
    Trackpad Thumb Detection (260):    0, 0
    Trackpad Thumb Size (261):    25, 70
    Trackpad Palm Detection (262):    0, 0
    Trackpad Palm Size (263):    40
    Trackpad Gesture Settings (264):    10, 100
    Trackpad Scroll Distance (265):    150
    Trackpad Scroll Buttons (266):    4, 5, 6, 7
    Trackpad Swipe Distance (267):    700
    Trackpad Swipe Buttons (268):    8, 9, 10, 11
    Trackpad Swipe4 Distance (269):    700
    Trackpad Swipe4 Buttons (270):    0, 0, 0, 0
    Trackpad Scale Distance (271):    150
    Trackpad Scale Buttons (272):    14, 15
    Trackpad Rotate Distance (273):    150
    Trackpad Drag Settings (274):    1, 350, 40, 200

```

---

### Post by jonas_t on 2012-01-25
*bump*? :)

---

### Post by MRGAY on 2012-01-25
> **jonas_t said:**
> *bump*? :)

I'm not sure if you tried this, but maybe manually enabling the trackpad from the xorg.conf might work:

"TrackpadDisable - Disables trackpad touch input. A value of 0 will enable the trackpad. A value of 1 will disable tapping and gestures but not movement. A value of 2 will disable all input. A value of 3 will also disable physical buttons. Integer. Default is 0."

Maybe add that?

[PHP]Section "InputClass"
     MatchDevicePath "/dev/input/event8"
     Identifier "Touchpads"
     Driver "mtrack"
     Option "TrackpadDisable" "0"
     EndSection
EndSection[/PHP]

EDIT: I just started using Ubuntu a few days ago, so I'm not too sure what the hell I'm talking about. xD

---

### Post by jonas_t on 2012-01-25
> **MRGAY said:**
> I'm not sure if you tried this, but maybe manually enabling the trackpad from the xorg.conf might work:

hey,
yeah almost. what really did the trick for me was to set the FingerHigh option. In the xorg log, it said it was initialized with 70. In the documentation, I found that this is a percentage value and 5 should be the default. After some thinking, I remembered setting a similar option for the synaptics driver in /etc/X11/xorg.conf.d/. So it turned out, that this config file for the synaptics driver set the *same* option for the mtrack driver - FingerHigh (which I did not explictly overwritten in xorg.conf). Thus, the sensitvity for touches and moves was simply set way too high for mtrack to recognize any of those.

on the other hand, to be honest, I dropped mtrack again in favor of a custom multitouch driver build (with tapping disabled, it often does unwanted clicks) since I really like the ability to have one finger on the pad to click the buitlin button and move the cursor with another finger. mtrack always interprets this as scroll (two fingers on the pad), no matter how distant the two fingers really are.

@BlueDragon: Any plans on supporting the same as in multitouch -- one finger clicks the builtin button, the other moves the cursor?

---

### Post by fgmart on 2012-01-25
Dear BlueDragonX,

I'm the one with the Ubuntu 11.10 on a MacBook Pro 13" model 8,1 config.

I installed from your bins (thank you).  Nothing changed.

I have the info from the github readme in my /etc/X11/xorg.conf.

I also see a bunch of config files at /usr/share/X11/xorg.conf.d/.

I tried running the "dmesg | grep bcm" you suggested to someone else.  My machine does not have the bcm5974 driver loaded (no matches).

Help?  Thank you.

---

### Post by BlueDragonX on 2012-01-25
> **fgmart said:**
> Dear BlueDragonX,

I'm the one with the Ubuntu 11.10 on a MacBook Pro 13" model 8,1 config.

I installed from your bins (thank you).  Nothing changed.

I have the info from the github readme in my /etc/X11/xorg.conf.

I also see a bunch of config files at /usr/share/X11/xorg.conf.d/.

I tried running the "dmesg | grep bcm" you suggested to someone else.  My machine does not have the bcm5974 driver loaded (no matches).

Help?  Thank you.

You need to get the bcm driver loaded to handle your trackpad. Until you do that nothing will work. Try a "modprobe bcm5974" and check dmesg again to see if it loaded.

---

### Post by fgmart on 2012-01-27
BlueDragonX, 

I got bcm5974 running!  I cloned the git repo given at [http://bitmath.org/code/bcm5974-dkms/](http://bitmath.org/code/bcm5974-dkms/), installed, and added it to /etc/modules.

Here's the output of dmesg | grep bcm5974 now:

[   39.977172] usbcore: registered new interface driver bcm5974


Then I tried copying the info you gave to another for /etc/X11/xorg.config:

Section "InputClass"
MatchDevicePath "/dev/input/event8"
Identifier "Touchpads"
Driver "mtrack"
EndSection


But... still no trackpad showing up in Mouse & Trackpad system settings.

Point me along further?

Thank you.

---

### Post by BlueDragonX on 2012-01-27
> **fgmart said:**
> BlueDragonX, 

I got bcm5974 running!  I cloned the git repo given at [http://bitmath.org/code/bcm5974-dkms/](http://bitmath.org/code/bcm5974-dkms/), installed, and added it to /etc/modules.

Here's the output of dmesg | grep bcm5974 now:

[   39.977172] usbcore: registered new interface driver bcm5974


Then I tried copying the info you gave to another for /etc/X11/xorg.config:

Section "InputClass"
MatchDevicePath "/dev/input/event8"
Identifier "Touchpads"
Driver "mtrack"
EndSection


But... still no trackpad showing up in Mouse & Trackpad system settings.

Point me along further?

Thank you.

Don't use MatchDevicePath anymore, use:
```
MatchIsTouchpad "on"
```

---

### Post by EnderTheThird on 2012-01-31
I can't seem to get gestures working on my 11" MacBook Air.  I patched the kernel as described on the Ubuntu page for the MacBook Air ([https://help.ubuntu.com/community/MacBookAir4-2#Touchpad](https://help.ubuntu.com/community/MacBookAir4-2#Touchpad)), but it doesn't seem to be detecting 3+ finger gestures.  3 finger swiping to the left and the right works fine in xev in the terminal, but I don't get any "Button[X]" results for other 3 finger or 4 finger gestures in xev.

I'm working my way through this thread to try to find an answer, as search wasn't finding much for me.  So if this has been addressed, I apologize.

For reference, my xorg.conf is:
```

# mtrack
Section "InputClass"
    Identifier       "Multitouch Touchpad"
    Driver           "mtrack"
#    MatchDevicePath  "/dev/input/event*"
    MatchIsTouchpad  "on"
    Option           "CorePointer"     "true"
    Option           "Sensitivity"     "0.70"  #    1 : movement speed
    Option           "ScrollDistance"  "100"   #  150 : two-finger drag dist for click
    Option           "ClickTime"       "25"    #   50 : millisec to hold emulated click
    Option           "ThumbSize"       "35"    #   25 : min size of thumb
    Option           "PalmSize"        "55"    #   40 : min size of palm
EndSection # "Multitouch Touchpad"

```

This is a 2011 model 11" MacBook Air.  I've checked lsmod, and the bcm5974 module is running.  Let me know if you need more info.

---

### Post by BlueDragonX on 2012-01-31
> **EnderTheThird said:**
> 3 finger swiping to the left and the right works fine in xev in the terminal, but I don't get any "Button[X]" results for other 3 finger or 4 finger gestures in xev.

What gestures are you trying to do? The only supported three and four finger gestures are swiping up/down/left/right.

---

### Post by blackjay0419 on 2012-02-01
Thanks for the driver, BluedragonX. 
After some tweak, the multitouch pad come much closer to OSX experience.

I want to install dispad since my cursor jumping around when I am typing, but I don't know how to do this.
After I download the Zip from the gIfib, what should  I do then?


I also encountered the scroll up problem. It did not work as smoothly as scroll down.
If I adjust fingerhigh/low to a more sensitive setting and scroll distance (75), the situation is improved.
But sometimes it still happens. I am guessing whether this problem is related to  the difference of finger tap pressure between scroll up and scroll down.

---

### Post by BlueDragonX on 2012-02-01
> **blackjay0419 said:**
> Thanks for the driver, BluedragonX. 
After some tweak, the multitouch pad come much closer to OSX experience.

I want to install dispad since my cursor jumping around when I am typing, but I don't know how to do this.
After I download the Zip from the gIfib, what should  I do then?


I also encountered the scroll up problem. It did not work as smoothly as scroll down.
If I adjust fingerhigh/low to a more sensitive setting and scroll distance (75), the situation is improved.
But sometimes it still happens. I am guessing whether this problem is related to  the difference of finger tap pressure between scroll up and scroll down.

There are debs for dispad, install them the same way you installed the driver.

The scrolling issue is fixed in the dev branch and will be part of the next release.

---

### Post by blackjay0419 on 2012-02-01
> **BlueDragonX said:**
> There are debs for dispad, install them the same way you installed the driver.

The scrolling issue is fixed in the dev branch and will be part of the next release.


Thanks, I have installed the deb for Oneric (though I am using Precise, but the software center said it was installed successfully).  
However,  how do I start it ? 
I type the following command "dispad" on the terminal, and it shows
"[I] using config file: /home/taijan/.dispad"
But I didn't find the config file in the directory ?
Do I miss anything?

---

### Post by BlueDragonX on 2012-02-01
> **blackjay0419 said:**
> Thanks, I have installed the deb for Oneric (though I am using Precise, but the software center said it was installed successfully).  
However,  how do I start it ? 
I type the following command "dispad" on the terminal, and it shows
"[I] using config file: /home/taijan/.dispad"
But I didn't find the config file in the directory ?
Do I miss anything?

Yes, you did. /home/taijan/.dispad IS the config file. It's not a directory. It's auto-generated on the first run of dispad. You can have your window manager (Gnome/KDE/whatever) start it on login or you can do it manually the way you did it already. To stop it do a "killall dispad" in the terminal.

---

### Post by nightfrost on 2012-02-02
I would like to try to build mtrack from the dev branch (I'm on Precise Pangolin), but I'm not exactly sure how to do it. Does this give me the source code for 'dev'?

```
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack
git branch dev
git ceckout dev
```

and then, is this is how I start, right?
```
./autoreconf --install --force
```

Thanks for this driver, by the way! And thanks in advance for any help I might get :)

---

### Post by BlueDragonX on 2012-02-02
```
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack
git branch dev
git ceckout dev
./autoreconf --install --force
./configure && make && sudo make install

```

You may need to pass --with-xorg-module-dir=SOMEDIR to configure, where SOMEDIR is the install location of the xorg modules.

---

### Post by nightfrost on 2012-02-03
Thanks, BlueDragonX.

make fails though, like this:


```
./tools/mtrack-test.c:35:5: error: conflicting types for ‘xf86SetIntOption’
/usr/include/xorg/xf86Opt.h:73:22: note: previous declaration of ‘xf86SetIntOption’ was here
./tools/mtrack-test.c:40:5: error: conflicting types for ‘xf86SetBoolOption’
/usr/include/xorg/xf86Opt.h:76:22: note: previous declaration of ‘xf86SetBoolOption’ was here
./tools/mtrack-test.c:45:8: error: conflicting types for ‘xf86SetRealOption’
/usr/include/xorg/xf86Opt.h:74:25: note: previous declaration of ‘xf86SetRealOption’ was here
make[2]: *** [mtrack_test-mtrack-test.o] Error 1
make[2]: Leaving directory `/home/khashayar/Downloads/xf86-input-mtrack-build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/khashayar/Downloads/xf86-input-mtrack-build'
make: *** [build-arch] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

---

### Post by nightfrost on 2012-02-03
Sorry for the double post, but all of a sudden I'm doubting I get the dev branch using the git commands above.

Here's why: After cloning the git repo, I copied xf86-input-mtrack to xf86-input-mtrack-dev, then:

```
cd xf86-input-mtrack-dev
git branch dev
git checkout dev
cd ..
diff -Nur xf86-input-mtrack xf86-input-mtrack-dev.
```

and the results:


```
diff -Nur xf86-input-mtrack xf86-input-mtrack-dev/
diff -Nur xf86-input-mtrack/.git/HEAD xf86-input-mtrack-dev/.git/HEAD
--- xf86-input-mtrack/.git/HEAD	2012-02-03 13:02:51.155014084 +0100
+++ xf86-input-mtrack-dev/.git/HEAD	2012-02-03 13:23:52.351567897 +0100
@@ -1 +1 @@
-ref: refs/heads/master
+ref: refs/heads/dev
Binary files xf86-input-mtrack/.git/index and xf86-input-mtrack-dev/.git/index differ
diff -Nur xf86-input-mtrack/.git/logs/HEAD xf86-input-mtrack-dev/.git/logs/HEAD
--- xf86-input-mtrack/.git/logs/HEAD	2012-02-03 13:02:51.159014084 +0100
+++ xf86-input-mtrack-dev/.git/logs/HEAD	2012-02-03 13:23:52.351567897 +0100
@@ -1 +1,2 @@
 0000000000000000000000000000000000000000 71abf32ba62683de54821329f2470daf9b1e1386 Khashayar Naderehvandi <khashayar@medea.(none)> 1328270571 +0100	clone: from http://github.com/BlueDragonX/xf86-input-mtrack.git
+71abf32ba62683de54821329f2470daf9b1e1386 71abf32ba62683de54821329f2470daf9b1e1386 Khashayar Naderehvandi <khashayar@medea.(none)> 1328271832 +0100	checkout: moving from master to dev
diff -Nur xf86-input-mtrack/.git/logs/refs/heads/dev xf86-input-mtrack-dev/.git/logs/refs/heads/dev
--- xf86-input-mtrack/.git/logs/refs/heads/dev	1970-01-01 01:00:00.000000000 +0100
+++ xf86-input-mtrack-dev/.git/logs/refs/heads/dev	2012-02-03 13:23:48.739567799 +0100
@@ -0,0 +1 @@
+0000000000000000000000000000000000000000 71abf32ba62683de54821329f2470daf9b1e1386 Khashayar Naderehvandi <khashayar@medea.(none)> 1328271828 +0100	branch: Created from master
diff -Nur xf86-input-mtrack/.git/refs/heads/dev xf86-input-mtrack-dev/.git/refs/heads/dev
--- xf86-input-mtrack/.git/refs/heads/dev	1970-01-01 01:00:00.000000000 +0100
+++ xf86-input-mtrack-dev/.git/refs/heads/dev	2012-02-03 13:23:48.739567799 +0100
@@ -0,0 +1 @@
+71abf32ba62683de54821329f2470daf9b1e1386

```

Shouldn't the contents of those dirs be different?

EDIT: Sorry, found out how to do it: 
git clone --branch dev [https://github.com/BlueDragonX/xf86-input-mtrack.git](https://github.com/BlueDragonX/xf86-input-mtrack.git)

---

### Post by EnderTheThird on 2012-02-07
> **BlueDragonX said:**
> What gestures are you trying to do? The only supported three and four finger gestures are swiping up/down/left/right.

Sorry, I should have specified.  Yes, I was talking about the swiping gestures as mentioned on the github page for the driver.

I've been messing with the xorg.conf more since then, and they seem to be working now that I've set each of them in xorg.conf.  I'm now getting it to read "button 10" and whatnot when I test the gestures using xev in the terminal.

If you could be so kind as to answer a few more questions for me, it would make it much easier to finish fussing with this to get it working the way I want:
[LIST=1]
[*]How many "buttons" does this driver support?  I'm setting each of the swipe gestures to a button in xorg.conf, but I'm wondering how high up I can go (I'm up to 20+ now with swipe gestures, scale, rotate, etc.).
[*]Is there an easier way to apply changes from xorg.conf rather than restarting the machine?  I have the 11" MacBook Air, so I've been trying to find a good swipe distance for some of the gestures, and restarting while trying different values is a real pain!
[*]Each of the "buttons" I specify in xorg.conf and verify through xev in the terminal, are they seen as mouse buttons?  I ask because in CompizConfigSettingsManager I can't get them to work as bindings for things like scale.  I specify "Button15" as a mouse binding for a shortcut, but that doesn't work, and doing the gesture won't do anything if I try to enter it as a keyboard shortcut either. What do I need to do to get these gestures working with Compiz so I can re-create the behavior in OS X Lion?
[/LIST]

Thanks a ton for all the work you've put into this driver.  I can't wait to get it working for me the way I want it to!

---

### Post by BlueDragonX on 2012-02-10
> **nightfrost said:**
> Sorry for the double post, but all of a sudden I'm doubting I get the dev branch using the git commands above.

Here's why: After cloning the git repo, I copied xf86-input-mtrack to xf86-input-mtrack-dev, then:

```
cd xf86-input-mtrack-dev
git branch dev
git checkout dev
cd ..
diff -Nur xf86-input-mtrack xf86-input-mtrack-dev.
```

..snip..

Shouldn't the contents of those dirs be different?

EDIT: Sorry, found out how to do it: 
git clone --branch dev [https://github.com/BlueDragonX/xf86-input-mtrack.git](https://github.com/BlueDragonX/xf86-input-mtrack.git)

The "git branch dev" command created a new branch called dev. You should have just done a "git checkout dev" to check out the dev branch.

Or you can do what you ended up doing, which checks out the branch during the clone. The short form of --branch is -b. So:

[code]git clone -b dev https://github.com/BlueDragonX/xf86-input-mtrack.git



> **EnderTheThird said:**
> How many "buttons" does this driver support?  I'm setting each of the swipe gestures to a button in xorg.conf, but I'm wondering how high up I can go (I'm up to 20+ now with swipe gestures, scale, rotate, etc.).

It's however many Xorg supports. I don't know what the upper limit on that is, but I'm sure it's bounded by whatever data type it is. So I'd just keep going until it stops working :P

> **EnderTheThird said:**
> Is there an easier way to apply changes from xorg.conf rather than restarting the machine?

All of the config is modifiable via the xinput command, though anything you change there won't be saved across a restart of Xorg.

Just by logging out and logging back in your changes will be committed, since doing so restarts of Xorg. And if that still doesn't work you can restart it manually.

> **EnderTheThird said:**
> Each of the "buttons" I specify in xorg.conf and verify through xev in the terminal, are they seen as mouse buttons?  I ask because in CompizConfigSettingsManager I can't get them to work as bindings for things like scale.  I specify "Button15" as a mouse binding for a shortcut, but that doesn't work, and doing the gesture won't do anything if I try to enter it as a keyboard shortcut either. What do I need to do to get these gestures working with Compiz so I can re-create the behavior in OS X Lion?

All of them are mouse buttons. The limitation you're running into is in Compiz Settings Manager (or whatever it's called), not the driver, Xorg, or even Compiz itself. The settings manager won't save values greater than a certain number to the Compiz config, so you have to change it using gconf. Don't recall the specific values in gconf to change, a bit of Googling should get you what you need.


> **EnderTheThird said:**
> Thanks a ton for all the work you've put into this driver.  I can't wait to get it working for me the way I want it to!

You're welcome :)

---

### Post by EnderTheThird on 2012-02-14
> **BlueDragonX said:**
> 
All of them are mouse buttons. The limitation you're running into is in Compiz Settings Manager (or whatever it's called), not the driver, Xorg, or even Compiz itself. The settings manager won't save values greater than a certain number to the Compiz config, so you have to change it using gconf. Don't recall the specific values in gconf to change, a bit of Googling should get you what you need.


First, thanks for the reply.  I've been googling for a while now, and I ran into posts regarding what you were talking about as far as the button limit for CCSM, but I don't think that's what I'm running into.  I checked with gconf-editor, and the bindings are as I left them.  That doesn't appear to be the problem.

I have noticed, however, that when I enter a gesture button as a binding in CCSM, that button no longer registers when I do the gesture in xev.  Not sure if that's expected or not.  

To be honest, I'm kind of at a loss.  In case anyone has found a way to do this and can help me out, I'm basically just trying to recreate Lion's gestures with the following:
[LIST]
[*]Swipe4UpButton: Scale --> Initiate window picker.
[*]SwipeLeftButton:  Back button (as in browser)
[*]SwipeRightButton: Forward button (as in browser)
[*]SwipeDownButton: Page Down.
[*]SwipeUpButton: Page Up.
[*]Swipe4DownButton: Either Run dialog or the main Unity menu.
[*]Swipe4LeftButton: Go to previous tab in web browser (Ctrl+Shift+Tab).
[*]Swipe4RightButton:  Go to next tab in web browser (Ctrl+Tab).
[/LIST]

The closest I got was with using commands in CCSM and executing keyboard commands with "xdotool", but still ran into issues with repeating buttons with a single gesture.  For example, I got Scale working, but it would go in and out of the Scale plugin as I swiped up with 4 fingers because it would register multiple "button" presses unless I got the distance just right.  I checked the driver documentation, and I didn't see a way to keep gesture buttons from repeating within a certain timeframe or anything like that.  But if anyone can think of a way to do keep the touchpad from sending multiple button presses with certain gestures, I would be totally OK setting everything up through xdotool.

I've been using Ubuntu for about 6 years now, and I'm not huge on Lion, but I really loved the multitouch gestures.  I'm dying to get those stinking things working with a few personalizations in Ubuntu!

---

### Post by vsanchez1961 on 2012-02-22
Hi, 

I am very happy with mtrack (the problems with cursor jumping when typing is much minimized). However,  I have a problem that is driving me crazy and it is that if I use my thumbs to click then the cursor moves too much loosing the position. I guess the large area of the thumb is making the centroid move when pressing as the thumb print increases... what parameter do I need to tweak to try to minimize that????

These are my current settings:

     MatchIsTouchpad "on"
      Identifier      "Touchpads"
      Driver          "mtrack"
      Option          "ThumbSize" "35"
      Option          "PalmSize"  "55"
      Option          "ClickTime"  "25"
      Option          "ScrollDistance" "300"
      Option "TapButton1" "0"
      Option "Sensitivity" "0.85"
      Option "TapButton2" "0"
      Option "TapButton3" "0"
      Option "ScrollDistance" "175"
      Option "FingerHigh" "10"
      Option "FingerLow" "10"
      Option "IgnorePalm" "true"

---

### Post by BlueDragonX on 2012-02-23
> **vsanchez1961 said:**
> Hi, 

I am very happy with mtrack (the problems with cursor jumping when typing is much minimized). However,  I have a problem that is driving me crazy and it is that if I use my thumbs to click then the cursor moves too much loosing the position. I guess the large area of the thumb is making the centroid move when pressing as the thumb print increases... what parameter do I need to tweak to try to minimize that????

These are my current settings:

     MatchIsTouchpad "on"
      Identifier      "Touchpads"
      Driver          "mtrack"
      Option          "ThumbSize" "35"
      Option          "PalmSize"  "55"
      Option          "ClickTime"  "25"
      Option          "ScrollDistance" "300"
      Option "TapButton1" "0"
      Option "Sensitivity" "0.85"
      Option "TapButton2" "0"
      Option "TapButton3" "0"
      Option "ScrollDistance" "175"
      Option "FingerHigh" "10"
      Option "FingerLow" "10"
      Option "IgnorePalm" "true"

The centerpoint of your touch is calculated upstream of the mtrack driver, and is used as-is. There's nothing you can do to change that value. The best you can do would be to change FingerHigh/FingerLow so that the trackpad ignores the touch until your finger (or thumb) has further settled into the trackpad. Past that the only thing you can do is change how you use it...

---

### Post by vsanchez1961 on 2012-02-23
> **BlueDragonX said:**
> The centerpoint of your touch is calculated upstream of the mtrack driver, and is used as-is. There's nothing you can do to change that value. The best you can do would be to change FingerHigh/FingerLow so that the trackpad ignores the touch until your finger (or thumb) has further settled into the trackpad. Past that the only thing you can do is change how you use it...

Thanks for the explanation... increasing FingerLow/FingerHigh to 20 made the situation more managable.. increasing to 30 made swiping the finger to move the cursor too hard...

---

### Post by ngativ on 2012-02-23
I am having a hard time using the tap to drag feature, in Dolphin you use just one tap to open a folder or file, but dragging is impossible, the double tap just triggers the single tap before i can even drag anything.

Is there any way to tell the driver to wait if i am attempting to do a double tap and drag gesture before to trigger the single tap click?

---

### Post by Quicksand on 2012-02-27
> **ngativ said:**
> I am having a hard time using the tap to drag feature, in Dolphin you use just one tap to open a folder or file, but dragging is impossible, the double tap just triggers the single tap before i can even drag anything.

Is there any way to tell the driver to wait if i am attempting to do a double tap and drag gesture before to trigger the single tap click?

Known issue, I'm afraid.  See [here]("https://github.com/BlueDragonX/xf86-input-mtrack/issues/19").

That's my bug report from way-back-when.  I still use mtrack, though, because in all other ways it's really good.  I have adjusted to pushing down on the trackpad to actuate the hardware button for dragging, but with luck someday I shall be free to tap-drag again!

---

### Post by blackjay0419 on 2012-02-28
@bluedragonx

The "www.dev.fatedmariner.org/" where stores the deb for dispad driver is going down. 
I cannot download the deb for dispad anymore.
Can you please fix it or upload deb to other places?

Thanks

---

### Post by machsna on 2012-03-01
> **BlueDragonX said:**
> ```
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack
git branch dev
git checkout dev
./autoreconf --install --force
./configure && make && sudo make install

```

I am stuck at:
```
bash: ./autoreconf: No such file or directory
```

Same happens with ./configure

Where'd I go wrong?

Also, the site with the [Ubuntu mtrack binaries](http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/) seems to be down, and also, I cannot find any mtrack in the alternative repositories mentioned in [“apt-get” not finding packages on Terminal](http://askubuntu.com/questions/104587/apt-get-not-finding-packages-on-terminal). So basically, my poor Linux wits are all exhausted and I am unable to get mtrack. Any other ideas or help?

---

### Post by cubuspl42 on 2012-03-08
I have exacly the same problem, ubuntu binaries are unavailable. It makes popular MacBook Air script "post-install-oneiric.sh" unusable :(

---

### Post by cubuspl42 on 2012-03-08
> **machsna said:**
> I am stuck at:
```
bash: ./autoreconf: No such file or directory
```Same happens with ./configure

Where'd I go wrong?


Tool named autoreconf is not a script, it's a GNU utility. You also need a few dependencies.
Correct usage:
```

sudo aptitude install autoconf libtool libmtdev-dev xserver-xorg-dev xutils-dev
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack/
autoreconf --install --force
./configure --prefix=/usr
make
sudo make install

```

I'm not certainly sure about "--force" part, you can experiment with that.

By the way:
I modified "post-install-oneiric.sh" for MacBook Air 2011 (4,X) and it works now (it downloads stuff from git, like above). Link:
<deleted>

---

### Post by dfacto on 2012-03-08
> **cubuspl42 said:**
> Tool named autoreconf is not a script, it's a GNU utility. You also need a few dependencies.
Correct usage:
```

sudo aptitude install autoconf libtool libmtdev-dev xserver-xorg-dev xutils-dev
git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
cd xf86-input-mtrack/
autoreconf --install --force
./configure --prefix=/usr
make
sudo make install

```

I'm not certainly sure about "--force" part, you can experiment with that.

By the way:
I modified "post-install-oneiric.sh" for MacBook Air 2011 (4,X) and it works now (it downloads stuff from git, like above). Link:
[http://dl.dropbox.com/u/23195601/post-install-oneiric-cbs.sh](http://dl.dropbox.com/u/23195601/post-install-oneiric-cbs.sh)

What on earth are you talking about? You simply copied the code from my script
[http://almostsure.com/mba42/post-install-oneiric.sh](http://almostsure.com/mba42/post-install-oneiric.sh)

Moreover, you did it stupidly--all you had to do was change the "false" to "true" in the blocks you edited.  Next time, just contact me instead of polluting the web with bastardized versions.

That's why I put my contact info in the header.  Needlessly forking code makes it very hard for novice users to know what is the correct/most up-to-date version to use.

---

### Post by Splooshie123 on 2012-03-09
On my mbp 6,2 running 64bit lucid, I can install it and Xorg logs show it getting loaded and unloaded and then i get no trackpad functionality at all.

I remember seeing that mtrack will be in the repositories in Precise (next LTS).

I'll just wait until then.

---

### Post by NickSH on 2012-03-12
Hello,
I have a noob question (only been using linux for about a month).  I just installed Lubuntu 11.10 on my macbook air 4,1.  After doing this, I used the post-install-oneiric.sh script to get drivers and configure things.  This script installed mtrack. When I restarted and logged back in, I no longer need to use 'nomodeset' in the boot loader.  However, my trackpad is completely disabled now...I can't move the curser at all.

Has anyone else had this problem or does anyone know how to fix it?  I will have to complete any fixes at the command line as that is the only thing I can access right now (no mouse!). I did check the file /etc/X11/xorg.conf (as described in a previous post) and found to to be identical to what was recommended to turn on mtrack. 

Any help would be greatly appreciated.

Thanks,
Nick

---

### Post by WarBearFace on 2012-03-16
I'm kind of new to linux and I'm running into some walls here. I finally figured out I needed to run autoreconf -i and that went through perfectly. Now however when I try to run ./configure it says no package xorg-server found. I'm running fedora 16 and have the latest version of xorg-x11-server-Xorg through yum. It is however 1.11 and it is not explicitly stated that it is supported. Can someone help me out? Do I need to run a lower version of xorg-server or am I just retarded and don't know what I'm doing? Either way a simple straightforward answer would be appreciated.

*Edit: Nevermind I figure it out almost 3 minutes after posting. I needed xorg-x11-server-devel.

---

### Post by litemotiv on 2012-03-16
@BlueDragonX, is the Coast branch ready for testing yet? I have tried it out with the following parameters:

```

Option "ScrollCoastEnable" "1"
Option "ScrollCoastEnableSpeed" "50"
Option "ScrollCoastDecelerate" "20"

```

But behaviour seems erratic, i do notice a bit of coasting but it is jumpy and unpredictable. I'm using a MacBook Air 4,2 / Chromium with smooth scrolling enabled for testing.

---

### Post by hypest on 2012-03-25
> **NickSH said:**
> ...However, my trackpad is completely disabled now...I can't move the curser at all.

Has anyone else had this problem or does anyone know how to fix it?

I'm having this exact issue too! No response from the touchpad. 

Even tried rerunning post-install-oneiric.sh selecting the second option ("2. synaptics + touchegg") but no luck...

---

### Post by cubuspl42 on 2012-03-28
Sry, dfacto, for editing your script, I deleted the link.

@hypest

Check if the driver installed correctly, coz I had the same problem and it didn't. BTW, using Firefox is also possible without mouse.

---

### Post by dfacto on 2012-03-28
> **cubuspl42 said:**
> Sry, dfacto, for editing your script, I deleted the link.

@hypest

Check if the driver installed correctly, coz I had the same problem and it didn't. BTW, using Firefox is also possible without mouse.

Editing == good.

Incorrectly editing then forking old version == bad.

---

### Post by dpb on 2012-04-12
Question 1:

Anyone else having a problem with the the mtrack driver on precise and not being able to reveal a hidden launcher?

I can hit the Super key to show it, but if I scroll to the left and push, nothing happens.

I've tried messing with the sensitivity, etc to no avail.

any thoughts?


Question 2:

Is there any hope of a GUI to configure this a bit more?  Even using the built-in trackpad gui would be a good start.

This driver is great, thanks for all the work by everyone invovled!

---

### Post by BlueDragonX on 2012-04-12
> **litemotiv said:**
> @BlueDragonX, is the Coast branch ready for testing yet?

No, it is not. The only stable branch is master. The dev branch is the working unstable branch. Nothing else is guaranteed to work.

---

### Post by fabietto1982 on 2012-04-12
> **hypest said:**
> I'm having this exact issue too! No response from the touchpad. 

Even tried rerunning post-install-oneiric.sh selecting the second option ("2. synaptics + touchegg") but no luck...

Very same issue here (MB Air 11", late 2011)... :(

---

### Post by Splooshie123 on 2012-04-17
EDIT: Nevermind. It seems that evdev was grabbing the device. Commented out the relevant sections in 10-evdev.conf and put my mtrack configuration in 09-mtrack.conf

Hello.
My mtrack configuration doesn't seem to affect my apple trackpad at all.
I can even disable the trackpad completely in the configuration and it still works, proving the configuration didn't do anything.

The Xorg.0.log file shows that mtrack loads without errors. I also have evdev and synaptics installed. They both generated configuration files in /usr/share/X11/xorg.conf.d. Maybe one of them is overriding the mtrack settings?

---

### Post by NickSH on 2012-04-30
Splooshie,

Anychance you could walk me through what you did.  I'm wondering if I'm having the same problem, as installing mtrack hasn't changed any functionality, however, I'm pretty sure it installed correctly, as someone walked me through building it with automake in a thread in the developers section.

I know that my /X11/xorg file has the has the mtrack configuration in it, so it seems like it should be working, according to posts. But I don't know what else I'm supposed to do to get it to work, as I'm very new to this.

Thanks,
Nick

---

### Post by Splooshie123 on 2012-05-10
Nick,

Could you post your X11 configuration?

---

### Post by Splooshie123 on 2012-05-13
Hello.

EDIT: I removed the coast branch version and reinstalled using apt-get and now it works. [COLOR=Red]THIS IS A BUG WITH THE COAST BRANCH.[/COLOR]

I compiled the coast branch from git so I could use the BottomEdge option. I use two fingers: one to click and one to move the cursor. I can't do this with the synaptics driver because that just results in a two-finger click (right click). I've got a macbook pro so there is no separate button.

As far as I can tell, BottomEdge works. When I try to move the cursor in that area, it won't move. But it still doesn't ignore my thumb when I try to click. I still get the right click menu. I think I have the same issue as this: [https://github.com/BlueDragonX/xf86-input-mtrack/issues/26](https://github.com/BlueDragonX/xf86-input-mtrack/issues/26)

This doesn't look like a problem with configuration because the same thing happens if I use the defaults (no extra configuration).

I also tried xf86-input-multitouch. Thumb detection works and it does ignore my thumb. I don't get accidental right clicks. Unfortunately, multitouch has tap to click which I just find annoying.

---

### Post by NickSH on 2012-05-15
Sorry...I've been offline for a while during finals week.  Have since reinstalled with 12.04 and trackpad appears to be working fine with the synaptics driver, so I think I'll just stick with that for now.
Thanks,
Nick

---

### Post by MiXor on 2012-05-16
> **unagimiyagi said:**
> Any documentation on how to compile using autoconf and automake for those who are not familiar with these tools?

PING! Reiterating the request! :)

---

### Post by tomm3h on 2012-06-10
Hi all,

Using a Macbook Air 4,2. I have 12.04 LTS installed, utilising mtrack. It's working a litle better than synaptics, but there's still one particularly annoying issue that I can't seem to tweak.

When I am using the track pad, I like to use two hands. One to move the cursor (right hand) and one to click the "left mouse button". It just seems natural. Clicking the touchpad with the same finger I use to move around usually results in the cursor 'slipping'. 

The problem is, if I [accidentally] rest my clicking finger on the lower part of the trackpad, it stops the cursor entirely. This same behaviour does not lock the cursor in OS X. Given that these devices are meant to encourage 'multiple touches', **I presume that both drivers are wrongly assuming this to be a two-finger touch, despite the distance between them.**

Can anyone think of a way to adjust this behaviour? I wonder if we need extra configuration options -- i.e. minimum/maximum distance between multiple fingers?

Please correct me if I'm missing something obvious in the [README]("https://raw.github.com/BlueDragonX/xf86-input-mtrack/master/README.md"). :)

Tom

---

### Post by joskapista on 2012-08-12
I've tried to download the driver as a DEB package from the link:

[http://www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu](http://www.dev.fatalmachine.org/xf86-input-mtrack/ubuntu)

It is not working. Do you know a where can I download it?

---

### Post by pbhedlund on 2012-08-12
> **joskapista said:**
> Do you know a where can I download it?

It's in the precise packages [http://packages.ubuntu.com/precise/xserver-xorg-input-mtrack](http://packages.ubuntu.com/precise/xserver-xorg-input-mtrack).

---

### Post by BlueDragonX on 2012-08-12
> **pbhedlund said:**
> It's in the precise packages [http://packages.ubuntu.com/precise/xserver-xorg-input-mtrack](http://packages.ubuntu.com/precise/xserver-xorg-input-mtrack).

You'll ave to compile it from source for now. My webserver's been down for a while and I haven't had time to set up a PPA.

---

### Post by joskapista on 2012-08-15
[http://packages.ubuntu.com/precise/xserver-xorg-input-mtrack](http://packages.ubuntu.com/precise/xserver-xorg-input-mtrack)

this link worked. thanks!

---

### Post by petersphilo on 2012-08-15
> **BlueDragonX said:**
> You'll ave to compile it from source for now. My webserver's been down for a while and I haven't had time to set up a PPA.


ok.. how do i do that again?
Sorry for the lame-itude of my lameness...

The instructions provided [here]("http://ubuntuforums.org/showthread.php?p=10744815&postcount=34") stop to function at 'make'

---

### Post by BlueDragonX on 2012-08-15
> **petersphilo said:**
> ok.. how do i do that again?
Sorry for the lame-itude of my lameness...

The instructions provided [here]("http://ubuntuforums.org/showthread.php?p=10744815&postcount=34") stop to function at 'make'

Posting your error would help. Otherwise all I can say is "try again".

---

### Post by hmaarrfk on 2012-10-01
Hi all,

This is a long shot, but did anybody have any luck installing mtrack on Fedora 17 (x64 if that makes a difference).

I ran
```

libtoolize
aclocal
autoconf
automake --add-missing --copy
./configure
make
sudo make install

```

I see mtrack_drv.la  mtrack_drv.s in /usr/local/lib/xorg/modules/input but when I put the minimal configuration in my /etc/X11/xorg.conf.d/ file, my Trackpad just stops working.

I'm thinking X11 isn't looking in the right directories to find the mtrack driver. Any clues on how to make sure it does?

---

### Post by BlueDragonX on 2012-10-01
> **hmaarrfk said:**
> This is a long shot, but did anybody have any luck installing mtrack on Fedora 17 (x64 if that makes a difference).


You need to post your Xorg.0.log otherwise we're just guessing as to what the issue is.

---

### Post by hmaarrfk on 2012-10-03
So sorry for not including the file.


Thanks for the fast reply, just haven't had time to tweak my computer since.

---

### Post by BlueDragonX on 2012-10-03
Your logfiles indicate that ModulePath is set to /usr/lib64/xorg/modules. You'll need to try again and set the appropriate module path in configure.

---

### Post by rcrath on 2012-10-04
Tried autreconf-i -f and the whole toolchain, but get errors on both.  I have been unable to figure out what to do to fix it.  Any help appreciated.

```
[xf86-input-mtrack]$libtoolize && aclocal && autoconf && automake --add-missing --copy
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: You should add the contents of `m4/libtool.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltoptions.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltsugar.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltversion.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/lt~obsolete.m4' to `aclocal.m4'.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
/usr/local/share/aclocal/xorg-macros.m4:1780: XORG_INSTALL is expanded from...
/usr/local/share/aclocal/xorg-macros.m4:1760: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
aclocal.m4:1802: XORG_INSTALL is expanded from...
aclocal.m4:1782: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
aclocal.m4:1802: XORG_INSTALL is expanded from...
aclocal.m4:1782: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
Makefile.am:10: error: Libtool library used but 'LIBTOOL' is undefined
Makefile.am:10:   The usual way to define 'LIBTOOL' is to add 'LT_INIT'
Makefile.am:10:   to 'configure.ac' and run 'aclocal' and 'autoconf' again.
Makefile.am:10:   If 'LT_INIT' is in 'configure.ac', make sure
Makefile.am:10:   its definition is in aclocal's search path.
[xf86-input-mtrack]$autoreconf --install --force
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
/usr/local/share/aclocal/xorg-macros.m4:1780: XORG_INSTALL is expanded from...
/usr/local/share/aclocal/xorg-macros.m4:1760: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
aclocal.m4:1802: XORG_INSTALL is expanded from...
aclocal.m4:1782: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:24: warning: PKG_PROG_PKG_CONFIG is m4_require'd but not m4_defun'd
aclocal.m4:1802: XORG_INSTALL is expanded from...
aclocal.m4:1782: XORG_DEFAULT_OPTIONS is expanded from...
configure.ac:24: the top level
configure.ac:17: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:18: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/local/bin/autoconf failed with exit status: 1
[xf86-input-mtrack]$

```

---

### Post by hmaarrfk on 2012-10-04
> **BlueDragonX said:**
> Your logfiles indicate that ModulePath is set to /usr/lib64/xorg/modules. You'll need to try again and set the appropriate module path in configure.

Thanks BlueDragonX,

That worked.

For future reference, you need to run configure with (on 64bit fedora):
```
./configure --with-xorg-module-dir=/usr/lib64/xorg/modules/
```

---

### Post by BlueDragonX on 2012-10-08
> **rcrath said:**
> Tried autreconf-i -f and the whole toolchain, but get errors on both.  I have been unable to figure out what to do to fix it.  Any help appreciated.


You're missing libtool, it needs to be installed. Googling the error would help in this context.

---

### Post by wiz561 on 2012-11-27
This is a long shot, but when I try to make, I get an error...  

I'm on Ubuntu 12.04 LTS and did the following...

$ libtoolize && aclocal && autoconf && automake --add-missing --copy
$ make

```
$ make
make  all-am
make[1]: Entering directory `/home/wisniewski/mtrack/xf86-input-mtrack'
  CC     capabilities.lo
  CC     gestures.lo
  CC     hwstate.lo
  CC     mconfig.lo
  CC     mtouch.lo
  CC     mtstate.lo
  CC     trig.lo
  CC     mtrack.lo
  CC     mprops.lo
  CCLD   mtrack_drv.la
  CC     mtrack_test-capabilities.o
  CC     mtrack_test-gestures.o
  CC     mtrack_test-hwstate.o
  CC     mtrack_test-mconfig.o
  CC     mtrack_test-mtouch.o
  CC     mtrack_test-mtstate.o
  CC     mtrack_test-trig.o
  CC     mtrack_test-mtrack-test.o
./tools/mtrack-test.c:39:22: error: unknown type name ‘XF86OptionPtr’
./tools/mtrack-test.c:44:23: error: unknown type name ‘XF86OptionPtr’
./tools/mtrack-test.c:49:26: error: unknown type name ‘XF86OptionPtr’
make[1]: *** [mtrack_test-mtrack-test.o] Error 1
make[1]: Leaving directory `/home/wisniewski/mtrack/xf86-input-mtrack'
make: *** [all] Error 2
```

---

### Post by BlueDragonX on 2012-11-27
> **wiz561 said:**
> This is a long shot, but when I try to make, I get an error...  

I'm on Ubuntu 12.04 LTS and did the following...

$ libtoolize && aclocal && autoconf && automake --add-missing --copy
$ make


You need to install the X development dependencies.

---

### Post by wiz561 on 2012-11-27
Thanks for the response.  I believe I did.  Here's what I have...

```
$ dpkg -l | grep -i xorg | grep -i dev
ii  xorg-dev                               1:7.6+12ubuntu1                         X.Org X Window System development libraries
ii  xserver-xorg-dev                       2:1.11.4-0ubuntu10.8                    Xorg X server - development files
ii  xserver-xorg-input-evdev               1:2.7.0-0ubuntu1.2                      X.Org X server -- evdev input driver
ii  xserver-xorg-video-fbdev               1:0.4.2-4ubuntu2                        X.Org X server -- fbdev display driver
```


I got it installed using the deb through apt-get and it seems to be working great.  The git one didn't want to install, so who knows...  It would be nice to install the latest and greatest though.


Thanks!

---

