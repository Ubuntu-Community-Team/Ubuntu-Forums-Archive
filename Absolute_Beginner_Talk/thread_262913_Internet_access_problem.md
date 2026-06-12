---
title: "Internet access problem"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by woodpidgeon on 2006-09-22
After installing Dapper I tried to connect tp the internet using an external ethernet modem but wouldnt connect.  This was rectified by typing #sudo invoke-rc.d networking restart# into the terminal and all was fine for a couple of weeks.  When I booted up the commy connection was automatic.  Now I have to use the terminal to connect every time.  Is there anywhere I can put the manually entered  line of code so the commy will once again connect automatically?

---

### Post by whizbaby on 2006-09-22
Yes, there is:
[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

or (if you didn't do it) perhaps activating the modem in *network connections* is a good thing.

---

### Post by woodpidgeon on 2006-09-22
The modem is active and worked beautifully at first, then didn't.  However i will try you other suggestion

---

### Post by whizbaby on 2006-09-22
You can also try the terminal-based
*sudo pppoeconf*
which will ask you if you want the connection started at boot.

---

### Post by woodpidgeon on 2006-09-22
Thanks Whizbaby, I tried that but it said another instance of pppoe was already running.  Could you tell me how to troubleshoot this?

---

### Post by whizbaby on 2006-09-22
For finding the process id(s):
**ps aux|grep pppoe**
remember the pid(s) (first number in the line) and
**kill -9 *pid_you_remembered***
untill they're all dead. Then try again 
**sudo pppoeconf**

---

### Post by jimminy_kriket on 2006-09-22
I'm having a problem with sudo pppoeconf, when I imput it for the very first time, all is good but it doesnt reconnect on startup. I have to re-run sudo pppoeconf, then deactivate and reactivate my ethernet adapter in the network connections panel.Anyone have any idea how to fix this?

---

