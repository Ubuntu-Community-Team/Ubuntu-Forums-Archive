---
title: "wine resolution"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by realizee on 2008-03-29
Hi, I was trying to fix my wine resolution from the winecfg but then o sort of missclicked and now the windows that open when u write winecfg in alt+f2 is in 1024*768 does someone know how i can change this resolution? i've tried to open winecfg but it pops up a small window with the resolution 1024*768 and i can't change it's resolution. I've tried to complete delete it from the synaptic package mananger but it haven't been a diffrence, Please help , thanks. !

---

### Post by forrestcupp on 2008-03-29
Your problem is that you chose to 'Emulate a virtual desktop.'  Just go in and uncheck that box in the Graphics tab.  What that does is make a window whatever size you choose that emulates a Windows desktop.  When you do that, every time you run a program in Wine, it will create a large window that emulates a desktop with whatever you want to run as a smaller window within the big one.  The purpose for that is that sometimes it helps some compatibility issues.

Evidently that is not what you want, so uncheck that box.  A virtual desktop is the only thing you need to set a resolution for.  You don't need to set any wine resolutions if you're not using it.  You can set individual resolutions within full screen wine apps that have that option.

---

### Post by realizee on 2008-03-29
If i could i would do that but the window is to small and i cant resize it, and the cfgwine window is to big for the windows i cant scroll it down.

---

### Post by forrestcupp on 2008-03-29
then open up a terminal and type
```
cd ~
rm ./.wine
```
And that will remove all of your wine settings.  **Warning**, it will also remove everything you've installed with wine, so you'll have to reinstall everything.

After you do that, type
```
winecfg
```
and everything should be back to normal.

---

### Post by realizee on 2008-03-29
when i write cd ~ 
it doesn't happen anything and when i write "rm ./.wine" it says "rm: cannot remove `./.wine': Is a directory"

---

### Post by forrestcupp on 2008-03-29
When you type **cd ~** nothing happened because you were already in your home directory.

About the 2nd command, sorry, it should have been
```
rm -rf .wine/
```

---

### Post by realizee on 2008-03-29
> **forrestcupp said:**
> When you type **cd ~** nothing happened because you were already in your home directory.

About the 2nd command, sorry, it should have been
```
rm -rf .wine/
```   hehe, that didn't either work. sorry for my bad knowledge about ubuntu :P

---

### Post by forrestcupp on 2008-03-29
Well, just open up Nautilus in your home directory and go to the View menu and check the 'Show hidden files' box.  Then find the .wine folder, right click it, and move it to trash.

---

