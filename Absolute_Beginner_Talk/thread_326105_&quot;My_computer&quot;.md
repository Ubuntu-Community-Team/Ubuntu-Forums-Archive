---
title: "&quot;My computer&quot;"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by gen on 2006-12-27
hi, im new in linux, and im learning english so try to understand me. xD

i installed ubuntu yesterday and im looking for the "My Computer" icon, or similar, to know the specifications of my computer, is there an icon like that?.. or a command for prompt?..
thanks

---

### Post by 23meg on 2006-12-27
Go to System / Administration / Device Manager to see what components of your computer are recognized.

---

### Post by gen on 2006-12-27
really quick..thanks..
almos everything is recognized, but where is the RAM memory?..i want to know how much do i have..

---

### Post by 23meg on 2006-12-27
```
cat /proc/meminfo
```will give you detailed info.

---

### Post by gen on 2006-12-27
thanks a lot :p

---

### Post by 56phil on 2006-12-27
Type free in a terminal.  Applications / Accessories / Terminal  Free will tell you how much memory the system has and how much is free.

---

### Post by Dies on 2006-12-27
If you right click the taskbar and select add to panel you can add System Monitor to the panel, which will display your cpu usage and you can click on it to bring up "task manager".

It's called gnome-system-monitor, in case you want the command, I think that's probably what you're after.

---

### Post by gen on 2006-12-27
thanks for the info..
i have another noob question.. everytime i close the lid of my laptop, the screen goes black and i have to reboot :S..but its not seep or anythig, you can hear it working, but you cant see anything.. any ideas?

---

### Post by houstonbofh on 2006-12-27
> **gen said:**
> thanks for the info..
i have another noob question.. everytime i close the lid of my laptop, the screen goes black and i have to reboot :S..but its not seep or anythig, you can hear it working, but you cant see anything.. any ideas?
It is your power management.  First, check the computer BIOS.  Make sure it doesn't have "Close Lid" action set to "Suspend."  Then check the Ubuntu power management.

---

### Post by J.Vega on 2006-12-27
You don't have to reboot completely if your laptop is in suspend mode.
Depending on the laptop you just have to press a button or the power button once (and don't hold it down). Then your laptop should return from suspend mode and you should be able to continue where you left.

---

