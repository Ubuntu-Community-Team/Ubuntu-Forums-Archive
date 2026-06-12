---
title: "problem assigning keys"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-06-25
Everywhere I've used Ubuntu Feisty, I have this problem. The problem is that I'm only able to assign one key at a time. It doesn't recognize combinations.

For instance, I tried assigning Terminal to super(win)+F1. As soon as I hit the super key, it assigns it to that key alone. I've tried hitting both at the same time, but it didn't work of course. Is this a common problem? I'd imagine I would find this every where, but I haven't been able to find anything.

Also, if it's not to complicated to assign keys via command, I'd love to learn.

---

### Post by BobCFC on 2007-06-26
I seem to have a problem assigning superkey aswell.  Also there is limited choice of actions.

To get it to do anything you want follow this:

Press Alt-F2 and type **gconf-editor**

Then click **Apps** -> **Metacity** -> **Global Keybindings**

Then scroll down to **run_command_terminal** click on disabled and type **<Super>F1** or whatever you want... being careful not to conflict


If you want to run a custom command for something not in the list for instance this example brings up the system monitor when you press crtl-alt-del like on windows:

Click on **run_command1** and type **<Control><Alt>Delete**

Then on the left click on **keybinding_commands** and change **command_1** to **gnome-system-monitor** or whatever you desire.

---

### Post by clinto on 2007-06-28
Thank you kindly. I'm still learning my way around things. That was very helpful.

---

