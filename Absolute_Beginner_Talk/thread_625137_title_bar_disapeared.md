---
title: "title bar disapeared"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-27
i dont know what i clicked, this has happend before.. the title bar disapers from al aplications... i cant move the windows around or close them just esc

---

### Post by PeterJS on 2007-11-27
Oh yeah happens all the time, are you running Compiz? that's pretty much what it does when it crashes. The fastes solution is Atl+F2 and then run *compiz --replace* to restart it. A more permenant solution is to open up the Compiz Settings Manager and configure the crash handler plugin, just put *metacity* in the window manager command line box, this will cause compiz to fall back to the gnome defaults if it crashes in the future.

---

### Post by UtahApocalypse on 2007-11-27
I have been dealing with the same problem. Once Compiz fails, I cant get it to retstart without the title bar crashing. I reinstalled Compiz once to fix it, would rather not again. I seriously am considering not using Compiz until this issue is resolevd.

---

### Post by DutyDuty on 2007-11-27
I'm assuming you are using emerald. I can't really help you if you're not, but if you are, here: 

```
emerald --replace
``` then close terminal.
```
compiz --replace &
``` then close terminal.

Title bars will shift on and off through the process, but you'll finish just fine.

---

### Post by Znort_Ubern00b on 2007-11-28
what graphics cards are you all using...are they nvidia??? i had that problem then entered a bit of code into terminal and it sorted it out...

---

