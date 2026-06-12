---
title: "Extremly newbie sound question"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-11-03
Hi! I'm on Kubuntu 7.04 and I can't listen to music. My buffers are not recognized, the botton-right buffer icon is always with a red X. Maybe I'm not connecting well the buffers, where's the entry point of the buffers? There seems to be three: Pink, green,blue. I've tried connecting the jack entry of the buffers in each of the holes and the red X crossing the blue buffer on the botton right of the desktop still remains.

How can I get my buffers working and listen to music?

---

### Post by Pumalite on 2007-11-03
At the terminal:
aplay -l

---

### Post by fredscripts on 2007-11-03
it says to me: aplay: device_list:222: no soundcards found...

---

### Post by Pumalite on 2007-11-03
Your kernel is not recognizing your card and not mounting the module.
Try this:
sudo apt-get install linux-backports-modules-generic
Reboot.

---

### Post by fredscripts on 2007-11-03
Ups seems I don't have luck with this:

```
fredeprog@laptop:~$ sudo apt-get install linux-backports-modules-generic
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-ge                                                                                                   neric but it is not installable
E: Broken packages
```

---

### Post by Pumalite on 2007-11-03
That's your answer. You could go to Synaptic>Edit>Fix Broken Packages, but I doubt it will work. Better to reinstall.

---

### Post by fredscripts on 2007-11-03
Thanks for your help. Do you mean execute again the apt-get command? I've done it a few times and always appears the message I've posted. Do you know any other way to fix my problem?

---

### Post by Pumalite on 2007-11-03
You don't have sound since you installed?

---

