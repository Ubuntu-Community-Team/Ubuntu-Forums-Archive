---
title: "Booting my second desktop Ubuntu from my other (failover) disk..."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by fiprojects on 2008-02-04
I have a nice new HP dv9000 (dv9618ca) laptop that comes with duel 120Gbyte disks. Long story cut short I want to duplicate my current environment on to "the other disk" allowing me to roll back if I install something on one disk that buggers up my environment (my sound broke previous to this and I had to re-install to resolve).

My current setup:

Both my disks are configured exactly the same (sizes and partition numbers) - swap is at /dev/sda1 and /dev/sdb1 and boot and root sit together on /dev/sda2 and /dev/sdb2

Grub has entries allowing me to select from the menu an entry to boot from but by default it boots from /dev/sdb2

I have written a script that mounts /dev/sda2 onto /dev/sdb2 and copies my entire root and boot partition across to the 'other side'

When I try to boot from /dev/sda2 it goes so far and then just halts - even recovery mode fails - sits there looking intelligent but not even a shell prompt.  

When I CTRL+ALT+DEL to a reboot and boot to my default /dev/sdb2 just fine but all attempts to boot from /dev/sda2 fail.

Can one of you fine people advise me what have I missed out on?  UID labels are new to me and I note them in /etc/fstab and grub's menu.lst file and I'm wondering if this might be the problem.

Thanks for reading...

---

### Post by mikewhatever on 2008-02-04
Have you edited the mount points in the fstab of the 'copy' installation? If /dev/sda2 is a new root partition, it must be mounted accordingly in the 'copy' installation.

---

### Post by fiprojects on 2008-03-05
Hi, I just noticed that my mail from ubuntuforums was going into my thunderbird junk folder hence my late reply...

Your suggestion though was spot on - I edited the /etc/fstab on the sceondary disk - it was referencing UUID=[hash] which is totally new to me... 

Why did /etc/fstab have UUID=[some hash] ?  Ii am more used to naming a physical path in there instead... thanks for the help!

---

