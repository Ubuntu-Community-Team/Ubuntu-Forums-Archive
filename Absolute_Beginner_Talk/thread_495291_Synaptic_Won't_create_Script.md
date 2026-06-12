---
title: "Synaptic Won't create Script"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-07-07
I want to make an executable shell script for another computer of all the packages I have installed on my own machine. Basically- I'm making an exact copy of my computer. And this should be easy- Synaptics even makes the script for you to download all your packages-- the only problem is, it isn't making the script. I've tried doing it twice now and when I open the 10 BYTE (yes, byte) file, it says this:     

#!/bin/sh

Thats it. Nothing else. Naturally, when run, it does nothing. I tried to "save a list" of all the markings in Synaptic as well and when I checked on the created file? Blank. What is going on, how do I fix this?

Is there another program that does this instead of synaptic?

Thank you!

---

### Post by p_quarles on 2007-07-07
You could try Apt-on-CD ```
 sudo apt-get install aptoncd
```

It will appear in System >> Admin, and will allow you to make a CD/DVD with your packages on it. When loaded, it can act as a restore disk.

---

### Post by Protagonistics on 2007-07-07
Thank You!

---

### Post by p_quarles on 2007-07-07
Sure. I can't guarantee it'll work flawlessly, though. I've had mixed success with it. Good luck.

---

