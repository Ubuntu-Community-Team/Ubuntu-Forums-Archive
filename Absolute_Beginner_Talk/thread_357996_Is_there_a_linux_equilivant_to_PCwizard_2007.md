---
title: "Is there a linux equilivant to PCwizard 2007"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by ADT on 2007-02-10
PC wizard 2007 is a freeware tool for windows that tells you about your hardware in detail. RAM, CPU, Graphics etc. Is there any linux software that does the same thing? If there is which is the best one?

---

### Post by JockeTF on 2007-02-10
You could just click on System --> Administration --> Device manager.


If you want to something else, try lshw, you should already have that installed.

Open up a terminal and type:

```
sudo lshw -html > ~/Desktop/my_hardware.html
```

Or if you don't have root privileges:

```
lshw -html > ~/Desktop/my_hardware.html
```

That will put a .html file named my_hardware.html on your desktop, just open it in your webbrowser. Or were you thinking about something else?

---

### Post by Marsolin on 2007-02-10
You could also try [HardInfo]("http://linuxappfinder.com/package/hardinfo").

---

### Post by ADT on 2007-02-10
Thanks very much for the information.
I tried out both programs. lshw and hardinfo and they both work great.

cheers

---

