---
title: "newbie can't get Wings3d to work in Ubuntu"
date: 2008-05-17
forum: Art &amp; Design
---

### Post by shelbyvision on 2008-05-17
I'd like to try using wings in Ubuntu (Gutsy), and I downloaded and installed the version on the repository, 0.98.38. When I open it, the viewport is totally black, and nothing I do to it changes that. I read in the Ubuntu Forum somewhere that someone had better luck with a newer version. Newer versions are only available through sourceforge. I downloaded and installed versions 0.99.00b, 0.99.01, and 0.99.02, and all of them behave the same way, blank, black. Since apparently others have gotten Wings3d to work on Ubuntu, It seems to me that there ought to be something I could tweak that would fix this problem. Any ideas out there?
Steve

---

### Post by Tomatz on 2008-05-17
Are you running compiz (desktop effects)?

If you are, disable it in *system, preferences, appearence*

Then try ;)

---

### Post by shelbyvision on 2008-05-17
I was so hoping that was the solution. So simple. I went to System/Preferences/Appearance/Visual Effects, and selected "None". Unfortunately, it didn't change anything.
Steve

---

### Post by Tomatz on 2008-05-17
Fount this:

> On all platforms but Mac OS X, Wings clears the back buffer immediately after swapping (because that is somewhat faster). That is what Björn calls "early clear". On Mac OS X, it seems that the back buffer can be used by the OS, which resulted in a blank Wings window. When the option is turned off, Wings does a "late clear", i.e. it will clear the back buffer immediately before starting to draw in it.

On this page:

[http://en.wikibooks.org/wiki/Wings_3D:_User_Manual/The_Edit_Menu](http://en.wikibooks.org/wiki/Wings_3D:_User_Manual/The_Edit_Menu)

Hope it helps ;)

---

### Post by shelbyvision on 2008-05-17
Thanks for pointing that out. That could very well be the problem, but the instructions in the manual say to go to Edit/Compatibility, and it even shows a picture of the Compatibility menu, but for some reason, there is no "Compatibility" menu under Edit, or anywhere else. I tried it on all four versions that I have installed, and it's not there. 
Steve

---

### Post by Tomatz on 2008-05-17
What graphics card are you using?

---

### Post by shelbyvision on 2008-05-17
> **Tomatz said:**
> What graphics card are you using?

ATI Radeon 7000

---

### Post by Xfcn on 2008-05-17
Have you installed your ATI's proprietary drivers?

*EDIT* Woah, I hadn't tried the 3D packages on this distro yet! Man, this blows and is NOT working right at all!

Weird. Good thing I'm not much of a 3D nut, eh?

---

### Post by shelbyvision on 2008-05-17
[QUOTE=Xfcn;4982498]Have you installed your ATI's proprietary drivers?

Apparently that video card is too old. It's not listed on ATI's driver download site, and the Ubuntu documentation agrees.
Steve

---

### Post by Tomatz on 2008-05-18
> **shelbyvision said:**
> ATI Radeon 7000

You may have to install the official ati drivers from ati's site. You can do this with envy which automates the process:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Using envy you run the risk of breaking your system so _[COLOR="Red"]use it at your own risk[/COLOR]_.

;)

---

### Post by shelbyvision on 2008-05-18
> **Tomatz said:**
> You may have to install the official ati drivers from ati's site. You can do this with envy which automates the process:
Tomatz,
As I tried to say in my previous post, ATI's official site does not list my video card (ATI 7000) for drivers. All the cards on their list are much newer. Perhaps some drivers are backward-compatible?
Steve

---

### Post by Xfcn on 2008-05-18
I had installed drivers using ATI's method. After updating, apparently everything broke, so I uninstalled the drivers via the Restricted Driver Manager, then reinstalled after a restart. Works flawlessly now, for me.

---

### Post by Tomatz on 2008-05-18
> **shelbyvision said:**
> Tomatz,
As I tried to say in my previous post, ATI's official site does not list my video card (ATI 7000) for drivers. All the cards on their list are much newer. Perhaps some drivers are backward-compatible?
Steve


I think envy allows you to automatically install the ati legacy (old) drivers. It definatly does this for the nvidia drivers.

There would be no harm in installing envy. Then you could run it (from the applications menu). Then in envy select **"install the ati driver manually"**. Then check the **version numbers** of the drivers in google to see what ati card they are for.

---

### Post by shelbyvision on 2008-05-18
OK, I installed Envy, and tried it out. On the menu there is no information about which drivers are "legacy" or not. I tried auto first, and that failed, so I tried manual install and it gave me three choices, version 8-3, 8.40.4, or 8.28.8. It had 8-3 already selected, so I decided to try that. It went through the installation process successfully. Now I can't  open Wings 3d at all, but it still shows the terminal process, and at the bottom it says: 
Failed to find any suitable OpenGL mode.
Make sure that OpenGL drivers are installed.

---

### Post by Tomatz on 2008-05-18
> **shelbyvision said:**
> OK, I installed Envy, and tried it out. On the menu there is no information about which drivers are "legacy" or not. I tried auto first, and that failed, so I tried manual install and it gave me three choices, version 8-3, 8.40.4, or 8.28.8. It had 8-3 already selected, so I decided to try that. It went through the installation process successfully. Now I can't  open Wings 3d at all, but it still shows the terminal process, and at the bottom it says: 
Failed to find any suitable OpenGL mode.
Make sure that OpenGL drivers are installed.


Open synaptic and completely remove all traces of ati (by searching for ati) r click on the packages and **"mark for complete removal"**. Then try envy again.

I think you still have the old drivers (or part of) installed and these are conflicting with the new ones.

If you bork and are presented with the cli (black screen of death) type **sudo dpkg-reconfigure xserver-xorg** *(write that down)* ;)

---

### Post by shelbyvision on 2008-05-19
That just made things worse.
Everything I read about the subject says that those proprietary drivers won't work for anything older than 8500 (mine is 7000, smaller number, older card). I think that unless I can find documentation that shows a certain driver will work for my card, I'll leave well enough alone.
Steve

---

### Post by Tomatz on 2008-05-19
> **shelbyvision said:**
> That just made things worse.
Everything I read about the subject says that those proprietary drivers won't work for anything older than 8500 (mine is 7000, smaller number, older card). I think that unless I can find documentation that shows a certain driver will work for my card, I'll leave well enough alone.
Steve


Sorry that didn't help you.

The best thing to do is get a second hand nvidia card        (fx5600 agp and up) if you are strapped for cash. Nvidia is very well supported under linux. Try to get one on ebay or somthing then do a fresh install.

ATI is a pain in linux ask anyone ;)

---

### Post by shelbyvision on 2008-05-19
Well, this computer has no AGP slot. It's a bottom of the line Gateway celeron. I'm thinking that if I want to do 3d in Linux, I'll spend the money to get my HP laptop fixed, which needs a new hard drive and cooling fan unit, but it's a much better computer.
Steve

---

