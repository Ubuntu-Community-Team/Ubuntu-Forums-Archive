---
title: "[SOLVED] How do I install an .exe program with WINE? [Solved]"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-10-02
Hi,everybody.
I've just installed WINE in order to run DMT.exe, a program that monitors my SpeedTouch 536 router and gives useful information about the ADSL connection.Nevertheless,I've tried double-clicking on the DMT.exe icon on the desktop, but it tells me : 
"Cannot open /home/socrates/Desktop/DMT.exe: No application suitable for automatic installation is available for handling this kind of file".

What am I doing wrong?
Thank you.

---

### Post by Majorix on 2007-10-02
You have to associate WINE with .exe files by right clicking any exe file and typing in "wine" under open with.

---

### Post by NovaAesa on 2007-10-02
Open the console and type:

```
wine path/to/program/DMT.exe
```

Making sure to set the appropriate path.

---

### Post by sdim on 2007-10-02
Thank you both for the answers.
The console command didn't work but the first solution did.

---

### Post by shavenlunatic on 2007-10-02
strange.. had you ran winecfg when you initially installed it?

---

### Post by sdim on 2007-10-03
No,nothing like that.

---

### Post by shavenlunatic on 2007-10-04
ah.. when you first install wine... type winecfg in the console.. it brings up a settings window.. most of the settings you can leave as default but browse through each of the tabs anyway.. once you ok and close it.. it completes the setup fully.

---

