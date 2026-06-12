---
title: "What are static and dynamic dev?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-08
I was reading over some instructions for lm-sensors installation and set up and one of the steps references two methods based on which one you are using, static or dynamic. I don't even know what they are. Common sense should tell me that this is over my head but I learn faster by breaking stuff and then having to fix it:) . Can someone take me to school?

---

### Post by Bachstelze on 2007-03-08
Could you paste a link where you saw this ? I usually just install the lm-sensors package from the repo - or occasionnally build it from source - and I'm up and running.

---

### Post by 67GTA on 2007-03-08
I installed lm-sensors via synaptic but seems to require some configuration to work. I was looking at this stie... [http://doc.gwos.org/index.php/Lm-sensors_hddtemp](http://doc.gwos.org/index.php/Lm-sensors_hddtemp)

---

### Post by 67GTA on 2007-03-08
This is the error I get when I run sensors 

shawnr@fastback:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

---

### Post by Bachstelze on 2007-03-08
Just in case you don't have them installed :

```
sudo apt-get install libsysfs2 libsensors3
```

---

### Post by 67GTA on 2007-03-08
It says they are both installed and are the newest versions. I was afraid I had some missing dependencies, so I installed lm-sensors with apt-get and it said that nothing new was installed or upgraded. I tried the hardware sensors monitor (panel applet) and it said no sensors found. I think I just need to configure lm-sensors to work with my Intel board. Any links to instructions for this?

---

### Post by Bachstelze on 2007-03-08
You ave the sensors-detect tool that will let you know the kernel module(s) you need to load in order for lm-sensors to work but the output of sensors when you don't have them loaded is just "no sensors found". I think the problem lies somewhere else but I can't help you much; as I usually build it from source.

---

### Post by 67GTA on 2007-03-08
I ran sensors-detect and it listed the modules, but I don't know where to go from there. What does it mean by load modules? I answered yes to adding the modules to etc/modules. What else is there to do?

---

### Post by Bachstelze on 2007-03-08
The modules listed in /etc/modules are loaded when you boot. So you can either reboot or load them manually with *modprobe*.

---

### Post by 67GTA on 2007-03-08
I think it may be my board. I found this this while searching the forums.

[http://www.ubuntuforums.org/showthread.php?t=340060&highlight=lm-sensors](http://www.ubuntuforums.org/showthread.php?t=340060&highlight=lm-sensors)

I will do some more research and see what I come up with. Thanks for the help.

---

