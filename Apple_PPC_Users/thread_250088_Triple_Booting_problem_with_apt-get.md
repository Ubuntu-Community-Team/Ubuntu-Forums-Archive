---
title: "Triple Booting problem with apt-get"
date: 2006-09-03
forum: Apple PPC Users
---

### Post by rscow on 2006-09-03
I'm working on getting my MacBook set up for a triple boot configuration.  I have Mac OS X installed, and have successfully installed Windows XP.  I used  the guides at [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCapmp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCapmp_Ubuntu) and [http:///bin/false.org/?p=17](http:///bin/false.org/?p=17).

I'm at the Ubuntu install phase, now.  When I boot from the Ubuntu Live Cd, I do get into the installer and set up partitions.  As predicted, the installer balks at installing GRUB, but when I click OK, instead of moving on I get the message:  "Installer has Crashed."  and that is it.  

I moved on to the instructions listed in the above links.  I managed to get everything done, up to the point when I try to apt-get and install lilo, etc.  

My apt-get setup (/etc/apt/sources.list) includes all the right repositories, and I updated it, as well, but I get errors with "temporarily unable to contact" such and such a repository.  So, no install.

When I use Synaptic, the files are shown to be installed.

Then, when I get to the point where I am supposed to run lilo, I get a /bash no such file message.

I'm not sure where I have gone wrong.  Should I go back and try to reinstall Ubuntu again?

Thanks.

Roger

---

### Post by rscow on 2006-09-03
Went back and tried it again.  If I sudo  apt-get install lilo lilo-doc linux-686-smp linux-restricted-modules-2.6.15-23-686 linux-kernel-headers

from a NON chrooted terminal, everything works fine.  The repositories are found, and the files download and install.  Of course, this is from the live CD, so it does no good.  

When I try apt-get from a terminal Chrooted into /mnt/Ubuntu then, it won't work.  

I am at a loss.  Any suggestions on where I am going wrong?

RDS

---

### Post by Greywhind on 2006-09-05
You may want to check your network connection... if you can't access the internet when you're about to type apt-get, you need to try resetting and working with the network connection to make it work again before you apt-get.

When I installed Ubuntu a while ago, the first time I tried it I had to do some work to get my network connection (non-wireless) working and then everything went smoothly.

Hope that helps.

---

### Post by rscow on 2006-09-05
I tried again, and finally was able to install via a chroot'd terminal.  I don't know why it finally worked. 

Your suggestion was the right one.

Thanks.

Roger

---

### Post by scloopy on 2006-09-06
I'm having this same problem too. I didn't get any errors when I installed Ubuntu from the LiveCD, but now the network won't work when chrooted. I am connected to the internet. Firefox works and I can install lilo when not chrooted..

I installed to an external firewire drive (dev/sdb1) if that makes any difference.

I've also tried "ifup eth0" and "gksu network-admin" but neither of those work in the chroot terminal..

Any ideas?

---

### Post by Matt Danger on 2006-09-15
I just delt with this problem myself, here's what I came up with:

First make sure DNS is working in your chrooted environment by checking the nameserver in /etc/resolv.conf

If the file does not exist copy it from your non-chrooted environment or edit it to fit your network settings, my looks like:

```
nameserver 10.130.0.50
```

To double check your DNS requests are resolving properly do:

```
host google.com
```

It should resolve some IPs, if it doesn't your DNS is not working properly and thus apt-get won't either.

Now, before you try installing lilo try running:

```
apt-get update
```

Now "apt-get install lilo" should install lilo.

---

