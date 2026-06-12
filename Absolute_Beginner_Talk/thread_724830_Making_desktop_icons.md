---
title: "Making desktop icons"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-15
I know how to make the desktop icons but their are some problems I am having.

and sorry I am slow with linux based OS

for example I have installed a psxe emulator and I want to make an icon of it to launch from my desktop.

the problem I have is that I am unsure of what file I have to look for to launch it. All I know is that I can type the name in the terminal and it will launch automatically. I am wonder what would be the type of file that i need to look for that launches a program in this ubuntu os. ( for instance windows has .exe files.

My second problem is I want to put my own pictures as the icon.

When I select a picture to use it just shows up as a a piece of paper rather than the picture I selected. Does the picture have to be in a certain format like I was using jpg. for this one haven't tried others. Also if I can add a picture over folders for it to show up

another thing to add since I am talking about customization I wanted to know if their are anyone desktop theme or also known as styles that look kind of like window versions. 

what I mean is I download one theme on my windows OS that had many extra add-ons already in it like weather report tab that appears on the top or one that shows my computer cpu usages or temperature my computer is running at. maybe even a built in player that pops up when the mouse is over it. 

actually let me just show you one here is the link

[http://www.wincustomize.com/skins.aspx?skinid=2621&libid=31](http://www.wincustomize.com/skins.aspx?skinid=2621&libid=31)

something close to that for this OS. I know you can download them seperate but does anyone have a link to one that has it as a package. the only desktop themes I see are ones that only change the color but nothing with add-ons or a cool drop down menu.

Sorry but I like eye candy


also if someone can tell me a good program to use for desktop customizing

---

### Post by PeterJS on 2008-03-15
> **RyviusRan said:**
> I know how to make the desktop icons but their are some problems I am having.

and sorry I am slow with linux based OS

for example I have installed a psxe emulator and I want to make an icon of it to launch from my desktop.

the problem I have is that I am unsure of what file I have to look for to launch it. All I know is that I can type the name in the terminal and it will launch automatically. I am wonder what would be the type of file that i need to look for that launches a program in this ubuntu os. ( for instance windows has .exe files.

Extensions really aren't used as much in linux as they are in windows, there really isn't an executable extension. If you want to know if something is an executable check it's file permissions, if it has execute permission it's an executable.

> 
My second problem is I want to put my own pictures as the icon.

When I select a picture to use it just shows up as a a piece of paper rather than the picture I selected. Does the picture have to be in a certain format like I was using jpg. for this one haven't tried others.

I would think jpegs should work but I've never tried them. Most of the icons shiped with packages come as png, or svg. You might try converting your icon to one of those formats with GIMP.

> 
another thing to add since I am talking about customization I wanted to know if their are anyone desktop theme or also known as styles that look kind of like window versions. 

what I mean is I download one theme on my windows OS that had many extra add-ons already in it like weather report tab that appears on the top or one that shows my computer cpu usages or temperature my computer is running at. maybe even a built in player that pops up when the mouse is over it. 

actually let me just show you one here is the link

[http://www.wincustomize.com/skins.aspx?skinid=2621&libid=31](http://www.wincustomize.com/skins.aspx?skinid=2621&libid=31)

something close to that for this OS. I know you can download them seperate but does anyone have a link to one that has it as a package. the only desktop themes I see are ones that only change the color but nothing with add-ons or a cool drop down menu.

Sorry but I like eye candy

Gnome-look.org has about all the gnome skinning and themeing stuff you want. I'll take a look at the theme you posted and see if I can dig up anything similar.

As for applets, gnome comes with a lot of stuff for the panel built in, right click on a panel and check out the stuff in add to panel.

And don't feel guilt about loving eye candy, I know I do, shh :)

EDIT in response to an EDIT

> 
also if someone can tell me a good program to use for desktop customizing


Gnome it self does all the themeing, take a look at System > Preferences > Appearance.

---

### Post by PeterJS on 2008-03-15
How about these?

Overglossed Blue:
[http://gnome-look.org/content/show.php?content=74813](http://gnome-look.org/content/show.php?content=74813)
and
[http://gnome-look.org/content/show.php?content=74873](http://gnome-look.org/content/show.php?content=74873)
Blue Heart:
[http://art.gnome.org/themes/gtk2/1125](http://art.gnome.org/themes/gtk2/1125)
MidnightBluePlastic:
[http://gnome-look.org/content/show.php?content=66389](http://gnome-look.org/content/show.php?content=66389)

---

### Post by RyviusRan on 2008-03-15
well when you check out that theme you will know what I mean by customizing. if there was some way to use wine to open that windows desktopx program to use their theme I would but sadly I doubt that.

also isn't there a way to make some type of file that i could click on that would send a command to the terminal to run the program? 

and I will try converting the picture to see if it will work.

---

### Post by RyviusRan on 2008-03-15
wow you were fast with that. desktops look ok, I saw one on that site that I wanted but sadly the link has over bandwidth use so a no go on downloading it was an animating lighting theme.

I know most of the add-ons I was talking about can be found just by going through some settings, but it would be cool to just have them on the desktop so i can just run my mouse over it and it pops out like an extra toolbar or window.

---

### Post by PeterJS on 2008-03-15
> **RyviusRan said:**
> 
also isn't there a way to make some type of file that i could click on that would send a command to the terminal to run the program? 


You could certainly put a script, link to a script, or a .desktop file pointed at a script, on your desktop that you could double click to run.

Well... I was going to suggest screenlets... but it looks like they've completely up and disappeared from the internet entirely.

For monitors you might try looking in to Gkrellm or conky, both of which are in the repositories.

---

### Post by RyviusRan on 2008-03-15
yah i figured out the hard way while adding

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

and using the commands

wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O-

I got couldn't find HTTP

so that means I can't use screenlets?



also is it possible to run a windows desktop theme manager with wine and use that?

also can u tell me how or give me a link to a tutorial on how to make a script to run a program for use as a icon?

---

### Post by RyviusRan on 2008-03-15
bump

---

### Post by PeterJS on 2008-03-15
> **RyviusRan said:**
> yah i figured out the hard way while adding

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

and using the commands

wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O-

I got couldn't find HTTP

so that means I can't use screenlets?

Looks like it for now, hopefully somebody new will crop up with a repo or a fork soon.

> 
also is it possible to run a windows desktop theme manager with wine and use that?

You can install .msstyle themes in wine, but they only apply to wine applications. Also because of the monolithic (and X free) nature of the windows graphics system it has no X window managers, so even if you could get a theme you like working there would be no WM to use it with.

> 
also can u tell me how or give me a link to a tutorial on how to make a script to run a program for use as a icon?

Simple scripts are easy to write, it's exactly like you're using a terminal other than the header.
```

#!/bin/bash
ls

```
Is a very simple script that will just run ls. You can put any number of commands in there you want and it will run them one at a time in order, you can certainly do more complicated things if you want, but there's no need to do anything very complicated. The TLDP guide is pretty good:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

For the icon, right click on the desktop, select create launcher. Next to the command box, is a browse button, click that and go find your script, to set the icon click on the icon itself in the upper left corner. Fill in the rest and you're done.

---

