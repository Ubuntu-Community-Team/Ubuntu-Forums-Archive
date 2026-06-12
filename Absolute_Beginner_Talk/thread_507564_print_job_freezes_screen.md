---
title: "print job freezes screen"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by novice_forever on 2007-07-23
Hi,

I have just set up my hp deskjet 5550. When I print something, the screen freezes for 2 Minutes or so. Then suddenly, the printer starts to work and prints O.K. Any idea what might cause this?

---

### Post by Pragmatist on 2007-07-23
What application(s) are you printing from?

---

### Post by novice_forever on 2007-07-25
> **Pragmatist said:**
> What application(s) are you printing from?
openoffice
kate
kivio

---

### Post by Pragmatist on 2007-07-25
What happens if you print a very simple text file from a basic editor like kedit?  Just open kedit and type this (or a few lines of your choosing):

> 
Testing 1...2...3...
Hello, World!
Line 3
Line 4
Goodbye!


After printing this file in kedit, save the file in your home directory, and type this (I'll call the file "testfile")(make sure to include the semicolon ";" after cd)

```
cd; lpr testfile
```

---

