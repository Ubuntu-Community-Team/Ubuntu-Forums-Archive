---
title: "Help new user"
date: 2010-03-18
forum: Apple Hardware Users
---

### Post by amcamc on 2010-03-18
Hi,
I just installed Ubunto 10.3 (I think) onto my macbook pro along side the existing operating system. Now I can't load my normal macbook operating system! 
it just stops at "FireWire (OCI) Lucent ID 5901 built in now active, GUID 002b0fffed6357c; max speed s800

What does this mean and how do I fix it?

Thanks

---

### Post by amcamc on 2010-03-18
OK so I tried the turn off turn on trick and now
AppleInelCPUPowerManagement:initialization complete
Still waiting for root device
Still waiting for root device

---

### Post by jamesey on 2010-03-19
> **amcamc said:**
> Hi,
I just installed Ubunto 10.3 (I think) onto my macbook pro along side the existing operating system. Now I can't load my normal macbook operating system! 

Explain the method you used to install ubuntu? 
did you install refit first? 
did you make partitions?

---

### Post by phildini on 2010-03-19
If you have your original Mac OS install disk, you could try doing a repair from that DVD. There are tutorials for MacOS disk repairs online.

Once that's done, look up a tool called rEFIt. Its a replacement boot manager for Mac that makes things easier. Good luck!

---

### Post by jaco223 on 2010-03-28
I would suggest a reinstall, use bootcamp to create your FAT32 and then install Refit 0.14, then insert your ubuntu cd, shutdown the Mac, reboot holding down the "c" key, install, reboot in Mac OSX, restart, go to Refit partition tool, hit "y", shutdown again, start and select the penguin and you should boot into ubuntu.

---

