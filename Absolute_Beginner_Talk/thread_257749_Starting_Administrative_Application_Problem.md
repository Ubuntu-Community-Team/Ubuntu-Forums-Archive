---
title: "Starting Administrative Application Problem"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Super5h33p on 2006-09-14
I have updated Ubuntu and when i restarted i could not run an administrative application.  Thanks for your help,

---

### Post by Skia_42 on 2006-09-15
What happens exactly? Do you get any error messages that could help identify the problem?

---

### Post by Super5h33p on 2006-09-15
no error message it just acts as if it is goin to start the admin application but it never opens and the buttons on the taskbar go away. worked fine before i updated.

---

### Post by Najand on 2006-09-15
Can you run "sudo" from the terminal.

NOTE: terminal is located at APPPLICATION -> Accessories.
Open terminal and run something like "sudo mount" or something similar and see if there is an error or not.

---

### Post by Super5h33p on 2006-09-15
nothing happens

---

### Post by Brunellus on 2006-09-15
> **Super5h33p said:**
> nothing happens
try 

gksudo synaptic

and see what happens.

---

### Post by Super5h33p on 2006-09-16
thanks you guys but i just decided to do a re-install and it fixed the problem.

Thanks again

---

### Post by mn_kthompson on 2007-08-12
Well that stinks!  I'm having the same problem that you're having and I don't want to reload my machine.

So here's the deal.  I can click on the administrative applications and a space will show up in the taskbar that says "opening administrative application" but after a short amount of time it will go away.  And the application never opens.

Here are some other details.  I never have any trouble running sudo <something>.  gksu on the other hand doesn't always run.  If I run an application with gksu right after I run something with sudo then the administrative application will come up right away without asking me for a password.  On the other hand, if I run gksu <something> before running sudo <something> then it just sits there.

Any thoughts?

---

### Post by mn_kthompson on 2007-08-13
OK, I found a thread [http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root]("http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root") that suggested a fix to the problem was to ensure that permissions and ownership of the file were correct and that setuid root was also in place.  I believe that I have verified that:
```
kevin@MSU1375020:~$ ll /bin/su
-rwsr-xr-x 1 root root 27K 2006-12-19 14:35 /bin/su
kevin@MSU1375020:~$ ll /usr/bin/sudo
-rwsr-xr-x 1 root root 90K 2006-10-09 06:37 /usr/bin/sudo

```

Unfortunately things still aren't working for me.  Does anyone have any other ideas on how I can troubleshoot or fix this problem?

---

### Post by mn_kthompson on 2007-08-15
I've also read a bunch of threads suggesting that something might be wrong with /etc/hosts and /etc/hostname, but I've checked them out and they look good to me.
```
kevin@MSU1375020:~$ cat /etc/hostname
MSU1375020
kevin@MSU1375020:~$ cat /etc/hosts
127.0.0.1       localhost       MSU1375020      MSU1375020.campus.mnsu.edu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
kevin@MSU1375020:~$ 

```

There are a couple of interesting things to note on this.  For one thing, even though GKSU doesn't work, SU does work.  I've also noticed that KDESU works for me.  I'm tempted to just change the launchers so that they all use KDESU, but I'm still not quite ready to give up on this gksu thing.  

Does anyone have any ideas on how I can troubleshoot this further?  I'm trying really hard to figure this out on my own, but I'm going to need a push.

---

### Post by mn_kthompson on 2007-08-15
Is anyone even reading this?  I don't want to waste my time posting in a forum that no one is reading.  Am I posting in the right place?

---

### Post by mn_kthompson on 2007-08-16
I didn't think that it was relevant, but I might be having problems because I'm using PAM and Winbind to connect to Active Directory.  Here are some details on an open bug in gksu that might be causing my woes.
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/15093]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/15093")

---

