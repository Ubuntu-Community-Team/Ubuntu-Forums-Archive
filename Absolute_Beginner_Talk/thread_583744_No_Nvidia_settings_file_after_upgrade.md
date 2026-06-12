---
title: "No Nvidia settings file after upgrade"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-10-20
After the upgrade to 7.10 I no longer have a Nvidia settings file. here's the error message:

Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)

Because of that the Desktop Effects will not work. 

How do I get it back?

---

### Post by FredB on 2007-10-20
Install nvidia drivers using restricted manager. Nvidia-settings will be back.

---

### Post by geovino on 2007-10-20
I tried... this is the error message I get:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

What can I do to solve this? Should I just wait until the repos are working properly?
Is that the trouble?

---

### Post by Frak on 2007-10-20
run
```
sudo apt-get install -f
```
then
```
sudo aptitude reinstall nvidia-glx-new && sudo aptitude install nvidia-settings
```

---

### Post by geovino on 2007-10-20
Thanks for the command lines... but this is the error message after they ran and completed and I rebooted:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2


Looks like the same message as before. I'm  thinking that these upgrades don't work very well. It may be better to copy the files you want to save and do a clean install. What do you think?

---

