---
title: "Intel Proset Wireless 3945"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by The55Gon on 2007-02-16
Hi, my wireless doesnt work at all. When i go to the network connections, the wireless doesnt show up. I dont think i have the driver installed, but i dont know where to find it. 

How do i enable wireless/get the driver if its needed? Thanks

---

### Post by Bachstelze on 2007-02-16
Open a terminal and type

```
sudo iwconfig
```

Do you see anything that doesn't say "no wireless extensions" ?

---

### Post by The55Gon on 2007-02-16
this is what it returns:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by Bachstelze on 2007-02-16
The drivers aren't installed then. That's funny, I also have an ipw3945 and it was detected out of the box in Ubuntu. Try doing

```
sudo modprobe ipw3945
```

---

### Post by The55Gon on 2007-02-16
this is what i get

FATAL: Error inserting ipw3945 (/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko): Invalid module format
2007-02-15 22:05:37: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

i think i may have unisntalled it -_- is there a way to reinstall it?

---

### Post by mikewhatever on 2007-02-18
Installing kernel restricted modules solved the wireless issue for me. I wonder if it is yet another HP laptop.

---

### Post by spaceman07 on 2007-02-19
can you please provide more info to how you added the modules to the kernel for a newbie.

---

### Post by mikewhatever on 2007-02-19
First check what kernel you're using, write down the output.
> uname -a

Then, open synaptic and search for 'linux restricted', choose the correct package and install. All that if you have wired internet. If not, the package can be downloaded from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all)
just make sure to pick the same one as the kernel.

Example:
kernel: 2.6.17-11-generic
restricted modules: linux-restricted-modules-2.6.17-11-generic

---

### Post by dphoebus on 2007-03-05
Check this article out....[http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754]("http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754")

hope this helps....

---

### Post by Jamshedk on 2007-03-20
> **mikewhatever said:**
> First check what kernel you're using, write down the output.


Then, open synaptic and search for 'linux restricted', choose the correct package and install. All that if you have wired internet. If not, the package can be downloaded from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all)
just make sure to pick the same one as the kernel.

Example:
kernel: 2.6.17-11-generic
restricted modules: linux-restricted-modules-2.6.17-11-generic


My card only disappears after I install my nvidia drivers, even if I get the restricted module installed, the wireless will work, BUT I have to reinstall the nvidia drivers for the new Kernel and boom once again my wireless card is gone..

HP DV2000 with 7200 nvidia..

---

