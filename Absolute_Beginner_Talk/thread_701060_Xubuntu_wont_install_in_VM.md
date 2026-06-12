---
title: "Xubuntu wont install in VM"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by radiocognition on 2008-02-18
Hey Everybody,

I have finally persuaded my girlfriend to switch to Linux.  We plan to install xubuntu 7.10 on her old laptop, but before I did that for her, I wanted to see if I could configure it for her without too much hassle.  I decided to practice the install on a virtual machine run in VirtualBox OSE, the only VM that runs on my architecture on my own Ubuntu install.  I downloaded the Xubuntu i386.iso and verified it with an md5 checksum.  Using the VM program, I mounted the ISO as a virtual CD on the virtual machine and booted into the Xubuntu live session (this method allowed me to successfully install a windows VM).  I ran the graphical installer, and began my installation.

Twice now, when the install bar reads 82% and gives the message "configuring apt", the install hangs for fifteen minutes or more, then abruptly closes without an error message.  Rebooting the VM leaves me a blank screen and not a trace of the Xubuntu install.

What Gives?

---

### Post by amingv on 2008-02-19
I do not know what might be causing that; but as for virtual machines I've always had better luck with the alternate install CD. It might be worth a shot...
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/7.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/7.10/release/)

---

### Post by dcstar on 2008-02-19
> **radiocognition said:**
> 
...........
Twice now, when the install bar reads 82% and gives the message "configuring apt", the install hangs for fifteen minutes or more, then abruptly closes without an error message.  Rebooting the VM leaves me a blank screen and not a trace of the Xubuntu install.


I have had no trouble installing any Ubuntu distro in VMware server.

There is a separate Virtualization forum, post these questions there.

---

### Post by radiocognition on 2008-02-20
Right thanks for letting me know about the other Virtualization forum - and I am trying the alternate install now.

---

### Post by radiocognition on 2008-02-23
Her install ran without a hitch, I just dont know If we like the xfce system . . .  regardless we have another convert

---

### Post by dcstar on 2008-02-23
> **radiocognition said:**
> Her install ran without a hitch, I just dont know If we like the xfce system . . .  regardless we have another convert

Just install a different desktop - there are options available in the package manager.

---

### Post by oh_yes on 2008-03-17
Hi, I have the same problem when I try install Kubuntu 7.10 in WinXP. 
My solution is to disable network adapter in VirtualBox, after that the installation continue successfully. Looks like at that time Kubuntu is trying to access its repository.

---

