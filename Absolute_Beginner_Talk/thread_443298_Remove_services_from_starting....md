---
title: "Remove services from starting..."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2007-05-14
Hi, I have dapper installed as a server, no GUI.  I need to know how to keep tinyproxy from running at boot time thru Bash.  I have it set up in crontab to start at 8.30am to shutdown at 5.30pm.  But I dont want it to run at boot.  Let me know, thanks.

---

### Post by bernied on 2007-05-14
The startup script will be in /etc/init.d/ but don't change this file.

It will be started at boot through links in the /etc/rcX.d/ directories, where X is 0-6. 0-6 are the runlevels. You are probably booting into runlevel 2, so you probably want to look in /etc/rc2.d/. 
Your default runlevel is defined in /etc/inittab. 

The /etc/rcX.d/ scripts are run in alphabetical order, those starting with a K are stopped (K is for kill), and then those starting with S are started. The numbers in the link names are to define their stop/start order. 

So an easy way to make a script not start at boot is to change its name from S##tinyproxy to K##tinyproxy in the appropriate rcX.d directory. Use the mv command:
```
mv /path/to/oldname /path/to/newname
```

---

### Post by bernied on 2007-05-14
[This](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html) might make more sense.

---

### Post by echo $USER on 2007-05-14
Spot on, thanks!

---

