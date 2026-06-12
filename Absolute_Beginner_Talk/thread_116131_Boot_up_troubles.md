---
title: "Boot up troubles"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2006-01-12
Whenever I boot up my computer and ubuntu begins to load, I run into a strange problem with certain steps failing. It's sorta like my computer skids out on ice, gets stuck in a snow bank, and spins its tires uselessly. Here's how it starts:

[I]
...
Calculating module dependencies				[failed]
...
Setting up networking					[failed]
...
Synchronizing clock to ntp.ubuntulinux.org		             [failed]
Initializing random number generator			[failed]
...
[/I]

Then the boot up switches to a text version of what was going on, focusing in on the 'calculating module dependencies' part. It says:

[I]
...
*Calculating module dependencies...
FATAL: Could not open /lib/modules/2.6.12-9-386/modules.dep.temp for writing: Read-only file system
...
Setting up networking...
/etc/rcs.d/s39ifupdown: line77: /etc/network/run/ifstate: Read-only file system
*Failure initializing /etc/network/run/ifstate
...
[/I]

Then after waiting for a few minutes, the text on the screen starts repeating this message over and over:

[I]
open: Read-only file system
/usr/sbin/termwrap: line 140: $tmpfile: ambiguous redirect
/usr/sbin/base-config: line 31 /var/log/base-config.timings: Read only file system
[/I]

It keeps on doing this for about 20 seconds until it stops and says:

[I]
 * Id "1" respwaning to fast: disabled for 5 minutes
[/I]

Then after 5 minutes, it tries repeating the message again, to no effect. I'm sure if I let it, it would continue like this forever.

The funny this is that this only occurs every *other* I boot up. Here's what I mean: I turn on my computer at the start of my day, and I run into these errors, which I have grown accustomed to. So then I put my coffee mug down, and reach down and press the restart button on my computer tower. 

All of the suddenly my boot up goes smoothly. Next day, same problem.

How can I fix this? It's talking about a Read-only file, but I'm a newb and don't know how to deal with that.

---

### Post by daschl on 2006-01-12
it sounds like your root partition is mounted with the read only option

please post your /etc/fstab here, so that we can have a look at it

---

### Post by benplaut on 2006-01-12
[QUOTE=daschl]it sounds like your root partition is mounted with the read only option

please post your /etc/fstab here, so that we can have a look at it[/QUOTE]

if needed, you can access that with a LiveCD

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=daschl]it sounds like your root partition is mounted with the read only option

please post your /etc/fstab here, so that we can have a look at it[/QUOTE]

What command should I enter into the terminal to find and view /etc/fstab ?

---

### Post by johnnymo87 on 2006-01-12
[QUOTE=daschl]it sounds like your root partition is mounted with the read only option

please post your /etc/fstab here, so that we can have a look at it[/QUOTE]

Never mind, I think I know how to get that file. I used this command:
```
sudo nano /etc/fstab
```

Here's the file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by johnnymo87 on 2006-01-13
**bump**

---

### Post by johnnymo87 on 2006-01-14
Anyone?

It sounds like all I need to do is make certain files not "Read-only", but I don't know how to do that.

---

