---
title: "Startup programs"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by palmtree on 2007-01-15
I am successfully able to get on-line with my Linksys wifi card on my thinkpad, HOWEVER  the only way I was able to get on-line is through the program WiFi-Radar. However I have to do this every time I start up my laptop. Is there a way to automate this so that I am able to get on-line automatically? I am using Ubuntu version 6.10

Thanks

---

### Post by NeoLithium on 2007-01-15
If all you have to do is start the program; you can add it with:
System -> Preferences -> Sessions and add it to the list of startup programs.

---

### Post by taurus on 2007-01-15
You can put that in System -> Preferences -> Sessions -> Startup Programs -> Add.

---

### Post by palmtree on 2007-01-15
Thanks for the solution. Being new to Linux, I am struggling trying to locate the whereabouts of actual wifi-radar program that I actually run from Applications, Internet .... but not sure where to browse to find the actual file location to enter into the add program field.

---

### Post by NeoLithium on 2007-01-15
you might try taking a look through /usr/bin  that's where quite a few of those programs are launched from; just browse through some of the file names, and you should be able to locate it

---

