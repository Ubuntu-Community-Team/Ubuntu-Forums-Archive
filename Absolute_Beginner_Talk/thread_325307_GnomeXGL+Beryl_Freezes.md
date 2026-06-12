---
title: "Gnome/XGL+Beryl Freezes"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by klayn on 2006-12-25
Hi all,

I am running Gnome/XGL+Beryl on my system configured with an ATI Radeon All-in-wonder 9700. I have more than enough RAM and everything else works fine, but occasionally, my desktop will freeze with the exception of the mouse pointer. Everything else stops responding, but things that were already running keep running (for example, my desktop will freeze but if I had music playing it will continue to play). I can move the mouse but I can't click on anything. The only thing that I get a response from is (Alt+SysReq+B), which doesn't help me too much. After searching some of the forums, I found out to get the output of my /var/log/Xorg.0.log, which outputs this at the end:
```


(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueTyp
e, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
```

Can anyone translate this for me? Is there a fix?

Thanks in advance...

---

### Post by BLTicklemonster on 2006-12-28
Me, too, but I'm using nvidia, and it started when I tried to use xgl for rendering in the settings menu. There's one renderer that makes the cube super clean, but I can't ever remember which one it is, and inadvertently clicked xgl and now it has the same symptoms you have. Nothing works, but I can move the mouse.

I'd have figured beryl would consider this untenable, and would resort back to metacity and reset itself, but I guess the beryl programmers didn't think of this.

Anyway, yep, I did it before, and danged if there's not a rm- something command you can use, but heck if I can find it again. I've been searching this forum for 30 minutes looking for it now.

If I find it, I'll try to remember to put it here for you.

(and if you found out how to correct this, please post back, too)

---

### Post by BLTicklemonster on 2006-12-28
lmao, I googled 

```
rm ~/.beryl
```
 
and found this command:

```
rm ~/.beryl-manager* -R

```

and I'm back up running again. 


Good thing I thought to post this time! Now I can just search threads I posted in and find this again 2 minutes from now when I mess it all up again. :)

---

### Post by actinium on 2006-12-31
Hello, 

I had been having the same problem, didn't find the solution to the crash of beryl but i can force metacity to load up again if beryl crashs:

Beryl Settings Manager / Crash handler

Select "Start Window Manager" and put metacity in the command line box below, think it just got left off the default so it just doesn't load any windows manager once beryl crashes.

Regards, 

Alan

---

### Post by eduac on 2007-08-11
i got this problem too :( what a pitty. Probably because open xgl is a beta.

---

