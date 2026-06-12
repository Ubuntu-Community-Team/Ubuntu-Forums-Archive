---
title: "[SOLVED] gVim default config"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by cybo on 2008-03-23
i have been using gvim for some time but i'm not experienced in it. i have accidentally deleted the default config file. i tried to look for it online but couldn't find. i know that it is a good idea to use somebody's file but i'm new to ubuntu and relatively new to vim and gvim. i would like to learn more about gvim and i think it is a better idea to edit a default config on your own. can anyone tell me where can i get a default config?

thnx

---

### Post by erginemr on 2008-03-24
To begin with, I'd like to congratulate you for having interest in Vim / GVim. I am also using vim whenever possible, and am also admiring its sheer power. Granted it has a steep learning curve, but once you get the hang of it, you will have a real powerful swiss-army tool in your hands. Enough commercials ;-), lets get back to the business. 

In context with the attached screenshots:

1) When you install gvim, it is under Gnome Main Menu -> Applications -> Accessories -> GVim text Editor. but by default it is hidden. So, you may want to right click on the menu, select "Edit Menus" browse to Accessories and tick the check mark beside GVim to make it visible.

2) The settings for both vim and gvim are kept in a hidden config file ".vimrc" inside your home directory, so its full path is: "~/.vimrc", where ~ is a Unix shortcut for your home folder.

3) Vim / GVim has two modes, command mode and edit mode (an a controversial third one; visual selection mode). Commands are entered to vim/gvim after a colon ( : ). To enter into the edit mode you need to press either "i" (for insert) or "a" (for append). You can return to the command mode by pressing "Esc". You open a file with ":e", save it with ":w", save and close with either ":wq" or "ZZ" and exit without saving with ":q!".

4) Don't worry if you have deleted your config file; GVim will create another one on demand. Editing this file is very easy from GVim menus. All you need to do is to open a sample file and try several options in the menus noting down each time what command is issued at the bottom left of the text screen. Then, you will need to enter these commands into "~/.vimrc" again by using the menus. 

5) For that purpose you will have two tools at your your service: "Settings Window" and "Startup Settings" under Edit menu. You can use the former as a guide to available options and the latter to populate the ".vimrc" file itself. When you are done, save it and restart vim/gvim to put the changes into effect.

6) I will also strongly recommend you to go though the original vim tutorial if you haven't done already. You can run it from the terminal with:
```
vimtutor
```

---

### Post by cybo on 2008-03-25
Thank you erginemr It really helped!

---

### Post by erginemr on 2008-03-25
You are welcome, cybo. Take care yourself. ):P

---

