---
title: "Multisync won't start"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by nandotron on 2007-05-16
Hi guys,

having a bit of a problem configuring multisync to sync my SE k750i with evolution.  I tried to configure it already but it didn't work.  now when i try to start multisync to edit the pair settings, multisync doesnt load.  when i try to run in terminal, i get:

> enda@enda-laptop:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/enda/.multisync/13/remotesettings
[evo2-sync] WARNING: File /home/enda/.multisync/13/remotesettings does not exist
[evo2-sync] DEBUG: end: sync_connect
Segmentation fault (core dumped)



if anyone can advise me, i'd be really appreciative, i'm very new to this

Thanks!

---

### Post by Pragmatist on 2007-05-18
Go into synaptic and install this package: "libmultisync-plugin-all"

Let us know if that helped.

---

### Post by nandotron on 2007-05-18
great, that seems to have worked, thanks for the advice.

---

### Post by badlydrawn69 on 2007-11-18
I tried downloading the package on synpatic and multisync still doesn't seem to want to open. 

This is what it says in terminal

naim@x-panther:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
Segmentation fault (core dumped)
naim@x-panther:~$ 

Please Help. 

Thank you

---

### Post by NatalieG on 2007-11-23
Same problem here :(

---

### Post by NatalieG on 2007-11-23
[https://bugs.launchpad.net/ubuntu/+source/multisync/+bug/103218]("https://bugs.launchpad.net/ubuntu/+source/multisync/+bug/103218")

---

