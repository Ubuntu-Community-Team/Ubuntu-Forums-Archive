---
title: "Is there any good anti virus firewall app for llinux"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-11-01
Is there any good anti virus firewall app for llinux

I use ubuntu linux

i have automatix installed and in it's menu it has clamAV and firestarter firewall
has any one of this software

I now that there aren't many linux viruses so
I am more interested in firewall to have contor of my connections

Suggest some or leave a link

---

### Post by xyz on 2006-11-01
Check this out:
[by Artificial Intelligence]("http://www.ubuntuforums.org/showthread.php?t=25421")

---

### Post by fasoulas on 2006-11-01
i am using multibooting pc with linux that means that i need an antivirus ??

I amm interested in firestarter 

if anyone can post the commants to put in the terminal to install it pls post them

---

### Post by bsussman on 2006-11-01
> **xyz said:**
> Check this out:
[by Artificial Intelligence]("http://www.ubuntuforums.org/showthread.php?t=25421")

Very questionable advice.

Sorta like 'Gee - almost nobody I know has AIDS...'

Sure there are less virus/malware/spyware issues with linux.  Of course many modern problems use less os-specific vectors.

But last time I looked, it only takes exactly 1 to ruin my day.

Running without firewalled, antispam, antivirus tools is only for folks who would link to learn how to deal with the (very) possible consequences.

---

### Post by bsussman on 2006-11-01
If you have a spare old pc, [IPCop]("http://ipcop.org")__ is excellent.

---

### Post by fasoulas on 2006-11-01
> **bsussman said:**
> If you have a spare old pc, [IPCop]("http://ipcop.org")__ is excellent.

what do you meen with spare old pc i have a very fast pc 3.2G 1G ram

---

### Post by fasoulas on 2006-11-01
what about cookie control?

In windows many antispyware porgrams find cookies as spyware or adaware
is there any app in linux for that?

---

### Post by bsussman on 2006-11-01
> **fasoulas said:**
> what do you meen with spare old pc i have a very fast pc 3.2G 1G ram

IPCop is a proper firewall meaning it requires it's own hardware.  But not very 'much' hardware :-D

---

### Post by OffHand on 2006-11-01
Really, the only thing you need is a firewall and even a firewall isn't really needed because ubuntu doesn't have any open ports by default.
Cookie control... Open Firefox > Clear Private Data. 
If you would like to have a bit more control you can also change some settings in Firefox's about:config 
(just type about:config in your address bar and hit the enter key).

[http://kb.mozillazine.org/About:config_entries#Privacy..2A](http://kb.mozillazine.org/About:config_entries#Privacy..2A)
[http://kb.mozillazine.org/About:config_entries#Network..2A](http://kb.mozillazine.org/About:config_entries#Network..2A)

---

### Post by fasoulas on 2006-11-01
ok thnx for the advice 

On xp i use outpost firewall it is a very powerfull firewall

But on linux i don't now anything about security software 

I am just asking to learn

Thnx again!!!

[IMG]http://i78.photobucket.com/albums/j101/fasoulas/BugbatterSigLearningFrog.gif[/IMG]

---

### Post by OffHand on 2006-11-01
> **fasoulas said:**
> ok thnx for the advice 

On xp i use outpost firewall it is a very powerfull firewall

But on linux i don't now anything about security software 

I am just asking to learn

Thnx again!!!

[IMG]http://i78.photobucket.com/albums/j101/fasoulas/BugbatterSigLearningFrog.gif[/IMG]

Linux has a build in firewall named ip tables. Firestarter is a Graphical Interface to configure the ip tables. Go to System>Administartion>Synaptic Package Manager. In Synaptic go to Settings>Repositories and enable universe and multiverse: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

After enabling the extra repos open a terminal and type:
```
sudo apt-get install firestarter
```

---

### Post by fasoulas on 2006-11-01
> **OffHand said:**
> Linux has a build in firewall named ip tables. Firestarter is a Graphical Interface to configure the ip tables. Go to System>Administartion>Synaptic Package Manager. In Synaptic go to Settings>Repositories and enable universe and multiverse: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

After enabling the extra repos open a terminal and type:
```
sudo apt-get install firestarter
```

what do you meen with enable universe and multiverse??

---

### Post by fasoulas on 2006-11-01
how can i make firestarter start at ubuntu startup?

---

### Post by r4ik on 2006-11-01
> **fasoulas said:**
> how can i make firestarter start at ubuntu startup?

Might find an answer here,

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

Good luck !

---

