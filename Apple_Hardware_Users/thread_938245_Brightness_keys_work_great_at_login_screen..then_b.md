---
title: "Brightness keys work great at login screen..then bizzare at desktop"
date: 2008-10-04
forum: Apple Hardware Users
---

### Post by dustynus on 2008-10-04
When ubuntu is at the login screen, the brightness works the way it should.

If I press to Lower the brightness, it lowers right to a black screen, pressing and hold brightness it will stay at a black screen.

Right after the little Ubuntu jingle sound thing plays all of a sudden if I now press Lower again, it flicks back to being bright !

It's a pain when I wan't to converse power and I press and hold the brightness key down and bam it goes to black then flickers up to bright again, and I have to carefully press once at a time to make it black.

Basically it works perfectly at the login screen then after the sound logo thing plays it get's messed up.

Could it be reloading the key handler pommed twice ? 
What is controlling the brightness keys at login ? Is there a way to force it to keep using that all the time?

Thanks very much:guitar:

---

### Post by kosumi68 on 2008-10-04
I believe pommed gets overridden by some hal/xorg functionality once you login; there seems to be regression for many models right now. What model are you using?

---

### Post by dustynus on 2008-10-04
It's a macbook 2,1  duo core if that helps 

thanks

---

### Post by kosumi68 on 2008-10-04
> **dustynus said:**
> It's a macbook 2,1  duo core if that helps 

thanks

It does, because the ATI X1600 graphics card seems better supported in HAL.

Reading your initial post again, it sounds like you are experiencing a small glitch in Hardy. Searching on launchpad and/or reporting the bug would be very much apppreciated. I sort of assumed we were talking about Intrepid and the new X server, which currently has greater problems with backlight.

---

### Post by Mazin on 2008-11-07
I have this same problem with my 2,1 Macbook.  I had upgraded to Intrepid from Hardy and brightness worked fine, but sound was broken and other weird issues popped up.  After I reinstalled Intrepid, the other problems were fixed but I got this odd backlight issue.

Essentially, brightness no longer scales linearly but semi-randomly.  I just have to keep hitting the button until I get lucky and get the brightness I want.

---

### Post by kosumi68 on 2008-11-07
> **Mazin said:**
> 
Essentially, brightness no longer scales linearly but semi-randomly.  I just have to keep hitting the button until I get lucky and get the brightness I want.

This is an amusing problem :-)

1. Can you modify the LCD brightness with xbacklight?

2. What does this line say?
```

hal-find-by-capability --capability laptop_panel

```

3. Have you tried installing the gnome-power-manager package from the mactel PPA? ([https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA))

---

### Post by Mazin on 2008-11-07
1.  Yes, with much flickering, but the final brightness is correct.
2.  "/org/freedesktop/Hal/devices/macbook_backlight"
3.  Already am.

---

### Post by Mazin on 2008-11-07
Downgrading to the default gnome-power-manager fixed the hotkeys for me.  However, panel still flickers when the system automatically changes the brightness (including xbacklight).

---

### Post by kosumi68 on 2008-11-07
2. Most likely this dbus interface is not in use (gpm prefers RandR before HAL), but to make sure, you may want to temporarily disable it by removing your mac model from /usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi.

3. The conjecture I have is that g-p-m is getting the number of levels of brightness wrong.

---

### Post by GerryLight on 2009-04-08
is there any news regarding this topic?

The brightness control of my MacBook 2,1 is completely disturbed since Intrepid, same in Jaunty, both 64bit. In Jaunty, I can't downgrade to the default g-p-m as Mazin. If i raise or lower brightness using he function keys, the brightness switches randomly or backlight goes off. I had the mactel PPA in Intrepid (for Jaunty I didn't try yet, but g-p-m is still version 2.24), have the latest MacOS updates, no pommed, removed the 10-macbook-backlight.fdi as suggested elsewhere - no change. I also wonder that nobody else seems to have trouble with the brightness control, at least I can't find any bug entry (most people complain that the function keys don't work at all). Can anyone else confirm this issue?

---

### Post by Mazin on 2009-04-08
switch to mainstream gnome-power-manager instead of Mactel PPA's gpm and this problem should go away (at least in my case).

---

### Post by lantor on 2009-04-13
> **GerryLight said:**
> is there any news regarding this topic?

The brightness control of my MacBook 2,1 is completely disturbed since Intrepid, same in Jaunty, both 64bit. In Jaunty, I can't downgrade to the default g-p-m as Mazin. If i raise or lower brightness using he function keys, the brightness switches randomly or backlight goes off. I had the mactel PPA in Intrepid (for Jaunty I didn't try yet, but g-p-m is still version 2.24), have the latest MacOS updates, no pommed, removed the 10-macbook-backlight.fdi as suggested elsewhere - no change. I also wonder that nobody else seems to have trouble with the brightness control, at least I can't find any bug entry (most people complain that the function keys don't work at all). Can anyone else confirm this issue?

I have a Dell XPS m1330 laptop with intrepid and have a very similar problem. Before login backlight adjusting works flawlessly but upon login using the fn shortcuts gives me a jump of usually 3 steps to the brightness! Dunno if this is related, but i would really like to fix it. 

If you havent already i suggest you create a brightness control in the gnome-panel. This way you can at least get the right brightness directly. No fancy fn shortcuts thou. ):P

---

### Post by Mazin on 2009-04-13
Wait, I'm repeating myself.  Sorry about that.  I've since reinstalled OS X on my MacBook, so I'm afraid I can't help much anymore.

---

