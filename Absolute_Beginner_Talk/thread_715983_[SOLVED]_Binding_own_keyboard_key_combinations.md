---
title: "[SOLVED] Binding own keyboard key combinations"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by natirips on 2008-03-05
Is there a way I can bind my own key combinations?

Acctually, I'd like to bind Right-Alt + - (dash) to act as slash (/) key, because this way (a non-US keyboard layout, moreover it's a laptop keyboard) I'm havin trouble using slash in console, i either have to use SHIFT+7 or Fn+0 (zero) on my laptop keyboard to get the slash sign (which is used quite often).

I've tryed "keytouch", but it doesn't work for key combinations, only for single keystrokes...

---

### Post by herbster on 2008-03-05
Are you using Gnome? There I only know of System > Admin > Keyboard shortcuts I believe.

---

### Post by natirips on 2008-03-05
Yes I am using Gnome, and you probably mean System > Settings > Keyboard Shortcuts, but that's of no use for my problem :S , it makes key combinations do certain jobs, I just want a key combination to act as another key.

What I want is this:   **RightAlt+Dash=Slash**     (RAlt+'-'='/'), because this combination does nothing for the time being, and on my keyboard dash('-') is where slash ('/') is on US keyboard.

---

### Post by olejorgen on 2008-03-05
xkeycaps is a rough keyboard layout editor. You should be able to do what you want with it. It's kinda arcane though, so it might be easier to look into xmodmap directly. I don't have all the syntax at the tip of my finger, so you'll have to read some man pages. Sorry about that

---

### Post by natirips on 2008-03-05
That worked, thanks.

Edit: I later noticed that while xkeycaps is running, I can no longer use SUPER+whatever combinations with Compiz, so I'll just keep on using SHIFT+7 for the slash symbol... :S

---

### Post by deepclutch on 2008-03-06
hmm..u can use gconf for launching some apps though.
adding gnome-dictionary shortcut as **CTRL+SHIFT+D** :
open a terminal(from menu Applications>Accssesories>Terminal) and run:
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Shift>d" 
```
and then:
```

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-dictionary"

```
Now try the key combination to launch gnome-dictionary.
u can add such shortcuts for some applications.also u can browse via "gconf-editor" graphically :)

---

### Post by natirips on 2008-03-08
> **deepclutch said:**
> hmm..u can use gconf for launching some apps though.
adding gnome-dictionary shortcut as **CTRL+SHIFT+D** :
open a terminal(from menu Applications>Accssesories>Terminal) and run:
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Shift>d" 
```
and then:
```

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-dictionary"

```
Now try the key combination to launch gnome-dictionary.
u can add such shortcuts for some applications.also u can browse via "gconf-editor" graphically :)

Sorry, but you're talking about a wrong problem here... but nevermind, it's "solved" already anyway.

---

