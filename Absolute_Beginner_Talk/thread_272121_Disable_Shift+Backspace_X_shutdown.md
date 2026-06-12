---
title: "Disable Shift+Backspace X shutdown"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by sleestak240 on 2006-10-05
Hey all,
So I find myself accidentally shutting down my X Server when typing every now and then because I hold shift and press backspace.  I've had to retype enough emails now that I've decided it's time to try and disable it.  Ctrl+Shift+Backspace is fine, but not Shift+Backspace.  What is the best course of action to remove the mapping on those keys?

---

### Post by henriquemaia on 2006-10-06
The default is ctrl+shift+backspace. I have tried on mine and shift+backspace doesn't do anything.

You can disable the xserver termination key sequence altogether by adding this to your xorg.conf
[B]
 Option "DontZap"  "boolean"[/B][INDENT]This disallows the use of the Ctrl+Alt+Backspace sequence. That sequence  is  normally  used to terminate the Xorg server. When    this option is enabled, that key sequence has no special meaning and is passed to clients.  Default: off.
[/INDENT]

---

### Post by Jeremiah478 on 2006-10-19
I just found this on another thread, to fix the same problem with shift+backspace, but I think it might be an compiz trouble.  If you type:
xmodmap -e "keycode 22 = BackSpace"
into a terminal window it should disable the key combination, and to make it perment you can add it to Startup Programs in Sessions.

Hope this help, I know it was bugging me.

---

### Post by Dual Cortex on 2006-10-19
Yeah, it's a combination from Compiz. I tried adding that command to the Startup PRograms and it still does not work :|

---

### Post by Jeremiah478 on 2006-10-19
Well I found another thread that has what I think is a little better solution, which is to add the command right to the compiz-start file.
Have a look:
[http://ubuntuforums.org/showthread.php?t=271156&highlight=shift+backspace](http://ubuntuforums.org/showthread.php?t=271156&highlight=shift+backspace)

---

