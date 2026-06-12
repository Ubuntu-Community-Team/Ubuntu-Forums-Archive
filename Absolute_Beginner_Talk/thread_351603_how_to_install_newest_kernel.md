---
title: "how to install newest kernel"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-02
I would like to use the apt command because I am not a kernel compiler yet. What commands do I use to get the newest smp kernel for 386?

---

### Post by Bachstelze on 2007-02-02
Short answer : you don't.

Long answer : Ubuntu is a release-based distro, it means that when a release is out, the main components of the system (including the kernel) will remain the same until the next release.

---

### Post by 67GTA on 2007-02-02
I missed that bit of information. I wanted to make the best of my dual cpu's. Maybe next release:(  Thank you.

---

### Post by Tomosaur on 2007-02-02
If your kernel has 'generic' in it, then it's the SMP kernel. The Ubuntu devs changed the name.

---

### Post by Bachstelze on 2007-02-02
> **Tomosaur said:**
> If your kernel has 'generic' in it, then it's the SMP kernel. 

In Edgy. In Dapper, the SMP kernel is *linux-686-smp*, so to install it you can run

```
sudo apt-get install linux-686-smp
```

but it won't give you a newer kernel, it will install the same kernel (2.6.15) but with SMP support. If you're running Edgy and for some reason you have the 386 (non-SMP) kernel, you can install the "generic" kernel, which has SMP support, with 

```
sudo apt-get install linux-generic
```

---

### Post by 67GTA on 2007-02-02
At the Grub menu it has 2.16 (default), and Linux Generic. I will try the generic and see if it is any faster. Thanks for the info.

---

