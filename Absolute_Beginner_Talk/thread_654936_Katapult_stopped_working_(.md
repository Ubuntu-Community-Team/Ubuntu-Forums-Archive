---
title: "Katapult stopped working :("
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-31
The shortcut "alt+space" isn't working anymore

I'm running Kubuntu with GDE installed over it.

It used to work fine, then I installed a new vid card, and rebooted (I have rebooted in the past) and there's no-go.

If I go to applications >> accessories > Katapult it works fine - but that's pointless.

I didn't just post here, I searched for like an hour on this crap, and the general concensus is that the global shortcuts are changed, great, but they're not in the menu and I don't know how to add to that menu?

It starts katapult when Ubuntu boots up (added it to the start session).

When I go to **System >> Preferences >> Keyboard Shortcuts** it's not listed in there, so I don't know how to assign it a key - it's not "launching" on alt+space anymore, nor control + space, nor any of the other common ones.

Any way to add to the keyboard shortcut menu?  I love katapult and I'd hate for it not to work just b/c of a new video card.

**PS:**
In the keyboard shortcuts menu there's a lot of options where the "shortcut key" is something along the lines of **0xa0**. - what the hell does that mean?

---

### Post by p_quarles on 2007-12-31
Just a guess here, but I think this is what happened: 1) new video card supports Compiz --> Compiz gets automatically enabled --> Compiz remaps the keyboard shortcuts. 

The easiest way to confirm this would be to install the Compiz settings manager:
```
sudo apt-get install compizconfig-settings-manager
```It has a very extensive keyboard shortcut menu, and you can easily create custom commands.

EDIT: You might also take a look at Gnome-Do -- it's a GTK tool similar to Katapult.

---

### Post by Syndacate on 2007-12-31
> **p_quarles said:**
> Just a guess here, but I think this is what happened: 1) new video card supports Compiz --> Compiz gets automatically enabled --> Compiz remaps the keyboard shortcuts. 

The easiest way to confirm this would be to install the Compiz settings manager:
```
sudo apt-get install compizconfig-settings-manager
```It has a very extensive keyboard shortcut menu, and you can easily create custom commands.

EDIT: You might also take a look at Gnome-Do -- it's a GTK tool similar to Katapult.

I'm sure this sounds like a retarded question, but how the hell do you turn it on (the manager).

I installed it, but how do you "get to it?"

It's not in any of the dropdown windows.

---

### Post by p_quarles on 2007-12-31
Not a bad question at all . . . I had to load up Gnome to find the answer. Anyway, it's in the Preferences menu -- Advanced Desktop Effects Settings.

---

### Post by Syndacate on 2007-12-31
> **p_quarles said:**
> Not a bad question at all . . . I had to load up Gnome to find the answer. Anyway, it's in the Preferences menu -- Advanced Desktop Effects Settings.

I don't see anything there about keyboard shortcuts :-\

?

---

### Post by p_quarles on 2007-12-31
> **Syndacate said:**
> I don't see anything there about keyboard shortcuts :-\

?
Yeah, it's not the simplest interface to figure out. IIRC, the key bindings are sub-categories of the main categories.

---

### Post by Syndacate on 2007-12-31
> **p_quarles said:**
> Yeah, it's not the simplest interface to figure out. IIRC, the key bindings are sub-categories of the main categories.

Yeah, I looked at all of them, none of the sub-categories even remotely relate :-\

---

### Post by Syndacate on 2008-01-01
> **Syndacate said:**
> Yeah, I looked at all of them, none of the sub-categories even remotely relate :-\

Well happy new years...anybody know about the key bindings??

---

### Post by GSF1200S on 2008-01-01
Well, when you have Katapult running, do you see it in the system tray? Right click on the system tray icon and go to 'Configure Global Shortcuts' and make sure its still set to Alt+Space.

Also, try to disable the desktop effects. This sounds like it could be the case, as for example, I cant change workspaces through KDE when compiz is enabled. Try:

```
metacity --replace
```

in a terminal and see if Katapult starts working...

---

### Post by Syndacate on 2008-01-01
> **GSF1200S said:**
> Well, when you have Katapult running, do you see it in the system tray? Right click on the system tray icon and go to 'Configure Global Shortcuts' and make sure its still set to Alt+Space.

Also, try to disable the desktop effects. This sounds like it could be the case, as for example, I cant change workspaces through KDE when compiz is enabled. Try:

```
metacity --replace
```

in a terminal and see if Katapult starts working...

I wish I did see it in the system tray, but I don't, possibly b/c I'm using GDE.

Also, it seems that compiz overwrote the global binds, so I gotta figure it out through there.

---

### Post by GSF1200S on 2008-01-01
> **Syndacate said:**
> I wish I did see it in the system tray, but I don't, possibly b/c I'm using GDE.

Also, it seems that compiz overwrote the global binds, so I gotta figure it out through there.

By GDE I assume you mean Gnome Desktop Environment, right? Just making sure...

Try typing the command above at a terminal and see what happens when you press alt+space. It should work..

Make sure katapult is running first- (type 'katapult' in a terminal). 

Also, go to the following location and open it in gedit:

/home/user/.kde/share/config/katapultrc

Being sure to change user to your username, respectively... (Youll have to show show hidden files to see the .kde folder)

Look through it, and ensure the option:

```
SystrayIcon=true
```

is that way.. At least then we can get it to your system tray and take a look at the global shortcuts..

---

### Post by Syndacate on 2008-01-01
I checked everything in Compiz and I can't find anything that's using the keybind of space + tab.

---

### Post by Syndacate on 2008-01-01
> **GSF1200S said:**
> By GDE I assume you mean Gnome Desktop Environment, right? Just making sure...

Try typing the command above at a terminal and see what happens when you press alt+space. It should work..

Make sure katapult is running first- (type 'katapult' in a terminal). 

Also, go to the following location and open it in gedit:

/home/user/.kde/share/config/katapultrc

Being sure to change user to your username, respectively... (Youll have to show show hidden files to see the .kde folder)

Look through it, and ensure the option:

```
SystrayIcon=true
```

is that way.. At least then we can get it to your system tray and take a look at the global shortcuts..

Katapult's always running, I added the command in the session so it starts when Ubuntu starts, but yeah, I typed it into terminal, just to make sure, and still, nothing.  Alt+space is binded to my browser right now in "keyboard shortcuts", I just binded it to "control + space" and neither works now, katapult still doesn't work, but I'm 100% sure it's on.

Though the path you listed doesn't exist, of course I have /home/user/ - but there's no .kde directory in there.  Yes, when I said GDE I meant Gnome Desktop Environment, not sure if that has to do with why it's there.

And since Ubuntu seems to lack the simple ability to search a whole medium for something, I can't find the file you want me to edit.

PS:
Sorry for long response, you actually responded in between when I hit "reply" and when I hit "submit reply" - and I closed the browser after I hit "submit reply" - so I never saw your reply.

EDIT:
Compiz is such a double edged sword.  On one hand, the cube is absolutely amazing :-D.  Even though I never have enough stuff use it ;), the effects are awesome too, on the other hand, it appears it completely raped my shortcuts.  Now I'm not sure which shortcuts overwrite what but it seems that some shortcuts override others so I need like "*sudo shorcuts*" if you know what I mean.

EDIT2:
Ah ****, I came to the conclusion that Compiz is the devil.  All of a sudden, EVERYTHING slowed down, like when I click "System" it takes like 3 seconds for the dropdown menu to SLOWLY fade in, and if I flip desktops, it takes like 5 seconds to center and get my mouse back - all of the effects are slow - Compiz is the devil, very addicting, but screws up everything :-\

EDIT3:
About EDIT2, I got it fixed, DON'T HIT **SHIFT + F10**!!

---

### Post by Syndacate on 2008-01-01
Okay, I found the .kde folder, I didn't realize it was a hidden folder.  Though in ../config/ there is no **katapultrc** file, there's "rc" files for a lot of other programs - but not katapult.

I removed katapult:
```

sudo apt-get remove katapult

```

Then installed it again:
```

sudo apt-get install katapult

```

And I got nothing.

---

### Post by Syndacate on 2008-01-01
> **GSF1200S said:**
> By GDE I assume you mean Gnome Desktop Environment, right? Just making sure...

Try typing the command above at a terminal and see what happens when you press alt+space. It should work..

Make sure katapult is running first- (type 'katapult' in a terminal). 

Also, go to the following location and open it in gedit:

/home/user/.kde/share/config/katapultrc

Being sure to change user to your username, respectively... (Youll have to show show hidden files to see the .kde folder)

Look through it, and ensure the option:

```
SystrayIcon=true
```

is that way.. At least then we can get it to your system tray and take a look at the global shortcuts..

I got to it using Katapult, then when it opens, "control + C" brings up global shortcuts.

Though most of them are blocked off due to compiz, gotta figure out a new shortcut system :-\

---

### Post by Syndacate on 2008-01-01
Anybody?

I don't believe I'm the only one who installed Compiz with Kubuntu using GDE.

---

### Post by p_quarles on 2008-01-01
> **Syndacate said:**
> Anybody?

I don't believe I'm the only one who installed Compiz with Kubuntu using GDE.
I guess I'm not completely clear on the nature of the problem at this point. Is it that you can't get Katapult to run at all, or that you can't get it set to a keyboard shortcut? Does it work properly once it's running? Are you able to use alt-space to bring it back up once it's running in the background? 

FWIW, I'm attaching my katapultrc. It has the systray icon set to "false," so you should change that prior to running it, if you choose to use it. 

Anyway, Katapult is a KDE application, and while many of them work fine in alternate environments, many of them will experience hiccups along the way. I'd again suggest the Gnome equivalent, which is called Gnome-Do.

Also: "GDE" isn't a thing. Gnome itself is an acronym for "Gnu Network Object Modeling Environment."

EDIT: I couldn't upload the file without adding an extension to it. Remove the trailing ".txt" before putting it in your .kde/share/config/ folder.

---

### Post by Syndacate on 2008-01-01
> **p_quarles said:**
> I guess I'm not completely clear on the nature of the problem at this point. Is it that you can't get Katapult to run at all, or that you can't get it set to a keyboard shortcut? Does it work properly once it's running? Are you able to use alt-space to bring it back up once it's running in the background? 

FWIW, I'm attaching my katapultrc. It has the systray icon set to "false," so you should change that prior to running it, if you choose to use it. 

Anyway, Katapult is a KDE application, and while many of them work fine in alternate environments, many of them will experience hiccups along the way. I'd again suggest the Gnome equivalent, which is called Gnome-Do.

Also: "GDE" isn't a thing. Gnome itself is an acronym for "Gnu Network Object Modeling Environment."

EDIT: I couldn't upload the file without adding an extension to it. Remove the trailing ".txt" before putting it in your .kde/share/config/ folder.

Katapult works fine, it's just that compiz overwrote the damn shorcut keys to alt+space and I can't find out how to turn it off - I like alt+space, but compiz took over all the key bindings when it was installed.  I figured out how to access the katapult shortcuts (you open katapult then hit "control+c" - then you can change it, but there's nothing really there as good as alt+space, and compiz took it over for something and I can't figure out what (it doesn't do anything).

Other than the binding issue it works fine.

I'll check out Gnome-Do, but if it can't overwrite these key bindings that compiz made it's just going to be the same issue.

I meant GDM, not GDE btw.

EDIT:
If I set it to control + space it only works sometimes (I don't know why, but control+space doesn't work right :-\), and super + anything locks it :(

EDIT 2:
I just re-set the controls for Katapult to alt+space and it works now, it must have had something to do with disabling some features in compiz - thanks.

---

