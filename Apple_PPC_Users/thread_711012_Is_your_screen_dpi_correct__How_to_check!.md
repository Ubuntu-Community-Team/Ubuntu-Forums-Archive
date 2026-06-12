---
title: "Is your screen dpi correct?  How to check!"
date: 2008-02-29
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-29
Is Xorg calculating the proper screen-dpi for your monitor?  I think for many of us it may not be, and that **we could be using sub-optimal DPI settings**!

Dirk and I got into a related discussion and this came up so I wanted to give it it's own thread since this may be more universal than I thought.

Normally Xorg is supposed to figure out what the optimal dpi settings are for your monitor.  It is based on the following in this order:

1) What you issue at the commandline, like startx -- -dpi 96

2) Xorg will calculate the proper dpi from your "DisplaySize" setting in the MONITOR section of xorg.conf.  I have never seen this on ppc!  I have only seen a display setting in the SCREEN section, but the dpi isn't calculated from that.

3) Xorg will take what it gets from DDC probing.

4) If all that fails, your dpi will be dropped back to a very low default of 75.

How to check what Xorg is currently using (rightly or wrongly):

```
grep DPI /var/log/Xorg.0.log
```

How to check what your dpi **should be**:

```
xdpyinfo | grep -b1 dot
```

In my G5 iMac, which has a 20" screen, the resolution is 1680x1050 and the dpi should be 100

```
bg@ubuntu:~$ xdpyinfo | grep -B1 dot
  dimensions:    1680x1050 pixels (427x267 millimeters)
  resolution:    100x100 dots per inch
```

Previously, after installation (this is Gutsy), I had just manually changed my dpi by going into font-preferences, finding the detail tab, and moving the dpi value up to 105 subjectively.  I guess I should knock it back down to 100.  Thing is, I don't recall if during installation, that it got it right initially.

Since I don't recall ever seeing any "DisplaySize" settings in my xorg.conf's monitor section, and if DDC probing fails to return a good value, you could end up with the fallback size of 75 dpi, which may not be right for your system.

I wonder how many of us are suffering from this?

I mean early 80's macs were at 72 dpi, and windows defaults to what, 96 dpi?  The link here might be useful:

[http://www.scantips.com/no72dpib.html](http://www.scantips.com/no72dpib.html)

.

---

### Post by stream303 on 2008-02-29
Fresh install of Feisty changes everything:

Oh boy.  Doing a grep DPI /var/log/Xorg.0.log shows that on Feisty on my box, it is set for 75,75 dpi.

However, when I go into the font preferences, it is defaulted to 96 dpi!  (which is what I *thought* was the logical dpi inch size for Linux)

And, an xdpyinfo | grep -B1 dot  shows 75,75 dpi.

HOWEVER dig this:
xdpyinfo returns a different physical size than Gutsy does!

Here it is in Gutsy:
```
bg@ubuntu:~$ xdpyinfo | grep -B1 dot
  dimensions:    1680x1050 pixels **(427x267 millimeters)**
  resolution:    100x100 dots per inch
```

Here it is in Feisty:
```
bg@ubuntu:~$ xdpyinfo | grep -B1 dot
  dimensions:    1680x1050 pixels **(569x356 millimeters)**
  resolution:    75x75 dots per inch
```

What is going on here??

I'm afraid to see what's up in Hardy! :)  I guess you can't really rely on anything, and just go by what looks good to you since changing dpi only affects font size / dialog boxes.  Easy to get confused with ppi.  From my understanding, ppi is the proper term for screen pixels, and dpi is for printing.

My head is swimming.  Fonts look good at 100 dpi in pref settings.  Going to bed. :)

---

### Post by stream303 on 2008-02-29
Well, looks like the difference between computed physical sizes between Feisty and Gutsy values is a bug in Xorg, not in Ubuntu.

This may be part of the reason that you never see a "DisplaySize" option in a monitor section in xorg.conf.

I think I may have taken a long train back to square one, since it appears that gnome just avoids all this silliness and sets the dpi value to 96 initially, leaving it up to you to change it to your own taste/eyesight.

I haven't seen if this affects printing at all however.  Man, wasted brain-cells I'll never get back! :)

---

### Post by stream303 on 2008-03-01
Well, this whole exercise did help in one regard.  I like to build up systems that are very simple cli-based with just a little bit of X thrown in with just a simple window manager like fluxbox, or even twm!  Other than specifying the dpi on the commandline, I found a few ways to set it manually:

[http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

It is interesting that they use 96 or greater if found for compatability reasons, and if your calculated dpi is smaller than 96, you need to manually tell this to the system.  hmmmm

Now starting Firefox from an Xterm look pretty decent! :)

---

