---
title: "Starting in non-graphical mode"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by stimpack on 2005-10-21
Sometimes I just want to run my ssh server without all the baggage of a desktop. Is there anyway to select a command prompt only at boot time? I dont want to remove the graphical option altogether as mostly I do use it as a desktop.

---

### Post by mtron on 2005-10-21
just remove the gdm package via apt-get, (or kdm if you are using kde), you will get text mode login, and can strill start the xserver with "startx" after login

---

### Post by stimpack on 2005-10-21
Ok thank you, I was hoping for a simpler way like a grub entry, but removing kdm should be ok on my spare computer.

Cheers

---

### Post by patrick295767 on 2005-10-21
[QUOTE=mtron]just remove the gdm package via apt-get, (or kdm if you are using kde), you will get text mode login, and can strill start the xserver with "startx" after login[/QUOTE]

startx -- :1
or
startx -- :2
or
startx -- :3
.... 
  
and  so on 
1, 2, ... represents the screen X server ( different than then loaded 0 for the gdm)

Regards,,
Patrick

---

### Post by davmac on 2005-10-21
An alternative is to just open up a virtual terminal - hit ctrl-alt-F1 thru F6 to get straight to a console.

HTH,

Dave Mac

---

### Post by patrick295767 on 2005-10-21
**FIRST :**

[QUOTE=davmac]An alternative is to just open up a virtual terminal - hit ctrl-alt-F1 thru F6 to get straight to a console.

HTH,

Dave Mac[/QUOTE]


**SECOND **
from the console tty1 (if no Xserver is available from (alt ctrl F6) until (alt ctrl F12)
  
> 
startx -- :1
or
startx -- :2
or
startx -- :3
.... 

and so on 
1, 2, ... represents the screen X server ( different than then loaded 0 for the gdm)

Regards,,
Patrick 

I hope taht will help you

Pat'

---

