---
title: "anti virus?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-05-05
I just put ubuntu on my comp, and since, for me atleast, it was a bitch to get done, I dont want to have to delete my **** and re install because some worm. Anybody know a good anti-virus prog.

---

### Post by Schalken on 2007-05-05
Is this a worm in Ubuntu or in another OS (eg, Windows) that you also have installed?

---

### Post by Najand on 2007-05-05
What is that warm you are talking about? If you can be more specified then we can help you!

---

### Post by Ocxic on 2007-05-05
there are not many viruses for linux systems, most of witch are only proof of concept are aren't circulating the net, i use clam av, rarly, you don't really have to worry about viruses and stuff.

---

### Post by slimdog360 on 2007-05-05
If you have to, I suppose calmav but you really dont need it. You will get some saying that you do, other will say you dont, others again will say you would be good with just a firewall. Imin that category, the firewall one. Install a firewall like firestarter or guarddog if your a bt more confident at setting things up. 

Honestly, I've been running Linux for a little over a year now and have deliberatley tested it against some of th worst sites on the net and I havent gotten anything but a few tracking cookies, but you get those from everything anyway. I have never even had any spyware etc so Id be pretty confident that Im safe.

for firestarter either lookin synaptic or add/remove programs for firestarter or open a terminal and type ```
sudo apt-get install firestarter
```
You really only need to run it once, it then configures your firewall which is loaded at boot time but I dont think it logs activity unless it runs all the time. What it does is, is configure an 'internal' firewall to Ubuntu called iptables, so really all firestarter is (and most other linux firewalls) are just a front end to this iptables.

---

### Post by Zkupa on 2007-05-05
He does not say he have a worm right now.
As I see it he tells us he's affraid to get a virus, and therefore is asking for some anti virus programs.

An i right em11488 ?

---

### Post by mikewhatever on 2007-05-05
If you use an email client or a server, install clamav from the repositories.
If you need an av for scanning your HDD, use AVG or AVAST:
[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)
[http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)

A popular belief, that users above have already expressed, has it that Ubuntu does not need an av software.

---

### Post by em11488 on 2007-05-05
yes

---

### Post by aysiu on 2007-05-05
Read this:
[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

By the way, I moved your Envy post to [its own thread](http://ubuntuforums.org/showthread.php?t=433851).

---

