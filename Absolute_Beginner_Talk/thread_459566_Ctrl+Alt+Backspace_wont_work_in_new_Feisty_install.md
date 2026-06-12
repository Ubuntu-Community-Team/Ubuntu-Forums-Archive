---
title: "Ctrl+Alt+Backspace wont work in new Feisty install"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-05-30
I can´t find any tutorials on how to enable the Ctrl+Alt+Backspace to restart Xorg. I cant live with out it please help.

---

### Post by starcraft.man on 2007-05-30
> **thelocust said:**
> I can´t find any tutorials on how to enable the Ctrl+Alt+Backspace to restart Xorg. I cant live with out it please help.

[Here you go.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME") You'll have to modify this one a bit.

1) Terminal (use the commands as is, changing what I say):
First command maps Command 9 to ctrl alt del (you can change delete to backspace of course)
Second command maps Command 9 to execute the gnome system monitor (You want to change whats in the quotes to "/etc/init.d/gdm restart")

2) Gui Gconf-editor
To open the editor, push Alt + F2 and then type in gconf-editor, push enter.
Then you can follow the paths listed in the commands (the /X/Y/Z) and it will lead you to the same command, then map what you like to them yourself as above.

That should do it :D

Oh and uh, darn it... I'm drawing a blank (bah, getting forgetful) on the CLI command for restarting xorg, I just use the default keybinding... hope ya know it (if not someone else tell both of us please). :p.

Edit: Thanks to daimaru, I remembered the command and edited it in. That should do it, my job here is done.

En Taro Adun!

---

### Post by ncappel1 on 2007-05-30
I think that is already the default, isn't it? I thought mine was broken for a long time, but then I realized that the problem was with my alt key. This may be a silly suggestion, but have you tried it with all combinations of ctl and alt?

---

### Post by starcraft.man on 2007-05-30
> **ncappel1 said:**
> I think that is already the default, isn't it? I thought mine was broken for a long time, but then I realized that the problem was with my alt key. This may be a silly suggestion, but have you tried it with all combinations of ctl and alt?

Isn't it shift + Backspace? I did that enough times before I stopped.... >.>. Anyway, bah, whatever it is. I gave ya the generic way to map any command you like to keybindings, have fun :).

---

### Post by daimaru on 2007-05-30
lol didnt bother to read all the thread so this might already be solved. if u can't use alt+ctrl+backspace @ least u can still use

```
/etc/init.d/gdm restart 
```

to do the same thing.

---

### Post by starcraft.man on 2007-05-30
> **daimaru said:**
> lol didnt bother to read all the thread so this might already be solved. if u can't use alt+ctrl+backspace @ least u can still use

```
/etc/init.d/gdm restart 
```

to do the same thing.

YAY! Thats the command I was looking for... bloody, I hope I'm not losing my memory already. I'm too young to be forgetful. Now my instructions are complete, thanks daimaru. :)

---

### Post by Dylnuge on 2007-05-30
Definatly Ctrl-Alt-Backspace. Should work without configuration, since it is an auto-intercepted command, just like CTRL-ALT-DEL in Windows.

Of cource, if if does not, keymap ```
/etc/init.d/gdm
``` restart to it.

EDIT: See this was already posted.

---

### Post by thelocust on 2007-05-30
ncappel1 got it, I guess I have to use the left Alt button. Its no problem just as long as I have the functionallity. Thanks for all the inputs Laters.

---

### Post by ncappel1 on 2007-05-30
woot

does anyone actually have a solution though? why does the left alt key work but not the right one?

---

