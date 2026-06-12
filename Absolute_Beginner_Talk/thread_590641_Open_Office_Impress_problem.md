---
title: "Open Office Impress problem"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-10-24
My OO Impress won't start.  When I click to start it, it freezes after the frame pops up.  Any thots would be appreciated,
Thanks ; )

---

### Post by jfinkels on 2007-10-25
Do you get any error output when you open the program from the terminal by typing this:```
/usr/lib/openoffice/program/simpress
```

---

### Post by MrKlean on 2007-10-25
nope..the cursor jumps to the next line and just sits there ; (

---

### Post by jfinkels on 2007-10-25
Okay that means that the program is running...to see processes and their processor usage, open a terminal and type:```
top
``` See if you can find 'simpress' or 'ooffice' in there. I don't really know what to tell you about this, have you tried reinstalling?```
sudo aptitude reinstall openoffice
```

---

### Post by MrKlean on 2007-10-25
I have the quickstarter loaded.  When I click for presentation...I only get the boeder...nothing else. When I click the X to close it, I get the box that shows the force quit ; (
I tried reinstalling, but will again 
Thanks ; )

---

