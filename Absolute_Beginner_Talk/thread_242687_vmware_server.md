---
title: "vmware server"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by fouhay on 2006-08-24
Hi 

I'm pretty sure I've read every thread I can relating to this, but if I've missed something feel free to point me in the right direction

I've installed vmware server on server 6.06

when attempting to create a vm (win2k3) it won't boot from CD. CD is fine (will boot bare metal machine) and the cd is connected for this particular machine (so says the little icon in bottom right)

Seems a simple problem, but i've tried every combination of mount, umount, boot order etc, but the darn thing will just always try to boot from network.

have i missed the bleeding obvious??!?!?:confused:

---

### Post by fouhay on 2006-08-24
Hi

found the solution on the vmware forums

for future reference for other newbies

"legacy emulation" in 

VM Menu
   Removable Devices
      CD-ROM
        Edit

was the key, try turning it on and restarting vm

---

