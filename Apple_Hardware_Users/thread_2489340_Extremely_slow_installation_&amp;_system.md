---
title: "Extremely slow installation &amp; system"
date: 2023-07-26
forum: Apple Hardware Users
---

### Post by dake84 on 2023-07-26
Hey guys,

i'm trying to install ubuntu 23.04 on my Macbook Pro 2014. I'm pretty sure I've had it installed before without problems but now I'm stuck.

The live installer (tried 22.04, 23.04, 23.04 legacy installer, and 23.10 daily isos, all the same behavior) runs fine until it starts to work inside the newly installed system. I've run iotop alongside the installer and while copying the ubuntu image it shows a disk write speed up to 150mb/s. When the installer begins "configuring the system" the write speeds fall down to sth. under 1Mb/s like 116K/S or even lower. I ran a complete installation (did take 1,5hrs or longer) and the system was mostly snappy but the same problems while installing software (not the download).
I tried to install the 6.4.6 mainline kernel but it didnt make a difference.
Vanilla OS (ubuntu based) and Fedora both install and run totally fine so it must be an ubuntu quirk.
At boot I get an "ACPI Error: Needed Type [Reference] found [Integer].........." error but I think its unrelated, I get the same message on Vanilla OS wich runs fine.

I really want to install Ubuntu on this system, any help apprechiated :))

/edit SMART values of the drive seem OK

---

### Post by MAFoElffen on 2023-07-26
I have an A1181 MacBook (3,1) 2007... I have it for tests, to make sure my scripts are compliant with Mac hardware. It is running Ubuntu 22.04.2.

I replaced my drive with an SSD and it runs great. My original drive that it came with was 'very slow'. But more important, so is the USB2.0 speed of the USB ports!!! It is a torture. 

The installation process really depends on the USB Flash drive read and write speeds, which doesn't have to do with which Linux distribution you use. If you use a cheap USB2.0 Flash drive, be prepared for a wait. Even though ours is both USB2.0, it does works a bit faster if you use a USB3.x flash drive, as the read speed is higher on the flash storage inside of it.

---

### Post by dake84 on 2023-07-26
Its not the USB Drive (Adata 16Gb USB 3) or the machine's general speed. It has a 250Gb SSD and just installed fedora 38 in under 10 minutes. Debian 12 has the same problems. The copying of the OS image happens reasonably fast but as soon as the installer works inside the new installation (chroot or sth like this) the r/w speeds go to under 1Mb/S (and even if I let the installation finish, the new system behaves the same)

Ubuntu 18.04 installed fine but after updating it it had the same troubles.
Apprechiate the help :)

---

### Post by DuckHook on 2023-07-26
*Thread moved to **(Apple Hardware)** as the more appropriate forum.*

---

