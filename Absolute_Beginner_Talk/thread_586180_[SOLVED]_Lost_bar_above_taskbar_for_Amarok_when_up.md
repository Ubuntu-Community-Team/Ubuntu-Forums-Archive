---
title: "[SOLVED] Lost bar above taskbar for Amarok when upgraded to Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by marko_4454 on 2007-10-22
So I lost the bar above the task bar, the one used to move windows, minimize them, close them...etc. This happened after upgrading to Gutsy, and it only happens to the Amarok window. The Amarok window places itself "on top", so above everything, including the main Ubuntu bar.
I am posting a screenshot, and please take into account that this is what ** I see in my monitor** no cuts or nothing. See how its above everything? 

Please note, that the taskbar is fine, so doing ctrl+m doesnt help. 
I also tried removing the whole ~/.kde/share/apps/amarok/ folder and it didnt help.
Something that did help however, was reinstalling amarok, but the problem came back after a restart.

Also, I am attaching what happens when I start it using terminal:
```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8144a68 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8144a68 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
marco@marco-desktop:~$ amarok: WARNING: Pixmap not found for mimetype application/ogg

```

The image:
[[IMG]http://img138.imageshack.us/img138/2254/screenshot1tr7.png[/IMG]](http://imageshack.us)

---

### Post by Vansinnesvisan on 2007-10-22
What happens when you type "kde-window-decorator --replace" in a terminal?

---

### Post by marko_4454 on 2007-10-22
> **Vansinnesvisan said:**
> What happens when you type "kde-window-decorator --replace" in a terminal?

Thank you for your input, It first complained about me not having the compiz-kde package installed, so I did. I tried it and nothing happened. It changed the decorator from emeral to kde in all of my windows but not in the amarok one. 
Any other possibilities that come to your mind?

---

### Post by Vansinnesvisan on 2007-10-22
> **marko_4454 said:**
>  It changed the decorator from emeral to kde in all of my windows but not in the amarok one.

That's peculiar. I believe window decorations are handled by kwin for KDE applications. You're using Compiz, so emerald is managing them. You could try emerald --replace. 

But I assume something else is wrong. You could try disabling compiz, log out, restart X with ALT-CTRL-Backspace, then logging back in. Then you'd know if it was compiz or something else. 

Just an idea if no one else knows a solution.

---

### Post by marko_4454 on 2007-10-22
> **Vansinnesvisan said:**
> That's peculiar. I believe window decorations are handled by kwin for KDE applications. You're using Compiz, so emerald is managing them. You could try emerald --replace. 

But I assume something else is wrong. You could try disabling compiz, log out, restart X with ALT-CTRL-Backspace, then logging back in. Then you'd know if it was compiz or something else. 

Just an idea if no one else knows a solution.

Ok, so it works now. I dont really know if its temporary or for good, but it works ;)
Anyways, I just logged out after installing Kwin and KDE decorator and it came up with the problem in compiz. I changed it to kwin and the bar appeared, then changed back to compiz and it worked fine! 
I then restarted twice with compiz enabled and it was able to give the window to my amarok. I then restarted and it was still there. 
Thanks for your help vansinnesisan.

---

### Post by sailor2001 on 2007-10-22
alt/f2 and type in:   metacity --replace

---

### Post by marko_4454 on 2007-10-22
> **sailor2001 said:**
> alt/f2 and type in:   metacity --replace

I had tried that but i didnt work. 
It works now though, thanks for your help!

---

