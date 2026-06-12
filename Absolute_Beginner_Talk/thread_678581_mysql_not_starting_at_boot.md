---
title: "mysql not starting at boot"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by icceric on 2008-01-26
Hello once again.  

I installed LAMP on my 7.10 installation.  Everything is running good, but today when logging into phpmyadmin, I get the following error...

```
Error #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
```

So, then I just started it manually with 
```
sudo /etc/init.d/mysql start
```
and then everything is fine.

I rebooted a few times to make sure it did it everytime, which it did.

What can I do to autostart it?  I checked my Main Menu > System > Administration > Services and everything mysql is checked. (sorry, I'm sure it's something easy, I'm just somewhat new to Linux)

---

### Post by cmnorton on 2008-01-26
Is there something else that needs to start first on a boot, but has started already by the time you manually start the service?

---

### Post by Iowan on 2008-01-26
Check Main Menu > System >Preferences > Sessions  for Startup Programs.

---

### Post by icceric on 2008-01-26
Thank You both for the replies.

I'm not sure if theres a dependency for mysql that needs to start first or not. ???

Startup Programs under sessions do not say anything about mysql (or apache for that matter, but it is started.), but I can add the command... should I?

---

### Post by Iowan on 2008-01-28
You could check your runlevel, then inspect the rc#.d (# being the runlevel) directory for a S##mysql  file.  If it's not there...

---

### Post by icceric on 2008-01-29
I will check it out, Thank You.

Regards,
Eric

---

### Post by emarkd on 2008-01-29
Try installing startup manager from the repositories.  You should be able to see MySQL from there.  Adding it to your sessions is not a good idea and may not even work because those processes there are owned by you, not the system.

---

### Post by moloth on 2008-07-15
I found that it had a network error that prevented it from starting first time.

cat /var/log/messages | grep mysql

In /etc/mysql/my.cnf I had the following:

bind-address = 127.0.0.1
bind-address = 192.168.0.195

the latter being the one my dhcp server assigned my test server.
However in my /etc/network/interfaces I only had:

auto lo
iface lo inet loopback

No mention of eth0! So in System > Administration > Network
I changed my wired connection from roaming to straight dhcp and MYSql worked on reboot. This is because it changed my /etc/network/interfaces to the following:

auto lo
iface lo inet loopback
iface eth0 inet dhcp

---

