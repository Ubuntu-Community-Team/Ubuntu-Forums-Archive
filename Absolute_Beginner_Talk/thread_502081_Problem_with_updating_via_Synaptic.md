---
title: "Problem with updating via Synaptic"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by raptor87 on 2007-07-16
Hi guys, my problem is this:

I want to update my ubuntu version into the last one (the 7.02) but before I need to update my "update-manager" from the 0.42 into the 0.45 version. I have read the wiki about and I followed all the instruction, but for synaptic the last update-manager version available on the net is the 0.42.

So how can I force synaptic to download the 0.45?

---

### Post by overdrank on 2007-07-16
> **raptor87 said:**
> Hi guys, my problem is this:

I want to update my ubuntu version into the last one (the 7.02) but before I need to update my "update-manager" from the 0.42 into the 0.45 version. I have read the wiki about and I followed all the instruction, but for synaptic the last update-manager version available on the net is the 0.42.

So how can I force synaptic to download the 0.45?

Hi can you post the link to th "how to" and maybe we can help.:guitar:

---

### Post by raptor87 on 2007-07-16
This is the wiki which I followed [https://wiki.ubuntu.com/EdgyUpdatesEnabled](https://wiki.ubuntu.com/EdgyUpdatesEnabled)

---

### Post by 56seeker on 2007-07-16
You need these two terminal commands:

```
sudo apt-get update
```

This will update apt's (the engine behind synaptic) database with information on available software

```
sudo apt-get upgrade
```

This will update your installed software; including the update manager.

---

### Post by Pheodax on 2007-07-16
Ubuntu Feisty Fawn 7.04 is actually the latest stable version (not 7.02). Apt-get can also upgrade your distro to the latest version with:

sudo apt-get dist-upgrade

All the commands given in this topic could have been found with:

apt-get --help
man apt-get

---

### Post by raptor87 on 2007-07-16
> **56seeker said:**
> You need these two terminal commands:

```
sudo apt-get update
```

This will update apt's (the engine behind synaptic) database with information on available software

```
sudo apt-get upgrade
```

This will update your installed software; including the update manager.

I have written it on the terminal, but apt haven't also updated the "update-manager", so unfortunately the problem remain :(.

> **Pheodax said:**
> Ubuntu Feisty Fawn 7.04 is actually the latest stable version (not 7.02). Apt-get can also upgrade your distro to the latest version with:

sudo apt-get dist-upgrade

yep, sorry I have wronged the version number :P.

Are you sure that I could write that command on terminal? In the "how to" I read that is necessary to upgrade the update manager first...

---

