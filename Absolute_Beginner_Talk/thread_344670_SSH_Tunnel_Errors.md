---
title: "SSH Tunnel Errors"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by jwtalbot on 2007-01-23
getting access errors when I try to setup an SSH tunnel
I'm using Port 3389 as 22 is blocked, No problem... lets me login on to my linux machine at home ok using the following command...

sudo ssh -L  80:NetgearRouter:8080 Username@RemoteLinuxMachine -p 3389 -C -v

but when I try to access [http://localhost:80](http://localhost:80) from Konqueror or Firefox I get the following error msg... "Connection Refused"  Any help would be great fully appreciated

******************************************************************************

debug1: Local connections to LOCALHOST:80 forwarded to remote address gateway:8080
debug1: Local forwarding listening on 127.0.0.1 port 80.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on ::1 port 80.
debug1: channel 1: new [port listener]
debug1: channel 2: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux Botto 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Jan 23 13:03:35 2007 from 194.176.105.1
jwt@Botto:~$ debug1: Connection to port 80 forwarding to gateway port 8080 requested.
debug1: channel 3: new [direct-tcpip]
channel 3: open failed: connect failed: Connection refused
debug1: channel 3: free: direct-tcpip: listening port 80 for gateway port 8080, connect from ::1 port 36150, nchannels 4
debug1: Connection to port 80 forwarding to gateway port 8080 requested.
debug1: channel 3: new [direct-tcpip]
channel 3: open failed: connect failed: Connection refused
debug1: channel 3: free: direct-tcpip: listening port 80 for gateway port 8080, connect from ::1 port 36151, nchannels 4

*****************************************************************************

---

