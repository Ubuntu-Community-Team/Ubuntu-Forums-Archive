---
title: "VMware Server - Howto Mount Real Partitions"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by AEngineer on 2006-12-29
I've successfully installed Edgy and then VMWare server, and then created an XP VM for the server.  

I've also added the ability to see ext3 systems from within XP (fs-driver.org).

Now I want to see my ext3 partitions from within my XP VM.
I'm attempting to do what it says in the manual: [http://www.vmware.com/pdf/server_vm_manual.pdf](http://www.vmware.com/pdf/server_vm_manual.pdf)

I thought I had it, but going to Virtual Machine Settings when the VM was stopped and then "adding" a new piece of hardware.  I get almost there, but am stopped because I am told that I may not load partitions for /dev/sda because "Permission denied"

I assume this is something to do with Ubuntu not running in SU mode.

Can someone tell me how to get around this.

Jim Mitchell

---

### Post by stalker145 on 2006-12-29
I am assuming that /dev/sda is your physical and internal hard disk...

From what I understand, you can not actually mount your internal disks. You will have to set up file sharing (e.g. samba) to be able to share the disk and it will, technically, be done over the network. <shuffling> I'm sure there's a link here somewhere... ahhh, yes, [this should do...]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

Hopefully this helps. Check back if you need anything else :)

---

### Post by anaconda on 2006-12-29
stalker145 is right. You can't mount internal disks.. and samba is a good solution.

However.. I am lazy, and I use external USB-HD or USB-stick, or DVD:s to move data between virtual machine and ubuntu...

---

### Post by AEngineer on 2006-12-29
Thanks to you both.  I'll pursue the Samba option.  That was on my list of things to do anyway, just further down it.

Jim Mitchell

---

