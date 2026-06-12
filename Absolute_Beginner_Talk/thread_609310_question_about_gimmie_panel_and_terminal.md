---
title: "question about gimmie panel and terminal"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by windfer on 2007-11-10
how do I get the gimmie panel to show up when I type gimmie in the terminal it show up but when I exit the terminal it goes away how do I keep it there. And how do I launch programs from the terminal

---

### Post by jordanmthomas on 2007-11-10
when you launch a program from a terminal, it is a *child process* of the terminal.  When the terminal dies, its children die as well.

To get around this, the simplest way is to press alt + f2 to launch programs you want to stay running.  Of course, as with most things in Linux, there's about 10 other ways to do it too.

---

### Post by windfer on 2007-11-10
thank you

---

### Post by Paul820 on 2007-11-10
Hi windfer, you can make a menu entry for it. First, go to the terminal and copy and paste this or type it in:
> whereis gimmie
That will give you the path to it. It should be **/usr/bin/gimmie**, but you better check anyway. Now you need to go to System->Preferences->Main Menu and make the menu item. In the left box choose where you want it to go, accessories looks good, and on the right choose **new item**, for the name type **gimmie** and the command **/usr/bin/gimmie** then click ok.

If you want it to start when you boot into ubuntu, go to System-Preferences->sessions and click add, for the name put **gimmie** and the command **gimmie** again. You should be set now. :)

---

### Post by jw5801 on 2007-11-10
You can also separate any process from the terminal by placing an "&" after it. So that you can then close the terminal:
```
gimmie &
```

---

### Post by jordanmthomas on 2007-11-11
> **jw5801 said:**
> You can also separate any process from the terminal by placing an "&" after it. So that you can then close the terminal:
```
gimmie &
```

I don't believe this will work.  Try it with say...gedit or something.
This would work, though, if you still wanted to use a terminal to launch thing:
```
nohup gimmie &
```
The nohup is there so the program doesn't get the hang-up signal when the terminal is closed.

---

### Post by Ub1476 on 2007-11-11
Or you can right click on the panel>add to panel..>Gimmie:)

---

### Post by jw5801 on 2007-11-11
> **jordanmthomas said:**
> I don't believe this will work.  Try it with say...gedit or something.
This would work, though, if you still wanted to use a terminal to launch thing:
```
nohup gimmie &
```
The nohup is there so the program doesn't get the hang-up signal when the terminal is closed.

The nohup isn't necessary. Running gedit (or anything) from terminal with "&" appended creates a new and separate process that doesn't get a kill signal when the terminal is closed.

---

### Post by jordanmthomas on 2007-11-11
I'm just suggesting you try it...because you appear to be misinformed.  The & just backgrounds the process, letting you continue to use the terminal.

To make sure I was right, I just tried it and when I closed the terminal, gedit closed as well.

---

### Post by jw5801 on 2007-11-11
well that's strange because I've done it hundreds of times and I did it again the second I read your post, and gedit didn't close when I closed the terminal! Ok, miscommunication! It depends how you close the terminal window as to what happens, if you close it by clicking the "x" in the corner, then yes, gedit also closes. But if you close it by running "exit" or pressing ctrl+d (does the same thing as typing exit), then it doesn't close gedit. Not entirely sure why. Apologies for contradicting you, I haven't used a window manager to close a terminal (ie. clicking the "x" or using alt+F4 or another keyboard shortcut) in a long time. so I wasn't aware of the alternate behaviour.

The ampersand doesn't just background the process though, if you run gedit and then background it (ctrl+z) and then try to exit (by typing exit or hitting ctrl+d) you get different behaviour. Closing the terminal via the window manager has the same effect however.

---

### Post by jordanmthomas on 2007-11-11
Ah, well there you have it.  :)
My apologies to you as well, and thanks for the lesson on & and it not just backgrounding.

I rarely start programs from a terminal that don't live in terminals.
(xbindkeys handles all the GUI apps I use pretty easily)

---

