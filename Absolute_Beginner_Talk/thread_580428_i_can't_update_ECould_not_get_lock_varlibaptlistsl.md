---
title: "i can't update E:Could not get lock /var/lib/apt/lists/lock"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by pacofvf on 2007-10-18
i've changed my sources.list with the automatic generator but this happened
paco@paco-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

here is mt sources list:
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

---

### Post by Stemp on 2007-10-18
Do you have another apt process running ? 

```
ps -e | grep apt 
```

Update : [https://help.ubuntu.com/community/Troubleshooting#head-76a864274ec599a57da6c374cdb95ed62736e28c](https://help.ubuntu.com/community/Troubleshooting#head-76a864274ec599a57da6c374cdb95ed62736e28c)

---

### Post by wieman01 on 2007-10-19
Same issue here... I am puzzled. Updated it using the same source.list generator.

---

### Post by FredB on 2007-10-19
Update-manager must be running at the same time.

---

### Post by wieman01 on 2007-10-19
No... I have not used it. I waited for a few minutes, now the problem seems to have gone. No idea what is going on. Problem sovled, however.

---

### Post by NeoDesign on 2007-10-20
The post checking if apt is correct, you first check with ```
ps aux | grep apt
``` which processes are running, then inter their PID's and kill them with sudo kill -9 pid1 pid2 ...

This worked for me because ubuntu has a deamon for autoupdate that locks the apt list

---

### Post by dimbulb1024 on 2007-10-20
Same thing happened to me as wieman01.

First time I tried to update I received the error. I waited a few minutes and tried again with no problems.

Very strange.

---

### Post by zanoman on 2007-10-25
Hi,

It means in this case that a synaptic or upgrade had quit without cleaning the lock file and future package manager (update, synaptic, apt-get) see the list as locked.

I had the same problem and found a way that MIGHT work for you:
quit synaptic, in terminal:
sudo rm /var/lib/apt/lists/lock

If you're not a command-line fan (like me) you can also delete it via file browser as root, see an article in september in [http://blog.vocamen.com](http://blog.vocamen.com) for details, it's off subject in this forum. 

then run synaptic and hit 'reload'. It worked for me.

Keep me informed if it worked for you and if you tried the GUI way.

---

### Post by pacofvf on 2008-03-11
Thanks that solved the problem, sorry to take so long to thank you

---

### Post by jpirie on 2008-04-09
> **NeoDesign said:**
> The post checking if apt is correct, you first check with ```
ps aux | grep apt
``` which processes are running, then inter their PID's and kill them with sudo kill -9 pid1 pid2 ...

This worked for me because ubuntu has a deamon for autoupdate that locks the apt list

Hi,
I have the problem listed here...I think.  Can't update anything.  I tried your command above and got this:
james@K-Asus:~$ ps aux | grep apt
root      7429  0.0  0.1   5132  1788 ?        S    20:08   0:00 /usr/lib/apt/methods/http
root      7430  0.0  0.1   5132  1804 ?        S    20:08   0:00 /usr/lib/apt/methods/http
james     7514  0.0  0.0   2988   772 pts/2    S+   20:17   0:00 grep apt

I'm no expert but I dont think I should have two root entries and a James??  Or should I.  Anyway, that aside, is there anything there that I shuld kill or that would be causing Apt not to connect?

Thanks 
James

---

### Post by wieman01 on 2008-04-09
Reboot the PC and see if the problem disappears. That should do.

---

