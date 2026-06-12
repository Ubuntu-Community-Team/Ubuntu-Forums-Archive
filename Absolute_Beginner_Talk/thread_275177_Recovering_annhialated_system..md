---
title: "Recovering annhialated system."
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-10-11
So, I decided that 3D desktop would be a pretty cool thing to have, and so I followed some instructions that may or may not have been for installing 3D desktop at all. I'm not sure.

Anyway, I can't turn on my computer now. I get a blue screen that basically says "Good going, moron, now I'm dead."

I wasn't smart enough to make backups. Is there anything I can do to save my ubuntu partition?

---

### Post by jordanmthomas on 2006-10-11
Does the message refer to the X server not starting?

If so, go through the messages and press Alt + F2
log in as your normal user.
Type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then type
```
sudo gdm
```

Post back with the results and we can see what we can do.

**edit**  where is the guide you followed?
**edit2**  Generally, you can accept the defaults when reconfiguring.
**edit3 (gosh)**  There is also probably a backup of your xorg.conf in /etc/X11
```
ls -l /etc/X11
```

---

### Post by theknave on 2006-10-11
The guide I followed was at:

[http://forum.beryl-project.org/viewtopic.php?id=389](http://forum.beryl-project.org/viewtopic.php?id=389)

I want to make sure i have the right code written down before I reboot, otherwise I'll waste so much time waiting for Windows to shut down. I hate you, Microsoft.

Thanks in advance, too, mate.

---

### Post by jordanmthomas on 2006-10-11
You will probably still have problems:

```
sudo nano /etc/gdm/gdm.conf-custom
```
Go to the bottom and put a # at the start of every line after 
```
[servers]
```
Hit Ctrl-O

Then reboot or start gdm

---

### Post by theknave on 2006-10-11
Okay, so if I do what you said to do in the first post, then will I be able to boot up in the GUI and make the changes to the second file? Or will I have to change the second file from the dos-like thing?

---

### Post by jordanmthomas on 2006-10-11
You will need to do it at the command line probably.
You might get lucky, but I can't promise anything, so I'd just do it the first time around.

If you can get a GUI without it, then it is an unnecessary step.

Good luck!

---

### Post by theknave on 2006-10-11
'Kay, I'm going to get to work on it. Thanks!

---

