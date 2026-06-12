---
title: "Lost app bar that moves app &amp; has Min/Max/Close Icons while trying compiz"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-09-01
Ok, another newbie messing around with compiz! But something I've done has lost me the application menu bar than allows an application to be moved around, and contains the min/max/close icons!
I've also screewed up my Panel so now no open applications show up, even tho I've re-added Window Lists & Selectors!

It is only in the 1 User account (the one I tried using compiz for), the others are fine.

So, this configuration must reside in the /home/<username>/???? file/folder somewhere? As otherwise all accounts would be messed up. And it must of been something I done to compiz setup to cause compiz to change this setting?

Thanks in advance!

---

### Post by pbaehr on 2006-09-01
It sounds like you don't have a window manager loaded. Normally, Compiz would replace metacity (the default). Probably, compiz is not loading properly. Try starting it from the command line and see what errors it gives you. Otherwise, you can start metacity until you get compiz up and running by typing "metacity" (no quotes) in the terminal while you're logged in. You should see your windows come back to their old selves.

---

### Post by IanVaughan on 2006-09-01
God you guys are good! And soooo quick!!!

The (newbie) Ubuntu community would be lost without your help, cheers!

Typed "metacity", and got menu back. 
I now know what I did! I messed something up so removed compiz from the Sessions->Current Session & Startup Programs! What a plank huh!

So I just gotta add metacity (or compiz) back in there to start automatically now! Should be able to do that!

---

### Post by pbaehr on 2006-09-01
Glad that cleared it up!

Also, I'm as much a part of the "Newbie Ubuntu Community" as you are, I'm sure. It just so happens that I had to deal with a similar problem not long ago.

Now when you see someone ask what happened to their menus, you can help them too!

---

