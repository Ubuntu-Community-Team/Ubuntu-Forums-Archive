---
title: "[SOLVED] arrow key &amp;quot;down&amp;quot; doesnt  work"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by conphara on 2007-09-06
Suddenly on my laptop the down arrow doesnt work in apps in order to scroll down pages in browsers, openoffice etc. but it does work scrolling menues. Strange, since I havent messed around with changing shortcuts or anything. 
Any suggestions? :confused:

---

### Post by Daveski on 2007-09-12
Silly I know, but you haven't got scroll-lock on have you?

---

### Post by conphara on 2007-09-13
The problem solved itself. Now it works again. It must have been scroll-lock even though the lit doesnt show on my laptop. I dont know what caused it to do so. Another guy on the board had the same problem...

---

### Post by Burekarna on 2007-10-09
well i'm having the same problem on my laptop (it's HP 6715b). The problem is the same like you had it. My down arrow key is not working.
So i was wondering if there is any chance to get it working.
Please help because it's driving me crazy. I tried even with the xev command and i've got this:
> 
FocusOut event, serial 28, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 28, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

so please please, can anybody help me on this? I do not have scroll On because i tried it many times. 
Thnx, B


SOLVED: The problem was in keyboard shortcuts. Down key was defined as a shortcut for a "log of" so that's why it didn't work.

---

