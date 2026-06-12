---
title: "[SOLVED] Problems with &amp;quot;Take Screenshot&amp;quot; shortcut ... prevent it NOT to use Compiz Fu"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-10-10
Hi

I got some problems about the "Print Screenshot" shortcut.
I recently removed Compiz Fusion from my Ubuntu 7.04 desktop to be ready for the 7.10 version

Now, when I hit the "PrtSc"-bottom on my keyboard I get this error (in Danish):

*"Der opstod en fejl ved kørsel af "/usr/share/compiz/take-screenshot.sh": Fejl under kørsel af underprocessen "/usr/share/compiz/take-screenshot.sh" (No such file or directory)." *

It seems that it still tries to take a screenshot via the Compiz Fusion program, which is impossible.
How do I change the shortcut to use the default "Take Screenshot" program like in **Programs -> Accessory -> Take Screenshot**?

The "gnome-panel-screenshot" command still works, but the key shortcut doesn't.

---

### Post by rsambuca on 2007-10-10
Can you reset it from "System -> Preferences -> Keyboard Shortcuts"?

---

### Post by phr0ze on 2007-10-10
Its a cheap work-around but you could always just put a file called usr/share/compiz/take-screenshot.sh in your system which calls the default gnome screen shot.

---

### Post by rsambuca on 2007-10-10
I think I found it.  If you open gconf-editor in a terminal, go to Apps > Metacity.  There is a section on Keybinding Commands where you can set the print screen action.

---

### Post by Wikzo on 2007-10-10
> **rsambuca said:**
> Can you reset it from "System -> Preferences -> Keyboard Shortcuts"?
No, the shortcut is correct. The Print Screen bottom is set to take a screenshot ... can't change the screenshot program there.


> **phr0ze said:**
> Its a cheap work-around but you could always just put a file called usr/share/compiz/take-screenshot.sh in your system which calls the default gnome screen shot.
If no one can help me, will you help me to make that file?

---

### Post by Wikzo on 2007-10-10
> **rsambuca said:**
> I think I found it.  If you open gconf-editor in a terminal, go to Apps > Metacity.  There is a section on Keybinding Commands where you can set the print screen action.
How do I open gconf-editor?

---

### Post by rsambuca on 2007-10-10
"Applications -> Accessories -> Terminal"

```
gconf-editor
```

---

### Post by Wikzo on 2007-10-10
I thought you had to do something special about it, but I figured it out now.

It works. Thanks! :D

---

### Post by rsambuca on 2007-10-10
Good stuff!!  So after that you may as well post us a screenshot of your desktop!

---

### Post by Wikzo on 2007-10-10
Hehe, it is not something special. Very similar to the standard Ubuntu desktop on a clean install :P

But thanks again, it is a nice shortcut to have.

---

