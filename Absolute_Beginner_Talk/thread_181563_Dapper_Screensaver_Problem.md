---
title: "Dapper Screensaver Problem"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-24
when i just leave my linuxbox for a little bit of time, the screensaver show up and stuff, but when i move my mouse so i can get back to work it freezes up and i gotta reboot, also this happens when i lock the screen too
it never happened in Breezy
is it only a problem with Dapper Beta?

---

### Post by Jason_25 on 2006-05-24
Post your hardware specs and your video driver.  Also post the output of 
```

glxinfo

```

---

### Post by youthforlinux on 2006-05-24
ATI 9200 SE
i used the ubuntu driver but the problem still happened with the fglrx driver

---

### Post by Jason_25 on 2006-05-24
Ok post your full hardware specs.  Like your CPU and memory.  

Before the lockup, are the temperatures for your graphics card, motherboard, memory and cpu all ok?

edit: You also may want to see you if you can switch to a virtual terminal when the lockup happens or if you can SSH into the PC.

---

### Post by confused57 on 2006-05-24
I just started having the same problem with Dapper on an old computer with onboard graphics(Trident or Via, I think).
I've tried moving the mouse & it takes several minutes for the GUI to resume.
Might be a bug in Dapper...I'll check the default driver Ubuntu is using when I restart the computer...

---

### Post by youthforlinux on 2006-05-24
P4 512 RAM 
yea everything was fine before the lockup and after reboot everything worked fine and still does except for the screensaver lockup problem

---

