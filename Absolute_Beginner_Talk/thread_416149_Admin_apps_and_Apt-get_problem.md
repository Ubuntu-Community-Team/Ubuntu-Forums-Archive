---
title: "Admin apps and Apt-get problem"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ascendantlive on 2007-04-20
I just installed Ubuntu 6.06 and know very little about linux. I've played with Freespire a little but that's about it. 
I am unable to run most of the programs on the administration menu under 'system' including the user manager, Synaptic, and software properties. When I go to 'Add/Remove' things seem fine until I try to install and a tab appears on the taskbar that says 'Starting Administrative Application' and then nothing happens, the tab goes away and nothing loads. 

in the terminal apt-get gives me this message :
[COLOR="RoyalBlue"]ascendantlive@5675765768:~$ sudo apt-get update
sudo: unable to lookup 5675765768 via gethostbyname()[/COLOR]

I really appreciate any help you could give me,

---

### Post by taurus on 2007-04-20
Can you post the output of these two files here?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by ascendantlive on 2007-04-20
ascendantlive@5675765768:~$ cat /etc/hostname
5675765768
ascendantlive@5675765768:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       5675765768

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ascendantlive@5675765768:~$

---

