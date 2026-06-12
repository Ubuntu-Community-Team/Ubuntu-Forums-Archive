---
title: "Video problems with Gutsy"
date: 2007-11-21
forum: Apple Intel Users
---

### Post by megs on 2007-11-21
First thing - nice touch with the similar threads when creating a title :-)

Onto the issues I'm having.  Running an intel Mac Mini, have had edgy, fiesty, and now gutsy installed - upgraded each time.  This time though, I'm having some problems I can't find the solution to with X.

Fisrt up - Xgl.  this made my system completely unusable in terms of speed.  As a dirty fix, I removed the line in xstartup (I think, I've not got access to confirm at the mo).  Leaving the standard Xorg server running.  My problems now are 2-fold.
First, the resolution at startup.  I can't tweak my xorg.conf to get anything above 1280x1024 to work.  My monitor is an IBM P77, which is capable of 1600x1200.  More to the point, I can use xrandr to select 1600x1200, so I know it *can* work with X.  Second - since the gutsy upgrade, I can't watch videos at this resolution.  mythtv and mplayer (and possibly kaffeine) can't output to the screen properly, I just get a blue screen.  If I swap back to the lower resolution, all is well.  Or, if I change the vo mode on mplayer, that works too, but doesn't fix the mythtv problem (or really explain why it no longer works as it used to).  I think I'm using -xv by default, swapping to x11 or gl seems to work, but I don't understand why.  Can anyone help with either of these problems (fixing no.1 may fix no 2 I hope).  
Cheers,
Megs

---

### Post by megs on 2007-11-21
And of course, some useful information might be to explicitly state that it's the intel graphics

---

### Post by cyberdork33 on 2007-11-21
> **megs said:**
> Fisrt up - Xgl.  this made my system completely unusable in terms of speed.  As a dirty fix, I removed the line in xstartup (I think, I've not got access to confirm at the mo).  Leaving the standard Xorg server running.  My problems now are 2-fold.
The Mac Mini does not even need to have XGL running. Using the Intel video driver which now supports AIGLX, there is no need for XGL, I would just uninstall it. (Also,  you don't need a seperate session for XGL anymore if you did need to use it as the scripts automatically start it if it is installed).

> First, the resolution at startup.  I can't tweak my xorg.conf to get anything above 1280x1024 to work.  My monitor is an IBM P77, which is capable of 1600x1200.  More to the point, I can use xrandr to select 1600x1200, so I know it *can* work with X. 
Many have been having trouble with the new Xorg autodetecting everything. Make sure you are using the 'intel' video driver. You may need to expand your video RAM or use a virtual line:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
Also, there is a 'Screens and Resolutions' tool in Gutsy now, if it works for you, great, but it usually just causes more problems.

> Second - since the gutsy upgrade, I can't watch videos at this resolution.  mythtv and mplayer (and possibly kaffeine) can't output to the screen properly, I just get a blue screen.  If I swap back to the lower resolution, all is well.  Or, if I change the vo mode on mplayer, that works too, but doesn't fix the mythtv problem (or really explain why it no longer works as it used to).  I think I'm using -xv by default, swapping to x11 or gl seems to work, but I don't understand why.  Can anyone help with either of these problems (fixing no.1 may fix no 2 I hope). I can't say for sure, but I have similar issues on my iMac (but using ATI fglrx, so no help there). Seems that things work better with desktop effects turned off.

---

### Post by megs on 2007-11-21
> **cyberdork33 said:**
> The Mac Mini does not even need to have XGL running. Using the Intel video driver which now supports AIGLX, there is no need for XGL, I would just uninstall it. (Also,  you don't need a seperate session for XGL anymore if you did need to use it as the scripts automatically start it if it is installed).

I've not intentionally switched on Xgl (or aiglx).  However, once upon a time I did try (decided it didn't play nice with mythtv frontend so turned it off again) and there could be some remnants I guess.

> **cyberdork33 said:**
> 
Many have been having trouble with the new Xorg autodetecting everything. Make sure you are using the 'intel' video driver. You may need to expand your video RAM or use a virtual line:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
Also, there is a 'Screens and Resolutions' tool in Gutsy now, if it works for you, great, but it usually just causes more problems.

 I can't say for sure, but I have similar issues on my iMac (but using ATI fglrx, so no help there). Seems that things work better with desktop effects turned off.


Will give the tool a try, can't hurt.  If nothing else, it'll give me a few new xorg.confs to try and work out which are good and which are bad...  The virtual line I will investigate too, ta.

---

### Post by cyberdork33 on 2007-11-21
> **megs said:**
> I've not intentionally switched on Xgl (or aiglx).  However, once upon a time I did try (decided it didn't play nice with mythtv frontend so turned it off again) and there could be some remnants I guess.
just 'sudo aptitude remove xserver-xgl'


[code]Will give the tool a try, can't hurt.  If nothing else, it'll give me a few new xorg.confs to try and work out which are good and which are bad...  The virtual line I will investigate too, ta.[/quote]
just backup your config first!

---

### Post by megs on 2007-11-22
> **cyberdork33 said:**
> just 'sudo aptitude remove xserver-xgl'


[code]Will give the tool a try, can't hurt.  If nothing else, it'll give me a few new xorg.confs to try and work out which are good and which are bad...  The virtual line I will investigate too, ta.
just backup your config first![/QUOTE]

I've now removed xserver-xgl.  I also discovered that the file that I'd modifed was /etc/X11/Xsession.d/98xserver-xgl_start-server. I commented out the last few lines that started xgl.  
Anyway, then I re-ran a dpkg-reconfigure command.  I think it was dpkg-reconfigure -phigh xserver-xorg.  This gave me a much smaller xorg.conf.  From that, and possibly using xrandr once, I have now got to the stage where I am in 1600x1200 from the outset, which is ace.  However, I've still got the blue screen when watching any videos.  I'm not even sure of the right terminology for that, in terms of what to google for - video overlay or something?  Basically, mplayer works with -vo x11, but it is defaulting to -vo xv, which doesn't work.  mythtv doesn't work either, presumably due to using -vo vx, or an equivalent.  Is this likely to be a bug, or a config issue?
Cheers,
Megs

---

