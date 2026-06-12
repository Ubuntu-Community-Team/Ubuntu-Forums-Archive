---
title: "Fluxbox can't get to command prompt"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by RoadWarriorEWR on 2006-07-04
I recently installed the absolute bare minimum system with fluxbox, xdm and synaptic after using the base kubuntu server install. I didn't think to install a terminal like xterm, as I figured that it was installed by default. However, that doesn't seem to be the case. 

I'm in Fluxbox, no problem, but I can't get to a command prompt to add any more applications (firefox, terminal, etc.). Even when I exit the system, it just takes me back to the login screen, so I can't even get to something there.

How can I go to a command prompt to install these programs? 

Your quick help is greatly appreciated, as the system's pretty much non-functional now. Thanks in advance.

---

### Post by taurus on 2006-07-04
<Ctrl><Alt>F2

---

### Post by confused57 on 2006-07-04
Since you have Synaptic installed, you may be able to install some programs from Synaptic Package Manager.
You might want to do what taurus suggested first, then enable the extra repositories:

```
sudo nano /etc/apt/sources.list
```

then remove the # in front of anything that looks like a url.
I'm assuming you have a fast internet connection.

---

### Post by RoadWarriorEWR on 2006-07-04
Thank you both. That took care of it for me. I'm working again.

---

### Post by RoadWarriorEWR on 2006-07-05
One last question, if I may. After getting to the command prompt and doing what I need to do there, how do I get back into Fluxbox without needing to restart?

---

### Post by taurus on 2006-07-05
<Ctrl><Alt>F7

---

