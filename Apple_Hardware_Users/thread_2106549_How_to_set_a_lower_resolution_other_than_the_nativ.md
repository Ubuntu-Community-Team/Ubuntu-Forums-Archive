---
title: "How to set a lower resolution other than the native 2880x1800 on the 15' rMBP?"
date: 2013-01-19
forum: Apple Hardware Users
---

### Post by HarryX on 2013-01-19
I am running Ubuntu 13.04 64-bit daily build for Macs on my 15' Macbook Pro with Retina Display. After I got the nVidia drivers to work, though, I could no longer find resolutions other than 2880x1800 in System Settings.

This makes everything on the screen look tiny. I would like to run the panel at a lower resolution, presumably at 1440x900 (so the loss of detail would be minimal). 

However, I could not find anyway to add other resolution options. I tried adding

```
Modes   "2880x1800""1440x900"
```

to the "Display" subsection of xorg.conf. No luck. Nor can I find any way to add other resolutions in nVidia's X Server Settings.

Any help? Thanks a lot!!!

---

### Post by Garlandg on 2013-01-23
This guide of mine covers this:  [http://linuxmacbookproretina.blogspot.com/](http://linuxmacbookproretina.blogspot.com/)

I wasn't able to add modes either, but this script of mine works well.  

Hope this helps.

---

### Post by HarryX on 2013-01-24
I'm really sorry for the trouble but could you copy the related part out of that article and put it in the reply? I'm Chinese and Blogspot is blocked here... Really sorry thank you!!!

---

### Post by Garlandg on 2013-01-24
No problem.

Let me know if you can't get through to github, as that's where the shell script is being stored.  If you can't, you can still use the command to scale it, and I'll put the script up for you.

Here's the entire part of my post about this topic.  If your nvidia chip is configured correctly, this should work, but do check the xrandr -q to make sure DP-2 is the correct name.

> Well, after having this set up, I wanted to be able switch resolutions  (the screen is really tiny, and it drops the frame-rate of games rather  significantly)  I tried all of the standard xorg.conf configuration,  addmode, newmode, all of that.  But nothing worked.

Today, I stumbled on a solution:  xrandr's --scale option.  This allows  you to scale that screen to almost any resolution you want.

 for example:

[LIST]
[*]xrandr -q
[/LIST]
 (this returns certain names e.g. mine is DP-2. Another is HDMI-0.  One will say "connected" and that's the one you need.

[LIST]
[*]xrandr  --output DP-2 --scale .5x.5
[/LIST]
 This scales it to a 1440x900 resolution.

One thing to note.  Sometimes trying to go from one scaled resolution to  another will fail with an error.  Don't panic:  just change the scale  back to 1x1, and the next scale you choose will work. The scaling  numbers don't have to be simple: I managed to get ~1650x1050 by putting  the scale value as .5729x.5729.


Here's a link to the script:  [https://gist.github.com/4552263/](https://gist.github.com/4552263/)

This script takes one parameter: the width in pixels of your screen.

Sample run:

   sh ./Res.sh 1680

The result is a 1680x1050 scaled screen.

---

### Post by HarryX on 2013-01-24
Thank you!!! The command worked, and I could get the script from GitHub, which worked really well for me too.

However, after I set the scale, the trackpad seemed to get wacky. I couldn't click on anything on the screen accurately, except in the dock. After trying to click on things all over the screen, I guess it was because despite the screen being scaled, the system still thought it was operating under 2880x1800 on the 15' screen area, and the trackpad acted accordingly. For example, if I want to click on something at the lower right corner of the screen, I need to click on the center of the screen instead.

Another problem is that, after I rebooted via terminal, everything went back to what they used to be.

Is there a way to make the scaling settings 'stick'? Also, what should I do to solve the trackpad problem?

Thank you so much!!!

---

### Post by Garlandg on 2013-01-24
You can't exactly make the settings "stick," but you can write a simple shell script that calls the script I gave you with the default width you want and make that run at startup, which achieves approximately the same thing. The script is pretty much just this:
```

#!/bin/bash
Res.sh 1650

```The only thing is to make sure you have set $HOME/bin in your executable path, and that Res.sh is executable and in your $HOME/bin folder.

As for the trackpad issue:  after you change the resolution, if you move your mouse to the edges of the screen, does it scroll?  if so, it's actually "panning" with a window of the size of the actual pixels rather than scaling to it.  I've had that happen a couple times, though my track-pad never did what you describe from what I remember. (If I noticed it was scrolling and only to top left corner contained the screen, I re-ran the script, which solved the issue, so I actually never tried to click anywhere.  (That shouldn't happen very often)

Actually I guess I faintly remember something like that, but I'm not sure enough to say whether it happened or not (I think it may have happened when I tried to set it to 1920, but I generally use my computer at 1680x1050 now.  So try re-running it a couple times with different resolutions, and see if that fixes it.  I haven't many problems with it, and I may add a force option later to force the resolution change so you don't have to change it twice to retry a specific resolution.

---

### Post by HarryX on 2013-01-25
Thank you man!!! I found 1680x1050 to be the magic number for me as well, and everything is working now! Thanks a lot for your help!!!

---

