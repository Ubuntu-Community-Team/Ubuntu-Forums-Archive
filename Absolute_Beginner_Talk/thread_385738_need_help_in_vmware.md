---
title: "need help in vmware"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by cf1709 on 2007-03-16
hello, i'm a complete beginner in linux. i tried to install vmware workstation but i can't. it displays the following:

A previous installation of VMware software has been detected. Failure Execution aborted.

i've seen topics about removing the /etc/vmware. i've found the /etc/vmware directory but i can't delete it as it shows "permission denied." i searched for topics on logging here as root and did the same things instructed in that thread. still, i can't delete that folder (the /etc/vmware). should i use the terminal? i know how to make dir's but can't delete it in terminal. call me noob, but i won't laugh, coz i'm really are. it also seems that i can only access the "/home/"username"" folder in terminal.

is somebody there kind enough to  have a guide in installing the vmware workstation (or redirecting me to somewhere who has that)?

thanks!

---

### Post by docshawnc on 2007-03-16
Hi - a couple questions:  1) have you tried removing the old installation using synaptic? and 2) do you have vmserver installed?  Workstation and server can bang heads

---

### Post by seshomaru samma on 2007-03-16
How about [this]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware")?

If you want t to delete the directory you can just
```
sudo rm  -R vmware
```

---

### Post by u.b.u.n.t.u on 2007-03-16
May I suggest "virtualbox".

Screenshots
[http://www.virtualbox.org/wiki/Screenshots](http://www.virtualbox.org/wiki/Screenshots)

I found virtualbox to be intuitive and fun to use.

For example, you can run a Ubuntu live CD within virtualbox on a XP operating system. The right "ctrl" moves you in and out of the virtualbox.

Very fast and worth a look.

---

