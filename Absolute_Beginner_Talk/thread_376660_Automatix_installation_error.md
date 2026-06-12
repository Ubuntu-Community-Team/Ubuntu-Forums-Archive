---
title: "Automatix installation error"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-03-05
Hi, I got a clean install of edgy working. just downloaded automatix which downloads fine. When I hit the 'install Package' button i get this error:

"Only one software management tool is allowed to run at the same time...
Please cloase other application e.g Update manager, aptitude or synaptic first"

I cant work out how to check what is open and how to close the thing that is stopping automatix from working.    Thanks all....

---

### Post by bobbob1016 on 2007-03-05
It sounds like either Synaptic (or Adept since your tag says KDE), or the Update Manager running.  Just check your taskbar and make sure none of these are running, if Automatix still says the error, try rebooting.

---

### Post by proxima estacion on 2007-03-06
Nothing else is running in the taskbar except automatix install app. I tried rebooting and using Gnome.  But get the same message everytime.

I suspect I am missing something very obvious but cant think want.

How can i find out what applications are open at any one timein XP i would do Ctrl+Alt+del and check what processes are running, is there  an equivalent in Ubuntu?  Thanks All....

---

### Post by Obor on 2007-03-06
to find what is running go to system-administration-system monitor

Have you tried [Automatix forums]("http://www.getautomatix.com/forum/index.php?showforum=29") for help?

---

### Post by taurus on 2007-03-06
Or open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
ps -A
```

---

