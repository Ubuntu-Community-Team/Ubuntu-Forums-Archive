---
title: "i really need to know if a program is running, can you help?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-12-21
hi, i use a program called Privoxy for a proxy. i just restarted Ubuntu and didn't launch Privoxy but i'm still able to use my browser. i just managed to get Privoxy to popup so it must be running. but, it's not in the system manager and i don't know how to tell it's running for certain. for firestarter i use this command:
sudo /etc/firestarter/firestarter.sh status

there is no Privoxy.sh on my system so how do i know what Privoxy's executable is to run a similar command? thanks.

---

### Post by mo_x on 2005-12-21
You can list all running programs with the ps command. Try the following command from a terminal window:
```
ps -ef
```

---

### Post by aysiu on 2005-12-21
```
top
``` or ```
gnome-system-monitor
```

---

### Post by 23meg on 2005-12-21
You can start it with ```
/etc/init.d/privoxy start
```
and stop with ```
/etc/init.d/privoxy stop
```
To detect whether privoxy is running, type ```
ps -e |grep privoxy
```
If you get some output, it's running. You can substitute privoxy with any other app/daemon name to check whether it's running.

---

### Post by Danielle on 2005-12-21
great, i found it with ps -ef. it doesn't show in System Monitor, do you know if there's an option to show the results from ps -ef in system monitor? it's not important.

---

### Post by 23meg on 2005-12-21
You run it as root; that's why you can't see it in "My processes". Hit "View" and choose "All processes".

---

### Post by Danielle on 2005-12-21
thanks, 23meg. i'll write that down with the other commands in Tomboy.

---

### Post by Danielle on 2005-12-21
[QUOTE=23meg]You run it as root; that's why you can't see it in "My processes". Hit "View" and choose "All processes".[/QUOTE]
Brilliant! i found it in System Monitor now as well :D thanks for the help. O:)

---

