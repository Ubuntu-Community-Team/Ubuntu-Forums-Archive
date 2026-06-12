---
title: "gksudo launch error - qtparted"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by abhi_am on 2006-04-02
Hello,

I just installed qtparted and was trying to run it when I ran into a strange error. I'm running Kubuntu (5.10) and I'm the only user on the system.

When I try and launch from the "System" submenu (from KDE's main menu), nothing happens. When I try and launch it from the "Run Command" window, I get the following error 
"KDEInit could not launch '/usr/bin/gksudo'." If I try and run it from the command line (xterm or konsole), it opens up.

Now, I read somewhere the commands that need gksudo should not be run from the command line. Could you tell me how to correct this error?

FYI: "groups ashu" outputs the following
ashu disk cdrom sudo audio users dhcp admin

I'd changed the default groups I belonged to by mistake one time. Also, if these are not the correct default groups a user should belong to, could you tell me how I could correct it.

Thanks!
Ashu

---

### Post by Sutekh on 2006-04-02
Try using kdesu instead of gksudo
```
kdesu <name of program>
```

---

