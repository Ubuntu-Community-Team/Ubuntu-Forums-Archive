---
title: "AD user cannot log on - misconfigured bridge?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by roob_the_doob on 2008-04-10
Hello all,

Here's my problem - I'm hopeful that it's simple-ish to sort out, but I *cannot* find how to do it.  I'm running Gutsy 7.10.

My main user ID logs on to a remote server (probably AD but I'm not 100%).  I've been setting up VirtualBox to run Windows XP on the guest (works OK), and needed to have proper communication over the network (to install Office over the network) - NAT wasn't good enough.  To enable this, I followed the instructions on the [community pages]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03").  But when I rebooted I got the dreaded "no logon servers" message.  It doesn't go away (i.e. waiting doesn't help).

I wondered that my error might have been that I used the "sudo dhclient br0" command, when I should have given a fixed IP address, But it may also/alternatively have been that the bridge didn't get set up properly.

I was going to try and remove the bridge and tap completely, just so I could do some work, but when I log on as admin all the settings look normal, and there is no sign of a bridge or a tap.  etc/network/interfaces says:

> auto lo
iface lo inet loopback

iface eth0 inet static
address xxx
netmask xxx
gateway xxx

auto eth0

How can I remove/correct the settings for the user?  There are so many configuration files that I'm rather lost.

Thanks for your help, folks,

roob

---

