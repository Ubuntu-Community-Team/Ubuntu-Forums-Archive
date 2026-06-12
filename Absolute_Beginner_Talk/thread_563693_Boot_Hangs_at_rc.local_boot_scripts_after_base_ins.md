---
title: "Boot Hangs at rc.local boot scripts after base install and reboot"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by bear2 on 2007-09-30
I am a new user trying to get ubuntu-6.06.1-server-amd64 install to work. It completed a base install and rebooted but hangs when it reaches "Running local boot scripts (/etc/rc.local).

I would try something newer, but I had picked this version of Ubuntu to start with because i wanted to get VMware Server running on it, and the 'administration guide for vmware server 1.0' lists 'Ubuntu 6.06' as a supported distribution for a linux host OS. I didnt see any higher versions of it listed as supported yet.

The hardware i am using is
motherboard: MSI K9 Neo V3  (socket am2)
processor: athlon 64X2
hard drive: 80 gb WestergDigital IDE
memory: qty2, DDR2 667 sdram

Any help getting started is greatly appreciated.

---

### Post by overdrank on 2007-09-30
> **bear2 said:**
> I am a new user trying to get ubuntu-6.06.1-server-amd64 install to work. It completed a base install and rebooted but hangs when it reaches "Running local boot scripts (/etc/rc.local).

I would try something newer, but I had picked this version of Ubuntu to start with because i wanted to get VMware Server running on it, and the 'administration guide for vmware server 1.0' lists 'Ubuntu 6.06' as a supported distribution for a linux host OS. I didnt see any higher versions of it listed as supported yet.

The hardware i am using is
motherboard: MSI K9 Neo V3  (socket am2)
processor: athlon 64X2
hard drive: 80 gb WestergDigital IDE
memory: qty2, DDR2 667 sdram

Any help getting started is greatly appreciated.

Hi and welcome, maybe use checksum to verify the cd
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by louieb on 2007-09-30
:lolflag:Its a feature! Press enter to get the login prompt.

---

### Post by overdrank on 2007-09-30
> **louieb said:**
> :lolflag:Its a feature! Press enter to get the login prompt.

Me feel like a   :oops:

---

### Post by bear2 on 2007-09-30
Thanks everyone :)
Appreciate it.

---

### Post by LisaM on 2007-10-19
So what do you do after you get a login prompt?  

Thanks!

---

### Post by bodhi.zazen on 2007-10-19
log in ...

Try : ```
sudo /etc/init.d/gdm start
```

I assume you may have a problem with X (your gui) but we would need to know more information, like videocard, monitor, error message.

---

