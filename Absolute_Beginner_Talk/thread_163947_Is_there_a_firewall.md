---
title: "Is there a firewall?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by stevieg on 2006-04-21
Please forgive my ignorance, but I would like to know if there is a firewall of any kind in Ubuntu. I come from using OS X and use the build in firewall app with that os.

Thank you for your help.

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=stevieg]Please forgive my ignorance, but I would like to know if there is a firewall of any kind in Ubuntu. I come from using OS X and use the build in firewall app with that os.

Thank you for your help.[/QUOTE]
Yes, Ubuntu comes with the powerful iptables firewall.

---

### Post by taurus on 2006-04-21
Yes and one of them is called firestarter.  If you don't have it on your system, use apt-get (or synaptic) to install it...
```

sudo apt-get install firestarter

```

---

### Post by adamkane on 2006-04-21
Howto:
[http://linuxhelp.blogspot.com/2005/12/essential-house-keeping-in-ubuntu.html](http://linuxhelp.blogspot.com/2005/12/essential-house-keeping-in-ubuntu.html)

---

### Post by stevieg on 2006-04-22
Thank you all for your help!

---

### Post by stevieg on 2006-04-22
I have installed Firestarter on my machine. How do I know it is protecting my system? How should I set it up?

---

### Post by louis_nichols on 2006-04-22
Well... first things first. The most important thing to know is that a default ubuntu install doesn't have any lstening daemons, so a firewall is actually not needed.

About firestarter, you don't really see it. It's just there. firestarter is just a front-end and a GUI to the iptables firewall, which is built into the kernel.

for info about using firestarter, go to [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

Personally, what I do after installing firestarter is first to set outgoing policy to "restricted by default". Then in outgoing connection rules, add needed ones, like DNS, http, ftp etc, which are in the dropdown. For others, to which I don't know the port, I just disable the firewall and the watch on the main screen the port they use and the direction (depending on the source and destination, you can tell wether it's incoming or outgoing). Then I create a new rule with that port, either in the incoming or outgoing list.

---

### Post by Mustard on 2006-04-22
[QUOTE=stevieg]I have installed Firestarter on my machine. How do I know it is protecting my system? How should I set it up?[/QUOTE]

To confirm its running...
```
sudo /etc/init.d/firestarter status
```

As long as you don't install any listening daemons, its pretty fine as it is.  The setup wizard is somewhat self explanatory.

---

### Post by stevieg on 2006-04-22
Thanks again. I'm sure I'll have more questions in time.

---

