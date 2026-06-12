---
title: "[SOLVED] Cinelerra error on startup"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-01-13
I'm running 7.10 on an AMD64 machine. I installed Cinelerra, but on startup I get this error:

```
void MWindow::init_shm():WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

When I do as the error message says, I get a permission denied error:
 ```
"bash: /proc/sys/kernel/shmmax: Permission denied"
```

I used sudo.

I heard that I should add to etc/sysctl.conf

```
kernel.shmmax = 2147483647
```

but this also does nothing.

Can anyone shed some light on this?

---

### Post by cotcot on 2008-01-13
Not sure what you have done exactly. The error is mentioned in the cinelerra manual (section 21.9.3)  including the solution. 

EDITED with the comments of mridekash

Before running Cinelerra do the following:

```
sudo su
echo "0x7ffffff">/proc/sys/kernel/shmmax
```

You missing the sudo there.

For a permanent change, add to the `/etc/sysctl.conf' file the following line: 
kernel/shmmax=0x7fffffff

```
sudo gedit /etc/sysctl.conf
```

or if you prefer: 
kernel.shmmax = 2147483647

For the first time, to avoid restarting your computer, use the following command as root: 
```
sudo sysctl -p 
```

---

### Post by mridkash on 2008-01-13
I also face this problem, and sudo doesn't work here, it still gives permission denied. 

running "sudo su" before entering the command works.

But it seems to be some kernel setting which I dont like to mess with.

---

### Post by cotcot on 2008-01-13
Sorry, I forgot the conf in  sudo gedit /etc/sysctl.conf (I have edited my first post).

And for the echo : indeed it must be done with sudo su (edited in the first post as well). But you do not need to the echo ... because normally you want the permanent solution.

---

### Post by dinostabOMG on 2008-01-13
Hey cotcot, thanks for the help. One thing, I'm not sure if this is an inconsistency or a mistake or something, but you suggested both

kernel/shmmax=0x7fffffff

and 

kernel.shmmax = 2147483647


Should that be a slash or a dot or either? Is there a difference?

---

### Post by cotcot on 2008-01-14
I have quoted the answer from the cinelerra manual.
I use kernel/shmmax=0x7fffffff   (so with the slash) and know that this works.

---

### Post by dinostabOMG on 2008-01-14
Oh, well thanks!

---

