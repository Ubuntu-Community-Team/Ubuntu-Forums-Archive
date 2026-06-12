---
title: "Ubuntu 6.10 Laptop Issues"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by damichi on 2007-02-25
I just switched to Ubuntu from Windows and I really love the look and feel and stability

Unfortunatly I cant get the Hibernate feature to work. My screen turns black but the laptop doesn't go off, the hdd led is blinking time by time and the fan is still on. I tried to turn it of manually. After reboot all my apps are running again so I guess Hibernate is working besides it doesnt turn the Power off

my second problem is I installed an gnome applet to watch the frequenzy of my Prozessor and no matter what I do its always 1,6 Ghz what drains the battery pretty fast. Can I somehow enable a "Power Saving feature?"

Thx for your HELP

My hardware:
Sony VGN-S4
driver: centrino
 hardware limits: 800 MHz - 1.60 GHz
 available frequency steps: 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
 available cpufreq governors: conservative, ondemand, powersave, userspace, performance

---

### Post by chaplanger on 2007-02-25
> **damichi said:**
> I just switched to Ubuntu from Windows and I really love the look and feel and stability

Unfortunatly I cant get the Hibernate feature to work. My screen turns black but the laptop doesn't go off, the hdd led is blinking time by time and the fan is still on. I tried to turn it of manually. After reboot all my apps are running again so I guess Hibernate is working besides it doesnt turn the Power off



Not that I have a personally tested solution for you (I am running Ubuntu on a desktop) but it sounds as if when you go to hibernate the machine is actually in suspend mode (This is the default sleep mode).  What I have read suggests that you can change from suspend mode to hibernate: right click on the gnome-power-manager icon, select Preferences and click on the Options tab and change computer sleep type and actions you want performed.  

However these instructions from "Ubuntu Hacks" warns that if your system is configured to boot multiple OSs you need to make certain you boot back into the OS that is hibernating or bad juju will occur.

Hope this helps

---

### Post by gabbman on 2007-02-25
Have a look [http://www.gnome.org/projects/gnome-power-manager/faq.html](http://www.gnome.org/projects/gnome-power-manager/faq.html)
here.

---

### Post by damichi on 2007-02-25
thx for the posts so far unfortunatly I was not able to fix the issue 
I think its a problem with acpi but I am not sure if I can do anything about it

---

