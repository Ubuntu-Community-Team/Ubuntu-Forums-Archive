---
title: "Which is the default CPU governor on Ubuntu?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Unnicknamed on 2008-04-13
?

---

### Post by diablo75 on 2008-04-13
Could you explain what you're talking about?  What do you mean by "CPU governor".  Are you talking about some kind of dynamic frequency scaling?

---

### Post by insane_alien on 2008-04-13
maybe he means sheduler?

if he does it uses the CFS as of hardy heron.

---

### Post by Unnicknamed on 2008-04-13
Yes. There are six governors listed: conservative, ondemand, powersave, userspace and performance. I want to know which is the default that uses Ubuntu for a desktop machine?

---

### Post by plasmatonic on 2008-04-17
Every unit I've ever installed Ubuntu on used ondemand by default.

---

### Post by 3rdalbum on 2008-04-17
Ondemand.

---

### Post by SirThom on 2008-06-13
Is it possible to change that?  My machine gets really hot unless it is on powersave, and I have to keep manually setting it when i boot up, unplug it or plug it in.

---

### Post by ene_dene on 2008-06-13
> **SirThom said:**
> Is it possible to change that?  My machine gets really hot unless it is on powersave, and I have to keep manually setting it when i boot up, unplug it or plug it in.
I'm not sure what you think, you want to start on powersave governor on boot?
Generally you can put the comp on powersave by:
```
sudo cpufreq-selector -g powersave
```
Or on boot time you can write a script:
```
#!/bin/bash
sleep 60
/usr/bin/cpufreq-selector -g powersave
```
I'm not an expert in scripting (quite the opposite actually) but it works for me.
You write this to file "cpuscript", go to preferences, change to executable file, move the file to /etc/init.d. After that set that script runs during boot time:
```
sudo /etc/init.d/update-rc.d cpuscript defaults
```

---

### Post by Golem XIV on 2008-06-13
I was able to change the default policy by running gconf-editor and replacing the policy in apps/gnome-power-manager/cpufreq/policy_ac
Since you're on a desktop you won't need policy_battery.

However, if your system is running too hot this may be a patch over a more serious problem.  I suggest you check if your cooling system is working properly.

---

