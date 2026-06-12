---
title: "Missing Operating System. Macbook Air 2,1."
date: 2011-03-18
forum: Apple Hardware Users
---

### Post by guy m on 2011-03-18
I had a working triple boot system then Lion was released. Creating a partition for Lion resulted in my knackering Grub so I decided to reinstall Ubuntu from the LiveCD rather than figure out how to fix Grub. Unfortunately now I find when my new Ubuntu install boots I get a message "Missing Operating System".

I have this setup: [http://cl.ly/0u0m1510331E3j3z3f33](http://cl.ly/0u0m1510331E3j3z3f33) 

...and am installing ubuntu onto /dev/sda5, formatting it ext4, mount point /

...and I'm installing grub here:

[http://cl.ly/2t1w0n3L1y0F251a0I1G](http://cl.ly/2t1w0n3L1y0F251a0I1G)

The partition tables are in sync according to Refit and I've tried shutting down, booting into OS X then tried to boot into Ubuntu several times. 

Does anyone know an easy way to fix this? I've tried installing Ubuntu 3 times each with the same result.

---

### Post by guy m on 2011-03-24
Kind of figured out a solution for myself. Rather than going through the install process and installing grub in front of the linux partition, sda5, I installed it before the Windows 7 partition, sda4. After the installation finished Refit displayed both 10.6 & 10.7 OS X icons plus a linux icon. The Windows icon had disappeared. However when I booted off the linux tux grub loaded and gave me the option of booting into either Windows or Ubuntu.

Both boot perfectly.

Problem solved.

---

