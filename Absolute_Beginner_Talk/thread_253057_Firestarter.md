---
title: "Firestarter"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by tjb891 on 2006-09-07
Can anyone tell me how to make firestarter start on system startup?

---

### Post by meng on 2006-09-07
Is there a specific reason for wanting to do this? Firestarter merely configures the firewall, the firewall is operational even when firestarter is not running.

---

### Post by GonZo1323 on 2006-09-07
> **meng said:**
> Is there a specific reason for wanting to do this? Firestarter merely configures the firewall, the firewall is operational even when firestarter is not running.

really? wow cool they y would people want to keep firestarter running?

---

### Post by MiKuS on 2006-09-07
so they can configure the rules with a gui (allowing/disallowing)traffic

---

### Post by szf on 2006-09-07
I'm in on this thread. I never discovered why I couldn't get firestarter to startup after adding the link to it *sudo|gksudo*'ed to Sessions (System -> Preferences -> Sessions -> Startup Programs)...

I did the same thing that was sucessful before - but no dice on Ubuntu.

p.s. Yes, I did visudo /etc/sudoers with username ALL=NOPASSWD :/usr/sbin/firestarter

---

### Post by tjb891 on 2006-09-07
I am sorrey for my ignorence of iptables, please forgive my ignorance, I am used to the windows version of using a external program to control ports instead of the OS itself. I also did not read my port scan against myself correctely.

---

### Post by wieman01 on 2006-10-05
First of all the command "firestarter" only fires up the GUI for the Firestarter daemon. Firestarter itself is running as a system service and is loaded when you boot your system. 

Even if you quit the GUI, Firestarter keeps running in the background. It makes use of Linux' IPTables which it configures "dynamically". 

It's not quite correct to say that the firewall is operational even if Firestarter is not running (if you are referring to the system service) because in that case you would have to configure IPTables manually.

_So to summarize:_
1. Firestarter starts as a system service as part of the boot process.
2. Firestarter makes "dynamic" use of IPTable.
3. The command "sudo firestarter" starts the Firestarter GUI that let's you configure the daemon.
4. If the system service is terminated ("killed") the Firewall goes down.

---

