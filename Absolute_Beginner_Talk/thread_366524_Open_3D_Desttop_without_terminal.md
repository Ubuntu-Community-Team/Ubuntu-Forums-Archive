---
title: "Open 3D Desttop without terminal"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jpboyes on 2007-02-21
I am trying to get 3d desktop to work without opening the terminal. I have a 5 button mouse that only has 3 working buttons, so i would like to assign the task of opening 3d desk to one of the buttons on my mouse. I've tried to bind it using xbindkeys, but it didn't work. Nothing happens when i push the button and i can't figure out how to assign. Basically, what i am trying to do is set my mouse button (button 9) to run 3ddesk. Also, is there a way to make the keyboard do other things than what is available with the shortcuts menu in Preferences?

---

### Post by agiamba on 2007-02-21
sure, go into terminal, type gconf-editor

go to apps, ah hell, here it is from readme. works for anything, not just 3ddesktop-

Run "gconf-editor". Drill down to apps --> metacity -->
global_keybindings. Find "run_command_1" and change it to your key
such as "F12" or "<Control><Alt>S".  Then in apps --> metacity -->
keybinding_commands find "command_1" and set it to "/usr/bin/3ddesk".

---

### Post by Tomosaur on 2007-02-21
If you still don't want to use the terminal, hit Alt+f2. You can run commands like that.

---

### Post by jpboyes on 2007-02-21
thanks a lot. that worked great.

---

