---
title: "basic proftpd configuration question"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by John Isner on 2007-02-25
I installed proftpd on an Ubuntu 6.0 system connected to my home network.  I did not modify any of the original /etc/proftpd.conf settings (since everything else I have installed tends to work right out of the box).  However I am unable to ftp from a Windows machine on the same network using graphical clients (WinSCP, FireFTP) or even the Windows command line:

C:\>ftp 192.168.1.104
ftp: connect: Unknown error number

I tried telnetting to port 21

C:\>telnet 192.168.1.104  21
Connecting to 192.168.1.104...Could not open connection to the host on port 21: Connect failed.

As I understand it, proftpd is started by inetd.  /etc/inetd.conf contains one line:

ftp stream tcp nowait root /usr/sbin/tcpd /usr/sbin/proftpd

The tcpd man page talks about the tcpd possibly having being compiled with a "paranoid" option.  I experimented with making an entry in /etc/hosts.allow but it did not have any effect.

I'm sure it's something simple!

---

### Post by houstonbofh on 2007-02-25
I have ProFTPD on many systems with default config, and working fine.  Have you installed any extra security stuff on your box that might be interfering?  Can you ftp from the box to itself on both 127.0.0.1 and the real IP address?

---

### Post by John Isner on 2007-02-25
ftp 127.0.0.1 from the linux machine itself gives
ftp: connect: Connection refused

ftp 168.192.1.104 hangs (ftp doesn't give a prompt) until I ctrl-C it.

I don't have any special security software installed.  In fact, there is nothing special about my installation!

---

### Post by houstonbofh on 2007-02-25
type 'netstat -l' and post the response.  I only need the connections, not the sockets.  The first part like this.
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 localhost:34379         *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN     
udp        0      0 *:xdmcp                 *:*                                
udp        0      0 *:bootpc                *:*                                
Active UNIX domain sockets (only servers)

```

---

### Post by lenny8088 on 2007-05-23
Any resolution of this. I just installed proftpd on a base install server that was allowing me to ftp but now doesn't after the install - gives the same error as above. Dead in the water and wondering what I did wrong.


Minutes later - after a cup of old burnt coffee and struggling with a greenbar printer that decided to wrap itself up like a xmas present - I got it.

In the proftpd configuration screen it asks "Hey do you think this ftp server will be accepting a bajillion requests every hour or is this just kind of a thing you use every now and then?"
In my situation I was thinking.. well... if I am doing a site upload then it will be doing a fair amount of work but not a ton. And if I'm not then it won't be used at all (intranet server). So I choose the "hardly at all" usage profile which is inetd or something. WRONG. Do that and you have to start it (like it says but I'm just a web guy/manager fellow) or it won't work.  Start it? I just want to connect, upload a file and then move on to something else. 

Solution. Go the config. Change the type to "standalone". Restart it and connect.

---

