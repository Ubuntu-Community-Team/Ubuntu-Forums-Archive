---
title: "Problem upgrading Wallstreet PowerBook from Breezy to Dapper"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by DavidTheNew on 2006-07-20
I have tried to upgrade my Wlaastreet PowerBook from 5.10 to 6.06 using the Synaptic package manager and apt-get. I get the same error message:
-----------------------------------
 * Stopping web server (Apache2)...                                      [ ok ]
(Reading database ... 104578 files and directories currently installed.)
Preparing to replace lvm2 2.01.04-5ubuntu1 (using .../lvm2_2.02.02-1ubuntu1_powerpc.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------------

Any idea what is wrong?](*,) ](*,)

---

### Post by linear on 2006-07-21
Might be a broken dependency problem. There is good troubleshooting advice [here]("http://www.ubuntuforums.org/showthread.php?t=186672").
 
(You also might want to repost in the Dapper Mac/PPC forum - more people read that.)

---

### Post by arnieboy on 2006-07-21
> **DavidTheNew said:**
> I have tried to upgrade my Wlaastreet PowerBook from 5.10 to 6.06 using the Synaptic package manager and apt-get. I get the same error message:
-----------------------------------
 * Stopping web server (Apache2)...                                      [ ok ]
(Reading database ... 104578 files and directories currently installed.)
Preparing to replace lvm2 2.01.04-5ubuntu1 (using .../lvm2_2.02.02-1ubuntu1_powerpc.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------------

Any idea what is wrong?](*,) ](*,)

I would suggest you go for a fresh install but if u want to get around this error u may try the following:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_powerpc.deb
```

---

