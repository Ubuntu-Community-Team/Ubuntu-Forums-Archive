---
title: "Silent Port Blockings"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Qharos on 2008-02-20
I recently set up an apache and telnet host on my computer for private use. This worked fine for some time.

Recently, it's been having issues. Everything is fine after my computer reboots, but after a time it shuts down - none of the outside access works. I can access everything internally through localhost and 127.0.0.1, and it's flawless. Replace it with my IP (which as I said, works just after a reboot), and I get "Failed to connect" (with Firefox). It's as if all ports are suddenly blocked for no apparent reason.

I have access to my router and can ensure that all ports, on that side, are properly forwarded. I really have no idea what this is; I've also tried restarting the apache2 and inetd services, with no luck. 

I don't think it's related to my iptables, but here's the output of "sudo iptables -L" just in case:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

There doesn't seem to be any application or certain activity that causes this to stop working, either. Just suddenly, no access. Any ideas? Thanks for your time.

---

### Post by mattismyname on 2008-02-20
Can't help you with the problem.

But...don't use telnet...it is not secure.  ssh is the currently accepted best way to remotely login.

---

### Post by macogw on 2008-02-20
When you start a service, it's port opens.  Did you start Apache?  What port do you have it configured to use?  As Matt said, use SSH, not Telnet, because Telnet is insecure.  If you install openssh-server, it'll install SSH & SFTP.  Start it with ```
sudo /etc/init.d/sshd
``` if it doesn't start automatically.

---

