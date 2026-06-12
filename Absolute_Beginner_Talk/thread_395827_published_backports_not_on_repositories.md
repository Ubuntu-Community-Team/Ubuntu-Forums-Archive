---
title: "published backports not on repositories"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by agrimstad on 2007-03-28
I'm probably missing something basic, being new to ubuntu. I'm hoping to find a clue in response to this posting.

First, I'm fairly familiar with the use of apt-get and adding repositories to sources.list. I'm using dapper and my backports repository is:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multivers

I have a problem with totem-xine. The dapper version is 1.4.1, which has at least one nasty bug (crash from totem_logo.png) for which there is a work around. But there is also an official dapper backport of totem-xine to version 1.4.3:

[https://launchpad.net/ubuntu/dapper/i386/totem-xine/1.4.3-0ubuntu1](https://launchpad.net/ubuntu/dapper/i386/totem-xine/1.4.3-0ubuntu1)

Now, here's the problem. I can't use apt-get to do the update--based on what I currently know--because the updated version isn't in the repository. The only way I see how to get the update is a deb file that the URL above provides a link to. I don't use dpkg but am aware that it can be used to install and remove packages in deb files. But I don't understand how dpkg handles a couple of things: (1) upgrade an existing package and (b) deal with the dependencies of the newer version of the package. I have a working totem-xine; I'd like to improve it but I'm afraid I will make a mess of the update.

Is there something that describes the general strategy of installing published backports that aren't, for some reason, put on the normal repositories and so hard for users like me to deal with?

---

### Post by WW on 2007-03-28
It appears that the package that you want is in **dapper-updates**.  You can add these lines to /etc/apt/sources.list:
```

deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

```
Then, as usual, do an update (either **sudo apt-get update** in a terminal, or hit **Reload** in Synaptic).

---

### Post by agrimstad on 2007-03-29
Ah. That was it. I had universe and multiverse in many places in sources.list, just not in the updates lines. So, that solved my problem. Thanks.

---

