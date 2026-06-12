---
title: "Installing ALSA 1.0.15 help?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Codix121 on 2008-01-11
I have the same problem as this guy:

[http://ubuntuforums.org/showthread.php?t=645041](http://ubuntuforums.org/showthread.php?t=645041)

but when I did:

```
sudo apt-get install linux-backports-modules-generic
```

I got this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic but it is not installable
E: Broken packages

```


and it still doesnt work

my:

lshw -C sound

returned with:

```

codix@codix-laptop:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:dc440000-dc443fff irq:11

```

Any help or ideas?

---

### Post by swoll1980 on 2008-01-12
try ```
sudo lshw -C sound
```

---

### Post by Codix121 on 2008-01-13
UM I already did that..
it's up on the first post....

not to be rude,
but that was NO help.

please fully read a post if your gonna
attempt to help man...

---

### Post by nikoPSK on 2008-01-13
It comes as an update. :)

---

