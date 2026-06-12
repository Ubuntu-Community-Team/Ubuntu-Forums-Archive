---
title: "Help with Ubuntu Server setup Macbook Pro Late 2013"
date: 2019-06-21
forum: Apple Hardware Users
---

### Post by alissals96 on 2019-06-21
I have a late 2013 Macbook Pro with Marjovi as the current macOS platform.

I was going to use it as a server due to it's high processing power via an Intel I7 CPU and 16 GB RAM.

The problem is I am trying to install Ubuntu Server on the machine but it's basically blocking me from doing it. I tried everything and can't seem to get the server installed, all I get is a GRUB Command Line which doesn't allow me to install anything.

I tried installing Ubuntu Desktop and that works perfectly so why can't I install Ubuntu Server. I also searched everywhere on Google and can't find much for Ubuntu Server but a lot for Ubuntu Desktop on Mac.

Can someone help me with this problem?

For now, I reverted all partitions back to the original setup of just macOS until I can get some proper instructions.

Thanks

Alissa

---

### Post by TheFu on 2019-06-21
I don't know anything about Apple hardware. Sorry, but ... 

The "Server" installer doesn't include many drivers that the "desktop" releases do include.
You can fight to have "Server" installed if you prefer or just install a very light desktop and remove the GUI stuff immediately.  Install whatever server packages you like. They all work.  The kernel is the same.

If you really want to install the Server, I'd install the desktop variant and make a list of all the drivers the desktop version used, then be prepared to manually install each of those into the server.

But with a Core i7, why not just use virtual machines for the server stuff?  You'll keep the different services segregated, which is a best practice, and be able to run ... er at least 16 different services in different VMs.  

If you want to try out LXD containers, then you might be able to get 10x that service density because containers are so much more efficient. Of course, there is some higher risks in using Containers, since the security maturity isn't as high.

Both VMs and Containers can be run on either the desktop or server releases.

---

### Post by wildmanne39 on 2019-06-21
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by alissals96 on 2019-06-21
Thank you for the advice, if I ran the desktop version and got rid of the GUI, will that still work as Ubuntu Server?

---

### Post by TheFu on 2019-06-22
> **alissals96 said:**
> Thank you for the advice, if I ran the desktop version and got rid of the GUI, will that still work as Ubuntu Server?

Some things will be a little different, but all the services you hope to run won't be any different.  For example, desktop version comes with bluetooth. I don't think the server version does.  Remove the bluetooth stuff and that doesn't make it "server", but in Linux, any package desktop/server can be installed on either. Doesn't matter. They all work.  There are millions of desktop install running web and mariaDB servers right now.  For a home environment, it doesn't matter.

But if you really want a server install, then use a virtual machine.  Mac hardware is a little funky already. If some Apple guru doesn't post the sort of instructions you want, and you aren't inclined to figure it out yourself, that's the only way I know to get an actual server install.  Most Linux servers run in a virtual machine in this world.  I have 2 physical installations, but run about 25 VMs.  That's pretty common.  Every VPS is a virtual machine too.  VMs let us abstract away the actual hardware.  If you aren't running geospacial workloads on your laptop (or something like that), I'd use a virtual machine.

If you want a stable hypervisor, then KVM is what I'd strongly recommend. It is Linux/x64 only. No 32-bit. It won't run on any other OSes. Works on both linux servers and desktops.  My experiences with most of the hypervisors out there all had stability issues, except KVM. KVM is rock solid. It stays up until I bring it down.  KVM is more flexible than the commercial hypervisors and faster than them all, IME.  I use a separate workstation to manage my KVM VMs with a GUI - virt-manager.  This is basically the same type of GUI that all the other hypervisors have, but it runs remotely, over an ssh tunnel, to the hypervisor. It doesn't require root on the hypervisor and provides console access the 1 time a year we need it. Very handy.

If you need only 1 server application running, say nginx, then I'd use a Linux container.  Containers are 10-100x lighter than full virtual machines.  Linux containers work on any Linux - platform independent - so ARM, Intel, MIPS, PowerPC, whatever, the CPU doesn't matter.  Canonical's LXD is light like a container, but can be treated like a VM, if you don't want to have the added full protection that a VM provides.

---

### Post by timmnoll on 2019-09-18
Thanks for help!

---

