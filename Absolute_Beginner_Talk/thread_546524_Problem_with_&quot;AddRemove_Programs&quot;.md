---
title: "Problem with &quot;Add/Remove Programs&quot;"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Nin10dude on 2007-09-08
I'm a huge Linux newbie, I've only had it for about a week. I've installed one or two things through Add/Remove programs, but now when I either check or uncheck any box to install/remove anything, it just loads (as in, the mouse changes to the circle loading thing), and I can never install anything. I don't really know what I could have done to cause this, but is there anything I can do to fix it?

---

### Post by graham-cracker on 2007-09-09
This is in no way a solution, but if you're using Gnome, you could use Synaptic to install & remove programs instead 
Goto:
System->Administration->Synaptic Package Manager

Does that still allow you to install/remove programs?

---

### Post by Nin10dude on 2007-09-09
Ah, I got it working. For future reference, it turns out something was wrong with my install of virtualbox. So, I just typed in

```
sudo  dpkg --remove --force-remove-reinstreq virtualbox
```

which removed the install, and now everything's working fine. So, if anyone's having any issues like this, try removing a program you recently installed with that.

---

