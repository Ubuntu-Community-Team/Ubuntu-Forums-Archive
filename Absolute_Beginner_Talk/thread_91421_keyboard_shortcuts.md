---
title: "keyboard shortcuts"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Kazung-Q on 2005-11-17
are there also shortcuts in (k)ubuntu? In windows I know quite a few:
winkey + e = explorer
alt+F4 = close / Shutdown (also works in ubuntu i noticed)
winkey + d = minimize all windows to desktop
ctrl+esc = winkey = start menu
winkey + l = lock computer
....
etc etc etc

is there a list of these commands for (k)ubuntu ? and why not use the winkey? i find it handy.....

---

### Post by rpaller on 2005-11-17
If you go the System -> Preferences -> Keyboard Shortcuts you can see what is predefined with the install and then define your own. 

I have just recently setup "Super Key" (aka Windows Logo Key) - L for Logout  and Ctl - Alt - L for Lock Screen. I was hoping to define custom shortcuts to launch applications (GEdit and other common applications I use at work), but this particular location under Preferences is not it.

---

### Post by kevin79 on 2006-01-05
[QUOTE=rpaller]If you go the System -> Preferences -> Keyboard Shortcuts you can see what is predefined with the install and then define your own. 

I have just recently setup "Super Key" (aka Windows Logo Key) - L for Logout  and Ctl - Alt - L for Lock Screen. I was hoping to define custom shortcuts to launch applications (GEdit and other common applications I use at work), but this particular location under Preferences is not it.[/QUOTE]

I know this was a while ago, but how did you do this? I would like to lock my desktop with Win+L

Thanks.

---

### Post by Leigh on 2006-01-06
To remap the Windows key to lock your screen, go to **System -> Preferences -> Keyboard Shortcuts**, click on *Lock Screen* and press the Windows key and any other key with it, e.g. Windows Key and 'L'

---

### Post by kevin79 on 2006-01-07
[QUOTE=Leigh]To remap the Windows key to lock your screen, go to **System -> Preferences -> Keyboard Shortcuts**, click on *Lock Screen* and press the Windows key and any other key with it, e.g. Windows Key and 'L'[/QUOTE]

I tried that but when I hit the Windows K it puts in "Super_L" and won't let me put in the L key.

---

### Post by aysiu on 2006-01-07
[QUOTE=kevin79]I tried that but when I hit the Windows K it puts in "Super_L" and won't let me put in the L key.[/QUOTE] Gnome binds the Windows key is its own key. KDE binds it as an auxiliary key.

---

### Post by kevin79 on 2006-01-07
[QUOTE=aysiu]Gnome binds the Windows key is its own key. KDE binds it as an auxiliary key.[/QUOTE]

And that means???

---

### Post by aysiu on 2006-01-07
[QUOTE=kevin79]And that means???[/QUOTE] It means if you're in Gnome (Ubuntu) and defining keyboard shortcuts, and you press the Windows key, it'll assume that that key is itself the keyboard shortcut, and it'll show up as *Super_L*. Only one command will be able to use the Windows key.

If you're using KDE (Kubuntu) and defining keyboard shortcuts, and you press the Windows key, it'll assume that you want to add a second key along with the Windows key, and your shortcut will show up as *Win + A* or *Win + T*.

In other words, Gnome views the Windows key as just any other key (a, b, c, d, 1, 2, 3), and KDE views the Windows key as a helper key (Control, Shift).

I'm not 100% sure this'll work, but you can try changing this behavior in Gnome by going to System > Preferences > Keyboard Preferences and selecting one of the options I highlighted in red (a little trial and error).

You could also try KDE...

---

### Post by kevin79 on 2006-01-07
[QUOTE=aysiu]It means if you're in Gnome (Ubuntu) and defining keyboard shortcuts, and you press the Windows key, it'll assume that that key is itself the keyboard shortcut, and it'll show up as *Super_L*. Only one command will be able to use the Windows key.

If you're using KDE (Kubuntu) and defining keyboard shortcuts, and you press the Windows key, it'll assume that you want to add a second key along with the Windows key, and your shortcut will show up as *Win + A* or *Win + T*.

In other words, Gnome views the Windows key as just any other key (a, b, c, d, 1, 2, 3), and KDE views the Windows key as a helper key (Control, Shift).

I'm not 100% sure this'll work, but you can try changing this behavior in Gnome by going to System > Preferences > Keyboard Preferences and selecting one of the options I highlighted in red (a little trial and error).[/QUOTE]

Thanks. I'll give that a try.

---

### Post by Leigh on 2006-01-09
**@aysiu: ** I think you may have Ubuntu and Kubuntu keyboard assignments the wrong way round.  I use Ubuntu (Gnome) and my Windows key is seen as a shortcut key, so I was able to assign Win + L as my shortcut. (I've never used KDE so cannot compare.)

---

### Post by Thirsteh on 2006-01-09
There's a control panel for all the hotkeys in the KDE settings :)

---

### Post by aysiu on 2006-01-09
[QUOTE=Leigh]**@aysiu: ** I think you may have Ubuntu and Kubuntu keyboard assignments the wrong way round.  I use Ubuntu (Gnome) and my Windows key is seen as a shortcut key, so I was able to assign Win + L as my shortcut. (I've never used KDE so cannot compare.)[/QUOTE] I'm pretty sure I don't. I found out, though, that you can enable Win as an auxiliary key in Gnome by going to System > Preferences > Keyboard > Layout Options > Alt/Win Key Behavior > Meta is mapped to the Win-keys

---

