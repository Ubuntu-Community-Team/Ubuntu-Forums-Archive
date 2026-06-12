---
title: "matrox millennium II - Better than 1024x768 possible?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-03-30
On my old PC I have a 4MB Matrox Millennium II card.

I'm pretty sure, under windows I can get a res higher than 1024x768 but I've just installed Xubuntu and deleted that, then installed Ubuntu, and both only let me have 1024x768 at 85hz as a maximum screen res.

I'd like 1280x1024 and doing a google search, it sound like the card will go up to 1920 x 1200 when pushed (presumably at a lower colour depth)

So, is there anything I can do, to get past 1024x768?

---

### Post by smurphy_it on 2008-03-30
If both your monitor and your video card can support those rates, you should be able to add those modes in.

You would have to edit your xorg.conf file in order to achieve this.

In a terminal you could type ***sudo gedit /etc/X11/xorg.conf***
That above command is case sensitive.

Once you are viewing the xorg file in gedit, scroll down to the device section dealing with your screens.

Look for a line that says:

Device "Screen"
Within  a couple of lines of that you should see a [COLOR="SandyBrown"]modes "1024x768"[/COLOR]

You have to change that to read [COLOR="Red"]modes "1280x1024" "1024x768"[/COLOR]
Do this for each area of Screens.  As you may have multiple lines for each *DefaultDepth*

Afterwards, save what you are doing, logout, then while at the login screen hit Ctrl+Alt+BckSpce to reload X-Windows.

That will hopefully give you the option.

You can confirm this by going to system, administration, screens and graphics

---

