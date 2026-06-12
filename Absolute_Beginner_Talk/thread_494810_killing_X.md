---
title: "killing X"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by davidsrsb on 2007-07-07
Please remind me how to kill X windows ( so that the Nvidia install script can be run)
ctrl-Alt F1 does not actually stop X in the background

---

### Post by AlexenderReez on 2007-07-07
Ctrl + Alt + backspace

---

### Post by taurus on 2007-07-07
```
sudo /etc/init.d/gdm stop
```

p.s.  Ctrl + Alt + backspace only restarts X.

---

### Post by AlexenderReez on 2007-07-07
> **taurus said:**
> ```
sudo /etc/init.d/gdm stop
```

p.s.  Ctrl + Alt + backspace only restarts X.

baka ...what happen before restart?stop then start again ..... but by the way if anybody want to install anything.....just use
> sudo /etc/init.d/gdm **restart**

or ctrl + alt + backspace......

---

### Post by davidsrsb on 2007-07-07
both the gdm stop and the ctrl-alt-bspc methods jump to text and hang executing /etc/rc.local

looking at rc.local there is nothing odd, but permissions are maybe wrong

---

### Post by taurus on 2007-07-07
Or just boot into recovery mode from GRUB menu and install nVidia script.

---

### Post by davidsrsb on 2007-07-07
using recovery mode gets a complaint about runlevel one ie you are root.
Nvidia thinks that the script won't work as it cannot find libraries
The prompt suggests a switch to runlevel 3, which immediately jumps into X

---

### Post by taurus on 2007-07-07
Any reason why you don't want to use synaptic to install nVidia driver for your graphic card?  It's available from the repos.

---

### Post by davidsrsb on 2007-07-07
I need the latest for a 7300 card, the repository version has problems

---

### Post by taurus on 2007-07-07
Can you post your /etc/rc.local since you said that it causes problem when you try to stop gdm?

```
cat /etc/rc.local
```
and
```
ls -la /etc/rc.local
```

---

### Post by davidsrsb on 2007-07-07
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

ls -la /etc/rc.local
-rwxr-xr-x 1 root root 306 2007-04-15 19:49 /etc/rc.local

---

### Post by taurus on 2007-07-07
> **davidsrsb said:**
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

ls -la /etc/rc.local
-rwxr-xr-x 1 root root 306 2007-04-15 19:49 /etc/rc.local

Is there an empty line after **exit 0** in /etc/rc.local?

---

### Post by davidsrsb on 2007-07-07
It ends in a newline or cr

If I execute it as user it completes silently

---

