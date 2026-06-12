---
title: "Windows Question in Xubuntu"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by climbjm on 2007-01-27
I was wondering what were some good programs I could find on Synaptic Package Manager that I could use to A: Remote into a Windows XP machine and B: Create and run windows as a Virtual Machine. (like vmware)

---

### Post by Jussi01 on 2007-01-27
Vmware player is in the repos, but a better option is virtualbox IMO. it has a .deb download so its easy to install. [www.virtualbox.com](www.virtualbox.com) . As to your other question, are you talking about accessing files or actually logging onto the box? if it is just to get files then you can use samba to do that.

HTH

---

### Post by keithpeter on 2007-01-27
> **Jussi01 said:**
> Vmware player is in the repos, but a better option is virtualbox IMO. it has a .deb download so its easy to install. [www.virtualbox.com](www.virtualbox.com) 
HTH

Hello

I tried virtualbox under Xubuntu with the 686 Kernel and it wanted a couple of libraries. I installed those, and then having set up a virtual machine it would not start with errors as follows

```
Starting VirtualBox kernel moduleFATAL: Module vboxdrv not found.
(modprobe vboxdrv failed)...fail!

```

Can this be run on Xubuntu?

---

### Post by houstonbofh on 2007-01-27
I successfully installed VMware Workstation on Edgy last night.  (New version has Ubuntu support, but is beta...)  I also have used QEMU extensively.  Compiling kqemu support can be tricky, but it is cheaper than workstation!

For remote desktop, I use [www.tightvnc.com](www.tightvnc.com) on all my windows machines.  VNC is already on your Ubuntu desktop.  You just have to enable it...

---

### Post by climbjm on 2007-01-27
When you say that I need to enable it, does that mean use Snaptic Manager?  Or do I have to edit some file with vi and uncomment something?

---

### Post by Buck2348 on 2007-01-27
To the best of my recollection all I had to do was in a terminal type:
```
vncviewer 192.168.0.100:0
```
where 192.168.0.100 is the ip of the Windows machine.  Don't forget the :0 (the "display number") at the end of that.  (If you don't know the ip of the Windows machine, go to it and choose Start --> Run and type in "ipconfig" (without the quotes.))  Then you will get a small dialog asking for the password.  Of course you have to have vnc server already set up, with password, and running on the Windows machine.  When you give it the password you should get the Windows desktop on your screen.

Buck

---

### Post by houstonbofh on 2007-01-30
> **climbjm said:**
> When you say that I need to enable it, does that mean use Snaptic Manager?  Or do I have to edit some file with vi and uncomment something?
You go into the system configuration.  I believe it is something like "Remote Desktop" (Sorry.  At work.) to enable the VNC server.  The client just needs to be run.

---

