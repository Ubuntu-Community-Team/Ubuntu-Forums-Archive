---
title: "I could do with a pointer on managing desktop colour in Arch/Openbox - (Xfce)?"
date: 2009-01-30
forum: Arch and derivatives
---

### Post by handy on 2009-01-30
I spent some time re-installing Openbox on Arch today.  It sure would have been quicker if I hadn't of deleted all of the config files months ago.

I think I'll probably stick with Openbox & the Xfce-panel.  It is very similar to straight Xfce once it's set up & definitely faster.

I'm not done yet, but I have found some lighter, faster & more fully featured app's to use than I was using.  

I'm giving Beaver a go as a text editor, it is light, fast & *tabbed*, which puts it ahead of leafpad & mousepad, the only problem I have found with it so far is that it doesn't have a facility to be able to see hidden files, though you can type the path to a file.  

GQView is also light, extremely fast & a looks to be a full featured image viewer. I'm so glad that I have at last found the right one (until the next righter one comes along ;-)).

I have openbox-configuration-manager, lxappearance, gtk-change-theme & gtk-theme-switch2 but only through Xfce Settings, by choosing to allow Xfce to manage the desktop can I configure the desktop colour.

Naturally I don't want Xfce to manage the desktop I want Openbox to do that.

My theme from Xfce is working fine, apart from the title bar of windows & the RMB Openbox menu. I'll explain a little further down the page why this is happening.

Really this looks to be the only problem I have left to solve, & I can't for the life of me see how to do it.  It is not controlled in the gtkrc file, or the ~/.config/openbox/ directory, unless there is a way of setting the desktop in the autostart.sh file; I have tried using just the following line in autostart.sh, but it had no effect:

*BG="#000000"*

What I think is probably responsible for the problem, is that Openbox Configuration Manager does not list the Aero theme that I am using.  All of the other GTK2 compatible theme handlers I listed previously do see it.  

So I am using Artwiz-boxed in the Openbox conf' man'.  I have looked in the Artwiz-boxed theme & can see nowhere to edit the colour of the desktop.  So I'm lost, apart from my next step which will be to see if there is an Openbox version of Aero floating around on the web.

So that's my long winded (as usual :-)) question; can anyone enlighten me as to how I can set the colour of the desktop, without using Xfce to do it?

---

### Post by handy on 2009-01-30
Ok, I got it. :-D

I just realised that I was misreading this section of the autostart.sh file; all, but half of one line, I had deleted:

[I]# Set a background color
BG=""
if which hsetroot >/dev/null; then
    BG=hsetroot
else
    if which esetroot >/dev/null; then
   BG=esetroot
    else
   if which xsetroot >/dev/null; then
       BG=xsetroot
   fi
    fi
fi
test -z $BG || $BG -solid "#303030"[/I]


So I put it all back & changed the numbers at the end to "#000000" & I got the black desktop, which makes my eyes very happy. 8)

---

### Post by handy on 2009-01-30
Aero is available for quite a few different DE's & WM's but not specifically for Openbox, probably because it can use GTK.

I can handle the title bar & menu colours I've got.  Thankfully I don't have to spend all the hours editing another gtkrc to get the rest of it how my eyes like it.

---

### Post by handy on 2009-01-30
I was still experiencing some slowness with Terminal; when dragging its window to resize it, it lags terribly. Also, when using the expand/shrink gadget in the title bar, it takes 2 -> 3 seconds.  (Which is certainly an improvement from what it was like before the Catalyst driver upgrade in December.)

If I have programs open in each of my six desktops, including Terminal on one of the desktops, & then move from one to the other, they are all instantaneous except for the one with Terminal in it which takes 2 -> 3 seconds.

So I thought I'd try Sakura, as it is fast, light & tabbed.  

I found Sakura to be lightening fast at everything; it is not at all affected by this Xorg/Catalyst/Xfce bug.

Which means that today, in changing from using the Xfce DE, to using Openbox, with the continued inclusion of my xfce-panel, replacing Terminal with Sakura, grabbing Beaver for its speed & tabs, GQView for its speed & abilities, I have managed to leave the impediments of that Xorg slow down bug behind.  Which is nice. 

I appreciate that this situation would be making Openbox seem even faster than Xfce than it actually is, (or was,) I think.

---

### Post by mips on 2009-01-30
I used to love sakura, no idea why I don't use it anymore.

---

### Post by handy on 2009-01-30
> **mips said:**
> I used to love sakura, no idea why I don't use it anymore.

I just configured Xfce to use Sakura also; while I was there (in Xfce) I noticed (after using my Openbox Xfce look alike for much of the day), just how much slower Xfce is at the moment.  

Everything is just happening instantly under Openbox. :-D

---

### Post by gjoellee on 2009-01-30
You could have used "feh" ```
sudo pacman -S feh
```

---

### Post by handy on 2009-01-30
> **gjoellee said:**
> You could have used "feh" ```
sudo pacman -S feh
```

Thanks for your suggestion, though from what I remember, people use feh for desktop backgrounds & such in Openbox; (I know it is far more capable than that.) :-)  

I don't use a desktop background, & again if my memory serves, feh is a Terminal app', & I do prefer a GUI image browser/viewer.

---

### Post by chucky chuckaluck on 2009-01-30
handy, do you always use a black background?

---

### Post by handy on 2009-01-30
Yes, it seems to have become always. :-)

---

### Post by handy on 2009-01-30
I'm confused again!

Why, when I rearrange the order of sub-menu items of the Openbox RMB menu, does it not have any effect?

I have used both the OBMenu editor & a text editor, but the only items that I can move are the individual menu items.

In case that wasn't clear; moving the *File Managers*, sub-menu item, from the bottom of the list up to the top, above the *Accessories* sub-menu item, has no effect.

I hit the *Reconfigure Openbox* item as well for all it is worth.

---

### Post by handy on 2009-01-30
Ok, I'm obviously slowing down in my old age. ;-)

I just found by trial & error, that moving the sub-menu items around in their list positioned below the following line in the menu.xml file is the way to get results:

*        <menu id="root-menu" label="Openbox 3">*

I knew that there had to be logic involved in the process somewhere...

---

