---
title: "Black screen after Gnome / Beryl starts"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Mikeinnc on 2007-07-29
I have had Beryl working **perfectly **for some months now on Ubuntu Feisty. However, it had not been making full use of my screen resolution. Today, I fixed that and changed my screen resolution and the effect was great! Perfectly rendered fonts etc. However, Beryl seemed to have a glitch as the terminal program now only showed a pure white window when it was selected. The terminal program is obviously running - I can hover my mouse over the top of this entirely white window and see the pulldown menus. I can also type commands into the window, and they work - although, of course, I couldn't see the text! (Other program windows, such as Gedit were working fine.) In addition, I had lost the ability to use the mouse to directly move the windows, unless I did a right click on the taskbar window icon and selected 'move' when I COULD then move them. 

I looked in the forums for a possible fix to this problem and found a post that suggested I needed to choose 'Advanced Beryl Options > Rendering Path > Copy' and select this. I did - and now have a disaster! When the desktop starts, I see everything exactly as it should be, as all the various components start up. The Gnome desktop is perfect; the resolution is correct but (I guess), as soon as Beryl kicks in, the screen suddenly goes absolutely black with only the mouse pointer shown. Linux is still running - I can switch to other terminals ok, but obviously the seelection of that 'Copy' in the Beryl Advanced options has killed the GUI. This must be something really simple to 'undo' that command. Does anyone know where I can go or how to undo what I have done and  - at least - get back to where I had a working GUI desktop? I can worry about white terminal screens and non-movable windows later!!

(For info it is a HP F1703 LCD monitor with Nvidia GEForce4 graphics - although this shouldn't be too relevant as it was all working PERFECTLY!)

---

### Post by Mikeinnc on 2007-07-29
I think I may have answered my own problem - or at least the first part! I discovered and edited the file ~/.beryl-managerrc to change the value 'render_path' in the section [beryl-settings] to 0 instead of 2 (2 is obviously 'copy' which caused the problem). My GUI is back! :KS

However, now I'm back to the original problem - an all white terminal screen that "works" (if you consider white text on a white background working :) ) and windows that appear to have lost their border and "can't" be moved directly with the mouse, unless I right click on the taskbar icon for that window and choose 'move' first......

Any comments very welcome!

---

### Post by ReX0r on 2007-08-06
have you tried alt+mousedrag? Worked for me when I fixed my problem by using kde instead of gnome, I'm going to try your workaround now so I can access gnome again.

After looking a bit at [forums.gentoo.org]("http://forums.gentoo.org/viewtopic-t-500902-postdays-0-postorder-asc-highlight-compiz+white-start-25.html")
it seems you must downgrade glproto.

edit: ah black screen was your original problem,

---

