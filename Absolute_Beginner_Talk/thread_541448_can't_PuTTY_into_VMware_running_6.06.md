---
title: "can't PuTTY into VMware running 6.06"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Stooth on 2007-09-02
Hi All,

Having trouble shelling into 6.06 dapper using PuTTY, getting "Network error: connection timed out".  Have been trying to get help on the VMware support forum but they seem to think the problem is on the Ubuntu side.  

Host is Windows XP, guest OS is Ubuntu 6.06, running in VMware Workstation 6.0.0.  take a look at 

[http://www.vmware.com/community/thread.jspa?threadID=101079&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=101079&tstart=0)

for ifconfig and ipconfig output details.

any help would be MUCH appreciated!!
Stooth

---

### Post by Dr Small on 2007-09-02
Why don't you install openssh-server and connect to your Ubuntu 6.06 pc with PuTTY that way? You can execute shell commands that way too.

Dr Small

---

### Post by Stooth on 2007-09-02
can you tell me more about that??  I think somewhere along the way trying to solve this problem I did install openssh-server, is there a way to check?   and if I do it the way you're suggesting, would I still be launching PuTTY from my host OS (windows xp) desktop and typing in the ip address of the ubuntu vm?

stooth

---

### Post by Dr Small on 2007-09-02
I know nothing about VM, considering I have never used it, but if you have installed openssh-server, you should be able to go to the terminal and type:
```
ssh localhost
```

If it works, it is installed. If you get a "Connection Refused" or something, then it isn't installed. SSH is a "Secure Shell" which tunnels through port 22 (or whatever you deem it to be) and allows you to be on a remote computer and execute commands to your system with SSH on it. This can be done with PuTTY, as PuTTY is a SSH Client.

To be able to connect with PuTTY to your system with Openssh-server, you must first open port 22 on your firewall (preferably use Firestarter) so inbound connections on port 22 will be accepted. You should then be prompted with your username & password, and then will be remotely logged onto your system's computer with Openssh-server on it, allowing you to execute commands.

Dr Small

---

### Post by Hospadar on 2007-09-02
If you are trying to ssh through a router you'll probably have to foreward port 22 on the router.

---

