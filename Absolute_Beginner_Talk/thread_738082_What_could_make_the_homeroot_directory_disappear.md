---
title: "What could make the /home/root directory disappear?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by tjksn on 2008-03-28
First some background on the system.  I have a dual-boot Ubuntu/WindowsXP setup where Windows is used most often.  I am using Ubuntu to learn and get more used to Linux.  I have learned quite a bit regarding using terminal, apt-get, and synaptic so I'm fairly familiar with it at this point.  The Ubuntu version I'm using is the Hardy Heron beta which I upgraded to recently.  The problem I just ran across was an error when opening synaptic (it actually started with upgrade manager) that said it could not open the /home/root/.synaptic-mkdir configuration file because it didn't exist.  When I went into terminal and logged on as root (sudo -i) I got the message that there wasn't a /home/root folder!  To deal with this I created a new root folder (sudo mkdir /home/root) and synaptic and upgrade manager work fine now, but what I want to know is how could the root folder disappear in the first place?  I don't log in as root and only use sudo as I need to in terminal.

Tom

---

### Post by SpaceTeddy on 2008-03-28
root does not have it's home folder in /home (at least in standard configuration)... the homedir of root is usually found directly in /root (no /home infront)... that should still exist... no ?

---

### Post by LowSky on 2008-03-28
root is /  thats why it comes before home. In other words your looking for root home. And why are you using a Beta to learn on, that is like trying to learn to ride a bike that has no seat.. very uncomfortable.

---

### Post by Oldsoldier2003 on 2008-03-28
> **LowSky said:**
> root is /  thats why it comes before home. In other words your looking for root home. And why are you using a Beta to learn on, that is like trying to learn to ride a bike that has no seat.. very uncomfortable.

roots home dir is /root

---

### Post by Whiffle on 2008-03-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/208159](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/208159) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I guess the bigger question is, why is synaptic looking for /home/root ?

---

### Post by tjksn on 2008-03-29
> root is / thats why it comes before home. In other words your looking for root home. And why are you using a Beta to learn on, that is like trying to learn to ride a bike that has no seat.. very uncomfortable.
I didn't just start learning on Hardy, but started with Feisty and just upgraded as things went along.  This is not my primary system so I'm not concerned about losing anything.

I looked inside the /home/root folder I created and there are actually several files inside: .gconf, .goncfd, .gnome2, .gnome2_private, .hplip, .synaptic, wapi, .bash_history.  It makes absolutely no sense that this folder would be needed when it wasn't before.  Also, the /root folder is still there.

---

### Post by om1 on 2008-03-29
like Whiffle said it is a bug in the beta version (Hardy) if you dont want bugs like this i suggest to use a stable supported version

---

