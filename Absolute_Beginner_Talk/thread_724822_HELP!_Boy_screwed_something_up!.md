---
title: "HELP! Boy screwed something up!"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by robfindlay on 2008-03-15
I had compiz-fusion installed and after a few days found it buggy and uninstalled it.

Now now none of my windows have title bars! 

What do I need to reinstall?? 

I even tried using the theme manager for gnome to pick a new theme to no avail! 

HELP!

---

### Post by iansane on 2008-03-15
try system>preferences>appearance>visual effects and set it to none. Or try changing the appearance of the window from the theme tab.

I had a problem with compiz when special effects were used my title bar went away and had to use the menu key and arrow down to close a window. Seems like it would have changed back after unintstall though

---

### Post by herbster on 2008-03-15
Try this in terminal:

```
metacity --replace &
```

---

### Post by robfindlay on 2008-03-15
> **herbster said:**
> Try this in terminal:

```
metacity --replace &
```

Wow that did it, is that a permenent fix?

---

### Post by herbster on 2008-03-15
Probably not. Do what Iansane has advised as most likely you have the "Visual Effects" still set to being used. At least we know it just a window manager issue, no biggie.

---

### Post by robfindlay on 2008-03-15
> **herbster said:**
> Probably not. Do what Iansane has advised as most likely you have the "Visual Effects" still set to being used. At least we know it just a window manager issue, no biggie.


Problem is now I don't get any transparency back and if I do the "extra" visual effects I lose my borders again :-(

---

### Post by Fred_E _krugar on 2008-03-15
If you are going to use some of the effects you will have to do:


emerald --replace

---

### Post by robfindlay on 2008-03-15
> **Fred_E _krugar said:**
> If you are going to use some of the effects you will have to do:


emerald --replace

I do that and I lose my borders again!

---

### Post by robfindlay on 2008-03-15
> **robfindlay said:**
> I do that and I lose my borders again!

So I put compiz fusion back in and the cube etc.  now all of a sudden I can't draq windows.....what setting am I missing in the "advanced desktop settings"

---

### Post by robfindlay on 2008-03-15
Bump Bump -- Help Help ???

---

### Post by robfindlay on 2008-03-15
Bump again....any idea why I can no longer drag windows  around with my Mouse with compiz-fusion installed?

---

### Post by Sef on 2008-03-15
1) Don't bump unless 24 hours have gone by.   More frequently than that can get you an infraction.  Yes having problems is frustrating, but patience is required to resolve them.

2) What are your system specs?  This problem could have been already solved in another thread.  You might want to googe or use [Crunchbang's Ubuntu Search Engine]("http://crunchbang.org/ubuntu-search-engine/").

3) What version of Ubuntu are you using?

---

### Post by Tyke91 on 2008-03-15
my advice is just to completely uninstall/purge compiz-fusion from your system, then reinstall agian

---

### Post by dasunst3r on 2008-03-15
It's not in Advanced Desktop Settings -- it's in "Appearance."  Under "Visual Effects," choose "None."

---

### Post by justsomedude on 2008-03-15
> **robfindlay said:**
> So I put compiz fusion back in and the cube etc.  now all of a sudden I can't draq windows.....what setting am I missing in the "advanced desktop settings"

You're missing the "Move Window" plugin.

---

### Post by kamitsukai on 2008-03-15
> **robfindlay said:**
> Wow that did it, is that a permenent fix?

To make it permanent when you log out make sure you select "save session" or somthing like that in the options box that appears =P

---

### Post by octopuskevin on 2008-03-15
Hi Rob, the problem I think you are having is that when you have compiz fusion enabled it is also looking for the emerald window manager [that which draws the borders] However when your using metacity [the default] everything is fine as it uses metacity for rendering the gui and gtk for the windows....

try this out: install the fusion-icon deb from here 
[http://ubuntuforums.org/showpost.php?p=3163821&postcount=8](http://ubuntuforums.org/showpost.php?p=3163821&postcount=8)

this will put a blue cube on your notification area..
if you right click on it, choose compiz as the window manager, and for windows decorator choose gtk

hopefully that fixes the problem? if everything is dandy, add 'fusion-icon' to your 'system'-->'preferences'-->'session' so that it loads on boot.

- kevin

---

