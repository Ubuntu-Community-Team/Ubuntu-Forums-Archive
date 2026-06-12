---
title: "Cannot install updates or use apt-get"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Darmak on 2007-07-25
Whenever I try and download updates or use apt-get for anything, it gives me this error message:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_7.2_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

Anyone have an idea of what's going on and how I can fix it?

---

### Post by nichipet on 2007-07-25
Look at two files: /etc/apt/sources.list and /etc/hosts

I see that it tried to connect to localhost, that's your computer. One of those files may have something wrong that sends your attempted connection to us.archive.ubuntu.com to your own computer instead.

In fact, give the contents of both of them here so we can see what they say.

---

### Post by Darmak on 2007-07-25
Okay, /etc/hosts gives me this: 
```
127.0.0.1	localhost
127.0.1.1	Darmak

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

and /etc/apt/sources.list gives me this:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by nichipet on 2007-07-25
Try this. Go into Synaptic, then to Settings:Preferences:Network and see if it is set for a direct connection or a proxy. If it's a proxy, try a direct connection. Once it's a direct connection in Synaptic, try installing something from Synaptic and see if that has the same error.

---

### Post by Darmak on 2007-07-25
I checked and it was already set for direct connection.  I didn't do anything else except run the update manager and now it works.  I didn't do anything and now it works.  Maybe it's because I restarted my computer? (I had to go to work and now I'm back)

I don't know but either way thank you for your help, I really appreciate it all.

---

### Post by nichipet on 2007-07-25
I'm not sure I did much of anything, but you're welcome all the same.

---

