---
title: "need help! badly! grub failure"
date: 2009-03-25
forum: Apple Hardware Users
---

### Post by 0ra1suicid3 on 2009-03-25
i have installed ubuntu on my external hd, for testing to see if it work
when i reboot, none of my internal hd (sata) 1tb wich i newly got showed up
when i try to boot from cd and boot from first hard drive on ubuntu live and it give me grub failed to load

what to do! i need my mac os X on my internal hd and i dont want to lose 200G worth of photo and movie and em... other stuff

need help!

---

### Post by cyberdork33 on 2009-03-25
Create a rEFIt CD.
Boot it up.
Use the partition tool to sync the partition tables.

P.S. Booting Ubuntu from the external drive will not work like you are trying to do. You have to use grub-efi.

---

