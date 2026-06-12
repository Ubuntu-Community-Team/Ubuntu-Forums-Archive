---
title: "Add launchers to the Right-Click Menu?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by berylator on 2007-04-02
Hi everyone

I know about [nautilus-scripts]("http://http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/").

However, I would like to add launchers to the "first level" of the right-click menu to be able to right-click on the desktop, then choose e.g. "firefox" which will execute the command "firefox www.google.com".

Does anyone know how to do that? Adding the correct symbols would be awesome, too.

Thanks,

berylator

---

### Post by berylator on 2007-04-03
anyone? :(

---

### Post by zvacet on 2007-04-03
Download **nautilus actions**.here is link and some examples.
[http://ubuntuforums.org/showthread.php?t=91377&highlight=nautilus+actions]("http://ubuntuforums.org/showthread.php?t=91377&highlight=nautilus+actions")

---

### Post by berylator on 2007-04-03
> **arnieboy said:**
> the only feature that this editor lacks is the ability to edit right click menus in nautilus when NO files or folder are selected. 
I have added a feature request on the app's homepage and if this is implemented, it will make it a complete menu editor for nautilus and I will personally see to it that **this gets into ubuntu universe**.

As you can see, the program does not provide the feature I am looking for, thanks for your effort though! The Linux community is the greatest support-center ever :KS 

Does anyone else have an idea?

berylator

---

### Post by arbulus on 2007-04-03
I'm not sure if you can/how to do that in Gnome (I assume you're using Gnome since you mentioned Nautilus).  But it sounds like you might be interested in using Fluxbox as your window manager.  The entire main menu for Fluxbox is accessed by a right-click on the desktop and there you find your launchers and config options.

If you're interested in checking it out, you can always install it, and at your login screen choose which one you want to go into, Gnome or Fluxbox, so you can get a feel for it without having to choose one or the other right away.  

```
sudo apt-get install fluxbox
```

Then logout and click Options -> Sessions -> and mark the radio button next to the choice you'd like.  It will ask if you would like to set your choice to the default window manager, and you can chose yes or no, and then on in you go.

You can also try this same with any other desktop environment you'd like to experiment with

For KDE
```
sudo apt-get install kubuntu-desktop  
```

For XFCE
```
sudo apt-get install xubuntu-desktop
```

And so on.  Some environments give you more options than others, so playing around with the different ones available could give you an idea as to what you're able to do.

Just a note: Fluxbox doesn't install a desktop manager or a file manager by default.  For that you can:

```
sudo apt-get install rox-all
```

And then you can configure your options from there.  Also, alot of Fluxbox's configuration options are in config files that you have to manually edit.  It's a bit more work than a straight-up GUI, but it's well worth it for the configurability.

Hope some of this helps.

---

### Post by berylator on 2007-04-03
Sorry for the double-post, but I have the solution:

You have to manually add a *Advanced Condition* and just delete the "new-scheme" field. Put a checkmark beside it, restart nautilus and it will work!

cheers,

berylator

---

### Post by berylator on 2007-04-03
arbulus: Thank you for you suggestion; I will check it out! I am completely new to Linux and I'm just figuring things out.. thanks!

---

