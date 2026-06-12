---
title: "simple peer to peer network"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by entropy7 on 2006-06-25
Hi -

i am a networking beginner.  I have two ubuntu 5.10 systems connected by an 8 port switch. I use ifconfig eth0 command to set network ip addresses for each one. i can ping between them so i know that the switch and the cables are OK. they each have a host name and i tried different things in the etc/host file associate the network ip and the hostname. So when i try and use FTP, i get the result:

connect: connection denied

or something like that, that is different from what my UNIX book says should happen. Thanx

---

### Post by digby on 2006-06-25
Do you have an ftp server running on either computer?  In order to properly connect, one client would need to run the client, and the other would need to be running the server.  I *believe* that the ftp server on ubuntu is controlled by inetd.  inetd is a sort of catch-all sever that watches for traffic and opens the appropriate daemon (program) to handle incoming traffic.

I think it would handle most of what you need except for ssh and web traffic.

---

### Post by Apple 101 on 2006-06-25
Why would you be using FTP if all you need is a simple network?  Mounting shares should be enough.

---

### Post by gwm on 2006-07-13
Refer to:

[http://www.ubuntuforums.org/showthread.php?t=134854&highlight=howto%3A+setup+home+network](http://www.ubuntuforums.org/showthread.php?t=134854&highlight=howto%3A+setup+home+network)

This thread contains a helpful and meaningful discussion with practical suggestions too.

:D

---

