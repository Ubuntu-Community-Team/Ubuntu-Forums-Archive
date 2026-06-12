---
title: "Command to go to sleep mode?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-07-01
What is the command to put my computer into sleep mode?

Should I move my mouse or hit a key, it would wake up again.

What is the command to put just my monitor to sleep mode?

The computer is still on and performing tasks such as installing stuff in aptitude and playing music, but the monitor is asleep.  Should I move my mouse or hit a key, the monitor would wake up again.

Is it possible to add a timer to the above?  Wait such waiting 5 seconds before the action takes place.

---

### Post by angryfirelord on 2007-07-30
Suspend is in the same array of buttons that shut down and reboot are in.

You can adjust your screensaver by going to System-->Preferences-->Screensaver.

---

### Post by deadgobby on 2007-07-30
Most monitors will go into sleep mode with out doing any thing. It is clock in with the monitor it self. So like after 20 or so minutes the monitor will go to sleep. It called green monitor to save energy. Some monitors have time settings with in the monitors menu and some do not. So by pressing any key or moving the mouse will wake up the monitor from sleep mode.  My monitor will fall a sleep after a 30 minutes of idle. You may want to try looking into your monitor internal settings to set the sleep mode. 
Gobby

---

### Post by Nikron on 2007-07-30
Some of the lowest level commands for sleep/hibernate are.
```

vbetool dpms off #Only if you have vbetool installed, not sure if it comes by default
echo "mem" > /sys/power/state #You need to be root to do this, (sudo doesn't work, as far as I know)
echo "disk" > /sys/power/state #mem suspends to ram, disk suspends to disk

```

hitting the power button will fix mem and disk.  For vbetool, better let a program like gnome-sceensaver handle that

---

