---
title: "possible to exec multiple commands in one fluxbox menu entry"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-06-25
just as the title says
is it possible to exec multiple commands in one entry... 
like have a Shutdown entry that would
exec {something}
then
exec {sudo shutdown now}

all with the click of one menu entry???

---

### Post by BobCFC on 2007-06-25
That is what shell scripts are for.   I'm sure you can find a tutorial, they are basically just text files that you make executable

---

### Post by kerry_s on 2007-06-25
Yes, but you have to be using 1.0rc and up.

* Added new commands:
      * ToggleCmd
        Works like a macro but executes the commands one at the time in order.
        Example:
        Mod1 T :ToggleCmd {Exec xterm} {NextWindow}
        When Mod1 T is press the first time it will start xterm, the second time
        it will do NextWindow. When it reaches end it will start at the beginning.

[http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)


Edit: woops read that to fast. in the menu Yes and No, for applications you can do a script, but it's just a kinda hack, not worth the effort.

---

### Post by Nythain on 2007-06-25
> **BobCFC said:**
> That is what shell scripts are for.   I'm sure you can find a tutorial, they are basically just text files that you make executable
not quite a yes, here's how or no, but have you considerd, type of answer but effective non the least... thanks

---

