---
title: "Gnome on Server"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by vaximily on 2007-02-13
Long time Windows Server admin, trying to move to Linux and feel like a moron.  I'm in a Unix class so I can navigate the Command line decently, but I am still pretty lost.

Ok, I installed Ubuntu 6.06.1 LTS x64 Server on my AMD Sempron 64 w/ 768mb RAM.

Got all my stuff updated using apt-get like a friend showed me.  Everything seems fine and dandy.

Only 2 problems.  1, can't access webmin on port 10000 from another system on the network, even though I followed all the steps to open the port in iptables.   No biggie, I'm sure I can fix this later.



**_:::MAIN PROBLEM:::_**
I can't for the life of me get Gnome (or KDE for that matter) to install and run.  I tried everything I can find on here, plus on google, and randomly playing around for the last 3 hours with different files and commands.

I did the command
```
sudo apt-get install ubuntu-desktop
```
it asked me for my root password (hit enter, haven't changed that yet)
goes back to shell prompt.

I typed in the command
```
sudo /etc/init.d/gdm start
```   (found this on the forum)
asks for password again, hit enter again.
back to shell prompt.


So I'm guessing I'm either missing something really small or I'm a complete dummy and have no idea what I'm doing.

Either way can someone PLEASE help me through this?

Thanks!

---

### Post by Perfect Storm on 2007-02-13
Have you tried with
```
startx
```

May I suggest xubuntu if you really want to run a X on a server.

---

### Post by vaximily on 2007-02-13
Yes and every variation there of... a few years ago when I first attempted to hop into Linux that's the command I had to use.  Now I just get 

```
$startx
-bash: startx: command not found
$
```

/edit/

Missed the second part of your post.

In my experience Gnome doesn't use a SIGNIFICANT amount of extra resources compared to KDE, and is a much friendlier interface.

With that said, I haven't even seen a KDE system in atleast 4 years.  I'm sure things have changed.

---

### Post by vaximily on 2007-02-13
Well I have no idea what in the world I did.  Sent the reboot command, system rebooted. Logged back on.

Executed
```
sudo apt-get install ubuntu-desktop
```
and this whole long installer started running that I've never seen before.... I wonder if everything else I ran through sudo didn't work either.

I'll post how it goes, looks like the installer is about 11% completed right now.

---

### Post by vaximily on 2007-02-13
Keep getting a fontconfig error - cannot load default config file.

Other than that everything seems to be going smoothely.

---

### Post by vaximily on 2007-02-13
Alrighty, so now Gnome is running no trouble.  And all the updates I thought I did before I apparently never actually did, so I'm running them now. :).  Solved my own problem.

---

