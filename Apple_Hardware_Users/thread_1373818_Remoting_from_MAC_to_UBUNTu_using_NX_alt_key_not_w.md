---
title: "Remoting from MAC to UBUNTu using NX: alt key not working"
date: 2010-01-06
forum: Apple Hardware Users
---

### Post by dreamspy on 2010-01-06
Hi there

I'm using NX to remote controle my ubuntu machine from my Macbook, and the trouble is that the alt key is not working. 

Anyone know how to fix this?

regards
Frímann

---

### Post by daschel on 2010-01-15
Add a few lines to macosx:~/.Xmodmap to map the alt key, then restart X on the Mac.

    keycode 66 = Alt_L
    clear Mod1
    add Mod1 = Alt_L Alt_R

More info and some extra settings are on [http://stateless.geek.nz/2005/06/27/nx-osx-and-the-alt-key/](http://stateless.geek.nz/2005/06/27/nx-osx-and-the-alt-key/)

---

### Post by dreamspy on 2010-03-20
Thanks allot, worked beautifully.

---

### Post by cafewalter on 2010-04-21
I have the same situation and exactly the same problem.  However, I have already tried adding those lines to my ~/.Xmodmap on the Mac, quitting X11, running 'xmodmap ~/.Xmodmap' from a terminal window, and then reconnecting to my X session.  My Alt key still doesn't work.

When I run xev in Ubuntu (9.10), and press the left Alt key, I see this:

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x133, subw 0x0, time 583156147, (327,276), root:(333,358),
    state 0x0, keycode 66 (keysym 0xff7e, Mode_switch), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
(and then the corresponding keyRelease event).

When I press Alt+Tab, I see the above KeyPress for the Alt, and then this:

KeyPress event, serial 32, synthetic NO, window 0x4c00001,
    root 0x133, subw 0x0, time 583238047, (624,419), root:(630,501),
    state 0x2000, keycode 56 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "    "
    XmbLookupString gives 1 bytes: (09) "    "
    XFilterEvent returns: False
(and then both KeyRelease events).

Note the "state 0x2000" which I think means that it at least knows that Mode_switch is depressed.  

Do I need something specific in the .Xmodmap on the Ubuntu side, for the Mac .Xmodmap change to make a difference?

Thanks for any help!

---

### Post by BeeOnRope on 2010-10-25
What does

```
xmodmap -pm
```report on the mac and on the linux both?

What does xev report on the mac box when you push the alt key?

It seems like the NX client is not pushing the local keyboard map on the mac side to the Linux host.  Are you connecting to an existing X session on the remote box or a new one?  You could remove or rename your .Xmodmap on your linux box entirely to help diagnose the issue.

---

