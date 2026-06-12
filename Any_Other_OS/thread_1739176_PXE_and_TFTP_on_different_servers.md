---
title: "PXE and TFTP on different servers"
date: 2011-04-25
forum: Any Other OS
---

### Post by headvampyre@hotmail.co.uk on 2011-04-25
Basically, heres my setup:

Server 2003_R2:
 - Running openThinClient with NFS and TFTP.
 - Samba4 Domain Member.

Ubuntu 10.10(Mint 10):
 - DHCP & PXE (dhcp3-server)
 - Samba4

Aim: 
To configure my Ubuntu machine to pull the files via TFTP from my Windows box. 

Issue:
Everytime i boot, i get an error message saying: 

"pxelinux.cfg/linux could not be found"

then it drops back to the boot prompt. Any way around this? 

Thanks in advance :)

---

### Post by Perfect Storm on 2011-04-25
Moved to Other Os/Distro Talk.

---

