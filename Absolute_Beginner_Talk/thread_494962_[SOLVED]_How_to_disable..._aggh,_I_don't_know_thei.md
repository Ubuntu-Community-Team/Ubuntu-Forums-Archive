---
title: "[SOLVED] How to disable... aggh, I don't know their name!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-07-07
[EDIT: Name figured out, reflected on the title.]

Geez. Worst name for a thread ever, I know. Still..

You know those little yellow boxes that come up whenever you put your mouse over an icon or a window on a panel? The one that tells you what it is, etc? Since I got Beryl and their live preview of windows, I want to disable these tags. But... I can't find any info on them, since I don't even know what they're called... 

Help?

Thanks...

---

### Post by chessercizes on 2007-07-07
hey!

i believe they're called tool tips.
as to disable them, i really dont know.

good luck :)

---

### Post by reset3x on 2007-07-07
open gnome config  it's in /apps/panel/global/tooltips_enable.. Uncheck...

---

### Post by wpshooter on 2007-07-07
> **reset3x said:**
> open gnome config  it's in /apps/panel/global/tooltips_enable.. Uncheck...

Is this the correct/complete path ?  I don't seem to see an **apps** on my system.  Is this hidden ?

Thanks.

---

### Post by Waappu on 2007-07-07
> **wpshooter said:**
> Is this the correct/complete path ?  I don't seem to see an **apps** on my system.  Is this hidden ?

Thanks.

Hi

Press Alt+F2 and type ```
gconf-editor
```and then find that setting and uncheck

---

### Post by gcsoares on 2007-07-07
I think he means Applications or somethink like that...

---

### Post by sab0403 on 2007-07-07
Ok, got it.

So... do I reboot? Log out/in?

Thanks!!!

---

### Post by reset3x on 2007-07-07
> **sab0403 said:**
> Ok, got it.

So... do I reboot? Log out/in?

Thanks!!!

Then settings should work right away... If not open a terminal and :

```
killall gnome-panel
```

---

### Post by sab0403 on 2007-07-07
Ok... I restarted... it works but on the Menu items... not on the windows (well, the windows list), nor on the icons on the panel itself...

:(

---

### Post by Waappu on 2007-07-07
> **sab0403 said:**
> Ok, got it.

So... do I reboot? Log out/in?

Thanks!!!

Hi

Note that setting not disable Window List tool tips. I haven't find any setting to disable those

---

### Post by sab0403 on 2007-07-07
Hmm...

Well, thanks anyway. :)

---

