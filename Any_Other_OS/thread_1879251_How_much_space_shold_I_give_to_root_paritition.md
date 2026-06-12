---
title: "How much space shold I give to root paritition"
date: 2011-11-11
forum: Any Other OS
---

### Post by tech291083 on 2011-11-11
Hi,


My hard disk is only 80 GB and I have 3 OS installed as per the image attached to this thread. They have been installed in the same order as described below. I am actually triple-booting without any problem as of now.


1. Windows XP Professional (NTFS, 16 GB)
2. Fedora 14 (LVM, 27 GB)
3. Ubuntu 10.10 (Extended partition, 37 GB)


Windows here is not that I am going to need much to store my data etc. I need to learn both Fedora 14 and Ubuntu 10.10 by installing various programs on them as root user. I am the only user of the pc so nothing to worry about other users. I have installed some programs as root in Fedora and since I have kept the root partition only 5 Gb (and /home partition 20 GB) I am now getting an error showing space problem, low disk space. I think I made a mistake when installing Fedora by thinking that programs installed are saved in the /home directory. I have also made the same mistake when installing Ubuntu by giving 5 GB to root and 30 GB to /home partition. In short, I have given little space (5 GB only) to the /root partition and more space to the /home partition when installing both Fedora and Ubuntu. Now I am downloading the latest Fedora 16 and Ubuntu 11.10 and would love to keep the /root partition of such as a size in both the OS (Fedora 16 and Ubuntu 11.10) so that I can install various programs as root (in both the OS) and learn them. Is my thinking right that I should give more space to the /root partition next time? Am I right that if I install programs as root only then they are going to be saved in the /root partition only and not the /home partition? Please clear my doubts and do suggest me a rough plan as to how much I should give to each of the 3 OS next time? Thanks a lot.

---

### Post by mips on 2011-11-11
I suggest you fire up gparted and reduce your home partitions by 5GB and increase the / partition to 10GB on both. 10GB is plenty for /

You will have to boot into one distro and then resize the other distro, reboot into the distro you just changed the partition sizes of and then resize the alternate distro. Or you can do both at the same time from a live cd.

10GB should be fine for / but if you plan on installing plenty of apps maybe go a bit bigger, say 12-15GB. I've never gone over about 8GB for /.

Alternatively you can clean out your package cache to free up some space if you don't need the packages in cache anymore.

---

### Post by tech291083 on 2011-11-11
> **mips said:**
> I suggest you fire up gparted and reduce your home partitions by 5GB and increase the / partition to 10GB on both. 10GB is plenty for /

You will have to boot into one distro and then resize the other distro, reboot into the distro you just changed the partition sizes of and then resize the alternate distro. Or you can do both at the same time from a live cd.



First of all thanks. Yes, I agree with your opinion that 10-12 Gb is enough for root. But here I am in a bigger mess despite having used GParted Live CD successfully in the past and the reason is that Fedora is on LVM partition and if I am correct, then it does not deal with LVM resizing. Is there any other GUI tool that I can use to resize/expand the LVM in Fedora? I have tried using command such as lvm and resize2fs etc by opening a terminal in Fedora after booting off a Fedora DVD, but due to my lack of experience I have failed to achieve things ie reducing the /home partition and increasing the root partition and thus I am thinking that reinstalling all the 3 OS with more space for the root partition in mind (for both Fedora and Ubuntu) this time with Fedora 16 replacing Fedora 14 and Ubuntu 11.10 replacing Ubuntu 10.10. Please suggest me something, thanks a lot. Any help is appreciated.

Fedora 14 is soon going to be reaching its end of life stage and thus there will not be any update available for it and I will have no option left but to install the latest version ie Fedora 14 released this month only.

---

### Post by mips on 2011-11-11
[http://www.google.co.za/search?gcx=w&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=LVM+gui](http://www.google.co.za/search?gcx=w&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=LVM+gui)
[http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/all-pages.html](http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/all-pages.html)

---

