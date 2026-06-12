---
title: "[SOLVED] applications running"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2007-12-21
is there anyway to find out what applications are running and to terminate applications that are running something similiar to taskman in windows

---

### Post by taurus on 2007-12-21
Applications -> Accessories -> Terminal
```
ps -A
sudo killall **app_name**
```

---

### Post by eternicode on 2007-12-21
> **allsys3 said:**
> something similiar to taskman in windows 

If you're using KDE, there's ksysguard (KMenu -> System -> KSysGuard).  User privileges will give you enough to search and kill processes.  Though, to get the nice graphs of CPU usage and such, you have to run it with root privileges ("sudo ksysguard").

I think the Gnome equivalent is GKrellm

Universally, pull up a terminal and use ```
ps -ef | grep <appname>
``` to get the IDs of specific apps, then ```
killall <appname>
``` or ```
kil <appPID>
``` to kill it (PID is the second column).

---

### Post by heatpumpcontrol on 2007-12-21
> **allsys3 said:**
> is there anyway to find out what applications are running and to terminate applications that are running something similiar to taskman in windows

Even easier :

 Right click on top Panel (task bar) --> Add To Panel

Scroll down to System Monitor --> select and drag it onto any open spot on the Panel

Now single click that little new black icon (which demonstrates your CPU activity) and play around now in Processes and kill whatever App you want

---

### Post by nowshining on 2007-12-21
iif using gnome


system - administration - system monitor

i got mine set-up on my taskbar showing cpu, hd in/out internet in/out and more and if i need to look at it, i just click a graph and it brings up the whole sytem monitor program.

---

### Post by RomeReactor on 2007-12-21
Hi. In Gnome you can use the System Monitor (System->Administration->System Monitor) to kill misbehaving applications; once there, you can right click on the application and select "Kill Process".

EDIT: Too slow...

---

### Post by nowshining on 2007-12-21
here for example is a screenie of my taskbar

the things go from left to right

trash
time
audio
cpu (monitor cpu usage) - system monitor 
memory (monitor memory usage) - system monitor
Network/Internet (monitor internet/network usage) - system monitor
Swap (monitor swap space) - system monitor
System load average (monitor the systems load average) - system monitor
Disk usage (monitor disk usage) - system monitor
Window Selector (i use this instead of the tabbed windows on the taskbar as it keeps things more tidier.
main menu (yes u can change the icon)
Force an applicaiton to quit

Then the rest to the right is the notification area :)

u can change em' around and stuff, add/delete, etc.. :)

once u get the system monitor where u want it, right-click and select preferences to add the others and  change colors, size, update time, etc..

---

### Post by allsys3 on 2007-12-21
thanks everyone ,,thats what i was after:)

---

### Post by nowshining on 2007-12-22
ur welcome and i'm glad u found what u were looking for. :)

---

