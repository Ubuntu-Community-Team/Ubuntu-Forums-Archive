---
title: "apt-get/ synaptic problem.."
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-08-20
Hello all,
Some time back, i decided to install msttcorefonts..the Microsoft fonts..Something went wrong during the download process, and the package was not installed.
But everytime i install a new package, after the package is installed, apt-get/synaptic move on to installing the msttcorefonts package- which i do not want. I dont want to install those fonts now. So i ctrl+Z the installation process.
But now, it is saying that i will have to run dpkg --configure -a to install anything else. But the problem is that the above command is determined to install those fonts!
How do i tell apt/synaptic: i dont want to install those bloody fonts! 

Thanks in advance

---

### Post by foolsh on 2006-08-20
sudo apt-get remove msttcorefonts
 i think should work

---

