---
title: "No sound fresh feisty install powerbook g4"
date: 2008-01-03
forum: Apple PPC Users
---

### Post by anthonylane13 on 2008-01-03
I have recently installed feisty on my powerbook g4 gigabit ethernet.  I have no sound support at the moment, and despite having a copy of the official ubuntu book from my local library (thank you very much), it does not really deal with ppc architecture.  I'm having problems finding out what kind of sound card is in my machine - osx does not seem to list any sound devices in profiler - yet sound works very well in osx, so I know I have one somewhere.
Some advice on how to find out what hardware I have and what to do to make it work in ubuntu would be magic!
In advance, thank you...

---

### Post by frog_pilot on 2008-01-03
add the line ```
snd-powermac
``` to your /etc/modules. This will load the right driver module for your sound card on startup.

If you want to test, if this is the right module for you, you can execute ```
sudo modprobe snd-powermac
``` This will load the module for your current session.

---

### Post by anthonylane13 on 2008-01-03
I added the line
```
snd-powermac
```
to the file /etc/modules as suggested.

The sound works - at least I hear the default ubuntu sound as the login screen loads.

I do now have a bigger problem...

Since doing this my desktop environment will not load:confused: I login as normal, and (sometimes) I see the nautilus graphic in the centre of the screen, but when it disappears, only the wallpaper of my desktop is displayed. No menus, no icons, no fun!

The other scenario I encounter is that I don't even get the nautilus graphic. When this happens I just get the brown screen (no wallpaper) and after a few seconds a white square appears in the top left corner (about 500x400px) as though a window is about to appear, but nothing else happens.  If I move my cursor over this 'window' the pointer changes to a text pointer.  Incidentally, this is what happened when I tried to launch the live CD

Please help!!

---

### Post by Auria on 2008-01-04
See the FAQ, I think there is a mention on what to do with sound problems that cause brown screens

---

### Post by anthonylane13 on 2008-01-04
Sorry if I'm missing something obvious here, but have had a thorough look on this forum, and can't find the FAQ - can anyone post a link?

Thanks

---

### Post by Auria on 2008-01-04
It's a sticky in the PPC forums

I think you want this one:
[https://wiki.ubuntu.com/PowerPCFAQ#head-f0c7fe84ae69dd48197522097690b622b7ef39d2à](https://wiki.ubuntu.com/PowerPCFAQ#head-f0c7fe84ae69dd48197522097690b622b7ef39d2à)

which takes you to:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-e4609ed68a1e478be1d5398fa19bb43775f21936](https://wiki.ubuntu.com/PowerPCKnownIssues#head-e4609ed68a1e478be1d5398fa19bb43775f21936)

good luck

---

### Post by anthonylane13 on 2008-01-05
Thank you so much for that! I will post again and reveal my success (or failure)
:)

---

### Post by anthonylane13 on 2008-01-05
Fantastic - I am posting this message from Ubuntu!
Thanks again.

---

