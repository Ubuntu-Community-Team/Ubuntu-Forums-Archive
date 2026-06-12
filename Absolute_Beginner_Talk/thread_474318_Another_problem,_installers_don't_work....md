---
title: "Another problem, installers don't work..."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
augh. I'm in the process of trying out NDSwrapper or whatever, and I opened up my Terminal and tried to download/install something, here is what happened:

```
alec@AlecDesktop:~$ sudo apt-get install ndisgtk
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

Then, I tried opening up Synaptic, but I got this error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

I have no idea what's wrong. :(

---

### Post by NeoLithium on 2007-06-14
Open up a terminal window and type:
```
sudo dpkg --configure -a
```

Let it runs it's course and you'll be good to go :)

---

### Post by alecwh on 2007-06-14
yeah, thanks Neo. I figured that out about 3 seconds after posting. :)

---

### Post by NeoLithium on 2007-06-15
LOL. No problem :) Glad it's all workin out for ya.

---

### Post by alecwh on 2007-06-15
Actually, one more problem.

I'm getting a notice at the top right of my screen, it's the "update" notification. I click on it, and the update thing comes up, and it says...

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

I ran the code, and it brought up a Java console thing. (I've was downloading and installing this awhile ago, but it froze so I rebooted... anyway, I don't know what to do.

---

### Post by NeoLithium on 2007-06-15
Try running this:
```
sudo rm -f /var/cache/apt/*.bin
```
then
```
sudo aptitude update
```

---

### Post by alecwh on 2007-06-15
thankx. :)

---

