---
title: "programs and finding firefox dir"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by monkeysaidwhat on 2007-09-21
Hello, 
  I'm totally newbie to this whole Linux side of things.  I'm having two main problems. 
 
1) I can't find the firefox dir some programs are asking this question "where is your firefox program" Where would it normally be? 

2) I'm currently in the mode of trying to install a simple file and make it work. For example I went to download an IRC client when I do the program will tell me I need to download perl and then this other thing called RPM. Then when I download those things they tell me i need download something else to make that work.  So my question; Is there way where I can just download a so called package of files that way won't come across this problem. 

thanks for your help, 
 Sean

---

### Post by siralphred on 2007-09-21
If you would be more specific about the program you are installing that would help, and also ubuntu is debian based and uses .deb instead of .rpm  although u can convert rpm to deb with alien since you are new i would suggest you find the .deb of the rpm instead and it will be installed automatically with the deb installer

---

### Post by reckless2k2 on 2007-09-21
there is a "search" capability or "find files" in one of the menus up top but an easy way i do it is via the terminal:

```
sudo find / -name "firefox"
```

find is searching the "/" directory which is everywhere and it is looking for the name (-name) firefox ("firefox"). you can adjust this for other things you see fit.

example
```
sudo find / -name "totem"
```

as far as install IRC, i believe it's in there by default. Other than that you can use synaptic in the adminstration menu or add/remove programs in the main menu. Search for IRC.

---

### Post by Pumalite on 2007-09-21
pumalite@pumalite-desktop:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/X11R6/bin/firefox /usr/bin/X11/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz
pumalite@pumalite-desktop:~$ 

You cannot use RPM in Ubuntu.

---

### Post by LaRoza on 2007-09-21
> **monkeysaidwhat said:**
> 
1) I can't find the firefox dir some programs are asking this question "where is your firefox program" Where would it normally be? 


Any directory named bin or sbin contains programs, GUI programs are in sbin
```

whereis firefox

```

Installing things through Synaptic is the easiest method. RPM's require work, no way around that.

---

### Post by reckless2k2 on 2007-09-21
hahahaha...i don't know what i was thinking when i wrote find. i promise i was thinking whereis but i just wrote somewhere else about the which command and confused myself. hahaha

---

