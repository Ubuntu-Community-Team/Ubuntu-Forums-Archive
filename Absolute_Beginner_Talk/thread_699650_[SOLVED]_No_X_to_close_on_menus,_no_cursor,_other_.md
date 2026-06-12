---
title: "[SOLVED] No X to close on menus, no cursor, other probs"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by kujaabi on 2008-02-17
Well,every time I selected my second workspace everything disappeared except the wallpaper. I had to reboot (ctrl alt del. I noticed this happened after I had ended up one time while fussing around, in a menu and increased the number of desktops to "4". I thought it corresponded to the number of workspaces I had. Anyway, I could not find that menu again after the problem started to change it (it looked similar to a menu for doing that in kubuntu but I was in ubuntu).

I also have Kubuntu loaded but not running at the same time, and rebooted and chnged the session to go there and changed the number of desktops to "1". No luck in ubuntu once I returned. Then I noticed that my cube effects in advanced windows effects (compriz) didn't work. I then deleted compriz. I also noticed that the "X" in the upper right corner on the panel to close windows was now gone from all windows and a programs. I deleted compiz using synaptic. Now, on top of everything else I all of the windows are run up to the top of the screen and I do not get a cursor in any of the dialogue boxes (like to reinstall compiz) including in terminal. So I can't even reload stuff from anywhere (add and remove, synaptic or terminal.

Help!

---

### Post by RomeReactor on 2008-02-17
Hi. Sounds like you still have desktop effects running; press ALT+F2 and write or paste:
```
gtk-window-decorator --replace
```
And see if the problem is gone.

---

### Post by kujaabi on 2008-02-17
alt F2 doesn't work

---

### Post by RomeReactor on 2008-02-17
Do you have Emerald installed? Try going to 'System->Preferences->Appearance' and on the 'Visual Effects' tab disable Compiz. Then go to 'System->Preferences->Advance Desktop Effects Settings', find and press the 'Window Decoration' button and on the 'Command' section write:
```
gtk-window-decorator --replace
```
Then see if you can now enable Compiz.

---

### Post by bumanie on 2008-02-17
Do you have an nvidia graphics card?

---

### Post by kujaabi on 2008-02-17
Could not launch advanced effects  BUT the close minimize buttens etc. are now back on. Even though the normal effects radio button showed to be chosen, I click it again and I guess that did it. Let me try the other issues. Thanks!

---

### Post by kujaabi on 2008-02-17
I'm not sure what video card I have, How do I find out?

---

### Post by kujaabi on 2008-02-17
Yes, that cleared up the cursor and button issues. What about the inital problem where after choosing the 4 desktop option in a menu that I can't find anymore, cause everything to dissapear when I selected andother work space? any ideas. 

Should I re-install compiz? I kinda like the effects.

Thanks very much for your help.

---

### Post by RomeReactor on 2008-02-17
To find out which video card you have, you can go to 'System->Administration->Screens and Graphics' and go to the 'Graphics Card' tab (you can also see there which driver you're currently using).

As far as I know, if Compiz is disabled you can change the number of workspaces by right clicking on the Workspace Switcher applet next to the trashcan, select 'Preferences' and change the number of columns.

When Compiz is enabled you can do that in Advanced Desktop Effects Settings by opening it, pressing the 'General Options' button (first one on the top), going to the 'Desktop Size' tab and change the 'Horizontal Virtual Size'.

---

### Post by bumanie on 2008-02-17
Go to System --> Preferences --> Hardware Information. It should tell you in the list. It will most likel;y (but not definitely) say ATI or NVIDIA about halfway down the list.

---

### Post by kujaabi on 2008-02-17
Intel 915  Experimental modestetting driver

---

### Post by bumanie on 2008-02-17
Sorry, I have no idea about that card. If you had a nvidia card, I probably could have helped. Sorry.

---

### Post by RomeReactor on 2008-02-17
Try running the following and post the output:
```
glxinfo | grep rendering
```
and
```
sudo lshw -C display
```

---

### Post by kujaabi on 2008-02-18
kujaabi@kujaabi-laptop:~$ glxinfo | grep rendering
direct rendering: Yes
kujaabi@kujaabi-laptop:~$ sudo lshw -C display
[sudo] password for kujaabi:
  *-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
kujaabi@kujaabi-laptop:~$

---

### Post by kujaabi on 2008-03-15
The trick was to make sure that: System->Preferences->Advance Desktop Effects Settings', find and press the 'Window Decoration' button.

---

