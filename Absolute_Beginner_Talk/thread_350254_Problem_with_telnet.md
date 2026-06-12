---
title: "Problem with telnet"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by jimmy85 on 2007-01-31
This is my problem:
 
 jaume@labxarxes11:~$ telnet 172.28.1.11 80
 Trying 172.28.1.11...
 telnet: Unable to connect to remote host: Connection refused
 
 I can't connect with another PC unless they are connected by ethernet hub.
 I don't know why?

---

### Post by Preserved Killick on 2007-01-31
I tried to telnet to that site and got no message at all-- and no connection.  I also tried to ping it and got no pings back.  Is the site address correct?  Is the site up and running as far as you know?

-- Killick

---

### Post by jimmy85 on 2007-01-31
This host is a host which is connected in a ethernet LAN in my university is near than the PC where I write the telnet comand.

---

### Post by Nik_Doof on 2007-01-31
> **Preserved Killick said:**
> I tried to telnet to that site and got no message at all-- and no connection.  I also tried to ping it and got no pings back.  Is the site address correct?  Is the site up and running as far as you know?

172.*.*.* is a private non-routable subnet, much like 10.* and 192.168.*

Also, its connection refused. To me that means the service is not running on the computer. If it wasn't routable then you'd get a timeout.

---

### Post by Brunellus on 2007-01-31
> **Nik_Doof said:**
> 172.*.*.* is a private non-routable subnet, much like 10.* and 192.168.*

Also, its connection refused. To me that means the service is not running on the computer. If it wasn't routable then you'd get a timeout.
I agree with this post.  the host OP is trying to reach by telnet isn't listening for telnet connections.

---

### Post by chipmonk010 on 2007-01-31
might try:

telnet 172.28.1.11 25

I believe by default telnet listens on port 25 so perhaps the above will work otherwise you need to find out what port it is listening on.

---

