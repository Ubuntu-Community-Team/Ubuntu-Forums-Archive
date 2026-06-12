---
title: "dhcp issues"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by prezbedard on 2006-04-20
ok I thought I remedied my problem.

When trying to get an IP address using

sudo ifconfig eth0 start dhcp

or 

sudo dhclient eth0

I recieve an unable to get hostname error


I was able to get dhclient to work after booting into recovery mode but when I booted back into normal mode I am back to square 1. ](*,) 

any ideas?

Thanks

---

### Post by prezbedard on 2006-04-20
ok it seems it is more then just a dhcp issue

I get the same error when I type sudo with nothing after it

or any command involving sudo

sudo: unable to lookup "hostname" via gethostbyname()

---

### Post by prezbedard on 2006-04-21
ok tried this

[http://lists.debian.org/debian-user/2006/01/msg00784.html](http://lists.debian.org/debian-user/2006/01/msg00784.html)

but still no luck.

in recovery mode everything works fine but when booting back into normal mode nothing ](*,)

---

### Post by croak77 on 2006-04-21
First check /etc/hostname. It should have a name there.

Then check what's in /etc/hosts. Should be something like:
127.0.0.1 localhost.localdomain localhost  yourhostname (what was listed in /etc/hostname)

---

### Post by prezbedard on 2006-04-21
ok quick question before I do that since I have already done it numerous times.

should the /etc/hostname 

file have an IP and hostname or just the hostname?

 

Thanks

---

### Post by croak77 on 2006-04-21
/et/hostname should just be a hostname, mine is blackark. the default if you didn't change it during the install is ubuntu.

---

### Post by prezbedard on 2006-04-21
Thanks that worked. I must of screwed the file uo while messing around on the box.

---

