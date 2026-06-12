---
title: "trying to install wine"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by taxonrath on 2007-02-02
this is only my second day with ubuntu so im not very good with it. im trying to install wine but when i try it says 

configure: error: no suitable lex found. Please install the 'flex' package.

i dont know what that means or how to do it. can someone explain this to me?

---

### Post by ew16301 on 2007-02-02
Try this command

[PHP]sudo apt-get install wine[/PHP]

That should pull in the dependences. Otherwise, if you just want flex. Try:

[PHP]sudo apt-get install flex[/PHP]

---

### Post by taxonrath on 2007-02-02
and where would i have just installed that to?

---

### Post by mongooseman1128 on 2007-02-02
if you ran the apt-get for wine it will have installed, but not in a directory, in order to use it navigate in the command line to wherever the .exe file is for your windows program then type "wine <name of .exe>" (no quotes of course)

---

### Post by orb9220 on 2007-02-02
You can install wine from the synaptic package manger or Automatix installer.

---

