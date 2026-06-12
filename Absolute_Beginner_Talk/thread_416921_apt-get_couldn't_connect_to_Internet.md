---
title: "apt-get couldn't connect to Internet"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by bff7755a on 2007-04-21
When I try to install some package or 'apt-get upgrade', it couldn't connect to Internet. Maybe it's ipv6 problem? http.us.devian.org IP addres was resolved to 1.0.0.0.

I'm new to Ubuntu and I hope someone can help me.

---

### Post by brownknight on 2007-04-21
> **bff7755a said:**
> When I try to install some package or 'apt-get upgrade', it couldn't connect to Internet. Maybe it's ipv6 problem? http.us.devian.org IP addres was resolved to 1.0.0.0.

I'm new to Ubuntu and I hope someone can help me.
do you have internet connection? can you browse the internet but couldnt get apt-get to connect? need more info...

---

### Post by Nizzle on 2007-04-21
do you use a proxy?

---

### Post by bff7755a on 2007-04-21
> **brownknight said:**
> do you have internet connection? can you browse the internet but couldnt get apt-get to connect? need more info...
Of course I have :). ping, traceroute, firefox and etc. works well. I have problems with apt-get and "Add/Remove Programs" tool.
```
mutex@ibm:~$ cat /etc/apt/sources.list
# See sources.list(5) for more information, especially
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.
deb http://http.us.debian.org/debian stable main contrib non-free
deb http://ru.org/debian-non-US stable/ru main contrib non-free
deb http://security.debian.org stable/updates main contrib non-free
     
# Uncomment if you want the apt-get source function to work
# deb-src http://http.us.debian.org/debian stable main contrib non-free
deb http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed universe main multiverse restricted
# deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
mutex@ibm:~$ 

```

---

### Post by bff7755a on 2007-04-21
> **Nizzle said:**
> do you use a proxy?

No.

---

### Post by bff7755a on 2007-04-21
Anyone can help me? Maybe it's a DNS problem?

/var/log/system.log:

```
Apr 21 20:17:01 ibm /USR/SBIN/CRON[7710]: (root) CMD (   run-parts --report /etc/cron.hourly)
Apr 21 20:17:11 ibm modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 21 20:17:11 ibm modprobe: WARNING: Not loading blacklisted module ipv6 

```

---

### Post by codingmaster on 2007-04-21
Hello!

Apr 21 20:17:11 ibm modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 21 20:17:11 ibm modprobe: WARNING: Not loading blacklisted module ipv6

/etc/modprobe.d/blacklist sets modules that should not be loaded.

That the ipv6 module is not loaded does not influence your internet connection, as long 
as you are not on a ipv6 network (I doubt that you are).

Regards, Georgy Berdyshev

---

### Post by bff7755a on 2007-04-21
> **codingmaster said:**
> Hello!

Apr 21 20:17:11 ibm modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 21 20:17:11 ibm modprobe: WARNING: Not loading blacklisted module ipv6

/etc/modprobe.d/blacklist sets modules that should not be loaded.

That the ipv6 module is not loaded does not influence your internet connection, as long 
as you are not on a ipv6 network (I doubt that you are).

Regards, Georgy Berdyshev

Thanx, I guested. But I still cannot resolve a problem with apt-get :-k

---

### Post by diatribe on 2007-04-21
post output from apt-get update

---

### Post by bff7755a on 2007-04-21
> **diatribe said:**
> post output from apt-get update

```
mutex@ibm:~$ sudo apt-get update
Password:
0% [Connecting to http.us.debian.org (1.0.0.0)] [Connecting to ru.org (1.0.0.0)]

```

That's all :(

---

### Post by diatribe on 2007-04-21
any idea what that ru.org is there for?

---

### Post by bff7755a on 2007-04-21
> **diatribe said:**
> any idea what that ru.org is there for?

I've use a automatic sources.list generator ([http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")), and my sources.list look like that

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ru.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://ru.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://ru.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://ru.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
```

But the problem is the same. apt-get doesn't work.  If you don't know how to resolve a problem can you explain me in what direction I should move? I've looked into '/var/log/messages' and '/var/log/system' but I still cannot resolve a problem. I suppose that problem is in DNS or IPV6. All applications works well, but apt-get and GAIM don't.

---

### Post by nautilus on 2007-04-21
looks like dns poisoning to me or a broken router upstream.

no, ipv6 doesn't resolve to 1.0.0.0.

everybody keeps blacklisting ipv6 as their first response to every little issue.

it's kinda like blaming every bad smell on the dog just because of one little thing...

anyway, it was always broken upstream routers in the first place... i'm babbling, nevermind.

---

### Post by croxi on 2007-04-21
I wish I knew what all that code meant...for someone with almost no experience of being involved with source code, never mind UBUNTU, I´m completely lost. What i´m looking for is something that is safer than cr@ppy Windows but is not quite so "hands-on" as all this lot is. 

Anyone got the answer for me (I dare anyone to tell me to go and buy a Nintendo)

---

### Post by bff7755a on 2007-04-21
I've installed 7.04 and everithing seemes OK. Thank you all ;)

---

