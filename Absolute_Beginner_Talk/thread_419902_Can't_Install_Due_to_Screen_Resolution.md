---
title: "Can't Install Due to Screen Resolution"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by brockk on 2007-04-23
I am unable to install Feisty do to my maximum resolution only being 800x600.  Here are the specifics: 

My video card is a NVIDIA GeForce4 MX Integrated.  The max resolution is 800x600, and I figured that this was a driver issue that I could deal with after the installation, but I am unable to complete the initial installation due to the fact that the Cancel, Back, and Forward buttons are all off the bottom of the screen.  I tried tabbing over and making my best guess through the installation, but obviously this didn't work too well.  

Any thoughts as to what I can do to get through the install?  Is there some parameter that I can tweak in the live environment to increase the resolution.  

Thanks!

---

### Post by taurus on 2007-04-23
You can always try the alternate CD.  It's a text base installer but real easy to follow.

---

### Post by phidia on 2007-04-23
Try the alternate cd image to install with instead of the desktop/livecd.

---

### Post by paker on 2007-04-23
I guess it was an oversight. No reason to download another version. I just assumed NEXT would be the default choice, and hit ENTER. When I was taken back to previous screen, I hit TAB and ENTER. You can pretty much figure it out after a few tries.

---

### Post by brockk on 2007-04-23
Thanks, I'll play around with it, and let you know.

---

### Post by silverglade00 on 2007-04-23
If you hold down the Alt key, you can drag/move the window around to find the buttons.

---

### Post by oilchangeguy on 2007-04-23
if your max resolution is only 800x600, what are the specs of your computer? because you may not be able to run version 7.04.

---

### Post by owyn on 2007-04-23
The ALT tip is a good one to get past the installer.

If you want to actually use the LiveCD for other tasks, then try

```

sudo dpkg-reconfigure xserver-xorg

```

and take all the defaults with the exception of screen resolutions required. Check that the resolution you want is going to be supported when prompted (you may need to scroll down the list of available resolutions).  After xorg is reconfigured you will need to restart X.

```

Control+Alt+Backspace

```

This 800x600 only problem seems to be showing up with a lot of video cards. Problem with auto-dectect in LiveCD.

---

### Post by rumli on 2007-04-23
I had the same problem.  I had to drag the gnome panels at the top and bottom of my screen to the left and right of my screen to make them vertical.  Then I could just about see the buttons at the bottom.

This is a really annoying bug...

---

### Post by brockk on 2007-04-23
> **oilchangeguy said:**
> if your max resolution is only 800x600, what are the specs of your computer? because you may not be able to run version 7.04.

I run an AMD Athlon 3200 processor, with 1GB of Ram, and on board Nvidia video.  I don't believe this is an issue, as I have installed it without issue in a virtual machine on the same PC.

---

### Post by owyn on 2007-04-23
> **rumli said:**
> This is a really annoying bug...

Yep. Actually two bugs.

1) Some video cards are configured to max or only 800x600
2) Some standard Ubuntu dialogs require > 800x600. 

The installer dialogs are a particularly nasty case of built for > 800x600. Problems using the installer can stop new users at the starting gate.

---

