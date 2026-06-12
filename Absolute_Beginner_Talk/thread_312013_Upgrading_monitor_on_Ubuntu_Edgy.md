---
title: "Upgrading monitor on Ubuntu Edgy"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by kimro on 2006-12-03
I am 2 wks old to Ubuntu, actually Linux desktop in general so bare with this question plz :mrgreen: 

I'm currently using Dell 17" lcd but want to buy myself a nicer monitor for Christmas. I was wondering if Ubuntu would recognize the new monitor by itself or if I would have to take more action.

I'm currently using Edgy with Nvidia drivers with Beryl on AMD x2 3800+ & 6600GT. Thank you in advance!!

---

### Post by taurus on 2006-12-03
You probably have to reconfigure your X for the new monitor!  If you can't boot to GUI login screen, then boot into recovery mode from GRUB menu and at the prrompt, type

```
dpkg-reconfigure -phigh xserver-xorg
```

p.s.  I am still using Dell 17" CRT at home so maybe I need to get a 19" LCD monitor then!!!

---

### Post by kebes on 2006-12-03
Normally I think Linux would have no trouble recognizing the new monitor. I've had no troubles getting new LCD monitors recognized by Ubuntu.

However you mentioned that you were running Beryl, which might cause a problem. I know that alot of the time people have to make manual changes to "xorg.conf" to get Beryl working nicely on their system (I know I did!). If you made custom changes to the monitor section, then those changes might be wrong for the new monitor.

Of course you can always revert to a standard xorg.conf, get your new screen working, and then make another "fix" to get Beryl running again.

So overall I'd say that you should be fine.

---

### Post by atoponce on 2006-12-03
Your new monitor *should* be recognized, definitely if it is a widely used brand / model.  But, as mentioned above:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by kimro on 2006-12-03
Thanks all! Ubuntu forum's just amazing cuz so far, everyone's been right and so helpful. In Windows world, half the comments are stupid at best, not even related, and some does more damage then good.

Now, I gotta figure out if I'm gonna get the Dell 20" or 24"... comparing apples to oranges :mrgreen:

---

### Post by Mimsy on 2006-12-03
Yesterday, while out shopping, I saw a 37 inch widescreen LCD monitor... It was hooked up to a system running in-game movies recorded while playing Oblivion, to show off how good it could look... I don't think I have ever drooled that much in public before.

Ahem. :redface: 

Anyways.whenever I put the live CD in a computer hooked up to an LCD monitor, it works just fine. I've only had to adjust it once, and that was entirely the monitor's fault.

---

### Post by kebes on 2006-12-03
> **kimro said:**
> Thanks all! Ubuntu forum's just amazing cuz so far, everyone's been right and so helpful. In Windows world, half the comments are stupid at best, not even related, and some does more damage then good.

Now, I gotta figure out if I'm gonna get the Dell 20" or 24"... comparing apples to oranges :mrgreen:

You're welcome! Yes ubuntuforums.org is one of the main things that makes Ubuntu so great.

By the way, I'm using a Dell 20" screen with Ubuntu and it works great. I also debated between the 20" and 24" models... Keep in mind that (if you have a video card with dual outputs) you can run two 20" displays for about the same price as the 24" widescreen!

---

### Post by kimro on 2006-12-03
That's exactly what bugs me. For the price of one 24", I could get two 20"s. Although I wouldn't go dual with two 20s... probably one 17" or 19" on the side in the future to ease my life during web development.

With Dell days coming up here in Canada, I've lost faith in my decision skills lol.

37"... now that's a center piece.

---

### Post by Mimsy on 2006-12-03
[37 inches of gloriousness.]("http://hookedelectronics.stores.yahoo.net/welt37lcd.html")

---

