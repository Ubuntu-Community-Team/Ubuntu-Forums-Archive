---
title: "CISCO VPN Client"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by cclliu on 2006-07-12
I am trying to install a CISCO VPN client and it it is looking for the source code.  I searched /usr/bin/src and it is empty.  It needs that to complete the installation.  Where is it located?
Do I have to reinstall?  Did I missed something when I installed the OS?  I downloaded my from this website as an ISO file.

Lawrence

---

### Post by curtisf14 on 2006-07-12
Try this...

```
sudo apt-get install linux-headers-`uname -r`
```

This should install the source headers for your current kernel.  I think that most of the time, this is all you will need.

---

### Post by cclliu on 2006-07-12
Thanks.  Will try it again tonight.

---

### Post by kd7swh on 2006-07-13
I use vnpc for cisco vpn. the kvpnc front-end is nice too. vpnc is easy to use and doesn't require a kernel patch. check it out.

---

### Post by cclliu on 2006-07-13
Can you guide me on what I need to download?

I am new to Linux and have been workin in CPM, VMS, DOS, MVS, OS400, OS2, Windows most of my life.  I just started playing with Linux on Sunday for the 1st time in my life.

I see that it has 15 files and to be placed in different folders.  Do I manually place them in or is there an installer?

Maybe something like Automatix?  I have been spoiled by the world I was in.

---

### Post by chslaxcoach on 2006-07-18
I'm fairly new to Linux as well, but not a total newbie.

After much frustration with Cisco VPN client, I went with vpnc.  That installs easily on Ubuntu with

sudo apt-get install vpnc

You might need to add some repositories to /etc/apt/sources.list, but I don't think so.

Then, I would pretty much follow this how-to:

[http://www.gentoo.org/doc/en/draft/vpnc-howto.xml](http://www.gentoo.org/doc/en/draft/vpnc-howto.xml)

There is a section here on converting your company's Cisco config file (.pcf) and make a vpnc config file (.conf).  

This might be the blind leading the blinder, but I got my stuff to work.

---

