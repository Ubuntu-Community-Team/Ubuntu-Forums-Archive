---
title: "any antivirus software for ubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-06-24
well im new to the whole ubuntu scene, and is there anything i need for anti virus or w/e

---

### Post by gn2 on 2007-06-24
Anti-virus is simply not required to protect an Ubuntu PC/laptop.

---

### Post by Crafty Kisses on 2007-06-24
> **LiNuXxToOthEMaX said:**
> well im new to the whole ubuntu scene, and is there anything i need for anti virus or w/e
Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up, so it really doesn't matter. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited.

If you must have some Anti-Virus program though, you might want to try "AVG" or something to that nature.

Hope this helps. ;)

---

### Post by Tyke91 on 2007-06-24
It's extremely hard to actually RUN a virus on linux, so i think you are safe in that department :D

it's not just because people don't make viruses for linux, but because you cannot get a virus to automatically run from linux, you'd have to log into root, tell it to run and then install it.

here's some more info

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by Malibu Illusion on 2007-06-24
The only reason you'd want to run an AV on a Linux box would purely be a curstousy to Windows users if you often find yourself forwarding/sending out files from your box to Windows machines.  This is particularly true if you're using your Linux box as a mailserver.  There are applications such as ClamAV or avast! for Linux.

Other than that, there are very, very few "in the wild" viruses or malware for Linux machines mainly because of the way privileges work and the fact such an application would have to be purposfully installed by a user.  Everything in the default repositories is absolutely save and vetted, and that's where the majority of your installing will be happening.

As for firewall, Ubuntu is running iptables already.  If you need a GUI to manage this:

```
sudo apt-get install firestarter
```

Take care.

---

### Post by russell.h on 2007-06-24
I never understood why people even bothered to make antivirus programs for Linux until recently.

As it turns out there is actually a very good reason to use an antivirus program on Linux: Linux is widely used on servers, but not all that widely used on desktops. The thing is that desktops tend to connect to servers, and desktops tend to run Windows, so if you are (for example) running a linux mail server you will want an antivirus to prevent viruses from reaching the Windows based clients.

But I'm going to venture a guess that you aren't running a server, so really there is no need. You might grab a nice little program called "Firestarter" though, which provides a graphical interface to what is essentially Linux's built in firewall (as I understand it). It may not do you any good, but it makes it so you don't have to use the command line to open ports and whatnot.

---

