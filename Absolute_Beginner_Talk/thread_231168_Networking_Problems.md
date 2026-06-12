---
title: "Networking Problems"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2006-08-07
Hey,

Every time I start (or restart) linux I have to go into Networking and then deactivate and re-activate my ethernet connection, otherwise I can't get onto the net.

Any suggestions as to how I can make it so I don't need to reactivate it everytime?

Thanks
Josh

---

### Post by TFX360 on 2006-08-07
Wireless? Or Wired? eth0 in ubuntu can be both.

Give us the contents of:

```

less /etc/network/interfaces

```

---

### Post by Josh_b on 2006-08-07
It's wired. Here are the contents of that file

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp



iface eth1 inet dhcp

auto eth1


I've got dual gigabit onboard LAN connections. I use eth1

---

### Post by TFX360 on 2006-08-07
Could you try a workaround

Backup your original interfaces file.

Replace the whole line eth1 with and change te IP's to your network:

iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255

And retry then.

dhcp sometime fails.


Kind regards,

TFX

---

### Post by Josh_b on 2006-08-09
I would try that, but my router doesn't let me on the internet unless it assigns the IP address. Even if I manually set it to be the exact same IP address, it won't let me on.

Is there any other way to fix the problem?

---

### Post by drtvasudevan on 2006-08-09
i had this problem.
but i was missing filling in the server name detail.
anyway there is another hot thread going on here on this topic.
[http://ubuntuforums.org/showthread.php?t=193850](http://ubuntuforums.org/showthread.php?t=193850)
check it out.

---

### Post by TFX360 on 2006-08-10
> **Josh_b said:**
> I would try that, but my router doesn't let me on the internet unless it assigns the IP address. Even if I manually set it to be the exact same IP address, it won't let me on.

Is there any other way to fix the problem?
Well that just sounds f*ck*d up to me. That should be possible in any situation. With the correct settings of course.

Kind regards,


TFX

---

