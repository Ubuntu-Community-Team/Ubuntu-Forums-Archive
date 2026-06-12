---
title: "[SOLVED] using windows button as a modifier"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by captainwitherspoon on 2007-08-16
How do I set up the windows key to be used as a modifier?
I'd like to launch all of my aps with hotkeys and I'd like them to not interfere with other programs and I don't want to have to press 3 buttons.

---

### Post by 505 on 2007-08-16
The Win key is called the meta key. At my home computer I have several shotcuts set up, e.g. Meta+e for Nautilus, and Meta+t for the terminal. You can not use the keyboard shortcut window to set them up, but you have to use gconf-editor.

Go to /apps/metacity/keybinding_commands and type the command at 'command1'. Then go to /apps/metacity/global_keybindings and edit 'run_command1' Type <Meta> for the Win key, e.g. type <Meta>e for the shortcut Win+e. You can define up to 12 global commands.

---

### Post by YSH on 2007-08-16
there is an easier way,

System > Preferences > Shortcuts

you can just create ones there

---

### Post by aitorcalero on 2007-08-16
But, how, using this way can you handle Super/Win/Meta combinations? because when I push win key, I cannot make any combination at all! :( it just shows Super L or Super R, but I cannot combine Super with any other key.

---

### Post by glennric on 2007-08-16
> **YSH said:**
> there is an easier way,

System > Preferences > Shortcuts

you can just create ones there

That only works if the actions you desire to perform happen to be in the list already.  The gconf editor method allows any actions.

---

### Post by captainwitherspoon on 2007-08-29
Well, it seems to work if I either put <Mod4><Hyper> or <Super> into the hotkey boxes. Thanks for the help.

---

