---
title: "Synaptic Error"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by lillypilly on 2007-04-18
Every time I use the Synaptic Package Manager when the files I have been downloading finish I get an error message about

If I look at the details area of the manager I see an error like:

Setting up heimdal-kdc (0.7.2.dfsg.1-10unbuntu1) .....
hostname: Unknown host
kstash: writing key to '/var/lib/heimdal-kdc/m-key'
kstash: writing master key file: unable to find realm of host username
dpkg: error processing heimdal-kdc (--configure):

and

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to instrall. Trying to recover:
Setting up keimdal-kdc (0.7.2.dfsg.1.-10ubuntu1) ...
hostname: Unknown host
kstash: writing key to '/var/lib/heimdal-kdc/m-key'
kstash: writing master key file: unable to find realm of host username
dpkg: error processing heimdal-kdc (--configure):
subprocess post-installation script returned error exit status 1


I have tried uninstalling and reinstalling this file using the Manager and that does not seem to have had any effect.

Do I need this file and how may I fix it

---

### Post by Bachstelze on 2007-04-18
Please paste the output of

```
hostname
```

znd

```
cat /etc/hosts
```

---

### Post by lillypilly on 2007-04-18
HymnToLife, Here is what you requested

The output of    hostname  is:

username   (my login and computer name)


The output of   cat /etc/hosts  is:

127.0.0.1 localhost
127.0.1.1 username.userworkgroup   (login name and lan workgroup name

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Bachstelze on 2007-04-18
On the 127.0.1.1 line, try to add just the hostnamel, like this :

127.0.1.1 username username.userworkgroup

---

### Post by lillypilly on 2007-04-18
Tried that so the first lines fo   cat /etc/hosts now looks like

127.0.0.1 localhost
127.0.1.1 username username.usergroup

I have done a reboot and run Synaptic again and the result is still the same

---

