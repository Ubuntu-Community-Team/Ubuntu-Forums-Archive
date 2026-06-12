---
title: "boot problems"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by tommyp on 2008-01-22
Whoops!  I was trying to update the v4l-dvb driver in order to get a Pinnacle HDTV card to work using the file downloaded here:

[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

I then moved to the uncompressed directory, ran make and then make install.   This seemed to work fine.  I then rebooted and ran into some boot errors.

In safe mode, I get an error:

```
sbin/modprobe/ abnormal exit

/lib/firmware/dvb-fe-xc5000-1.1.fw for device  /class/firmware/i2c-3 cx8800

```

Then eth0 fails and after a couple of minutes the boot continues and the X window will not load.

Is there any way to correct this?  I'd prefer not to have to  reinstall a clean copy if possible.

---

### Post by tommyp on 2008-01-23
So a knowledgeable friend suggested that I probably screwed up the kernel modules and said that I might be able to reinstall the default gutsy kernel modules.  He mentioned something like dpkg.   

How would I do this?

---

### Post by dstew on 2008-01-23
Before you re-install, you could try to blacklist the module(s) you had installed. You blacklist modules by adding them to the file /etc/modprobe.d/blackist using a text editor. I am not sure what the offending module name is. I see on the error message that there is a problem with the device /class/firmware/i2c-3 cx8800, but I am not sure that this is really the problem. You can look at kernel log files in /var/log to see if maybe you can tell more. Or, if you know the name already, just try blacklisting it. I assume you can get a command line on your system.

---

### Post by tommyp on 2008-01-23
I'll try that, though I don't really know all of the modules that were installed.  I guess I will find them in /linux/drivers/media/ 

Is there any way to generate a list of all loaded modules on a system?

---

### Post by dstew on 2008-01-23
The command to list modules is **modprobe -l**
EDIT: Another thing to do when debugging is use the **dmesg** command. It lists the most recent system messages without needing to go into the /var/log directory and look at individual logs. Maybe there are errors in there that will give you some clues.

---

