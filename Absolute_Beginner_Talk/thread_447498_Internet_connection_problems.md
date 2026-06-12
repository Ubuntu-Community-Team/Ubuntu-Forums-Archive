---
title: "Internet connection problems"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by pierre15208 on 2007-05-18
I am a very new Linux user.  This is the first time that I made a serious effort to learn Linux and I chose Ubuntu because it's supposed to be the most forgiving to newbies. 

 I have dappled in Suse Personal Linux before it was phased out, and while I was using that distro, I was able to set up my DSL connection via pppoe very easily.  But when I switched over to Ubuntu, i was surprised that i had to open a console and **sudo  pppoeconf** in order to set up my connection. No biggie, I can do that, but the problem is that every time I shut my machine down and then start up again, it seems like I have to do that **sudo pppoeconf** procedure all over again in order to start my connection, I make sure that i select the option to have the connection start at boot time, but when i start my session, i get the icon in the upper right that shows that my connection is on, but I launch firefox, and I can't get access.   I am currently running the current Ubuntu Fiesty distro.  My ISP is Verizon,  Any help is greatly appreciated.

Pierre

---

### Post by dunedust on 2007-05-18
Well the connection might take some time to load 
Give it half a minute
If it doesn't start up just try

```
sudo pon dsl-provider
```

---

