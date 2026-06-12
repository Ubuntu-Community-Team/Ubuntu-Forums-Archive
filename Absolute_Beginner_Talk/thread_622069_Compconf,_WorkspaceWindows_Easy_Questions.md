---
title: "Compconf, Workspace/Windows: Easy Questions"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by DMBrazil on 2007-11-24
Three easy ones for everyone that have stumped me all morning....

1. I getting used to terminal but am not yet confiedent, I know I had to get to a compconf screen to change some things before but i CANNOT remember the name or command. For some reason i think it was 2 commands... something about root, and then comp.conf .

2. In customizing my panels i deleleted my workspace switcher thing that comes standard on the bottom right and now i dont know how to get it back. 

Also 

Im currently fighting with compiz to work but i was wondering if their is any other program that gives you some of those abilities. 

ALL I WANT IS: 
1. See my 4 workspace in a row in one view
2. See all my active windows... either in a row, filling up the screen, or like iTunes CoverArt
3. Be able to change my backgrounds on etc different workspace.

Anyone?

THANKS!

---

### Post by corney91 on 2007-11-24
2. Right-click on the panel and select 'add to panel.' The workspace should be in there - just drag it where you want.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-24
> 
1. I getting used to terminal but am not yet confiedent, I know I had to get to a compconf screen to change some things before but i CANNOT remember the name or command. For some reason i think it was 2 commands... something about root, and then comp.conf .

It's called Compiz Config Settings Manager or simply ccsm.
```

sudo apt-get install compizconfig-settings-manager

```
To run it after you've installed, type this on terminal or by pressing Alt+F2
```

ccsm

```


> 
2. In customizing my panels i deleleted my workspace switcher thing that comes standard on the bottom right and now i dont know how to get it back. 

[LIST]
[*]Right click empty space on your panel.
[*]Choose "Workspace Switcher"
[/LIST]


> 
Im currently fighting with compiz to work but i was wondering if their is any other program that gives you some of those abilities. 

ALL I WANT IS: 
1. See my 4 workspace in a row in one view
2. See all my active windows... either in a row, filling up the screen, or like iTunes CoverArt
3. Be able to change my backgrounds on etc different workspace.

[LIST=1]
[*]In "Compiz Config Settings Manager", navigate to:
"General Options" -> "Desktop Size" -> Experiment with option available there.
[*]In "Compiz Config Settings Manager", navigate to:
"Scale Addons" -> Select this options if not yet selected.
[*]I've seen this somewhere, but I forget, try the official compiz forums.
[/LIST]

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-24
Ouch, you got me corney91 :)

Addition, here's compiz's official forums: [http://www.compiz-fusion.org/]("http://www.compiz-fusion.org/")

---

### Post by DMBrazil on 2007-11-24
WOW thanks for the quick response... 
and WOW Im stupid! XORG.conf not CompConf 

Got my workspace panel up and running.

The XORG.conf question was unrelated(kinda)  to compiz so im sorry for the confusion.

I have everything I need for the Compiz to work but when i Atl + F2 and type    compiz --replace  nothing happens. So reading in the other forums I found I need to go into my XORG.conf and change my Video setting from "VESA" to "i810"  thats why i need the XORG.conf... anyidea what im talking about?

Also IF my dell 1100 cant run compiz, is there any other programs similar to it??

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-24
My bad, I thought it's compiz, because in your 3rd question, AFAIK, it's can only accomplish by compiz.

Maybe it's not compconf, but xorg.conf is it?
If so, there's tutorials on ubuntuforums to get compiz up and running with intel cards.
Basically, you need to edit the file /etc/X11/xorg.conf and change the "vesa" driver to "i810" or "intel" driver.

There's program "similar" to compiz, but only gives shadow and fade in-out to menu and windows, it's called xcompmgr.
```

sudo apt-get install xcompmgr

```
You can read the manual to set the options for xcompmgr.
```

man xcompmgr

```

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-24
Well, your 3rd question indeed talking about compiz, I feel dizzy :) , what a day.
I thought the questions were linked each other, sorry.

---

### Post by DMBrazil on 2007-11-24
> **Milk & Toast & Honey said:**
> My bad, I thought it's compiz, because in your 3rd question, AFAIK, it's can only accomplish by compiz.

Maybe it's not compconf, but xorg.conf is it?
If so, there's tutorials on ubuntuforums to get compiz up and running with intel cards.
Basically, you need to edit the file /etc/X11/xorg.conf and change the "vesa" driver to "i810" or "intel" driver.

There's program "similar" to compiz, but only gives shadow and fade in-out to menu and windows, it's called xcompmgr.
```

sudo apt-get install xcompmgr

```
You can read the manual to set the options for xcompmgr.
```

man xcompmgr

```



Thanks man! 
Its my second day with Ubuntu... can you tell :lolflag:

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-24
I'll guide you to change the xorg.conf to use the intel driver, since I can't found the howto. I'm sure there's some somewhere in this forums though.

The intel driver apply to i810, i815, i830, i845, i855, i865, i915, i945 and i965 chipset.
So your i810 card should be supported by this driver.

[LIST=1]
[*]Make sure the driver is installed, type this in terminal.
```

sudo apt-get install xserver-xorg-video-intel

```
[*]Also in terminal, type:
```

sudo gedit /etc/X11/xorg.conf

```
Find the line similar to this (in Section "Device"):
```

Driver  "vesa"

```
Change to:
```

Driver  "intel"

```
[*]Save the file and your documents (if any), and close any other programs.
[*]Log off.
[*]If suddenly the fonts looks bigger than usual, consult [this thread]("http://ubuntuforums.org/showthread.php?t=583915"), specifically [this post]("http://ubuntuforums.org/showpost.php?p=3673907&postcount=12") to fix it.
[*]After you change to intel driver, you should be able to use Desktop Effect, navigate to:
```

System -> Preferences -> Appearance -> Visual Effect's Tab -> Choose between "Normal" or "Extra".

```
[/LIST]

---

### Post by corney91 on 2007-11-24
> **Milk & Toast & Honey said:**
> 
Also in terminal, type:
```

**gk**sudo gedit /etc/X11/xorg.conf

```


Don't want to get into bad habits early :)
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Sorry:I'm in a picky mood:p

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-24
I just know that. Gotta change my habbit now :) .
Thanks for the article, corney91, it's a good reading.

---

