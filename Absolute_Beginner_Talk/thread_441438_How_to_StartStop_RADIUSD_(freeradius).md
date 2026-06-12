---
title: "How to Start/Stop RADIUSD (freeradius)"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by karla on 2007-05-12
Hello,

I have been spending lots of time on this and I am stuck.
I have installed the Freeradius from a Ubuntu package. It seem to run OK according to a log file. Its starts up at boot up. Its 'Ready to process requests.' 

1. However, I cant figure out want file is starting the radiusd -application up at start-up. I would like to have control of what parameters to start it with. Is there some kind of Autoexec.bat -file in Linux?

2. How to stop / shut the Radiusd - application down when running. It seems odd to have to reboot the computer do start/stop it.

Really happy for any tips!

All the best
karla

---

### Post by steve.horsley on 2007-05-12
I am guessing here - I haven't installed it to check - but... I guess it is probably started and stopped by running the script /etc/init.d/raduisd. If this file exists, it will get called like this:
**/etc/init.d/radiusd start**
by the init process during boot. And you will be able to start it and stop it manually with
**sudo /etc/init.d/radiusd start** (or stop, of couse)

The command **man radiusd** might help, and have a look in /etc for a radius file or directory holding configuration info.

---

### Post by karla on 2007-05-13
> **steve.horsley said:**
> I am guessing here - I haven't installed it to check - but... I guess it is probably started and stopped by running the script /etc/init.d/raduisd. If this file exists, it will get called like this:
**/etc/init.d/radiusd start**
by the init process during boot. And you will be able to start it and stop it manually with
**sudo /etc/init.d/radiusd start** (or stop, of couse)

The command **man radiusd** might help, and have a look in /etc for a radius file or directory holding configuration info.
Thanks Steve! The man radiusd command was a hit.
Regarding the 'init process' during boot - Is there a particular starting file like Autoexec.bat?
/Karla

---

### Post by steve.horsley on 2007-05-13
It's all a bit complex. Try googling for "linux init". But every file starting with "S" in the directory /etc/rc2.d is called with the argument start, in numerical order (rc2.d is short for **r**un **c**ommand for runlevel**2** **d**aemons).. The K files are called during shutdown to kill the services again. These files are normally just symbolic links to the real scrpts in /etc/init.d.

---

### Post by karla on 2007-05-15
Thanks again Steve.

---

