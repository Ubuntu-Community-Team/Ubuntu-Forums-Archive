---
title: "Feisty Booting Issues"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by spyke01 on 2007-04-25
Hi guys just upgraded from Dapper to Feisty with a few problems(mainly some packages not upgrading) but now with the new generic kernel(s) i have issues booting. Mainly no usplash and several errors.

The 2.6.20-15-generic kernel will not allow me to boot, it gives the following errors and then stops:
```

47.128916 hub 2-2:1.0: hub_port_status failed (err = -71)
47.128977 hub 2-2:1.0: hub_port_status failed (err = -71)
47.129907 hub 2-2:1.0: connect-debounce failed, port 3 disabled
47.130903 hub 2-2:1.0: cannot disable port 3 (err = -71)
47.131902 hub 2-2:1.0: cannot disable port 3 (err = -71)
53.700855 sdb: assuming drive cache: write through
53.715811 sdb: assuming drive cache: write through

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of bauilt-in commands.

/bin/sh : can't access tty : job control turned off
(initramfs)

```
After that nothing happens, the entire boot process stops.

The 2.6.17-11-generic kernel allows me to boot but it gives the following errors:
```

ACPI getting cpuindex for acpiid 0x1
sda: assuming drive cache: write through
sda: assuming drive cache: write through

```

Any ideas on fixing these issues?

---

### Post by jda1701 on 2007-04-25
When you use the 2.6.17 kernel are you able to finish the boot process to the point of a command prompt?

If so, have you tried using the command line to finish upgrading package?

If you're able to get to the command line try this, assuming you have an internet connection available:

Check to make sure all your sources have feisty and not dapper in them:
```
cat /etc/apt/sources.list | grep dapper
```

If that comes back with anything other than returning to the command prompt then:
```
sudo nano -w /etc/apt/sources.list
```
And search for dapper and replace it with feisty

Assuming now that your sources.list file is up-to-date go ahead and update the apt cache on your system.
```
sudo aptitude update
```

Once the cache is updated go ahead and try to do a dist-upgrade
```
sudo aptitude dist-upgrade
```

This should install any packages you don't already have.  Hopefully it will also fix your problem with the 2.6.20-generic.  

Post back if it doesn't.

---

### Post by spyke01 on 2007-04-25
Ok i was able to boot up after changing a line in sources.list that still had edgy sitting in it. i still get these erros:
```

47.128916 hub 2-2:1.0: hub_port_status failed (err = -71)
47.128977 hub 2-2:1.0: hub_port_status failed (err = -71)
47.129907 hub 2-2:1.0: connect-debounce failed, port 3 disabled
47.130903 hub 2-2:1.0: cannot disable port 3 (err = -71)
47.131902 hub 2-2:1.0: cannot disable port 3 (err = -71)
53.700855 sdb: assuming drive cache: write through
53.715811 sdb: assuming drive cache: write through

```

I also added raid456 to the modprobe blacklist. 

The weird thing about these errors is that i dont have any sata devices installed on this system. Any ideas?

---

