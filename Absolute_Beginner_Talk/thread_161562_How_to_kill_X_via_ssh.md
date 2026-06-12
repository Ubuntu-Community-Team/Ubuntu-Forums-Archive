---
title: "How to kill X via ssh?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by foxy123 on 2006-04-17
I have connected to a remote PC via ssh and want to kill X there. How should I do it? So far I tried
```
sudo killall Xorg
```
but it did not do anythng on the repote PC...

---

### Post by steve.horsley on 2006-04-17
Assuming the remote PC is an Ubuntu box, **sudo /etc/init.d/gdm restart** (or stop) might be a good way to go.

---

### Post by henryk69 on 2006-04-17
To kill the xserver you should kill the "X" process. It can be found e.g. like this:
```
 ps -ef |grep X 
```

Then kill it 
```
 sudo killall X 
```
or 
```
 sudo kill -9 PID 
```

You can identify the PID of X from the **ps** command.

cheers

---

### Post by foxy123 on 2006-04-17
thanks a lot guys, it works now!

---

### Post by navigator_xc on 2008-06-03
> **henryk69 said:**
> To kill the xserver you should kill the "X" process. It can be found e.g. like this:
```
 ps -ef |grep X 
```

Then kill it 
```
 sudo killall X 
```
or 
```
 sudo kill -9 PID 
```

You can identify the PID of X from the **ps** command.

cheers


Doesn't work for me.. 

navigator@XBox:~$ ps -fe |grep X
avahi     4877     1  0 09:56 ?        00:00:00 avahi-daemon: running [XBox.local]
root      5219  5215  2 09:56 tty7     00:00:10 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
1000      5888  5844  0 10:03 pts/0    00:00:00 grep X
navigator@XBox:~$ sudo killall X
X: process not killed

---

