---
title: "Switching between desktops with scroll-button on mouse"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2007-12-21
I've just installed the i386 version of 7.10 on my partner's machine; all is well with one small but irritating problem.

When the cursor is over the desktop background any movement of the scroll-button causes the desktop to very quickly flip back and forth between the left and right workspaces, accompanied by a small popup box in the middle of the screen with a left and right arrow displayed.

This is very annoying...!  (And - fortunately - it doesn't happen on my 64-bit install of 7.10).

I can't find mention of the application that the mouse scroll-button is activating to do this.  Her mouse is a fairly basic PS/2 variety with three buttons (one of which is of course the scroll-button giving 5 axes in total).  The mouse is working fine with everything else, including the scroll function.

How can I disable the application that's causing the workspaces to scroll left and right like this, or otherwise stop it happening?

Thanks,
Al

---

### Post by Lord_Dicranius on 2007-12-21
Checkout [this thread](http://ubuntuforums.org/showthread.php?t=601716), let us know if it works out for you :)

---

### Post by Prodromoi on 2007-12-21
Ah... I thought we had it for a second there.  I don't think ccsm is installed on the machine however.  There's no launcher for it (that I can find anyway) and when I type ccsm in the terminal I get this:

The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found

Is there another program similar to ccsm that it might be?

---

### Post by Lord_Dicranius on 2007-12-21
compizconfig-settings-manager is what we're looking for.  Use the command in that error
```
sudo apt-get install compizconfig-settings-manager
```
...to install it.  "CCSM" is the acronym for it, and also what they use as the name of the app :)

---

### Post by Prodromoi on 2007-12-21
Worked like a charm.
Many thanks.

---

### Post by Lord_Dicranius on 2007-12-21
No problem.  Glad it worked out :)

---

### Post by Prodromoi on 2007-12-26
I've just had to resurrect this thread since a very similar (and probably related) problem has cropped up.

I had to reconfigure my xorg settings while I was trying to get my twin-head monitor setup going (which is running the 64-bit version of 7.10).  Obviously a few settings were over-written; I've fixed most but this one remains.

The scrolling desktop switcher re-activated.  I un-checked the "desktop switcher" option in CCSM to prevent it, and now I can no longer switch desktops with the mouse scroll button, which is great.

But...

The 'two arrow' pop-up still appears in the middle of the screen when I switch desktops manually with the workspace icons in the bottom right of the screen, and the scroll animation when switching still activates, instead of the "instant switch" which is what it was doing before.

Is the "desktop switcher" part of CCSM not fully disabled, or is there something else wrong here?  (When I unchecked this option on a 32-bit machine, it instantly disabled the pop-up window and scrolling animation as well as the use of the scroll-wheel.)

(And furthermore, I've compared the CCSM settings on both machines; they're identical except for dbus which isn't enabled on the 64-bit machine, but I wouldn't think that's anything to do with this.)

---

### Post by Prodromoi on 2007-12-26
(Bumping the thread to get some new views and hopefully some suggestions...!)

---

### Post by LowSky on 2007-12-26
are you sure its diabled?

check under viewport something or other (im on a windows machine and can not remember the correct name, but its all the way to the right in the same grouping as desktop switcher, I know is sounds funny but compiz has two plugins that do nearly the same thing.

---

### Post by Prodromoi on 2007-12-27
The only effects under "desktop" that are enabled are:
Desktop Wall and Expo

Under Effects, all I have enabled is:
Animations, Fading Windows and Window Decoration.
(I tried disabling Animations to no effect.)

---

### Post by RomeReactor on 2007-12-27
Hi. To disable the arrows, open Advanced Desktop Effects Settings, press the "Desktop Wall" plugin button, go to the second tab ("Viewport Switch Preview") and uncheck "Show Viewport Switcher Preview".

---

### Post by Prodromoi on 2007-12-27
Excellent, thank you.  That's got rid of the arrows.  I'm now hunting in the various settings for a way to disable the scrolling.  Haven't found it yet... any ideas?

---

### Post by RomeReactor on 2007-12-27
You could go to CCSM->Desktop Wall->Viewport Switching and decrease the seconds it lasts (though that made it more annoying to me). You could try disabling "Desktop Wall" altogether, and go into General Options->Desktop Size and change the "Number of Desktops" to whichever number of desktops you're used to having. In my case it resulted in a very slow workspace switching process, though.

---

### Post by Prodromoi on 2007-12-27
I'm beginning to wonder if there's a bug in the switcher.

On the i386 computer with 7.10 installed, the Viewport Switcher is disabled; however in Desktop Wall, the viewport switcher preview *is* enabled - but the arrows are not displayed, and the workspaces instantly change without any scrolling animation.  (And there's no noticeable delay.)

On the 64-bit install I've had to disable Viewport Switcher and disable viewport switcher preview in Desktop wall.  This has got rid of the arrows, but the scrolling animation remains.

---

