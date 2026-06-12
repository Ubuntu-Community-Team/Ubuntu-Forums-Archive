---
title: "Updating from FF to GG on a C2D MacBook Pro"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by GeneralSunTzu on 2007-10-22
I wonder if anybody has updated, rather than installed from scratch, from FF to GG on a C2D MacBook Pro (2.33 GHz, not the SantaRosa).
I have a dual-boot MBP, on which I successfully installed Feisty Fawn 64-bit besides Mac OS X 10.4.10, but I haven't used Ubuntu in a long while because there seemed to be no way of easily getting WPA2 to work (Atheros chip set), in spite of the various voodoo recipes available here.
Now that perhaps GG has fixed this matter, I wonder if any good soul could tell me whether I need to re-install from scratch or can move up from FF to GG, and finally see whether I get WPA2 to work...

Thank you.

---

### Post by mcdull2k on 2007-10-22
I am using C2D MBP 2.16G ATI1600. AFAIK, the wireless is still not working with stock driver.  Anyway you need to recompile the driver and load the module.

One major issue that may stop you from upgrading is that suspend will NOT work with GG if you use fglrx driver.

---

### Post by cyberdork33 on 2007-10-22
> **GeneralSunTzu said:**
> I wonder if anybody has updated, rather than installed from scratch, from FF to GG on a C2D MacBook Pro (2.33 GHz, not the SantaRosa).
I have a dual-boot MBP, on which I successfully installed Feisty Fawn 64-bit besides Mac OS X 10.4.10, but I haven't used Ubuntu in a long while because there seemed to be no way of easily getting WPA2 to work (Atheros chip set), in spite of the various voodoo recipes available here.
Now that perhaps GG has fixed this matter, I wonder if any good soul could tell me whether I need to re-install from scratch or can move up from FF to GG, and finally see whether I get WPA2 to work...

Thank you.
If there is nothing to keep (I am assuming that there isn't since you don't use it...), then why not just do a complete reinstall?

---

### Post by GeneralSunTzu on 2007-10-24
> **cyberdork33 said:**
> If there is nothing to keep (I am assuming that there isn't since you don't use it...), then why not just do a complete reinstall?

Thank you.
Not a bad idea. That's what I did already.
List of the screwups so far:

- trackpad craps out as usual (difficult to instal the synaptics driver with your cursor moving at random and selecting random screen areas of its own will)
- ATI driver requiring again some careful exotic massaging (so far I managed only to get a totally blank screen, when carefully editing xorg.conf, though the Live CD works)
- keyboard non-existent in the repertoire (it is a US MacBook Pro ordinary QWERTY keyboard, not a bleeding Sanscrit one...)
- typefaces used are outright pathetic, even when compared to FF (already hardly a design masterpiece...)

I am rather underwhelmed...
Oh goodness, will I have to wait for Zany Zoolie Ubuntu, before they fix basic stuff like this?
And I haven't even begun to look at the WiFi, yet.
Also, I do not need plain "wireless". 
I would like to have WPA2 Personal, otherwise I cannot work on my own home network...

Accept any suggestions which do not include more than five links to quack obsolete recipes or fifty lines of "explanations" which explain nothing...

---

### Post by willnight on 2007-10-24
"...will I have to wait for Zany Zoolie Ubuntu..."

:lolflag:

awesome! made my afternoon. thx

---

### Post by cyberdork33 on 2007-10-24
> **GeneralSunTzu said:**
> Thank you.
Not a bad idea. That's what I did already.
List of the screwups so far:

- trackpad craps out as usual (difficult to instal the synaptics driver with your cursor moving at random and selecting random screen areas of its own will)
- ATI driver requiring again some careful exotic massaging (so far I managed only to get a totally blank screen, when carefully editing xorg.conf, though the Live CD works)
- keyboard non-existent in the repertoire (it is a US MacBook Pro ordinary QWERTY keyboard, not a bleeding Sanscrit one...)
- typefaces used are outright pathetic, even when compared to FF (already hardly a design masterpiece...)

I am rather underwhelmed...
Oh goodness, will I have to wait for Zany Zoolie Ubuntu, before they fix basic stuff like this?
And I haven't even begun to look at the WiFi, yet.
Also, I do not need plain "wireless". 
I would like to have WPA2 Personal, otherwise I cannot work on my own home network...

Accept any suggestions which do not include more than five links to quack obsolete recipes or fifty lines of "explanations" which explain nothing...
Ubuntu is obviously not for you.

Don't ask for help if you don't really want it.

---

### Post by GeneralSunTzu on 2007-10-25
> **cyberdork33 said:**
> Ubuntu is obviously not for you.

Don't ask for help if you don't really want it.

Tad nervous, aren't you?
I am grateful for any help I can receive, but I already lived through this experience with Feisty Fawn, where essentially many folks were very willing to help, some having indeed useful information to tell, others not.
Now, if I am asked something, I will only reply if I have useful information to supply, not just to whip up some electrons.
That's all I was saying.
Anyway, I am still looking for answers to my issues, listed above.
Should I get any, I promise I will write a hundred times: "I will be more patient with people who want to help without having much to say".
You might consider writing ten times" I will not be judgmental without hearing the poor b****d [i.e. me] out"...
For positive zen examples, read posts by ronocdh, to whom I owe much of what I glimpsed on Ubuntu FF, which was not a particularly brilliant release.

And now, back to rowing, trying de-install the synaptics driver, which does not work on GG (or else I do not know how to configure it properly, before it acts up.)...

Cheers from Europe, buddy!:)

---

### Post by cyberdork33 on 2007-10-25
> **GeneralSunTzu said:**
> Accept any suggestions which do not include more than five links to quack obsolete recipes or fifty lines of "explanations" which explain nothing...

You are putting conditions on your "help" that you obviously realize will not be met, so I say again, if you don't really want help, then don't ask for it. If you want an OS that just works on your Mac (which is what it sounds like), use the OS that was *designed* for it; likely Ubuntu is not likely for you. This is all I am trying to say. I don't know that nervousness has anything to do with it.

Linux is some hacked up software that was altered enough to get it to run on your Mac... Unfortunately, your wishlist for Ubuntu are not neccessarily the top priority for the distro. If you are willing to work a bit to get what you want, then I will be glad to help where I can, otherwise, forget it.

---

### Post by cyberdork33 on 2007-10-25
> **GeneralSunTzu said:**
> - trackpad craps out as usual (difficult to instal the synaptics driver with your cursor moving at random and selecting random screen areas of its own will)
I am not entirely sure what you mean since synaptics is the driver included with Ubuntu which is loaded by default, there should be no 'install' needed. 
I am aware that there are some issue with erratic behavior of the trackpad. I do not know anything specific to help you with there since I have no first-hand experience in this area.
> - ATI driver requiring again some careful exotic massaging (so far I managed only to get a totally blank screen, when carefully editing xorg.conf, though the Live CD works)Again, I don't really know what you mean here. If your system started initially, you should just check the box to install fglrx in the restricted drivers manager (which would have appeared on your taskbar, but can likely now be found in the menus. System > Administration
> - keyboard non-existent in the repertoire (it is a US MacBook Pro ordinary QWERTY keyboard, not a bleeding Sanscrit one...)The normal US keyboard layout should be fine. There are also several Mac/Apple choices during install. You can change your choices in System > Preferences > Keyboard
> - typefaces used are outright pathetic, even when compared to FF (already hardly a design masterpiece...)In System > Preferences > Appearance, you can attempt to alter the look of fonts on your system to your heart's delight.

> I am rather underwhelmed...
Oh goodness, will I have to wait for Zany Zoolie Ubuntu, before they fix basic stuff like this? Sorry

> And I haven't even begun to look at the WiFi, yet.
Also, I do not need plain "wireless". 
I would like to have WPA2 Personal, otherwise I cannot work on my own home network... You will likely need to compile madwifi drivers. (I would check that is not working already though. Welcome to a closed platform. There are several threads on this already.
Here is a good one: 
[http://ubuntuforums.org/showthread.php?t=587828](http://ubuntuforums.org/showthread.php?t=587828)
I know it says Santa Rosa, but it the same for you.

PS, WPA2 should have been working in Feisty the same as it does in Gutsy.

> Accept any suggestions which do not include more than five links to quack obsolete recipes or fifty lines of "explanations" which explain nothing...You get what you get, take it or leave it.

---

