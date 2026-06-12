---
title: "Icon Library - a little app to view icon themes"
date: 2008-09-07
forum: Art &amp; Design
---

### Post by | MM | on 2008-09-07
Hi,

I have made a little python application that makes it easy to browse installed icon themes.  I call it Icon Library.  Perhaps something similar already exists...

It's basic at the moment but its good for searching icon themes.  If you are looking for a particular icon to use in an app you are developing, i think Icon Library would be useful.  Also if you are an icon artist i think it would be good for checking your icon coverage and design consistency.

I've attaced a zip file for those that would like to play with Icon Library.  There are two .py files and a .pyc.  Just extract the files, go to where they are extracted, then run icon-library.py, so...

```
python /path/to/icon-library.py
```

I am open to suggestions, but i am learning python/gtk so i can't promise i'd be able to do anything too complex.  Bug reports are also welcome.

I've attached a screenshot as well...

---

### Post by MadsRH on 2008-09-07
Great work! :)

Havn't tried it yet, but it looks great.
[B]
//MadsRH[/B]

---

### Post by | MM | on 2008-09-07
> **MadsRH said:**
> Great work! :)

Havn't tried it yet, but it looks great.
[B]
//MadsRH[/B]

Cool let me know what you think.

---

### Post by BBgrave on 2008-09-07
**[Buy Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[Sell Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by ad_267 on 2008-09-07
That's pretty cool.

I had one issue where I had a png icon that had no data so the program just kept saying it was loading but in the terminal I got this error message:

```

Traceback (most recent call last):
  File "/home/adam/iconlibrary1/icon-library.py", line 112, in init_important_stuff
    self.IconDB = IconDatabase(Theme)
  File "/home/adam/iconlibrary1/icon-library.py", line 348, in __init__
    pb0 = Theme.load_icon(ico, 16, 0)
gobject.GError: Image file '/home/adam/.icons/Oxygen-Gnome/16x16/devices/gnome-dev-printer-network.png' contains no data

```

There probably should be some exception handling that just skips the file if it can't load it.

Also one feature that would be useful is a button that lets you go back to the original front page to select a different icon theme. Other than that it's pretty good! I'll probably use it a bit because I like trying out different icon themes.

---

### Post by OutOfReach on 2008-09-07
Wow the program looks good (I'm about to download), very creative.
EDIT: Just tried it, no complaints here. :)

---

### Post by | MM | on 2008-09-08
Hi,

@ad_267:  Hopefully i've fixed your problem, let me know as i none of my themes seem to cause that error.

I've also added the ability to change themes, its a bit rough and ready but it works.  To change theme; click the folder icon that lives in the top left corner.

I also changed the way the context filter is determined so it works properly when using keyboard up/down keys.

I was thinking, the ability to change the list background color could be useful, to see what icons look like against dark or light colors.  SO that might be something i work on.

---

### Post by | MM | on 2008-09-08
Woops, forgot to add the files ...

---

### Post by ad_267 on 2008-09-08
Awesome yup that fixed it.
Now I get:
```
Error loading icon gnome-dev-printer-network, skipping...
```
and it works fine. 

Now I just need to tell the icon theme author there's a broken icon. :)

---

### Post by | MM | on 2008-09-08
> **ad_267 said:**
> Awesome yup that fixed it.
Now I get:
```
Error loading icon gnome-dev-printer-network, skipping...
```
and it works fine. 

Now I just need to tell the icon theme author there's a broken icon. :)

:) glad to hear!

---

### Post by adewale on 2008-09-08
This project might be of interest to you. [https://launchpad.net/epidermis/](https://launchpad.net/epidermis/) 
Your program will be of great contribution

---

### Post by Flimm on 2008-09-08
> **adewale said:**
> This project might be of interest to you. [https://launchpad.net/epidermis/](https://launchpad.net/epidermis/) 
Your program will be of great contribution
Wow, you beat me to it!
As I was reading these posts, I thought to myself: "I've been needing something like this for my project, [Epidermis](https://launchpad.net/epidermis/)." I've been wondering whether it would be easy to code an automatic preview generator for themes, like the GNOME appearance app does, and you (MM) look like you know your way around icon themes, python and pygtk. I would really appreciate your feedback and possibly help on my larger project.:)
PM me soon?

---

### Post by SphereCat1 on 2008-09-08
Thanks a lot, | MM |! This will come in very handy while I'm working on the icons for [TWiMU]("tinyurl.com/TWiMU"), Great Job! :)

SphereCat1

---

### Post by | MM | on 2008-09-08
Hi,

I added the ability to change the background color of the icon view.  There is a little set of color swatches in the bottom right corner.  Just click whichever is desired and it'll change the color automatically.  This could be useful for seeing how icons with transparency come across in darker themes... or at least a theme color other than your system defualt.

At the moment its limited to the thematic default base color for a gtk.TreeView with state=gtk.NORMAL_STATE.  There are also two other arbitrary colors which i have made pure white and dark gray.

See if it still works for you people.  I'm interested to know if i get the right default treeview background color.  Also i use cairo to draw the color swatches, and i restricted it to systems that have cairo 1.4 or newer (just to be safe).

There's a screenshot attached.

---

### Post by | MM | on 2008-09-09
I fixed some problems.

Also, does anyone know a reliable way to determine the default background color of a treeview?  The method i used returns different results for themes based on clearlooks and murrine....

Regrads,
Matthew

---

### Post by adewale on 2008-09-09
Great program, thanks. I little problem, i feel the folder icon could be changed to something more descriptive. I didn't even know i could view other icon themes until i clicked on the folder by error.

---

### Post by | MM | on 2008-09-10
> **adewale said:**
> Great program, thanks. I little problem, i feel the folder icon could be changed to something more descriptive. I didn't even know i could view other icon themes until i clicked on the folder by error.

OK i'll have a think.

Oh, and i fixed some more glitches...

---

### Post by Orlsend on 2008-09-10
Hey thats my real life Bud project, Goo to hear it is getting around :D

---

### Post by pokemon_jojo on 2008-11-25
great great great application!!!!! it's really usefull for made icon theme.

Is it possible when you load theme, to choose 3 different way

- instaled icon theme (like actually)
- uninstaled icon theme package (often tar.gz)
- icon theme repertory (for help icon theme creator who want a preview of there theme without to mad a tar.gz and add it to them and active theme)

thanks a lot, i will use it for my new icon theme :)

---

### Post by niaz12 on 2008-11-26
If you are looking for a particular icon to use in an app you are developing, i think Icon Library would be useful. Also if you are an icon artist i think it would be good

---

### Post by niaz13 on 2008-11-28
I've been needing something like this for my project, Epidermis." I've been wondering whether it would be easy to code an automatic preview generator for themes, like the GNOME appearan

---

### Post by kwwii on 2009-10-29
Could you put this in launchpad? I'd like to add a link to your stuff in the artwork teams part of the wiki.

---

### Post by macvr on 2009-10-29
> **kwwii said:**
> Could you put this in launchpad? I'd like to add a link to your stuff in the artwork teams part of the wiki.

It's already on launchpad ;)
[https://launchpad.net/icon-library]("https://launchpad.net/icon-library")

---

