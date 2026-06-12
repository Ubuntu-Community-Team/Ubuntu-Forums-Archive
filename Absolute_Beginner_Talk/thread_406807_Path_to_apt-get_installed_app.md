---
title: "Path to apt-get installed app?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-04-11
I just installed Eclipse via apt-get on Feisty..  Now I need to install some plugins.. but I cant find where the files are located :confused: ?

Can anyone give me the path to where apt-get stores the application files?

---

### Post by urukrama on 2007-04-11
I've never used eclipse, though, so I wouldn't know where the plugins go. But if you want to know where a program is installed, open a terminal and type

```
whereis *name of application*
```

and you will get the directories into which the program is installed.

---

### Post by heimo on 2007-04-11
You could probably put those in /usr/local/lib/eclipse/plugins. You can find some plugins in /usr/lib/eclipse/plugins, but it's better to leave that directory for those installed using package management.

---

### Post by aktiwers on 2007-04-11
Thanks! I didnt know that command :)
Excellent command.. very useful. 

If others are looking.. the plugin folder is here:
```
/usr/local/lib/eclipse
```

Thanks to you too Heimo.. just saw your post now. :)

---

