---
title: "Trouble Installing Limewire"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Captain Jack on 2007-12-06
I am newb to Ubuntu. I am running 7.10 for AMD 64-bit. I searched around for answers but nothing seemed to resolve my problem. I am trying to install Limewire or Frostwire. But I cannot get either to install. When I try Frostwire, the package installer says "Error: Failed to satisfy all dependencies (broken cache)". So, installation pretty much stops there. When I try Limewire, it freezes on installation and I end up having to logout and log back into Ubuntu. Then when I try installation of Limewire again, it tells me that "Only one software management tool is allowed to run at the same time". Any help please?

---

### Post by kpkeerthi on 2007-12-06
> 
when I try installation of Limewire again, it tells me that "Only one software management tool is allowed to run at the same time". Any help please?


Thats due to abrupt termination of the last installation routine you were performing. Reboot and try to install again. If the problem persists, open terminal and install from command line and post the error message, if any
```

sudo aptitude install limewire

```

---

### Post by Captain Jack on 2007-12-06
simba@simba-desktop:~$ sudo aptitude install limewire
[sudo] password for simba:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
simba@simba-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
simba@simba-desktop:~$ 
simba@simba-desktop:~$

---

### Post by Captain Jack on 2007-12-06
What do you think is going on?

---

### Post by PmDematagoda on 2007-12-06
Do:-

```
sudo dpkg --configure -a
```

To try and fix the problem.

In order to use commands which change the core of the system, you need to append them with sudo or in some cases you can use fakeroot if you wish.

---

### Post by daengbo on 2007-12-06
I would suggest gtk-gnutella, which handles Limewire and some other networks, as the Limewire client has been accused of containing malware at various points. Gtk-gnutella is open source, so it's obvious what's in there.

---

### Post by staticvoid on 2007-12-06
+1 for Gtk-gnutella :D

Hope you get what you want installed though. Your choice :)

---

### Post by Captain Jack on 2007-12-06
The sudo command seemed to help things out. I had to do something in Synaptic. I had to apply the Java or something. Anyways, Limewire installation worked, now the application comes up blank when executed? Where is a good place to download Gnutela?

---

### Post by kpkeerthi on 2007-12-06
Synaptic :)

---

### Post by Joeb454 on 2007-12-06
Have to agree with the not using Limewire argument, I've used it in the past, and slowed my machines right down (they were Windows machines, but still, slowed them down even more!)

---

### Post by cbiere on 2007-12-06
LimeWire never *contained* any malware. Until about 4 years ago, it was *bundled* with some adware. See [http://en.wikipedia.org/wiki/LimeWire](http://en.wikipedia.org/wiki/LimeWire). It only affected the Windows version anyway. LimeWire *is* open-source, see [http://www.limewire.org/](http://www.limewire.org/) and it's **identical** to FrostWire except for the skin.

---

