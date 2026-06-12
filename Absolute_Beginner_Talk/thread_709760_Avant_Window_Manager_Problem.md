---
title: "Avant Window Manager Problem"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by seamustry on 2008-02-27
i installed it and i click on it in system>preferences but nothing happens. no box or bar or anything. it's like it's not there...how can i get started with this dock?

thanks!

---

### Post by fedex1993 on 2008-02-27
are you running a transparency manager like compiz or xcompmgr?

---

### Post by rustutzman on 2008-02-27
Is it also listed under Accessories? If so try that one.

---

### Post by rouge568 on 2008-02-27
1) Make sure you are using a window compositor, such as Compiz. Avant won't work without one.
2) Paste this into a terminal: avant-window-navigator
This should start it up for your current session, but you have to leave the terminal window open to keep it running (alternatively, you could press alt+f2 and insert the command, this won't leave a window lying around). This is a pain so...
3) Got to System>Preferences>Sessions. Add avant-window-navigator as a startup command. Now Avant will start every time you start the computer.

Reply back if you run into anything!

---

### Post by LuisGMarine on 2008-02-27
Try running it with:  Type this into a terminal window,

```
avant-window-navigator &
```

for the meantime.  However ....

If you want to manually add it to your menu, find menu list somewhere in the *Preference > Main Menu*.  Once there navigate on the left hand side to where it says Accessories and click on that, and then on the right hand side click on " New Item "

In the pop up window type in for the following fields

**Type:** Application
**Name:** Avant Window Navigator
**Command:** avant-window-navigator
**Comment:** A dock-like window navigator.

---

### Post by seamustry on 2008-02-28
ok i'll try it and yes i'm running compiz...just a question, what does "&" mean when you type it like "avant-window-navigator &"

thanks

---

### Post by Peter09 on 2008-02-28
The & sign makes the program run in the background. The prompt on the terminal will return and you can shut down the terminal without stopping the task.

---

