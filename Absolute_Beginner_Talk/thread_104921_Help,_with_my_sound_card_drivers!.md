---
title: "Help, with my sound card drivers!"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by madsalty on 2005-12-17
I downloaded my compatible linux sound card drivers from driverguide.com
When i extracted the files and read the readme it tells me to 
> To compile the driver, simply type "make" in the emu10k1/ directory.
This will generate the file "emu10k1.o"
but how do i do this, can somebody please help.

---

### Post by endersshadow on 2005-12-17
In your terminal (Applications>Accessories>Terminal), do this (assuming that emu10k1 is in your Home folder):

```
cd ~/emu10k1
make
```

And you'll be all set.  If emu10k1 is on your Desktop, change "cd ~/emu10k1" to "cd ~/Desktop/emu10k1".

---

### Post by madsalty on 2005-12-17
thank you, i love you! It means that most of my linux problems are over

---

