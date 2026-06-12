---
title: "Desktop"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by morsmodre on 2007-11-04
Hi all!

I'm VERY (40 hours) new to Ubuntu and I'd like to know a few things:

 - How can I customize my desktop? (colors, themes, etc)

 - Is it possible to show the files in a folder in a listed manner and not by icons?

 - when I use alt+tab to switch between windows, how do I make them move back words? [in windows is alt+tab+shift ... dunno here]

 - Is there a way to configure the "minimize all" keystroke?

 - Is it possible to add more desktops and make the movement between them circular?

I hope it's all!

tx guys!


[]

---

### Post by por100pre1 on 2007-11-04
Welcome to the forums! Which Ubuntu version are you using? :-k

If using Gutsy check **System> Preferences> Appearance**. Under **Theme** click **Customize**.

There should be a button to **Show Desktop**. If not add one right clicking a panel (taskbar) and click **Add to Panel**.

---

### Post by evilregis on 2007-11-04
** - How can I customize my desktop? (colors, themes, etc)**

System -> Preferences -> Appearance is where these are edited.

You can download additional themes and icon sets from [http://art.gnome.org/](http://art.gnome.org/) or [http://gnome-look.org/](http://gnome-look.org/)

You just download the theme/icon set and you 'install' them by dragging them into the Theme tab of the Appearance window.

** - Is it possible to show the files in a folder in a listed manner and not by icons?**

In Nautilus click View -> View as List.

If you want it permanent for every folder then click Edit -> Preferences and set the Default View to List View.

** - when I use alt+tab to switch between windows, how do I make them move back words? [in windows is alt+tab+shift ... dunno here]**

You will need to install compizconfig-settings-manager.  System -> Administration -> Synaptic Package Manager

Search for compizconfig-settings-manager.  Mark it for installation and Apply it.

Now go to System -> Preferences -> Advanced Desktop Effects Settings.

Scroll all the way down and in Window Management click Application Switcher.  Click the Actions tab.  Expand General (click the arrow).  Double-click Prev Window and then in the Key field enter:  <Shift><Alt>Tab and close the window.

** - Is there a way to configure the "minimize all" keystroke?**

The default is Ctrl+Alt+D.  I've set up the key combination of Alt+M to minimize all.  You can do this by going to System -> Preferences -> Keyboard Shortcuts.  Scroll just about all the way to the bottom and click "Hide all windows and focus destkop".  Then do the key combination that you want.  You can't use the Windows Key and another key in combination it seems.

** - Is it possible to add more desktops and make the movement between them circular?**

There's the cube, but I don't know of any circular desktops.

---

### Post by joe.turion64x2 on 2007-11-04
> **morsmodre said:**
> Hi all!

I'm VERY (40 hours) new to Ubuntu and I'd like to know a few things:

 - How can I customize my desktop? (colors, themes, etc)

 - Is it possible to show the files in a folder in a listed manner and not by icons?

 - when I use alt+tab to switch between windows, how do I make them move back words? [in windows is alt+tab+shift ... dunno here]

 - Is there a way to configure the "minimize all" keystroke?

 - Is it possible to add more desktops and make the movement between them circular?

I hope it's all!

tx guys!


[]
All of that is possible (most of it at least), you'd have to tinker a little with Nautilus to get the listing you have, and with Gnome desktop to get that desktop stuff. Don't be shy and right-click everything, there are Properties/Preferences windows waiting for you.

---

### Post by por100pre1 on 2007-11-04
There is anice tool for adding more themes, is called Art Manager. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo aptitude install gnome-art
```

You'll find it under: **System> Preferences> Art Manager**.

---

### Post by jlotempio on 2007-11-10
> **evilregis said:**
> [B] - 

** - Is there a way to configure the "minimize all" keystroke?**

The default is Ctrl+Alt+D.  I've set up the key combination of Alt+M to minimize all.  You can do this by going to System -> Preferences -> Keyboard Shortcuts.  Scroll just about all the way to the bottom and click "Hide all windows and focus destkop".  Then do the key combination that you want. [SIZE="3"][SIZE="3"][B]You can't use the Windows Key and another key in combination it seems.[/SIZE]
[/B][/SIZE].

If you are using compiz-fusion, you can, indeed, use the Windows Key (a.k.a. Super) and another key in combination. 
 Once the "Advanced Desktop Effects Settings" is open, General Options >> Actions tab >> click the general arrow >> "Hide all Windows and Focus Desktop".  
Enter your key combination.

---

