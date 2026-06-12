---
title: "Using SSH. Can connect by IP but not Name"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-03-14
As mentioned I can connect to my machines by IP address in the command line, but not by name. When I try connecting via the command line I get this:

> user@client:~$ ssh user@server
ssh: server: Name or service not known

Yet when I use Samba in the GUI I can connect by names or by IP. Checking my router it identifies the PC's on the network by name and IP, yet ssh will only play ball with the later.

Any ideas what I'm doing wrong?

---

### Post by kpkeerthi on 2008-03-14
Are you using your router as your DNS server for your network? Does /etc/resolv.conf point to the correct DNS Server?

You may also want to add an entry in your /etc/hosts file mapping the SSH server name and its IP.

---

### Post by HereInOz on 2008-03-14
Unless you have a DNS server which will resolve the host name, or you enter the IP address and the host name in your hosts file, you will not be able to access the machine with its host name.  Remember, Windows works on netbios names, so as soon as you connect a Windows box, the Windows machine will become the browsemaster, and keep a list of all netbios (host) names. Samba will know all about the host names, but that is all.

---

### Post by NeonSamurai on 2008-03-14
Thanks for the quick replies guys.

You've pointed me in the right direction to solve this AND explained why Samba works but command line doesn't. 

Nice one(s).

---

### Post by kesman on 2008-03-14
In my network I have to use
```

ssh user@server.local

```

add .local to the end of the servername for it to work.

---

