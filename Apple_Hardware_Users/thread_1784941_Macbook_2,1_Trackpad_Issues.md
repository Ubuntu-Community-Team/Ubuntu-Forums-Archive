---
title: "Macbook 2,1 Trackpad Issues"
date: 2011-06-17
forum: Apple Hardware Users
---

### Post by computerfreak97 on 2011-06-17
Hi,

I just installed ubuntu 11.04 on my macbook 2,1 and noticed that the trackpad was having many issues with detecting my finger, it works fine in OSX. I found [this]("https://help.ubuntu.com/community/MacBook2-1/Maverick") post, but cant find the xorg.config file and read that it no longer exists in ubuntu 11.04 (and yes, I know that that page is for 10.10, but it should still work). Is there anywhere that I could put in that code to make the trackpad more responsive?

Thank you!

P.S. Is there any way I can make a two finger tap register as a right mouse click?

---

### Post by DirtyPC on 2011-06-17
I've done this for you, add it to /etc/X11/

rename xorg.txt to xorg.conf

and with the double tap, if you do that you won't be able to access desktop icons, unless you set them to single click. Check the mouse settings.

---

### Post by computerfreak97 on 2011-06-17
It doesn't appear to have any effect. I was wondering if gsynaptics (which i installed earlier to fiddle with it) is overriding the x settings. Could that be it?

EDIT: it appears that now two finger clicking works (!) but the mouse is still not correctly detecting my finger. Also, I'm starting to find that for some reason it moves to the right basically with out any issues, but when moving to the left it can get "stuck"

---

### Post by computerfreak97 on 2011-06-22
Anyone? I need to get this up ASAP.

---

### Post by computerfreak97 on 2011-06-28
UPDATE: I got it to work by copy/pasting the xorg file into the 50-synaptics.conf file in /usr/share/X11/xorg.init.d/. Sadly, the settings on speed appear to have NO effect on the speed of the trackpad, and no other utilities don't do anything either.

---

### Post by lefrig on 2011-11-15
Hello,

I am working on the same issue.  I just want to disable the tap click.  It is very annoying as any time i graze my hand over the trackpad it 'clicks'.  

Have you or anyone found a solution or a set of configuration that can disable the tap click?

I have been doing some research and found some  stuff that i can try.  I have been having some funny issues where i try using the script this guy provides but it disables the keyboard.  I have been looking into the x log file but it comes up with too much stuff to sift through.  

there is a setting to disable the click.  Somthing like "TouchpadOff" = "2" as 2 enables trackpad but doesnt allow for tap clicks.  

[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

Tahts it for now.  Hopefully I can find somebody we can work together to fix this issue. :D

---

