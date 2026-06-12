---
title: "Thinkpad X40 suspend wireless problems"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by dr_d12 on 2007-01-28
Hi,
On a new install of Dapper on my Thinkpad X40, sleep and hibernate do not work as they should.

When desktop re-appears my wireless connection doesn't work. Sometimes it tries to connect, sometimes it says there are no network cards. I'm using network-manager-gnome to allow WPA.

When going into sleep or hibernate, the following error message is flashed:

"nsc-ircc, wrong chip version ff" This error is related to Infrared. I don't need IR so I can disable it completely if it's related to the wireless problem.

How do I get sleep and hibernate to work with wireless?

Where do I start? I'm new to this but I can follow instructions (I got Cisco VPNclient to work!) Thanks for your help,
DD

---

### Post by dr_d12 on 2007-01-29
I got rid of the nsc-ircc error by enabling irda in the system BIOS. Still working on the network problem...
Dave

---

### Post by dr_d12 on 2007-01-30
OK, answering my own message again. This problem already has a Bug number and some possible solutions here:

[https://launchpad.net/ubuntu/+source/network-manager/+bug/40125](https://launchpad.net/ubuntu/+source/network-manager/+bug/40125)

For now, deactivating then reactivating networking in the network-manager applet after wakeup works for suspend (but not for hibernate)...

---

