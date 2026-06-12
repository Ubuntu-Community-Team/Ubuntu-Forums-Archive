---
title: "Forwarding Traffic"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Drezard on 2008-03-30
How do I forward traffic through two interfaces?

So like, my current network set up is:

Internet > Modem > eth0 > Ubuntu Server (Want to forward thro this) > eth1 > Internal Network

How do I forward traffic from eth0 to eth1? So, that all my hosts on the internal network can access the internet?

Daniel

---

### Post by jcwmoore on 2008-03-30
> **Drezard said:**
> 
Internet > Modem > eth0 > Ubuntu Server (Want to forward thro this) > eth1 > Internal Network


so where is your router is all of this?  it looks like you are trying to use a server as a router... ideally you should go Internet > Modem > Router > (local devices, i.e. server, printer, scanner, multiple desktops)

---

### Post by Drezard on 2008-03-30
I am trying to use a Server as a Router. I have DHCP and a number of services installed on it. 

How would I do this?

Daniel

---

### Post by rkd on 2008-03-30
I have zero experience with this, but I did a little bit of Google searching and this seems to be something like what you want:

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

It is a Howto for setting up Ubuntu to be a wireless router, but I think you can just ignore the stuff about getting the wireless card working and just follow the steps as if the second interface is another wired ethernet device.

This post

[https://lists.ubuntu.com/archives/ubuntu-bugs/2007-February/409145.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2007-February/409145.html)

describes a bug in one of the settings that the first page tells you to set up.  In /etc/sysctl.conf it says:

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

But the guy has found that just uncommenting this line doesn't work some of the time.  He suggests that you need two lines:

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

to get it to work reliably all of the time.  The Howto in the first page I mentioned suggests that the line should be

net.ipv4.conf.forwarding=1

I don't know whether these are equivalent solutions; you may have to research this a bit more.  Maybe the underlying problem has been fixed by now.

This is an older thread that asks your question:

[http://ubuntuforums.org/showthread.php?t=25813](http://ubuntuforums.org/showthread.php?t=25813)

Posts 6 and 8 suggest some packages to solve the problem.

Finally, here is a Howto that shows how to use webmin to do the job:

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

webmin seems not to be in the Ubuntu repositories (the Howto gives a web site from which to get it). I don't know why it isn't in Ubuntu.

---

### Post by The Cog on 2008-03-30
I find that this entry in /etc/sysctl.conf works reliably:
```
net.ipv4.ip_forward=1
```

You can turn forwarding on without rebooting with this command:
```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

### Post by rkd on 2008-03-30
The approach of editing /etc/sysctl.conf does not require a reboot to turn on forwarding, either.

After modifying /etc/sysctl.conf, you need only run the command:

sysctl -p

and that will put the new settings into effect.  No reboot required.

---

