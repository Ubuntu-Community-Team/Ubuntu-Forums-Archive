---
title: "PCIe SSD CSM Mode"
date: 2018-03-12
forum: Any Other OS
---

### Post by zkab on 2018-03-12
I installed ipfire (Linux based stand-alone firewall) on a computer.
The only storage I have is Samsung EVO 960 (M.2) and I have problem booting after initial installation ... grub rescue.
Got this from ipfire forum:

[I]PCIe attached SSD's are not working in CSM Mode unless they have a extra Bootrom (like the Samsung 960 PRO) that emulate INT13h access.
grub2.00 cannot access this disks directly so it not find the device.[/I]

Since this is more a Linux issue than firewall my question is if there is a workaround for this ?
Appreciate all help ...

---

### Post by oldfred on 2018-03-12
Moved to Other OS since not Ubuntu nor Ubuntu based Linux.

That seems to be more an issue with ipfire as Ubuntu's version of grub2 works with NVMe devices. But have not paid attention if any used the very new NVMe drive with 35 year old BIOS/MBR configuration aka UEFI Compatibility Support Module (CSM)     . 
New systems that support NVMe devices all support UEFI.

Other distributions & hardware also support NVMe.
[https://wiki.archlinux.org/index.php/Solid_State_Drive/NVMe](https://wiki.archlinux.org/index.php/Solid_State_Drive/NVMe)
[https://lenovopress.com/lp0508.pdf](https://lenovopress.com/lp0508.pdf)

---

