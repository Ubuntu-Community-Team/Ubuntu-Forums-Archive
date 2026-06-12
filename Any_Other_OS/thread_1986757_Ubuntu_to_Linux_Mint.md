---
title: "Ubuntu to Linux Mint"
date: 2012-05-25
forum: Any Other OS
---

### Post by pooja on 2012-05-25
Hi everyone,
I'm considering a change to Linux Mint after years with Ubuntu. In the partitioning step of the installation CD I am given a choice for the **boot loader**:
[LIST]
[*]/dev/sda ATA ST9160821A6 (160.0 GB)
[*]/dev/sda1 Windows 7 (loader)
[*]/dev/sda5 Ubuntu 11.10 (11.10)
[*]/dev/sda6
[*]/dev/sda2 Windows Vista (loader)
[/LIST]

My questions are:
[LIST=1]
[*]What should I choose from the drop down menu of the boot loader, if I want Linux Mint in charge of the dual booting process?
[*]Do I need a swap partition for Linux Mint, or is it necessary for Ubuntu only?
[*]How can I get rid of the Windows Vista loader now that I have erased it completely and only use Win7 occasionally?
[/LIST]

---

### Post by darkod on 2012-05-25
If you want Mint in charge, you should select /dev/sda, the MBR of the disk. There should not be any numbers in it.

The Vista loader is reported because some boot files are found there. That could be a recovery partition or similar. It doesn't actually mean it's vista OS.

As long as any boot files can be detected, it will get reported.

Yes, Mint uses a swap partition too, as most linux OSs.

---

### Post by pooja on 2012-05-25
How can I get rid of the Vista partition? I don't need a recovery partition. I don't have a Windows 7 installation CD because I got it through an agreement between my University and Microsoft. Do I have to use some software from within Windows 7 to knock out that section (/dev/sda2)? Will GParted in Win7 work? How do I do it?

---

### Post by howefield on 2012-05-25
Thread moved to "*Other OS/Distro Talk*"

---

### Post by pooja on 2012-05-27
If anyone's having my same troubles, I've made a Live CD of GParted, inserted it in the PC, then rebooted. It immediately loaded from the CD and I was able to format the hard disk. Still kept Vista loader (actually GParted detected it as an HP recovery partition) but resized /dev/sda5 to 20 GB approx. and a linux-swap of 2GB. Will try installing Linux Mint 13 w/ Cinnamon. Keeping my fingers crossed...

---

