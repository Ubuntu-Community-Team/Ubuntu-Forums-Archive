---
title: "locking and logging out"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by saltyscott on 2006-11-26
ok so, i just recently switched to linux from windows.  one of the things i like to do is lock my computer and leave it for a long period of time while i am downloading something. after i lock my computer and it has sit for long enough it logs me out and closes everything i had running. how can i leave my computer locked for as long as i want?

---

### Post by taurus on 2006-11-26
How do you lock your machine?  I lock my machine before I leave work every night and that thing has been running for almost 30 days now...

---

### Post by saltyscott on 2006-11-26
i have the lock screen keyboard shortcut bound to Super_L. i just press that.

---

### Post by taurus on 2006-11-26
What if you click on the red icon on the upper right corner and pick lock screen from that menu, would that log you out after a long period?

---

### Post by saltyscott on 2006-11-26
ok i just tried that. it still logs me out.

---

### Post by saltyscott on 2006-11-26
so is it normal for it to be doing this? and if not how would i fix it?

---

### Post by CatKiller on 2006-11-26
It's not normal for it to be doing that. My (mostly speculative) guess is that it's one of your screensavers causing your X server to crash. When X restarts it goes to the login screen.

---

### Post by saltyscott on 2006-11-26
my screensaver is the molecule one. is that one unstable or something?

---

### Post by CatKiller on 2006-11-26
> **saltyscott said:**
> my screensaver is the molecule one. is that one unstable or something?

Ah. That one's definitely come up as being a likely candidate before. I don't know why, since it seems relatively simple compared to some of the others. Just one of those things I guess.

I would definitely try a different one.

---

### Post by saltyscott on 2006-11-26
i just tried engine too. the same thing happened. is there and screensaver that is known to be stable because i dont really care which screensaver i have as long as it doesnt crash gnome.

---

### Post by CatKiller on 2006-11-26
> **saltyscott said:**
> i just tried engine too. the same thing happened. is there and screensaver that is known to be stable because i dont really care which screensaver i have as long as it doesnt crash gnome.

Blank screen.

It looks like this could be indicative of a larger problem with your 3D graphics - so a 2D screensaver **might** still work OK for you. What happens if you run **glxgears** in a terminal?

---

### Post by saltyscott on 2006-11-26
the first time i ran glxgears, it showed up, but after i closed it it gave me some fatal IO error. then i ran it again and the gears did not show up and it completly locked up my computer. i tried it again and it locked it up the second time again.

---

### Post by CatKiller on 2006-11-26
That does sound like a driver issue, or similar.

---

### Post by saltyscott on 2006-11-26
i tried blank screen and left it. no problems. how would i fix my driver issue then? i dont know anything about getting or installing linux drivers. oh and i have a radeon 9600 card.

---

### Post by CatKiller on 2006-11-26
One of these, I guess, depending on whether you want the open source driver or the closed source one.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by saltyscott on 2006-11-26
ok i installed the opensource driver. it fixed the problem with the screensaver crashing and logging me out. now i cant use some of my games in wine though. do i need the ati driver to play my games in wine?

---

### Post by CatKiller on 2006-11-26
I have no idea to be honest. I don't use Wine for any games that would require any real drivers, and I don't really use any Ati drivers. It's possible you could reconfigure Wine to use your ati driver better, or it's possible that it does require some function of the fglrx driver, and you need that installed but better configured. I really couldn't say. Sorry.

---

