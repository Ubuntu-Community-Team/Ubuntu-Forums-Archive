---
title: "[SOLVED] Can not bind a port on SSH"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-09-26
Hi all,


  Anyone ever had a problem binding ports trough SSH? I've tried many ports and I get the same problem. 

  I'm using:

```
sudo ssh -v -L 1863:messenger.hotmail.com:1863 user@sever -p 443
```

  And I get:

```
debug1: Authentication succeeded (password).
debug1: Local connections to LOCALHOST:1863 forwarded to remote address messenger.hotmail.com:1863
debug1: Local forwarding listening on 127.0.0.1 port 1863.
bind: Cannot assign requested address
channel_setup_fwd_listener: cannot listen to port: 1863
Could not request local forwarding.
```


Thanks,

Vic.

---

### Post by steve.horsley on 2007-09-26
Maybe the port is already in use. use the command:
**sudo netstat -plnt**
to see.

---

### Post by victorbrca on 2007-09-26
> **steve.horsley said:**
> Maybe the port is already in use. use the command:
**sudo netstat -plnt**
to see.

  I'll try it tomorrow. But I did try many different ports today, like 8080, 80, 8000, 10000, 11863. None of them worked.


Vic.

---

### Post by knowmad on 2007-10-27
Check the loopback device is setup. I have to do ```
ifdown lo
``` and ```
ifup lo
``` to get things working.

---

### Post by sgla1 on 2008-03-03
Here's an added note related to this problem:
On ubuntu gutsy, with NetworkManager controlling networking, I found my /etc/network/interfaces file had been changed from this:
```
# The loopback network interface
auto lo
iface lo inet loopback 
```
to this:
```
 # The loopback network interface
auto lo
#iface lo inet loopback 
```
This prevented the loopback interface from coming up either automagically or with manual activation as other posters suggested.

---

