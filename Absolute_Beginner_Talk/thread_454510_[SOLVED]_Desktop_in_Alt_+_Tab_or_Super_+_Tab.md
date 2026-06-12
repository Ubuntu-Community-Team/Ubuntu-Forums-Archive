---
title: "[SOLVED] Desktop in Alt + Tab or Super + Tab"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-25
Is there any way we can configure Alt+Tab and Super+Tab to also include the Desktop as one of the windows that we can switch to ?

I'd like to switch to desktop sometimes..so i don't want to have to minimize 15 windows. I know we can use Ctrl + Alt + D, but i was thinking it would be cool to have it in Alt+Tab and Super+Tab

---

### Post by melancholeric on 2007-05-25
ctrl+alt+tab does that if I recall correctly.

Can't check becase I'm not on gnome now though.

---

### Post by starcraft.man on 2007-05-25
You could always map "fade to desktop" to a button, no? I assume your using beryl or compiz right? If not, ignore moi...

If your not using either, just push show desktop button no? Isn't that easier than adding the desktop to the alt tab menu?

---

### Post by Inxsible on 2007-05-25
> **starcraft.man said:**
> You could always map "fade to desktop" to a button, no? I assume your using beryl or compiz right? If not, ignore moi...

If your not using either, just push show desktop button no? Isn't that easier than adding the desktop to the alt tab menu?

Yes i do use Beryl. But the problem with Fade to Desktop is that its a toggle mechanism. Once I am at the desktop and i try to open a new window (lets say I had a shortcut to my external drive) i cant access the *new* window nor the already open windows. I have to hit Super+F6 (the key for Fade to Desktop) again to be able to do anything.

Try it...I don't know if its the same for you...If not, lemme know so I can change my settings too

---

### Post by Inxsible on 2007-05-25
> **melancholeric said:**
> ctrl+alt+tab does that if I recall correctly.

Can't check becase I'm not on gnome now though.

It doesn't do it for me. I use Gnome

---

### Post by starcraft.man on 2007-05-25
Your right, my bad, fade to desktop is really just for staring at your wallpaper, all your windows vanish :p

Well, I just push show desktop in the lower left when I want the windows minimized for a second (same as alt ctrl D). I mostly use the scale/expose feature when switching windows.

I guess its just show desktop, I don't think the desktop itself can be added to scale or ring switcher.

---

### Post by melancholeric on 2007-05-25
> **Inxsible said:**
> It doesn't do it for me. I use Gnome

Well, it does for me, but then again I did change the keyboard shortcuts quite a bit from gconf, so maybe it doesn't do that by default. In any case, it can be enabled from gconf.

---

### Post by Inxsible on 2007-05-25
> **melancholeric said:**
> Well, it does for me, but then again I did change the keyboard shortcuts quite a bit from gconf, so maybe it doesn't do that by default. In any case, it can be enabled from gconf.

Can you tell me how ?

---

### Post by TwiceOver on 2007-06-01
I am also interrested in this.  I find it very useful on my Vista desktop at work.

---

### Post by melancholeric on 2007-06-03
Whoops, forgot about this thread.

gconf-editor -> applications -> metacity -> global_keybindings -> set the switch_panels value to <ctrl><alt><tab> or whatever you like.

The description:
> The keybinding used to move focus between panels and the desktop, using a popup window.

That should work. Unless gnome developers decided to remove that feature in 2.18 ...

---

### Post by berlinbullet on 2007-09-03
Bump. Still curious if this can be done in beryl or something. It's so easy to get used to the feature on vista when I am at work :-k

---

