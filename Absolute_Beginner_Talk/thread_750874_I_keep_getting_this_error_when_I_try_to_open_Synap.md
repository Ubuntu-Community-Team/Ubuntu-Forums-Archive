---
title: "I keep getting this error when I try to open Synaptic [PIC]"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by KrisScofield on 2008-04-09
I'm running the Heron Beta 8.04
Whenever I go to Synaptic, I get this:

[IMG]http://i27.tinypic.com/ojpked.png[/IMG]

I'm fairly new (just a few months in) to Linux, so if this is an incredibly easy problem, or just a Heron bug that belongs elsewhere, I apologize! :lolflag:

---

### Post by Oldsoldier2003 on 2008-04-09
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade 
```

Then carry on :) all should be well

---

### Post by KrisScofield on 2008-04-10
It worked! Thanks! But now it says I have one "broken package" on my system?

---

### Post by Oldsoldier2003 on 2008-04-10
> **KrisScofield said:**
> It worked! Thanks! But now it says I have one "broken package" on my system?

try running sudo apt-get install -f again. If it doesn't fix the package please post the complete error message

---

### Post by KrisScofield on 2008-04-10
:) Fixed! Ubuntu Forums deliver once again.

---

