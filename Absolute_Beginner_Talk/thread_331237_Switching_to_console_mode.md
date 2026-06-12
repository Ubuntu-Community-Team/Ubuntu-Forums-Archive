---
title: "Switching to console mode"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-01-04
Using Edgy. Pressing Ctrl-Alt-F1 (or any of the other F key) does nothing. How do I fix this?

---

### Post by raul_ on 2007-01-04
what's the output of this command?
[code]
cd /etc/event.d
ls -a
[code]

---

### Post by Patrick K on 2007-01-04
Her you go:
> .                   rc0           rc2  rc6          sulogin  tty4
..                  rc0-halt      rc3  rc-default   tty1     tty5
control-alt-delete  rc0-poweroff  rc4  rcS          tty2     tty6
logd                rc1           rc5  rcS-sulogin  tty3


---

### Post by Patrick K on 2007-01-04
Here you go:
> .                   rc0           rc2  rc6          sulogin  tty4
..                  rc0-halt      rc3  rc-default   tty1     tty5
control-alt-delete  rc0-poweroff  rc4  rcS          tty2     tty6
logd                rc1           rc5  rcS-sulogin  tty3

Sorry for the double post

---

### Post by raul_ on 2007-01-04
Weird...what do you mean with nothing? They just do really nothing or take you to a blank screen with a blinking underscore?

---

### Post by Patrick K on 2007-01-04
Absolutely nothing. Nothing whatsoever happens. F1 by itself brings up HELP, so the keys aren't dead.

---

### Post by raul_ on 2007-01-04
What's your keyboard mapping/Layout?

---

### Post by raul_ on 2007-01-04
[https://launchpad.net/ubuntu/+source/xorg/+bug/24073]("https://launchpad.net/ubuntu/+source/xorg/+bug/24073")

Try these solutions. they're for breezy but may help you

---

### Post by Patrick K on 2007-01-04
I selected English standard, I'm not sure of the terminology, when I installed.

---

### Post by bapoumba on 2007-01-04
Are you using Xgl or beryl or some proprietary video drivers ? There are several threads on this forum talking about that problem.

---

### Post by Patrick K on 2007-01-04
I found this using the xkbcomp :0 - command:
```
    key <FK01> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F1, XF86_Switch_VT_1 ]
    };
    key <FK02> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F2, XF86_Switch_VT_2 ]
    };
    key <FK03> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F3, XF86_Switch_VT_3 ]
    };
    key <FK04> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F4, XF86_Switch_VT_4 ]
    };
    key <FK05> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F5, XF86_Switch_VT_5 ]
    };
    key <FK06> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F6, XF86_Switch_VT_6 ]
    };
    key <FK07> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F7, XF86_Switch_VT_7 ]
    };
    key <FK08> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F8, XF86_Switch_VT_8 ]
    };
    key <FK09> {
        type= "CTRL+ALT",
        symbols[Group1]= [              F9, XF86_Switch_VT_9 ]
    };
    key <FK10> {
        type= "CTRL+ALT",
        symbols[Group1]= [             F10, XF86_Switch_VT_10 ]

```

Wouldn't the VT_1 through 10 be the virtual terminals? Most of what was posted on that site made very little sense to me. 

> 
Are you using Xgl or beryl or some proprietary video drivers ? There are several threads on this forum talking about that problem.
I'm using the NV drivers that were installed with the original installation.

---

### Post by Patrick K on 2007-01-04
Well, it is sort of resolved. The right side alt and ctrl keys don't work but the left side do. I guess I can live with that. Thanks for your efforts.

---

### Post by raul_ on 2007-01-04
LOL! all this time you were doing it with the right side keys?

---

### Post by MkfIbK7a on 2007-01-04
i dont understand that  no computer i have used with edgy alows use of right side keys...

---

### Post by raul_ on 2007-01-04
It does, but the right side ctrl and alt are different from the left side ones:P no wonder he couldn't get to a console

---

### Post by Patrick K on 2007-01-04
> **wert613 said:**
> i dont understand that  no computer i have used with edgy alows use of right side keys...

It makes no sense to me either. I wonder if this is documented anywhere.

---

### Post by raul_ on 2007-01-04
They do work! Ctrl works fine, but Alt isn't Alt; it's ALT GR. Can't you write @ by presing right alt+2? Well at least it does here. It just proves that it works

---

### Post by Patrick K on 2007-01-04
> **raul_ said:**
> They do work! Ctrl works fine, but Alt isn't Alt; it's ALT GR. Can't you write @ by presing right alt+2? Well at least it does here. It just proves that it works With the right alt+27 I get 27, with the left alt+27, I get nothing. Maybe my KB has gone bad. I have another, I'll try when I shutdown and can unplug. It's very old with a large old style plug and adapter to a PS2 plug.

---

### Post by raul_ on 2007-01-04
If you want to compare later: alt+23

right alt: @£

left alt: swtiches tabs in firefox

I have an european keyboard

---

### Post by MkfIbK7a on 2007-01-04
hmm my xorg/conf file says i have the lv3:right alt switch rule set...

---

### Post by vtron on 2007-01-09
> **bapoumba said:**
> Are you using Xgl or beryl or some proprietary video drivers ? There are several threads on this forum talking about that problem.

I'm running Beryl and can't use any virtual terminals.  I ran a search for the threads you're talking about but can't find any.  Do you have any links?  Thanks.

---

### Post by bapoumba on 2007-01-09
[http://ubuntuforums.org/showthread.php?t=298678]("http://ubuntuforums.org/showthread.php?t=298678")
This one might be even more helpful ;)

---

### Post by Karuna_bdc on 2008-03-03
> **raul_ said:**
> Weird...what do you mean with nothing? They just do really nothing or take you to a blank screen with a blinking underscore?
Mine does that, i get the blinking underscore on a blank screen, whats the deal with that?

---

### Post by mali2297 on 2008-03-03
> **Karuna_bdc said:**
> Mine does that, i get the blinking underscore on a blank screen, whats the deal with that?

See here:
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

---

