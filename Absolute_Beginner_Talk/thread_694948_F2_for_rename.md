---
title: "F2 for rename?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-12
What happened to it? I press F2 when selecting a folder and it no longer lets me rename.... hmm... can't wait to reinstall with ubuntu 8.04 to fix this annoyance ;)

sv

---

### Post by HappyFeet on 2008-02-12
it works for me. sometimes just restarting will resolve minor niggles.

---

### Post by staticvoid on 2008-02-13
this has been going on for days... and finally i'm a little fed up with it.. after multiple reboots

sv

---

### Post by staticvoid on 2008-02-13
maybe in keyboard shortcuts..? its not in nataulius preferences.../


sv

---

### Post by staticvoid on 2008-02-13
: / bump... shucks... i hit F2 again... i can't get the hang of using a mouse! iI'm such a key board junky :(

sv

---

### Post by rkd on 2008-02-13
Is there any chance this:

[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)

is related to the problem you are having?

---

### Post by kellemes on 2008-02-13
Maybe stuff is messed up in your user settings?
Try to delete your user settings in ~/.nautilus and see if it works..

Edit: By the way, I assume you're trying to rename folders/files using the right permissions?

---

### Post by rkd on 2008-02-13
Maybe easier than fooling with your current user settings would be to create another user, login as that new user, and see whether the F2 works or not. If it does work for the new user, then your regular user settings somehow got changed to prevent it from working.  

Of course, if the problem is that the user default settings are preventing it from working, it will be prevented by default for the new user, too. But you can experiment freely with the new user's settings without messing up the user settings of the account you usually use when working on your computer. So you can go wild trying different things as the new user to see whether you can find something that affects the action of F2.

---

### Post by staticvoid on 2008-02-13
i tried everything everyone suggested but it still does not work

I have permissions, yes, and the F2 works in the new account

sv

---

### Post by staticvoid on 2008-02-13
hmm... is there like a metacity keybindins xml sheet i can edit? openbox has somthing like that...

sv

---

### Post by rkd on 2008-02-13
There is a package named gtweakui.  If you don't have it installed, install it using your favorite method (it's in Universe).

Once you install it, it adds a number of items under System -> Preferences. "gTweakUi - Menus" is the one of interest. Open it and tick the box beside "Can change menu accelerators".

Then open Nautilus, select a file, go to the Edit menu, move the mouse until the Rename selection is highlighted, then type F2 (or whatever key you want to be the shortcut), then type Esc. That should set F2 to be the Rename shortcut.  

Before you change it, take a look and see what it shows to the right of Rename in the menu. That should be the current accelerator. If nothing is there, or some other key, then that's why F2 didn't work. I don't know how it would have been changed accidentally. If it shows F2 before you try to change it, I have no explanation for why F2 doesn't activate the Rename function now.

---

### Post by staticvoid on 2008-02-14
it says F2 in the menu... i'll try what you said anyway..  :  /
thanks!

sv

---

### Post by jordanmthomas on 2008-02-14
Is your F2 key actually working right?
Try one of these:
does pressing alt + f2 bring up the run dialog?
OR
run
```
xev
```
and hit F2 a few times with your mouse in the window.  Does it report to your terminal that F2 is being pressed?

---

### Post by staticvoid on 2008-02-14
yes, alt F2 brings up the run dialog and pressing it in the terminal after running xev gives me this output (i had to move the mouse out of the terminal so I could copy and paste):

> FocusIn event, serial 27, synthetic NO, window 0x3600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


hmm...

rkd, I installed gtweakui (cool program by the way!) and I changed the menu Rename to F3, now, when I hit F3 it renames the file! but check this out, if I set it back to F2, then it does not work!

this is so wierd..

sv

p.s. i'll use F3 in the mean time... but now I'm curious why F2 does not work!! haha

---

### Post by jordanmthomas on 2008-02-14
This is weird.
Anyway, when I press F2, xev specifically mentions it:
```
KeyRelease event, serial 29, synthetic NO, window 0x1e00001,
    root 0x82, subw 0x0, time 113639635, (-71,8), root:(442,157),
    state 0x0, keycode 68 ([COLOR="Red"]keysym 0xffbf, F2[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

I wonder why yours doesn't?

---

### Post by staticvoid on 2008-02-14
well... I have a sony vaio pcg-tr3a with a wierd keyboard... : /

---

### Post by staticvoid on 2008-02-14
Hey! Wait a minute!  when I hit F3 and F4 I get output similiar to yours..

check out the difference:

> FocusIn event, serial 30, synthetic NO, window 0x4000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 30, synthetic NO, window 0x4000001,
    root 0x65, subw 0x0, time 486380872, (60,107), root:(63,131),
    state 0x0, keycode 69 (keysym 0xffc0, F3), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False



hmm... we're getting some where... is something screwy with whatever is controling my keys? sonypi or something? I think i needed something special for my Fn key to work...

so weird.......

---

### Post by jordanmthomas on 2008-02-14
Seems like it might be possible, and should be fixable with xmodmap since it is detected by the kernel at least.

```
xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p'
```
Run this in a terminal and press F2 then close xev; do any lines starting with
"keycode = "
get printed out?  If so, then we are in business.  If not, this could get complicated.
This page may be of interest to you:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

---

