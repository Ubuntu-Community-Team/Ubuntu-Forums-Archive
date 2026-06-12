---
title: "Cisco VPN needs to be reinstalled after every Kernel update"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by doug4641 on 2006-07-14
Hello,
I have installed Cisco's VPN client and followed all the instructions and it worked properly, that is, until I updated my kernel to the newest release just the other day. It seems this is common only to this software and not others. When I try to run the vpn from the command line I get an error saying that it could find the necessary files that are needed to run. The files that it says are missing are in the previous kernel and not the new kernel. Can anyone tell me how to make this migration automated between kernel releases so I don't have to reinstall this software after every kernel update?

Any help would be greatly appreciated!

Regards,
Doug

---

### Post by clauder357 on 2006-07-15
HEllO

This morning I had to connect to the office VERY urgently. 2 hours later I was still struggling with my cisco connection. I knew I had to reinstall the Cisco client after this week's major upgrade, so merrily I go, I got this stupid mesage I recognized from a post somewhere else:

> Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.10-5-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)


I followed this advice and got it working:

In a nutshel, it goes like this:
You need :
- the new source
- the new headers
- build-essentials
then all you have type on the command line is 

**sudo /location/of/your/vpn_install/file/./vpn_install **


That's how I got the damn thing going again.
In case I missed something, here is the text that helped me:


> to all those trying to compile this module, here are a couple of pointers:

get all the build tools using:
sudo apt-get install build-essential
this will install the compiler suite and other build tools.

get the "appropriate" kernel headers:
uname -r
will list the kernel version that you're running. go to synaptic and pull the appropriate header in. i think apt-getting linux-headers-<386/686> would pull in appropriate headers if you had installed the kernel via linux-<386/686> virtual package, i'm not sure. the module version mismatch happens when you compile a module against a different kenel-headers that doesn't match with the one that you're running.


hope this helps. I've been leeching thsi board for months, it feels good to contribute.:)

The nick of the person who helped me is **venkatu** thanks!

---

### Post by stillingen on 2006-07-21
Have any of you had issues with the Cisco VPN client causing system crash?
I'm using Cisco vpn client version 4.8.00.0490. Which version are you using?

---

