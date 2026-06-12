---
title: "How do I use Ushare??"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-09
I have no clue how to even run it? Little help please? :confused:

---

### Post by 449 on 2008-01-09
Ok when I do:

```
ushare -n HomeServer -p 49153 -c /home/erik/music
```

I get:

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address

```

:confused:

---

### Post by original_jamingrit on 2008-01-14
There's a howto here : 
[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/)

I was just about to try and check it out myself, I'll post again if there's anything to report.

---

### Post by original_jamingrit on 2008-01-14
> **449 said:**
> Ok when I do:

```
ushare -n HomeServer -p 49153 -c /home/erik/music
```

I get:

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address

```

:confused:

eth0 is the connection it's attempting to use.  If you're using a wireless connection, like with a laptop, the connection you need may be eth1 or ath0. See a list with the command "iwconfig".

Either that, or some permissions are wrong somewhere... :confused:

PS:  I think I got mine working without specifying a port (uPnP - Universal Plug and Play - software should open ports for you, both a usability blessing and a security curse).
```
$ ushare -n ServerName -i ath0 -c /path/to/shared/folder
``` where you replace "ath0" with whatever your interface should be.

---

### Post by Killerfocus on 2008-03-05
> **449 said:**
> Ok when I do:

```
ushare -n HomeServer -p 49153 -c /home/erik/music
```

I get:

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address

```

:confused:

I get the same error and I know eth0 is working fine.  I tried the command sudo route add -net 10.0.0.0 netmask 255.0.0.0 eth0 and still no luck

---

### Post by robert.alan.ramsay on 2008-04-30
I had similar trouble. This guide helped.

[http://falz.net/xboxstreaming](http://falz.net/xboxstreaming)

I needed to use a config file to get it to use a different network connection.

---

