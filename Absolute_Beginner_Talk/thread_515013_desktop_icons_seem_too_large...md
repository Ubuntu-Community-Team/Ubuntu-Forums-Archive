---
title: "desktop icons seem too large.."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-08-01
I'm hoping someone might be able to help me figure out why my desktop icons are showing up larger than they should be.. When I go into my nvidia settings it's showing my resolution at 1600x1200, but my icons look too big, about the size they should be at 1280x1024. Is there somewhere to change icon size? My program bar is showing at the right size, it's just the icons that are off. Thanks!!

---

### Post by Logical Dream on 2007-08-01
Its just how they look in Linux ... maybe there is a way to change it , but I dont know :)

---

### Post by yogo on 2007-08-01
Right click any icon and choose to stretch icon, you can change their size that way but it has to be done on each one.

HTH

---

### Post by Sayers on 2007-08-01
Yes they are very easy to scale and most are SVG's meaning that no matter how big they are they still keep their look :]

---

### Post by andyho on 2007-08-01
I don't think "that's just how they look" when I've seen them smaller before... and there is no option for scaling either. :( They seemed to have changed after I tried installing a prog with Wine and just haven't gone back, even after restarting. I could've swore I saw somewhere you could designate icon size like, x-small, small, medium and large, but I can't remember where I saw it.

---

### Post by Delkster on 2007-08-01
The desktop icons in Gnome generally follow the Nautilus (file manager) settings for icon size. Open any folder, go to Edit > Preferences (or something, I don't have my desktop set to English at the moment), and find the settings for the icon view.

---

### Post by andyho on 2007-08-02
still no such luck... any other ideas peeps? :popcorn:

---

### Post by Ek0nomik on 2007-08-02
> **andyho said:**
> still no such luck... any other ideas peeps? :popcorn:

I would have thought streching the icons would have done the trick...

Can you take a screenshot of the Desktop?

Applications —> Accessories —> Take Screenshot

---

### Post by andyho on 2007-08-02
[IMG]http://i2.photobucket.com/albums/y4/andyho623/Screenshot.png[/IMG]

---

### Post by Ek0nomik on 2007-08-02
Your desktop scared the h/ll outta me initially.

Do one of these offer any solutions?

[http://www.linuxquestions.org/questions/showthread.php?t=381182](http://www.linuxquestions.org/questions/showthread.php?t=381182)

[http://www.linuxquestions.org/questions/showthread.php?t=257279](http://www.linuxquestions.org/questions/showthread.php?t=257279)

[http://www.nabble.com/Size-of-icons-on-the-desktop-t4071262.html](http://www.nabble.com/Size-of-icons-on-the-desktop-t4071262.html)

---

### Post by superbungalow on 2007-08-02
do they make flash for linux now????

---

### Post by andyho on 2007-08-02
LOL!! why'd it scare you?!? Anyways, I went into terminal, typed in Nautilus and adjusted the icon ratio to 50%. It did change the icons within the window, but didn't change anything on the desktop?!?

---

### Post by andyho on 2007-08-02
> **superbungalow said:**
> do they make flash for linux now????

No, but it works fine with WINE! :)

---

### Post by Ek0nomik on 2007-08-02
> **andyho said:**
> LOL!! why'd it scare you?!? Anyways, I went into terminal, typed in Nautilus and adjusted the icon ratio to 50%. It did change the icons within the window, but didn't change anything on the desktop?!?

Your wallpaper just caught me off guard, that's all.  :)

What about any of the other solutions in the threads I posted?  None of those work either?

So you don't get a stretch icon option on *any* of the icons, or just not the programs installed with Wine?

Also, since when did Wine place icons on the desktop?  I have only installed around 2 programs with Wine, and that was a little bit back, but it never put an icon on the desktop.

---

### Post by andyho on 2007-08-02
Nope, none of the other ones helped either. Wine didn't place the icons on the desktop, I did. :) The resizing of the icons happened after I tried to get a game to work with Wine; Chocolatier, which doesn't work with Wine as I've found out. The resolution of the game is, I believe 1024x768. Even in Windows it would resize things, but after closing the game everything would go back. I previously had problems where it would freeze up the desktop... but it would always switch the resolution on me and I would have to log off and come back to get my background set correctly. The icons just haven't gone back for some reason?! And nope there is no stretch for any of the icons. I possibly thought of changing my resolution to 1024x768 and then back to 1600x1200 to see if something might just "fix itself". Sooner or later it'll get figured out! ;)

---

### Post by andyho on 2007-08-03
Solved it, for the most part... for anyone else that might have the same issue....

System Settings--> Appearance--> Icons--> Advanced

Change the size from 48 to desired size! :)

It still seems like the space "between" the icons is larger than it should be, but I'm pretty sure that's adjustable as well!

---

### Post by Gmbrdilos on 2007-08-03
I just realized from your screenshot that you are using KDE in which case I would doubt that you would be using nautilus.

---

