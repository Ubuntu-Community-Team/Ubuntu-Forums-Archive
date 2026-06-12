---
title: "Trying to create custom Run Level, how to?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by mac.daddy on 2007-06-07
Hello community :)
I have been using ubuntu for the past 4 wonderful days now and have started to get a hang of it after being a Windows user for past 10 years n i bet I got SOO much more to learn from linux.

My problem is I am trying to make a custom run level to boot without X server, n go directly into shell. What i am trying to do is remove GDM from  run level 3 configuration by:

```
sudo rm /etc/rc3.d/S13GDM
```

so far so good.
After that i am trying to tell Ubuntu to boot straight to run level 3, rather than the default of 2.
by

```
sudo gedit /etc/inittab
```

n editing id:2:initdefault
    to
id:3:initdefault

This is where the problem starts.... I can't find /etc/initab .....

Is there a workaround to get the job done?
Please guide. Thanks in advance.

---

### Post by sandwitch on 2007-06-07
telinit 3 will set you on a networked console
telinit 1 on a single user console

---

### Post by wicusross on 2007-06-13
I was looking into something relating inittab. I found a post that said that as of 6.10 inittab has been replaced with [Upstart]("http://upstart.ubuntu.com/").

---

