---
title: "I have lost administrative privileges [Resolved]"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by cherm on 2007-01-09
I have been trying to SAMBA to work on my system and have changed something (what that something is I have no idea!).  I no longer am able to perform any administrative functions, ie change network connections, get to sudo in terminal, update software via Synaptic Package Manager etc.

When I try to perform any administrative actions, I get a notification that the computer is "Starting Administrative Application" and then nothing happens and I do not have access to the program I was trying to work with.

In terminal, if I type sudo, I receive the response "sudo: unable to lookup (none) via gethostbyname()"

Anyone have any ideas?  I am very much a newbie, so plain english reponses are appreciated (and necessary for me to understand!).

Thanks for any help!

Chris

---

### Post by sardion on 2007-01-09
Sounds like you have messed up your /etc/hosts file somehow (I don't mean you did something, I mean something happened to it).

In a terminal, do

cat /etc/hosts

and post the results.

Also do

hostname

in the terminal and post what it says.

---

### Post by cherm on 2007-01-09
Sardion -
Thanks for the quick post.  As requested here are the results for the suggested terminal lines:

chris@(none):~$ cat /etc/hosts
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

chris@(none):~$ hostname
(none)

I hope this tells you something.  Could you explain what each of these command lines 
means and what the response means (if easily explained).  I would guess that hostname is the name of the computer.

Thanks

Chris

---

### Post by cherm on 2007-01-11
I have been trying to get SAMBA to work on my system and have changed something (what that something is I have no idea!). I no longer am able to perform any administrative functions, ie change network connections, get to sudo in terminal, update software via Synaptic Package Manager etc.

When I try to perform any administrative actions, I get a notification that the computer is "Starting Administrative Application" and then nothing happens and I do not have access to the program I was trying to work with.

In terminal, if I type sudo, I receive the response "sudo: unable to lookup (none) via gethostbyname()"

Anyone have any ideas? I am very much a newbie, so plain english reponses are appreciated (and necessary for me to understand!).

Thanks for any help!

Chris

---

### Post by taurus on 2007-01-11
Looks like you somehow mess up /etc/hosts and/or /etc/hostname!  Boot into recovery mode from GRUB menu and make sure the name in /etc/hostname is the same one as in /etc/hosts.  Otherwise, post them here.

```
nano /etc/hostname
nano /etc/hosts
```

---

### Post by mclaug28 on 2007-01-12
I had the same problem.  Check to make sure the first line has the correct name of the computer.  
So if your computer name is foo.  It should read

127.0.0.1 localhost.localdomain localhost foo

Hope that helps

---

### Post by cherm on 2007-01-12
Thanks everyone for your help!  I am all set and ready to sudo!

---

### Post by cherm on 2007-01-12
Thanks for everyones help - I am set and ready to sudo!

---

