---
title: "Server 7.10 hanging during booting"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by dustin_wielenga32 on 2008-02-29
I just installed Ubuntu Server 7.10 on my computer with the specs listed at the bottom.  The installation seemed to go perfectly.  When I boot, it hangs after the following line:

* Running local boot scripts (/etc/rc.local)        [OK]

The first time I started it, it hung at the line after that one, which said something about configuring SAMBA, but when I rebooted, it stopped at the above line.

Any idea what the problem might be?  Thanks in advance.

AMD Athlon XP 3000+ (2.167GHz)
768MB RAM (512+256)
10GB IBM Hard drive
Lite-On DVD-RW
Nvdia FX5200 AGP

---

### Post by taurus on 2008-02-29
Are you trying to mount some windows machine over the network in /etc/fstab?

---

### Post by mrsteveman1 on 2008-02-29
Once you can see the rc.local scripts running root is already mounted, so you likely have logs from the failed boot.

Boot using 'single' as a kernel option and see whats in /var/log/boot and /var/log/messages.

Sounds like xorg isn't starting though, once you can see it running rc.local scripts theres not much left to do.

---

### Post by Dr Small on 2008-02-29
> **mrsteveman1 said:**
> Once you can see the rc.local scripts running root is already mounted, so you likely have logs from the failed boot.

Boot using 'single' as a kernel option and see whats in /var/log/boot and /var/log/messages.

Sounds like xorg isn't starting though, once you can see it running rc.local scripts theres not much left to do.
Xorg should not even have to start, since this is a Server and not a Desktop.

---

### Post by dustin_wielenga32 on 2008-02-29
I think it's fixed, certainly quite strange though.  What happened was it loaded, asked for username and password, and then kept spitting out stuff after that.  So the prompt for username ran by very fast.  I typed in my username and password where it was hung, and it worked fine.  A bug perhaps?

Thanks to all for their thoughts though.

---

### Post by mrsteveman1 on 2008-02-29
Some people do install xorg on servers

Those messages keep coming because the login program runs before the system is done running init stuff, and the messages get printed to the console

---

### Post by dustin_wielenga32 on 2008-03-01
Alright, thanks for the explanation mrsteveman1, now I know things are probably not going to explode on me :)

---

