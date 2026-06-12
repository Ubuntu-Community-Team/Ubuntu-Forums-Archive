---
title: "no backlight on laptop"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by steve8track on 2008-03-03
After I log in, my backlight turns off after a few seconds after showing the desktop.  I can move the mouse, open programs, or do anything, except that it's hard to see since there is no backlight, so I can barely make out anything on the screen.

To get the backlight back on again, I have to either change to one of the ttys by Ctrl+Alt+F1 etc, or kill x with Ctrl+Alt+Backspace.  After I do this, the backlight comes on again, but it turns off a few seconds later, even in GDM and the ttys.  That is what I think is wierd, when the login screen or the virtual consoles loose the backlight as well.

I tried reconfiguring the xorg.conf.  I have an Inspiron B120 where the graphics chipset is the 915.  I'm using the intel driver instead of i810.  I also have it set up to use direct rendering and to use compiz fusion.

The bug sometimes goes away if I reboot.  It is really random if it happens at all.

Thanks for any help.

EDIT:  Oh, I'm using Gutsy (upgraded from Gutsy's earlier releases)

---

### Post by cmnorton on 2008-03-03
What's the brand of laptop? 

How old is it? 

Have you talked to to the vendor? (In my case, speaking with IBM/Lenovo did not help me solve my external monitor problem with a brand new T61p. However, in your case, your hardware vendor might know something.)

---

### Post by steve8track on 2008-03-03
It's a Dell Inspiron B120 way out of waranty (I bought it in December of 2005 with only a 90 day warranty).

I booted into Windows (sorry) and the screen never went black.  I have tried moving the screen back and forth to see if there is some loose connection and there isn't any.

After I reboot, if it doesn't go black after a few seconds after logging in, then it doesn't ever go black at all, so that tells me it is probably software rather than hardware.

Thanks for the help.

---

### Post by OffAxis on 2008-03-03
Is the backlight shutting off completely, or dimming, like a lot of laptops do when they're not plugged into the wall?
 It might be a power saving 'feature' that you can adjust in the system settings.

> The bug sometimes goes away if I reboot. It is really random if it happens at all.

If you haven't already, try rebooting while 'Plugged into a Wall' versus while 'Not Plugged into a Wall'. The power setting / power cutoff may be set based on that initial status.

A little more information...
Is it just this Intel driver under Gutsy that is giving you problems? How did the i810 driver perform?
Did Fiesty have the same issues?
Have you tried disabling Compiz? Does the problem persist?

---

### Post by steve8track on 2008-03-04
Because of this problem, I set my System->Preferences->Power Management to never "blank screen".  The only thing it is set to do is hybernate when my battery is low.  I almost never boot without being plugged into the wall, so I doubt that is related.

I never remember this problem with Fiesty.  I don't know if compiz could be to blame, I haven't tested that yet.  What I don't get is why it or anything else could cause this problem when when it carries over into GDM and the virtual consoles.  I guess if it is the intel driver it may make sense, but does compiz continue running after pressing Ctrl+Alt+Backspace?  I thought it would kill compiz along with X.

Maybe I should try going back to the i810 driver like you mentioned.  I never had this problem with that driver, but then again, can i810 get direct rendering?  That's why I switched to the intel driver in the first place, because I wanted better game performance through better drivers and/or direct rendering.  I don't even know if the direct rendering uses the intel driver, since they way I got direct rendering to work was through some mesa install and adding DRI to xorg.conf (if I remember correctly).  Maybe that's a problem, it's mixing drivers?  But xorg.conf doesn't mention mesa anywhere, so why should installing mesa have changed anything?  Here is what I used to get direct rendering:

[http://www.larsen-b.com/Article/231.html]("http://www.larsen-b.com/Article/231.html")

I looked at the link and it doesn't say I have to use the intel driver, so I'll try reverting to the i810 driver and see if that works.

What's really wierd is that if I use a Gnome panel to open a terminal and type:

```
glxinfo | grep direct
```

It says "direct rendering: Yes", but if I use a keyboard shortcut through compiz to open gnome-terminal and run the same code, I used to get a no, but now it seems to say yes as well...

Thanks for the suggestions.  Luckily it hasn't happened again today, so I'll cross my fingers the problem dissapeared, at least until the weekend when I'll have more time to look into it.

Thanks again!

---

### Post by steve8track on 2008-03-05
I have really really good and bad news.

The good news is I figured out why the backlight keeps turning off.  The bad news is it is a hardware problem.  I thought it was drivers or something, because this had never happened in windows.  Well, today the screen went black while showing the Ubuntu boot screen.  I decided to load Windows to try again to see if it could be hardware.  Sure enough, the screen went black in windows as well.

Now I know it isn't a bug after all.  What I don't understand is why did my backlight turned back on after pressing Ctrl+Alt+Backspace?  Why would that temporarily fix the hardware problem?  I mean, it makes more sense why banging an old TV temporarily fixes the picture, but how would a loose wire that powers the backlight be effected by a keystroke?  It makes me wonder if I just press the keys hard in anger at the black screen, or if there is some other reason...  

I can see that the pixels are still colored on my screen, just the backlight is off so the screen is almost unreadable.

Either way, thanks for all of the help.  For now I'll just have to use my monitor-out port to get my programming done.

Thanks,

Steve

---

