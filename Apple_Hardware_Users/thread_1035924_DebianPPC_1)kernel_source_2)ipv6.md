---
title: "DebianPPC: 1)kernel source 2)ipv6"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by noriek on 2009-01-10
hi all.

Installed debain PPC (4) on iMacDV using the net install disc, 2 issues:

1)IPv6 is enabled by default. Fine but my cruddy cheap *** modem/router doesn't seem to support it so I want to IPv4 installed. I assume this requires a kernel rebuild?

2)Where the heck are the sources for the PPC kernel (2.6.18-6)? Before it's suggested I can't use any of the package managers because of the above issue so I need to locate them manually but have had no joy.

Your help and (relevant) ideas most appreciated.


Thanks

---

### Post by tiresia on 2009-01-10
You may want to read this 
[http://wiki.debian.org/DebianIPv6](http://wiki.debian.org/DebianIPv6)
I do not think, that if your connection is not working has anything to do with ipv6.
How did you install Debian? During the installation, you choose most probably to give your iMac an IP Address via DHCP
Where you using that Modem/Router?

---

### Post by stream303 on 2009-01-10
> **noriek said:**
> 1)IPv6 is enabled by default. Fine but my cruddy cheap *** modem/router doesn't seem to support it so I want to IPv4 installed. I assume this requires a kernel rebuild?

No need for a kernel rebuild.  Just disable ipv6.

You can do this by editing **/etc/modprobe.d/00local**

If 00local doesn't exist, just create it, and add this one line:

```
 install ipv6 /bin/true
```

restart networking or reboot.

That line might look like you are trying to install ipv6, but it actually disables it.

---

### Post by noriek on 2009-01-12
BUMP.

Please excuse this bump but having read the suggested above I'm still no further on, it's currently beyond me. Does anyone else have any input (in laymen terms if poss)?

thanks

---

### Post by stream303 on 2009-01-12
You might be having more than one problem, but the above will surely make sure that only ipv4 is active.

In a terminal, log into your root account that you set up when you installed Debian using su and then supplying your root password.

```
su
<root password>
```

Then, edit that 00.local file:

```
nano /etc/modprobe.d/00local
```

Add this line to it:

```
install ipv6 /bin/true
```

Then, because you are using the nano editor, CTRL-O to save your file, and then CTL-W to exit.  Now just reboot.

You mentioned not being able to use package-managers, and I'm wondering if ipv4 is the real culprit - when you first installed, did you specify any mirrors?

If not, then go into System > Administration > Software sources and apply checks to at least the "main" repository.  Or, you can manually edit /etc/apt/sources.list manually.

Thing is, are you getting any sort of connection?  Are you running wired ethernet, or are you trying to use wireless to do this?

---

### Post by noriek on 2009-01-14
Thanks Stream.

I was looking further in to the issue before creating the 00local file which didn't exist when I came across the the following:

Edit /etc/modprobe.d/ailiases


by changing the line

ailias net-pf-10 ipv6

to

ailias net-pf-10 off

This actually solved all my connection issues, by disabling the module i understand. but I was wondering how exactly your method disables ipv6? 

thanks

---

### Post by stream303 on 2009-01-14
> **noriek said:**
> This actually solved all my connection issues, by disabling the module i understand. but I was wondering how exactly your method disables ipv6?

It actually accomplishes the same thing - from what I've been able to determine, it survives updates and upgrades, especially if they relate to aliases and blacklisting, modprobe upgrades etc.  Maybe the networking forum gang can help get to the very bottom of this.

I do know it is a LOT easier to remember. :)

What was frustrating was that I used to do this a lot with different distros in the past, and sometimes what worked a year before, no longer worked at all.  If you look around the net, you'll see *many* different ways of accomplishing this, but when you go and check for ipv6 with ifconfig or other utils, sometimes you find ipv6 still active! 

The way you show is good - as long as Ubuntu sticks to it!  I think that the 00local file mods precede any possible future changes that might come down the pike.  I've seen it happen to others where they configure for ipv4 only, and then later after a few updates/upgrades, they've got ipv6 running again. :)

I'd like to know the real scoop here as well - probably from someone skilled with modprobe and it's various changes over the ages.

---

