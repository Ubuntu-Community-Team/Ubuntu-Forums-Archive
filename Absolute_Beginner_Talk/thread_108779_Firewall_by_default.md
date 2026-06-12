---
title: "Firewall by default?"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2005-12-27
hi Guys. Hope nobody has asked this questions before :P
I've read in many Linux related articles that Linux comes with Firewall by default. Yet Ubuntu dosn't come with one. So here are my questions:

Does other Linux distro really come with Firewall by default [Ubuntu is the only distro I've tried] ?
What is the reason that Ubuntu doesn't come with one? 
Is Ubuntu more secure than others?

One example from [Linux Opinion: An Open Letter to a Digital World: The Windows platform is not just insecure](http://100777.com/node/1107)

> ...Then there is the issue of design. Linux was designed to be in a hostile Internet centric world. As people were programming it they knew this and it no doubt played a role in the designs of their products. **With Linux you will find that firewalls are enabled by default**, users rarely login as administrators, server applications run as users that have limited rights, etc. 

---

### Post by anil_robo on 2005-12-27
In Ubuntu, all ports are blocked by default. This means you have to "open" ports if you want some special web services to run (like apache web server).

To open the ports, you can use iptables. However, to simplify this process, Ubuntu does come with a GUI frontend for iptables called firestarter. You can install firestarter using the "add applications" menu, or using the terminal:
```
sudo apt-get install firestarter
``` 
Firestarter appears in Applications--> System tools

Firestarter may not show up as a tray icon at bootup, but it's running all the times. Proof: When you shut down your computer, you'll see "firestarter firewall" being stopped as a process of shutdown.

Some screenshots [here]("http://www.ubuntuforums.org/showthread.php?t=107634#14")

---

### Post by 23meg on 2005-12-27
> With Linux you will find that firewalls are enabled by default
That sentence is a bit too rough technically. With Ubuntu you don't need a "firewall" in the Windows sense of the word in most cases, because there are no open ports by default. The main difference in the internet traffic routing of Windows and Linux is that Linux does the routing right in the kernel rather than in the userspace, and you can tweak the routing rules with the iptables command, or frontends to it such as Firestarter, which you can find in the Ubuntu repositories.

---

### Post by ubuntu27 on 2005-12-27
Thanks for the quick replay anil_robo & 23meg.

I knew that Ubuntu posts are closed by default.
I just got confused about the article that I've read and some post from newbies [as myself :P] around here that says "Since this is Linux, it comes with Fireall, right?" 

Ok, all linux distro's ports are closed by default. But, so other distros dosn't come with firewall enabled by default as in Ubuntu? Then that article has a small error...

---

### Post by 23meg on 2005-12-27
[QUOTE=anil_robo]In Ubuntu (and any other linux distro for that matter), all ports are blocked by default.[/QUOTE]
[QUOTE=ubuntu27]Ok, all linux distro's ports are closed by default. [/QUOTE]
Wrong, not in all distros; in Ubuntu there are no open ports in a default installation, but in another distro there may be. It depends on the way the developers configure the distro's defaults; if, say, sshd is on by default, you'll start with an open port 22.

---

### Post by ubuntu27 on 2005-12-27
[QUOTE=23meg]Wrong, not in all distros; in Ubuntu there are no open ports in a default installation, but in another distro there may be. It depends on the way the developers configure the distro's defaults; if, say, sshd is on by default, you'll start with an open port 22.[/QUOTE]
Ahh! That explains everything then ;)

Thank you so much 23meg :)

---

### Post by anil_robo on 2005-12-29
[quote=23meg]Wrong, not in all distros; in Ubuntu there are no open ports in a default installation, but in another distro there may be. It depends on the way the developers configure the distro's defaults; if, say, sshd is on by default, you'll start with an open port 22.[/quote]

Thanks 23meg, I've edited my original post to reflect this! I'm learning each day! :)

---

