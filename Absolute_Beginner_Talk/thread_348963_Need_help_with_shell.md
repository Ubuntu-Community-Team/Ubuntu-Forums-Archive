---
title: "Need help with shell"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Jim Rogers on 2007-01-29
I need to execute the following command on boot.

      sudo dhclient ra0

I have created a symlink, "rt61' in /etc/rc3.d,  that points to a file, "/etc/init.d/rt61.sh".

I attempted to write a shell:
     #!  /bin/sh
     sudo dhclient -p <password> ra0

I drew the -p from memory and am not at all sure about that.  Have I done this correctly? I am still having a problem it seems, which I can clear by using terminal and entering the dhclient command.

Jim Rogers, W4ATK

---

### Post by njzillest on 2007-01-29
you first need to write the shell program to boot on startup... dont remember it but a simple google will help.. Do you know how to execute a shell program? Your problem is unclear.

---

### Post by Mithrilhall on 2007-01-29
Have you tried adding this in rc.local

```

cd /etc
sudo nano rc.local

```


Just add your code before "exit 0".

---

### Post by inCursorated on 2007-01-29
i think the easiest solution would be to add the following to /etc/network/interfaces

```
auto ra0
iface ra0 inet dhcp

```

btw, i dunno about your system, but on mine the default runlevel is 2 (which i was quite surprised to discover). so, unless you changed it or yours is different the stuff in /etc/rc3.d won't get processed

---

### Post by Jim Rogers on 2007-01-29
Thank you one and all.  inCursorated wins the prize. Solved the problem and I have made note of the solution so hopefully I will remember should I ever need to do this again.

As for run level, I do not even know what a run level is. I just found some information on the forum and his solution was to make that application to run level three

Now how do I mark this thread "SOLVED" as was requested on an earlier thread I started.

---

