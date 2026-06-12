---
title: "how to close currently selected widnow from terminal?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-06-04
is there a command to close the currently selected window from a terminal?

im want brightside to close windows when i drag them to the upper left corner of my screen.

Thanks,

---

### Post by drs305 on 2007-06-04
I don't think this is exactly what you are looking for but to me it would be just as easy. It wouldn't close the 'currently selected window' because when typing in terminal, the terminal IS the current window.

Anyway, in terminal, type xkill  .  It will turn the mouse cursor into a skull and crossbones. Use your mouse and whatever you next click on immediately closes. As I said, I don't think it is what you were thinking about. The reason I think it would work just as well is that you want to drag a window to close it, whereas this kills the window immediately, as soon as it is touched - no dragging required!

---

### Post by jinxjinx on 2007-06-05
thats a cool solution. 

but when i have firefox open it kills all windows and not just the one i click on.

---

### Post by jfinkels on 2007-06-05
> **jinxjinx said:**
> thats a cool solution. 

but when i have firefox open it kills all windows and not just the one i click on.

You mean all your firefox windows? Maybe the single firefox process that is killed includes the multiple firefox windows.

Of course, you could always just press <Alt>+<F4> or click the X or go to File > Quit :P

---

### Post by Carbonfish on 2007-06-05
Yeah, I was going to suggest <ALT>+<F4> myself, but that just seemed too easy. 


;)

---

