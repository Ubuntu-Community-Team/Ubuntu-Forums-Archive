---
title: "left click&amp;hold instead of right click"
date: 2006-11-15
forum: Apple PPC Users
---

### Post by frafu on 2006-11-15
Hello, 




There are users that can only use a single mouse button: for example many Macintosh computers have been sold with a mouse with a single button. 

These users have to use a workaround to access the contextual menu of items, because it is normally accessed with a click on the right mouse button; which they do not have. 



In the older MacOS 9, there was a system extension, that made the contextual menu appear with a click and hold of the single mouse button; in other words with a left click&hold. 
In Firefox for MacOSX, a left click&hold makes the contextual menu appear. (In Firefox 2 for MacOSX, it is turned off by default, but the relevant setting can be found by typing 'about:config' in the addressbar of Firefox.) 



Would it not be useful if Ubuntu users also had the possibility to make the contextual menu appear with a left click&hold; and this for every item that has a contextual menu; not only in Firefox.

To distinguish the left click&hold from the click&drag, the system could proceed like this: if after the mousedown, the mouse does not move for 1.5 seconds, then open the contextual menu; if it moves before 1.5 seconds have elapsed, go for a click&drag. 

Of course, the user should have the possibility to deactivate this function for the left click&hold in the preferences; moreover, the preferences should also allow to customize the time (1.5 seconds) to wait before showing the contextual menu. 



In launchpad, this function is already part of an accessibility feature: 
[MouseTweak feature]("https://features.launchpad.net/distros/ubuntu/+spec/mouse-tweaks")
[Corresponding wikipage]("https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks?highlight=%28tweaks%29")



I am grateful for any comment on such a left click&hold to make the contextual menu appear; particularly whether 
- it would be welcome 
- there could be a reason for not implementing it
- what would be necessary to implement it; maybe also specifying it in the wikipage given above. 



Any help making such a left click&hold become a reality will be appreciated. 



Have a nice day. 


frafu

---

### Post by HandyMac on 2006-11-15
Can't really respond to your query as I'm new to Linux (just installed Ubuntu on my iBook, haven't used it yet), but thought I'd let you know (in case you don't) that there're a couple of utilities to do this (click & hold to invoke contextual menu) in OS X; maybe they'll help?

[One Finger Snap]("http://www.macupdate.com/info.php/id/18941")
[Look Mom, No Hands]("http://www.macupdate.com/info.php/id/1103")

Haven't tried either myself; I'm content using the control key. But I gather there's no way to invoke contextual menus in Ubuntu on a PowerBook (trackpad with single button), then? Actually, I seldom use the button either, as I have the trackpad set for tapping -- is there no way to do this un Ubuntu?

---

### Post by frafu on 2006-11-16
Hello,

Thanks for the info about 1 Finger Snap; I did not know it. 

Concerning the right click with 1 button mice in ubuntu: as far as I could find in the documentation and in the forums and wiki: 
- F12 will open the contextual menu of the item under the pointer
- F11 is for the middle button (3 button mouse) 

Unfortunately, I can't test it with my setup: I am running Ubuntu on a headless celeronbox, that is remotely controlled via a Mac. 

frafu

---

### Post by Brian Smith on 2006-11-16
> **frafu said:**
> Hello,

Thanks for the info about 1 Finger Snap; I did not know it. 

Concerning the right click with 1 button mice in ubuntu: as far as I could find in the documentation and in the forums and wiki: 
- F12 will open the contextual menu of the item under the pointer
- F11 is for the middle button (3 button mouse) 

Unfortunately, I can't test it with my setup: I am running Ubuntu on a headless celeronbox, that is remotely controlled via a Mac. 

frafu

I've just now verified both of these functions on my G3 running Xubuntu6.06.  It's an excellent coincidence that I have been searching for the way to activate the contextual menu this week.  Until now I had only found that using control-<mouse click> was opening a menu on the panels.

Thanks!

---

### Post by frafu on 2006-11-17
> **Brian Smith said:**
> I've just now verified both of these functions on my G3 running Xubuntu6.06.  It's an excellent coincidence that I have been searching for the way to activate the contextual menu this week.  Until now I had only found that using control-<mouse click> was opening a menu on the panels.


Yes, it is not very intuitive for a macuser to open the contextual menu without clicking the mouse. Macusers tend rather to look for a modifier+mouseclick.

---

### Post by frafu on 2007-01-14
Hello, 

I have opened a thread about the mousetweaks (left click&hold and other mouse functions) in the accessibility forum; here it is: 
[http://ubuntuforums.org/showthread.php?p=2012732](http://ubuntuforums.org/showthread.php?p=2012732)

Any help or comment is welcome. 

Have a nice day.

---

### Post by 3rdalbum on 2007-01-14
I just bought a USB mouse with two buttons and a scroll-wheel - it works with all three buttons on Ubuntu, and it also works as a single-button mouse on OS 9.

---

### Post by frafu on 2007-07-16
Hello, 

An utility to open the contextual menu with a left click&hold is under development. It is called mousetweaks and the contextual menu function can be activated under the 'delay click' tab. 

You can find the current version in [this thread]("http://ubuntuforums.org/showthread.php?t=494037"). But you have to compile it yourself; I am not able to build a debian package for this architecture, as I don't have a Mac with Ubuntu running on it. 

Any feedback will be appreciated. 

Francesco

---

