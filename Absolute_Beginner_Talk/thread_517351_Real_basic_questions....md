---
title: "Real basic questions..."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-08-04
I'm assuming these would be some basic questions...

1- Occassionally Amarok decides it can't fine the Xine drivers?!? I just noticed one thing where a web page loaded some music and then for whatever reason I can't mute sounds, other than if I'm listening to music in Amarok, I can mute that, But usually after a page loads music is when it starts having issues. foxy tunes responds fine, but my keyboard mute doesn't work. I'm assuming I need drivers for my keyboard to function.. it's a logitech itouch wireless. 

2- The small icons that were next to the Kmenu, I guess it's like a quick launch menu, they up and disappeared. I've clicked the bar and tried to see if I could get them back but no luck. Any time I place them on the bar, they're enormous whereas before they were smaller like the system tray progs.

3- While I am loving my new setup.. How do you know what's OK to remove and what really needs to stay without screwing things up?!? Not that I wouldn't be right back in here after googling my brain out.. but I started off with Ubuntu, then wanted the Kubuntu desktop and things have just been a little squirrly here and there after addidng it. Sooo.. what to remove? Examples... Adept Manager vs. Synaptic Manager, SCIM vs. SKIM, Konqueror vs. Firefox.. See what I mean? It's almost like I have 2 of everything now (gnome and kde) and why have it junked up for no reason?

I just find myself trying to customize and fix things more than really enjoying using my computer! Not that it wouldn't be the same case if I had Windows! LOL! But it's been 3 weeks now from switching over and I gotta admit I've learned a hella lot of info, just seems like I'm stuck in this mode of still trying to figure it all out rather than just using my puter..

Thanks for the help everyone!! You guys rock! :guitar:

---

### Post by apswartz on 2007-08-04
There is nothing wrong with having both Gnome and KDE desktops installed, especially if you have a multiuser system where different users have different preferences.

I guess you could do this...
```
sudo aptitude remove gnome-desktop
```

But, I don't think that will remove all of the gnome applications. You may just have to remove them as you come across them.

Or, you can download at Kubuntu desktop Install CD and do a fresh install.

---

### Post by BobCFC on 2007-08-04
I would still keep Firefox though, just use Konqueror as a file manager

---

### Post by apswartz on 2007-08-04
Keeping Firefox is fine. It is part of the kubuntu install as well.

---

### Post by davidjmayo on 2007-08-04
> 2- The small icons that were next to the Kmenu, I guess it's like a quick launch menu, they up and disappeared. I've clicked the bar and tried to see if I could get them back but no luck. Any time I place them on the bar, they're enormous whereas before they were smaller like the system tray progs.


To do this you may need to right click and unlock panels

where you got the big icon before by a right click it will say "add to panel" this in not the option you want. Move your mouse over to the left a bit and another small black triangle should appear. Right click this and see the option 
quick launcher menu ==> add application  --then choose from the menu

This will give you small icons.  After you finish right click again and "lock panels"

Hope this is clear it is hard to explain but easy to do !!

---

### Post by andyho on 2007-08-04
> **davidjmayo said:**
> To do this you may need to right click and unlock panels

where you got the big icon before by a right click it will say "add to panel" this in not the option you want. Move your mouse over to the left a bit and another small black triangle should appear. Right click this and see the option 
quick launcher menu ==> add application  --then choose from the menu

This will give you small icons.  After you finish right click again and "lock panels"

Hope this is clear it is hard to explain but easy to do !!

Actually that's exactly how I was doing it and it's resulting in the larger icons. I just figured it out though.. Add applet to panel! :) Somehow the actual quick launcher panel was gone!

---

