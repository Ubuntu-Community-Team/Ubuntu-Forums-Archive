---
title: "Gimp question"
date: 2010-09-05
forum: Art &amp; Design
---

### Post by jcolyn on 2010-09-05
I asked this question in another forum but as yet have not received an answer.

Below is a snapshot of my desktop with Gimp 2.6.10 loaded. Notice there are 3 docks.

How can I eliminate the center dock and move the menu to the toolbox?

I have Gimp 2.6.10 on a Debian machine with it done that way so it is possible. I just haven't been able to figure it out.

I also noticed on the Gimp website at least 2 of the Linux screenshots have it done that way.



[IMG]http://fotografs.zenfolio.com/img/s10/v17/p711125938-4.jpg[/IMG]

---

### Post by mcduck on 2010-09-06
Older Gimp versions had the menu in both the image window and the toolbar. It was then removed from the toolbar as it's usually too small to fit the menu anyway, and having the menu in two places was pointless. 

(You can't eliminate the image window, that's where your image gets loaded so without it Gimp wouldn't be any use for you)

If you just want to save some screen space, I recommend moving everything else than just the tools (the Paintbrush dialog, in your screenshot) from the tool bar to the dock on the right side. That allows you to shrink the toolbar into a small, two-icon wide dock that doesn't get in your way.

---

### Post by jcolyn on 2010-09-06
> **mcduck said:**
> Older Gimp versions had the menu in both the image window and the toolbar. It was then removed from the toolbar as it's usually too small to fit the menu anyway, and having the menu in two places was pointless. 

When I first started using Gimp several years ago it had multiple panels on the desktop at startup. I'd arrange then but at next startup they'd be back all over the desktop.

> **mcduck said:**
> (You can't eliminate the image window, that's where your image gets loaded so without it Gimp wouldn't be any use for you)

Somehow Debian has. I installed Lenny on another computer. After update to 2.6.10 it only had the layers/channels and toolbox. No image panel. I can open images by going to the toolbox and clicking file-open.

> **mcduck said:**
> If you just want to save some screen space, I recommend moving everything else than just the tools (the Paintbrush dialog, in your screenshot) from the tool bar to the dock on the right side. That allows you to shrink the toolbar into a small, two-icon wide dock that doesn't get in your way.

The main reason for wanting to get rid of the image panel is because when closing an image it usually ends up at different locations on the desktop.

---

### Post by mcduck on 2010-09-07
If you really have the dialog on the toolbox, and it's latest version of Gimp, then I suppose it might still be possible, but the option to do that is removed and you only get it on your Debian setup because it's an upgraded system and the config files for Gimp are old. Or something like that... :D

Try copying the config files to your Ubuntu system to see if it works. Other than that I don't see any way how you could configure it that way, as there is no such option in Gimp any more.

What comes to dialog layout & window positions, you simply need to arrange everything the way you like, and then save your window layout (Edit/Preferences, and under Window Management click the Save Window Positions Now -button).

---

### Post by Fri13 on 2010-09-07
Yes, the older GIMP (2.4.x series) had the menubar on the toolbar as well. But in the newer one the Image window has the menubar. It is much wiser as we now have just one menubar and the settings for the application went to more logical places.

---

