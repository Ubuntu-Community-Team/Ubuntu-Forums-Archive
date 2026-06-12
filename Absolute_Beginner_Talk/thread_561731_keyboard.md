---
title: "keyboard"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by amtnbiker16 on 2007-09-27
my left and right directional arrows do not seem to be working, but they used to
perhaps someone knows what is going on

---

### Post by ofb on 2007-09-27
Have you checked to see if the keyboard is the problem? Like by booting into Windows if you dual-boot, or by trying that keyboard on another computer, or another keyboard on that computer.

(Computers should be Off when plugging and unplugging keyboards.)

---

### Post by amtnbiker16 on 2007-09-28
its a laptop, and i know that the buttons work on windows, actually
it was only recently that this started happening
i think it was working fine when i installed ubuntu a couiple of months ago
i think the problem is that it is missing the command to tell it what to do when i push the 
left or right arrow

---

### Post by ofb on 2007-09-28
Well, that's very odd. I guess the obvious question is what did you change when that happened? 

While you're thinking about that, open a terminal and enter: xev

The terminal now outputs your inputs -- you can see code scroll by as you key or mouse. Press the left and right arrows once each to see what you get for those. (Hit ScrLck after pressing the arrows to stop the terminal from scrolling further.)

For me,

KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0xa2, subw 0x0, time 683432, (206,-76), root:(221,0),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0xa2, subw 0x0, time 683598, (206,-76), root:(221,0),
    state 0x10, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0xa2, subw 0x0, time 690366, (206,-76), root:(221,0),
    state 0x10, keycode 102 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0xa2, subw 0x0, time 690470, (206,-76), root:(221,0),
    state 0x10, keycode 102 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

And I suppose, just for the heck of it, you can try plugging in an external keyboard to see what that does, and you can run your Ubuntu LiveCD too. What I'm half wondering is if your laptop uses a special keymap that isn't supported by Ubuntu at default, and you just didn't notice it at first.

---

### Post by amtnbiker16 on 2007-10-01
this is what im geeting (Left key, then right key)

FocusOut event, serial 30, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 30, synthetic NO, window 0x3800001,
    atom 0x104 (_NET_WM_STATE), time 1224883, state PropertyNewValue



now the right


FocusOut event, serial 30, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 30, synthetic NO, window 0x3800001,
    atom 0x104 (_NET_WM_STATE), time 1261551, state PropertyNewValue




i dont know what any of this means

---

### Post by amtnbiker16 on 2007-10-01
never mind, I figured out what i did

i used those keys as shortcuts for my music player, assuming they would only work as 
shortcuts while i was using it

---

### Post by amtnbiker16 on 2007-10-01
thanks anyway though

---

