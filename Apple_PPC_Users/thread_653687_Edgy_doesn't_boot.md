---
title: "Edgy doesn't boot"
date: 2007-12-30
forum: Apple PPC Users
---

### Post by indianajoost on 2007-12-30
Hi,

I have an blue slotloading iMac with 320 MB of ram and a harddisk of 6 Gb. I want to install Ubuntu on it. I've downloaded the ppc live cd, but when I try to boot it it won't work. I have tried to use the[ PowerPCfaq]("https://wiki.ubuntu.com/PowerPCFAQ") and [KnowIssues-page]("https://wiki.ubuntu.com/PowerPCKnownIssues"), but I don't get any further. 
When I try to boot with the 'live' command my iMac shuts itself down.

When I try:
```
live-nosplash-powerpc video=ofonly break=top.
```
my keyboard doesn't work at the busy box shell.

When I don't use 'break-top' the process stops at busy box shell and when I try to type the following commands in the busy box shell:

```
modprobe ide-core
```

and 

```
exit
```

I get the following errors:

cp unable to open '/root/var/log/' no such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed no such file or directory
mount: Mounting /sys on root/sys failed no such file or directory
mount: Mounting /proc on root/proc failed no such file or directory
Target filesystem doesn't have /sbin/init

Does anyone know what to try next?:confused:
(see also [this topic]("http://ubuntuforums.org/showthread.php?t=648175&page=2"), yet unanswered, so that's why I started a new one)
Hope you can help me.
grz,
Joost

---

### Post by Auria on 2007-12-30
What do you mean by "it won't work"?

Also I see you are using Gutsy fixes, I don't reckon they are needed for Edgy.

---

### Post by indianajoost on 2007-12-30
I see I have made a mistake. I am trying to install gusty (7.10). So that's what caused the misunderstanding, I am not using Gusty fixes. My problem is that during the boot-up process the iMac shuts itself down or stops. What I've tried to do I have described in my post above, but that didn't work...

---

### Post by wavetheory on 2008-01-02
I get the same errors trying to boot Gutsy on an G4 eMac . . .  when booting with the  'live-powerpc' image I get the Ubuntu startup splash with moving bars for awhile then it exits to 
busy box and hangs

---

### Post by indianajoost on 2008-01-04
I have succesfully installed opensuse, I haven't tried ubuntu any further, because there are too many bugs.

---

