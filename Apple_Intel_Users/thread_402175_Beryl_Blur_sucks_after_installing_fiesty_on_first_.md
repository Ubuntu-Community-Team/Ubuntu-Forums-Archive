---
title: "Beryl Blur sucks after installing fiesty on first gen MacBook"
date: 2007-04-05
forum: Apple Intel Users
---

### Post by ry4nolson on 2007-04-05
i used to use the blur effect on my windows with edgy. i especially liked it with a transparent terminal window. now that i installed feisty the blur seems to suck really bad. ive attached a screenshot to show you what im talking about.

---

### Post by benanzo on 2007-04-05
Yeah, I hear ya.

The Intel GMA950 graphics in the MacBooks are a little skimpy on power.  I can't run the blur plugin or water/rain without some serious performance issues.  But it's OK considering all Intel's graphics are open source.  I'm sure it will get better.

The rest of Beryl/AIGLX run great.

---

### Post by ry4nolson on 2007-04-06
yea but my point is that when i was running edgy the blur effect looked and worked great but now that i am running feisty it doesn't work right.

---

### Post by wecannotbesaved on 2007-04-06
Why do you need the blur effect?

---

### Post by ry4nolson on 2007-04-06
because i like it and it is useful with the transparent terminal window

---

### Post by Rashind on 2007-04-07
"Why does that need to work?" and variations thereof are not really appropriate responses on a support forum...

---

### Post by Chrisj303 on 2007-04-07
> **benanzo said:**
> Yeah, I hear ya.

The Intel GMA950 graphics in the MacBooks are a little skimpy on power.  I can't run the blur plugin or water/rain without some serious performance issues.  But it's OK considering all Intel's graphics are open source.  I'm sure it will get better.

The rest of Beryl/AIGLX run great.


I have no problems with the blur effect, but can't get water/rain AT ALL!

On a macbook c2d 2gb RAM...

---

### Post by Icarosaurus on 2007-04-18
I have the same issue on my pc...
Maybe it's a driver-related problem?
I've got an ATI radeon 9600 card and I'm using Mesa drivers... maybe blur works good with fglrx proprietary drivers...
so, maybe it's a fault of open source drivers...
Just an ipothesys...
Bye!

---

### Post by ronmarley1 on 2007-04-20
> **ry4nolson said:**
> yea but my point is that when i was running edgy the blur effect looked and worked great but now that i am running feisty it doesn't work right.
This is the same for me, except I'm using an IBM R51 Thinkpad with the Intel 855 card (which uses the same driver as the 950, I believe).  I have turned off Brur for the time being.  Everything else (Feisty and Beryl) work great!

---

### Post by muzzz on 2007-04-20
Same here. I'm behind a NEC notebook (also an Intel 855 card). Blur worked perfectly on Edgy but is horribly broken on Feisty. It almost looks like it takes random, or at least wrong, sections of the screen as "input" for the blur effect.

My only guess is that this is somehow related to the moving of AIGLX to the kernel.

---

### Post by javakidv1 on 2007-04-21
I'm having the same problem on my PC. My graphics card is also from Intel and using the 950 driver. Blur worked perfectly but rain didn't under 6.10. When I updated to 7.04 blur is broken but water works. I noticed that the colors in the "blurred" image roughly match those of the windows behind it but are horribly distorted.

---

### Post by hotdog003 on 2007-04-22
I can confirm that the blur plugin is broken on my Dell dimension E310 with an integrated intel i915 graphics card after upgrading to Feisty. Water now works, though, when it didn't before.

[Here]("http://forum.beryl-project.org/viewtopic.php?f=37&t=6067&p=32755#p32755") is the thread on the beryl forums.

I'm guessing it's an issue with the intel drivers. *shrug*

---

### Post by Icarosaurus on 2007-04-23
Blur is broken also with my ATI Radeon 9600 and open source drivers....

---

### Post by commonplace on 2007-04-23
Blur is broken (same as described above by everyone else; it 'works' but looks awful and definitely isn't how it should be -- i.e. how it was in Edgy) for me, and I'm using an ATI Radeon X700 (PCI-e) card with the open source drivers ('ati') that were automatically installed with my clean Feisty install.

/Kevin

---

### Post by morrisonpeter on 2007-04-23
Blur has the same effects for me (including the black bands behind the window decorations.) I have a Dell Latitude D620 with an Intel 945GM Express Chipset family graphics card. Everything else works perfect (including the water effects.) If I could get blur to work, my clear windows decorations would look amazing! Please post if anyone comes up with a fix!

---

### Post by Klarkshroder on 2007-04-25
I've got a similar problem. On my Dell Inspiron 600m with ATI Mobility Radeon 9000, Beryl's blur worked fine under Edgy, but wobbly windows did not. After upgrading to Feisty, wobbly windows work fine and blur is completely broken.

---

### Post by daderef on 2007-05-03
i have the same problem! transparency on my beryl is really awful and there's nothing i can do for it... i thought that my problem were the video drivers (i have a intel 945gm graphic card), but now i'm not sure about it... :confused:

---

### Post by padstrey on 2007-05-04
ermmm how about goin on this link.... it helps to make Beryl Blur better on the Mac, i found out.... here u go
[http://www.dubitinsider.com/tracker/log/13?uid=6726](http://www.dubitinsider.com/tracker/log/13?uid=6726)

---

### Post by ronmarley1 on 2007-05-04
> **padstrey said:**
> ermmm how about goin on this link.... it helps to make Beryl Blur better on the Mac, i found out.... here u go
[http://www.dubitinsider.com/tracker/log/13?uid=6726](http://www.dubitinsider.com/tracker/log/13?uid=6726)
Thanks for the link padstrey.  However, when I click it, I get redirected to [http://www.getupandplay.co.uk/](http://www.getupandplay.co.uk/)

---

### Post by Chrisj303 on 2007-05-04
> **Chrisj303 said:**
> I have no problems with the blur effect, but can't get water/rain AT ALL!

On a macbook c2d 2gb RAM...

Well i've moved up to feisty, and guess what...blur is broken for me too!

I think this one is out of our hands for now, but as was said before the Intel drivers are open so weve a good chance it'll get fixed.

I am now getting the water/rain effect - but i've noticed that the 'pointer wave' essentially breaks my system, as it will take effect but render the cursor useless and all i can do to get out of it is restart X.

---

### Post by tr4nce on 2007-05-13
* bump *

Double posting sorry :(

---

### Post by tr4nce on 2007-05-13
With a Intel GMA 3000 integrated graphics and shared 256mb I get the same problem, Blur and Water doesn't work well in AIGLX & Xorg 7.2. I'm not using Ubuntu (currently gentoo) but with Fedora6 without updates Blur worked fine. My conclusion is that there is something about 3D support and mesa is where you have to focus.

You can try in console
```
$ LIBGL_DEBUG=verbose glxinfo
```

I got:
```
libGL: OpenDriver: trying /usr/lib64/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib64/dri/i965_dri.so
```

and then
```
libGL warning: 3D driver claims to not support visual 0x6d
```

So my guess is mesa...At this time 'm trying to compile intel 2D driver and Mesa 3D support from git using this guide [http://www.intellinuxgraphics.org/install.html](http://www.intellinuxgraphics.org/install.html) (starting from point  **3.3 Xorg 2D driver**)

UPDATE! Yes working! Update mesa to 6.5.3 [http://mesa3d.sf.net](http://mesa3d.sf.net) >> Blur plugin now functional but water still have problems.
Some remarks about Blur: When you activate it moving windows becomes very sluggish. Well not so sh*tty but there is a big difference when you compare performance with disabled blur windows.

---

### Post by jbernardo on 2007-05-25
Same problem here, on a clean install of Feisty on a Fujitsu Amilo Pi1505 laptop, using intel drivers (intel 945GM).

Maybe this thread should be moved to a more generic forum, as the problem isn't limited to apple intel machines?

---

### Post by bittergourd on 2007-06-02
i haven't successfully get the mesa/dri/drm working yet.  but if you are not against repository driver, try fglrx + xgl + beryl.  in this way, blur works at least on x200m and 9600, so far as i have witnessed.  

it seems that the open source driver that doesn't have perfect support to some features. (i have no idea why edgy with some older version of xorg worked fine...) again, fglrx doesn't support aiglx, yet.  xgl is the only choice, and sadly no other 3D program can run with xgl (there isn't many anyways). 

waiting for fglrx to support aiglx..............

---

### Post by Icarosaurus on 2007-06-03
Blur works on Mesa 6.5.3 and above...

---

### Post by altaaa on 2007-06-06
I have the same problem. Feisty, i810 driver, AIGLX, beryl.

In 16-bit color depth the blur does work, if not optimal. So if you want a workaround, try it out.

---

### Post by d_xtremw on 2007-06-24
same problem as everyone else. i did get the rain effect to work though. for sum reason it works for me after i press ctrl+f9.. just a suggestion,,

---

