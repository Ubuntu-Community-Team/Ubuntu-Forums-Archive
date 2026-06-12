---
title: "How do I change keyboard shortcuts, which are not preconfigured."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2007-01-07
Hello. I know you can change keyboard shortcuts from System>Preferences>Keyboard Shortcuts but I would like to add some keyboard shortcuts which aren't present in this dialog. For example, I would like the music player shortcut to be configured to open amarok and not Rythbox. I would also like to add a keyboard shortcut for opening other programs, like Gnome Commander and XChat.

---

### Post by gborzi on 2007-01-07
If you are using metacity you can set the keyboard shortcuts you need with gconf-editor. For example, to use amarok with a keyboard shortcut open gconf-editor, go to /apps/metacity/keybinding_commands/command_1 and set it to amarok, then go to /apps/metacity/global_keybindings/run_command_1 and set it to the key you want to bind. Don't forget to disable the key in the keyboard shorcuts dialog. For the other keybindings you can use command_2, command_3 and so on. There is a similar setting for compiz, in /apps/compiz/general/allscreens/options/commandX - /apps/compiz/general/allscreens/options/run_commandX_key with X=0,1..,11.

---

### Post by jincast90 on 2007-01-27
> **gborzi said:**
> If you are using metacity you can set the keyboard shortcuts you need with gconf-editor. For example, to use amarok with a keyboard shortcut open gconf-editor, go to /apps/metacity/keybinding_commands/command_1 and set it to amarok, then go to /apps/metacity/global_keybindings/run_command_1 and set it to the key you want to bind. Don't forget to disable the key in the keyboard shorcuts dialog. For the other keybindings you can use command_2, command_3 and so on. There is a similar setting for compiz, in /apps/compiz/general/allscreens/options/commandX - /apps/compiz/general/allscreens/options/run_commandX_key with X=0,1..,11.

Ok. Now I am at /apps/metacity/keybinding_commands/command_1 but how do I change it to amarok? I tried to double click on it, but can only type in some value?

---

### Post by jordanmthomas on 2007-01-27
The value you would type in would be this
```
amarok
```
so that when the run_command1_key is pressed, amarok will be run

---

### Post by Hasen_A on 2007-02-02
I installed metacity using the SPM but the folger /apps/metacity/ doesnt exist. Also how do I use metacity?

---

