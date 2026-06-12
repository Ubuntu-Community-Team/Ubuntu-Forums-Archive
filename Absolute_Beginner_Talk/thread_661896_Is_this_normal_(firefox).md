---
title: "Is this normal? (firefox)"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Mular on 2008-01-08
I had the firefox2 version installed that comes generic with the 7.10 live cd of gutsy.

I notice when I am playing videos I get a lot of slow down.. Not huge videos either little ones, and if I have multible videos running (in tabs) my whole system will crawl and my CPU usage will be extremely high (70-90%)

Also I get choppy scrolling on few sites and just sluggish - stuff that didn't happen in XP. I installed version 3 of firefox beta I think its beta 2.. That made it a little better but the problem still is there.

I am running desktop effects (compiz). I have a 3.2gig P4 2gigs of ram and a nvidia 7800GT..

Is this normal or is there something misconfigured with my system? Also I installed my vid drivers with Envy, but I had these issues with the restricted driver as well. I read some posts about the nvidia-gfx-new driver maybe that would help?

Also I was wondering maybe this issue was related to my monitor not being detected right. I have a magnavox 19inch HDTV, its detected as a plug in play monitor and it had the wrong resolutions plus the wrong refreshrate. If I run the xserv config I can get it to see it as a magnavox in the xorg.conf but if I go system > screen and resolution it doesn't show up there. I selected wide screen generic widescreen monitor 1400x900 - and it won't let me select 60 refreshrate (thats all my tv supports).

Its really just firefox that is really sluggish and I am not sure what else to do? 

Also related too is when I first load up my computer the screen is always off center (did this in windows to I think its just the monitor) but is there anyway I can configure it to use a certain range so I don't have to always do auto image correct?

---

### Post by luisromangz on 2008-01-08
If you are running compiz, that is normal. Video playing performance is degraded sooo much.

Disable compiz while watching videos. I use fusion-icon, which is a systray icon that manages compiz/kwin/metacity launch allowing fast-switching between them.

---

### Post by Mular on 2008-01-08
oh ok, I will have to try that at home.. bummer ;( I love the pretty effects lol

---

### Post by Jense on 2008-01-08
Alternatively you can edit the compiz settings so it will not render video. This will black out the video screen when you are shifting windows or rolling the cube but it will not be so hard on the performance. Especially internet movies like youtube stuff uses codecs which have a high cpu usage in addition to compiz this can cause the system to get slow.
Also try installing swiftweasel browser. This is a version of Firefox that is specially compiled for your cpu which gains you some performance, not too much though.

---

### Post by skymera on 2008-01-08
yeah agree with videos im running the 7900GT and if i play vids my browser dosent respond till it finished.
bummer when you got a 30min clip

---

### Post by LowSky on 2008-01-08
you really dont have to turn off all the effects. Animation, windows blur and wobbly windows cause the most issues, turn them off one at a time, and see if things improve.

---

### Post by Mular on 2008-01-08
> **LowSky said:**
> you really dont have to turn off all the effects. Animation, windows blur and wobbly windows cause the most issues, turn them off one at a time, and see if things improve.

Its funny how going from windows I had none of these cool effects, and now I am so hesitant to turn them off lol..

So you guys think that I should be ok with just using the Nvidia Envy driver?

Also i read something about in compiz turning off Detect Refresh Rate?

---

### Post by LeDechaine on 2008-01-19
This is a known bug, sorry:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384)

Solved my problems by totally disabling the effects, though I really love them too :P
*Impatiently waiting for a fix* :)

---

### Post by doorknob60 on 2008-01-19
YOu don't have to disable it permanantly :) [http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

### Post by LeDechaine on 2008-01-19
Hmm, thanks, but I already found a similar thing already available in Synaptic, under the name... (verifying)
**Compiz Gnome Manager**
Gnome compiz manager is small utility, which manage GL Desktop configuration on
XGL/AiGLX. It&#8217;s composed of two applications :
 - **compiz-tray-icon** : which launch and stop compiz
 - gnome-compiz-preferences : which adjust GL effects
The goal isn&#8217;t to propose all compiz options but allow a simple configuration
of compiz.

:)

---

