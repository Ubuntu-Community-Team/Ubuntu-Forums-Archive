---
title: "Matlab 2007b launcher..."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Stochastics on 2008-04-13
Hi everybody,

I've just installed, without problems, Matlab 2007b under Ubuntu 7.10. I created a launcher for this program but everytime i push on it, i just see the splashscreen and nothing else. When i launch the program from the terminal emulator, there is no problem...anyone has the same problem ?

Stochastics.

---

### Post by skrribble on 2008-04-13
i have the same problem with matlab 2007a.  the only way i can get it to open and stay open is to launch it from a terminal and leave the terminal open.... i've never been able to figure it out, but its not a huge deal to me.

---

### Post by Stochastics on 2008-04-13
Ok, thanks !
I just want to know if there is something to do about this...but in the meantime, i will use the command line interface.

Stochastics

---

### Post by twistadias on 2008-04-13
you add a -desktop at the end of the command
so it would be matlabroot/bin/matlab -desktop

Im currently doing this for matlab r2008a, but it should work for the 2007 one as well

---

### Post by Stochastics on 2008-04-13
Yes ! That's working ! Thanks for your help !

Stochastics

---

### Post by kbless7 on 2008-04-14
Yep. Matlab needs the shell of the terminal unless you do the "-desktop" option.

---

