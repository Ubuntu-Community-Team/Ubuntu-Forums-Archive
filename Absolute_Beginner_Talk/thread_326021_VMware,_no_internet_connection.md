---
title: "VMware, no internet connection"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by sleepytom on 2006-12-26
Hi All,

I've got a working virtual machine running Windows XP within my primary OS, Ubuntu Dapper, but I cannot connect to the internet. I have a bridged connection specified, but have also tried NAT. When I power up the VM I get the following error, that I suspect may be related to how I answered all the install options as I initially installed VMware:

Could not open /dev/vmnet0: No such file or directory
Virtual device Ethernet0 will start disconnected.

I am connected via cable modem; no router because I thought that would complicate things.

Can anybody direct me how to get internet established on my VM. 

Thanks a lot!

---

### Post by nyxynyx on 2006-12-26
Not sure if this helps. I used all the default answers and networking worked fine.

---

### Post by sleepytom on 2006-12-27
Can I just reinstall the software (not sure how) or install the missing portion (again, not sure how)?

---

### Post by sleepytom on 2006-12-27
Okay, so I ran the uninstall script, then reinstalled and allowed all the defaults. My previous virtual machine was still available and when I powered it up I did not get the error message anymore. The connection still  failed, though, so I switched the ethernet connection from Bridged to NAT and voila! I'm connected!

---

