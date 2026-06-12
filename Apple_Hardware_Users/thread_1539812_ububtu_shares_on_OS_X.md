---
title: "ububtu shares on OS X"
date: 2010-07-27
forum: Apple Hardware Users
---

### Post by wlraider70 on 2010-07-27
I have an ububtu server that up and running pretty well. I can share folders to other ubuntu boxes and PC.

I just got my first mac. How do i access the shares from OS X. 

I used "GO" -> "connect to server" but that isnt working...

---

### Post by heimo on 2010-07-27
> **wlraider70 said:**
> I have an ububtu server that up and running pretty well. I can share folders to other ubuntu boxes and PC.

I just got my first mac. How do i access the shares from OS X. 

I used "GO" -> "connect to server" but that isnt working...

Did you try entering your ubuntu servers ip address on "Go->Connect to server->Server address"? It probably isn't found with name / autodetected by "browsing".

---

### Post by Macskeeball on 2010-07-27
> **heimo said:**
> Did you try entering your ubuntu servers ip address on "Go->Connect to server->Server address"? It probably isn't found with name / autodetected by "browsing".

Don't forget to include the smb:\\ at the beginning. For example, smb:\\192.168.5

---

### Post by wlraider70 on 2010-07-28
i used...

smb:\\10.10.10.2

and got...

The server may not exist or it is not operational at this time. Check the server name or IP address and try again.




i pinged it to be sure
```

RJMac:~ robbiejo$ PING 10.10.10.2
PING 10.10.10.2 (10.10.10.2): 56 data bytes
64 bytes from 10.10.10.2: icmp_seq=0 ttl=64 time=1.040 ms
64 bytes from 10.10.10.2: icmp_seq=1 ttl=64 time=1.666 ms
64 bytes from 10.10.10.2: icmp_seq=2 ttl=64 time=0.931 ms
64 bytes from 10.10.10.2: icmp_seq=3 ttl=64 time=2.259 ms
64 bytes from 10.10.10.2: icmp_seq=4 ttl=64 time=1.415 ms
64 bytes from 10.10.10.2: icmp_seq=5 ttl=64 time=2.717 ms
^C
--- 10.10.10.2 ping statistics ---
6 packets transmitted, 6 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.931/1.671/2.717/0.639 ms
RJMac:~ robbiejo$ 

```

Is there some setting that i need to have on the ubuntu side?

---

### Post by Macskeeball on 2010-07-28
> **wlraider70 said:**
> i used...

smb:\\10.10.10.2

and got...

The server may not exist or it is not operational at this time. Check the server name or IP address and try again.




i pinged it to be sure
```

RJMac:~ robbiejo$ PING 10.10.10.2
PING 10.10.10.2 (10.10.10.2): 56 data bytes
64 bytes from 10.10.10.2: icmp_seq=0 ttl=64 time=1.040 ms
64 bytes from 10.10.10.2: icmp_seq=1 ttl=64 time=1.666 ms
64 bytes from 10.10.10.2: icmp_seq=2 ttl=64 time=0.931 ms
64 bytes from 10.10.10.2: icmp_seq=3 ttl=64 time=2.259 ms
64 bytes from 10.10.10.2: icmp_seq=4 ttl=64 time=1.415 ms
64 bytes from 10.10.10.2: icmp_seq=5 ttl=64 time=2.717 ms
^C
--- 10.10.10.2 ping statistics ---
6 packets transmitted, 6 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.931/1.671/2.717/0.639 ms
RJMac:~ robbiejo$ 

```

Is there some setting that i need to have on the ubuntu side?

Sorry, my mistake. It's smb:// not smb:\\ so you should use smb://10.10.10.2

I looked at what I had in my own "Connect to server," saw backward slashes in there for some reason, and just assumed it was a Windows path thing and that that was how it had to be for Windows file sharing technology. When I actually tried connecting to it, however, it automatically prefixed an afp:// because it didn't parse smb:\\ (backward slashes) as a protocol.

So again, what you should use is smb://10.10.10.2

---

### Post by wlraider70 on 2010-07-28
that did it.
THANKS

It appears to disconnect on sleep or perhaps more often.
is there a way to leave it mapped?

---

### Post by conundrumx on 2010-07-29
You could add it as a login item.  (System Preferences, Accounts)

---

