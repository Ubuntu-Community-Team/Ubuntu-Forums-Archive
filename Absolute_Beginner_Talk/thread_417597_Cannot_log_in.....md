---
title: "Cannot log in...."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by krazed nun on 2007-04-21
Hello. I am using my windows partition right now (grr.) because i cannot log into my ubuntu. I turn on my computer, and then it loads, and when its time for the log-in screen to pop up, all i see is the little animated circle symbolizing to wait. I let it do that for about half an hour and it still showed nothin. Any suggestions? I will greatly appreciate them.

---

### Post by taurus on 2007-04-21
Did you upgrade or install something before that happens?  And I assume you are using Dapper, from your profile.

---

### Post by krazed nun on 2007-04-21
sorry, i need to change that. I have feisty. i had changed some settings in the login window prefrences, like installed a new one, and changed the color, and it worked fine when i rebooted. then, i restarted again and it said something about that the harddrive had been mounted 30 times without checked. i had also enabled desktop effects, but that also worked fine when i had rebooted. maybe changing the login window would help?

---

### Post by jtraub on 2007-04-21
Press <Ctrl>+<Alt>+<F1>. Now you can log in.
Execute
```
dmesg | less
```
for boot messages
Also you can check /var/log/messages

---

### Post by krazed nun on 2007-04-21
really weird words and numbers. how would i read this an d figure out wut to do?

---

### Post by jtraub on 2007-04-21
Probably you will upload your dmesg output.

Switch to console (by Ctrl+Alt+F1).
```
sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.bak
```
```
sudo cp /etc/gdm/factory-gdm.conf /etc/gdm/gdm.conf
```
```
sudo init 6
```

Your computer will reboot. Probably this will help.

---

### Post by krazed nun on 2007-04-21
same results.....

---

### Post by jtraub on 2007-04-21
Dou you have write access to your windows partition?
I need to check your system log to find out, whats wrong with your Ubuntu.

use cp to copy following files:

/var/log/messages
/var/log/syslog
/var/log/Xorg.0.log
/var/log/daemon.log
files from /var/log/gdm/

and don't forget to make
dmesg > /media/..../dmesg.log

After that pack all this log files and attach them here.

---

