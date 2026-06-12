---
title: "&quot;Task Manager&quot; -like program In Kubuntu?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by junglemike on 2006-04-09
If it is already preinstalled How do i open it? 
I only found Performance Monitor (Ksys Guard) But i didn't find there option to kill process , or chnage priority (or maybe i didn't look hard enough?)
TIA,

---

### Post by patrick295767 on 2006-04-09
I use the kicker bar 
```
apt-get -f -y install kicker
```
  
there is a lot: 
eg:
[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

greetz

---

### Post by pizzach on 2006-04-09
[QUOTE=junglemike]If it is already preinstalled How do i open it? 
I only found Performance Monitor (Ksys Guard) But i didn't find there option to kill process , or chnage priority (or maybe i didn't look hard enough?)
TIA,[/QUOTE]

psdoom is about as graphical as you can get for a kill process program. ;)
[http://psdoom.sourceforge.net/](http://psdoom.sourceforge.net/)

Or if you are feeling geeky in the terminal you can type:
```

ps -a

```
for all active threads.  Then use
```

kill thethreadnumberfromps

```
to kill the thread.

If you want to kill a whole application, just type:
```

killall theapplicationname

```

---

