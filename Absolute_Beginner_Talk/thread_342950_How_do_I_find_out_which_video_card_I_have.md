---
title: "How do I find out which video card I have?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by jabzwnein on 2007-01-20
I've mustered up the courage to try to install Beryl again, but I don't know which video card I have.  How can I find this out?  I've looked online and in the forums to no avail.

I'm running Dapper on a Dell with a Pentium 4, if that helps.

thanx!

---

### Post by Lord Illidan on 2007-01-20
EDITED : Please type ```
lspci | grep VGA
```

---

### Post by Sklasko on 2007-01-20
Dell? Look around on your PC case and try to find a model number. Use that number to find your specific computer on Dell's website and it should be in the specs there.

I've only been using Linux/Ubuntu for several months so I don't know how to check this from the terminal, but I'm sure you can. 

Hope this helps.

Edit: Beat me to it. :)

---

### Post by highneko on 2007-01-20
> **Lord Illidan said:**
> Try typing lscpi | grep 'VGA' in a terminal.

You typed it too fast! It's:
lspci | grep VGA

---

### Post by jabzwnein on 2007-01-20
Thanks!

This is what I get:

0000:00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)


so...?  um...just 'intel' then?  (i've just been reading about nvidia etc)

---

### Post by Lord Illidan on 2007-01-21
Yep, just intel. It still can be used to run Beryl..search for the forums on Beryl and intel..

and oops..sry for the misprint!

---

