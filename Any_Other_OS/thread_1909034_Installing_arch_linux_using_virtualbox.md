---
title: "Installing arch linux using virtualbox"
date: 2012-01-14
forum: Any Other OS
---

### Post by anshulfy on 2012-01-14
Hi,

I have my laptop with dual boot Winxp and Ubuntu 10.10. 
I want to try Arch linux without any changes to my system. I am thinking to install it using virtual box on an external 1TB HD, as I have no space left on my laptop for another OS. Is it possible to do so ???

--
Anshul

---

### Post by Elfy on 2012-01-14
Thread moved to Other OS/Distro Talk.

---

### Post by cryptotheslow on 2012-01-14
I see no reason why not - though I've not tried it specifically with Arch any other distro I have tried doesn't seem to care that it's being run in a VM.

Install VirtualBox from the repositories then when creating the VM for the Arch machine simply place its container file in a directory on the external drive.

Then download the Arch core install iso - which can also be saved to the external drive. Finally in VirtualBox look at the settings of the VM and attach the iso file as the CD drive and start the VM up - it should boot from the Arch install iso and away you go.

---

### Post by holycow131415 on 2012-01-14
You really only need 10-15gb hdd space.

Also, i would install virtualbox from [www.virtualbox.org](www.virtualbox.org) as it supports extra features and i think is a newer version.

---

### Post by mips on 2012-01-14
> **anshulfy said:**
> I am thinking to install it using virtual box on an external 1TB HD, as I have no space left on my laptop for another OS. Is it possible to do so ???


Don't see why not as the virtual hdd is just a file that lives on a normal file system and you can specify it's location. It will be slow though if your external drive is USB.

---

### Post by anshulfy on 2012-01-15
Thank you all for reply. I will try doing that :)

---

### Post by anshulfy on 2012-01-15
Hi,
I installed Arch Linux My network settings are not  working.  I have doubt on /etc/hosts settings.
File is as below
---
127.0.0.1   localhost.localdomain   localhost  <hostname>
<static ip addr>   <hostname>.domain.org   <hostname>
----
For above setting I followed the instructions from Arckwiki. Please help me with this.


Thanks,
Anshul

---

### Post by Barrucadu on 2012-01-15
Ensure you are connected to the network and that your resolv.conf is correct.

---

### Post by anshulfy on 2012-01-15
I am connected to network. Its working in Ubuntu. Also my resolv.conf is similar to that in Ubuntu.

---

