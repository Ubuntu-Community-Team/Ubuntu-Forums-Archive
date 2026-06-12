---
title: "How do you force close frozen aps (in wine, or otherwise)"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by WirlWind on 2007-06-24
I just had WoW freeze up on me and I am the newest newb at all things linux-based (First time user yesterday =p )

Is there some key shortcut or command in terminal to close "Non responsive" programs?

I think the reason WoW died is a warlock just ganked me, and wine doesn't know how to handle that =P

(And yes I searched before posting)

---

### Post by jfinkels on 2007-06-24
> **WirlWind said:**
> I just had WoW freeze up on me and I am the newest newb at all things linux-based (First time user yesterday =p )

Is there some key shortcut or command in terminal to close "Non responsive" programs?

I think the reason WoW died is a warlock just ganked me, and wine doesn't know how to handle that =P

(And yes I searched before posting)

Press Alt+F2 to bring up the "Run Application" dialog OR open a terminal. Type:```
xkill
``` and press enter. You will get a skull and crossbones as your mouse pointer. Click the offending window and it will die.

You can also open a terminal and type:```
killall *nameofprogram*
```

There are a couple other ways. Let me know if you need more help.

---

### Post by Golyadkin on 2007-06-24
I usually run  "ps aux" to find the pid of the program, and then "kill -9 <pid>"

---

### Post by BobCFC on 2007-06-24
You can bind the System Monitor to Ctrl-Alt-Del shortcut like in windows

credit goes to [aysiu from an old thread]("http://ubuntuforums.org/showthread.php?t=200873")

Alt-F2

```
gconf-editor
```

Apps > Metacity

Global Keybindings > Command_1

```
<Control><Alt>Delete

```
Keybinding Commands > Command_1
```

gnome-system-monitor

```


This works great for normal gnome but if you are using Beryl .. go to Beryl Setting Manager->General Options->Commands and put gnome-system-monitor in there and Shortcuts put <Control><Alt>Delete.

---

### Post by WirlWind on 2007-06-24
Thanks for that guys. Big help to a big noob, though one day I will rule the world. Muahahaha!

(I might do the ctrl+alt+delete bind, its instinctive after so many years in windows and the frequency of issues in it...)

---

### Post by jfinkels on 2007-06-24
> **WirlWind said:**
> Thanks for that guys. Big help to a big noob, though one day I will rule the world. Muahahaha!

(I might do the ctrl+alt+delete bind, its instinctive after so many years in windows and the frequency of issues in it...)

You won't need to go through all the hassle of opening a GUI, selecting the process you want to kill, and selecting "kill" once you've tried the other, faster ways. Got to break those bad habits :D

---

### Post by BobCFC on 2007-06-24
Actually I use it to check the space on the partitions and occasionally CPU/Memory;)

Also its nice to be able to reorder processes by Memory or %CPU

---

### Post by jfinkels on 2007-06-24
> **BobCFC said:**
> Actually I use it to check the space on the partitions and occasionally CPU/Memory;)

Also its nice to be able to reorder processes by Memory or %CPU

You might also enjoy:

```
df
```
which shows disk usage on different partitions.

and ```
top
``` or some people prefer ```
htop
``` (you may have to install that one) to view CPU and memory usage.

and ```
free
``` will show you more precise information on free and used memory.

Read more about these programs at:```
man df
man top
man free
```respectively.

---

### Post by BobCFC on 2007-06-25
yeah if you do   

df - h


You get it in human readable form of Gigs and Megs not 488264736 bytes

---

