---
title: "Dual Boot / VMWare"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-06-07
Hello and thanks in advance.

I have the following setup

1 Hard drive w/ dual boot between win xp pro and ubuntu 7.  windows is on the first partition. Ubuntu Root is on the next partition, then a partition for swap and the last partition is for /home.

I want to:

Install VMServer in Linux
Use VMConverter to convert the winxp partition to a Virtual Machine. (So I can use both OSes at the same time)

I think I might have a problem with:

XP is install on the boot partition, if I use VMconverter to create a VM, when I try to boot the VM will grub appear and ask if I want to boot into xp or ubuntu? (and fail to boot, I assume?) - Is this a correct assumption?

If I try to 'reclaim' the space from the first partition, that was xp, after I create the VM, won't this overwrite the bootloader and prevent me from booting into ubuntu and thus logically prevent me from starting the VM of XP and so I'm without any OS, again I assume.

Questions:
1.  Can this be done?
2.  Without re-installing either os?

Thanks again.

---

### Post by muguwmp67 on 2007-06-07
I believe that the vmware converter actually creates a second copy of the contents of your windows drive that you can then import into vmware-server/player.  This means that the original windows installation should not be affected in any way.  So you will still be able to dual-boot windows after doing the conversion (changes won't be reflected in VMware though).  

If you want to reclaim the space from your windows installation, you can just repartition/format it (gparted or another partitioner).  After that, edit /boot/grub/menu.1st  to remove the windows boot option.  

Good luck, and be careful!

---

### Post by captlogic on 2007-06-07
Thanks for the reply,
I've backed up all my data, so even if everything goes totally wrong, I'm covered.  (I just hate having to restore from Backup, I'd rather do the research up front and avoid problems later) -(Makes you wonder what I'm doing in the tech industry :p  )

---

### Post by starcraft.man on 2007-06-07
> **captlogic said:**
> Thanks for the reply,
I've backed up all my data, so even if everything goes totally wrong, I'm covered.  (I just hate having to restore from Backup, I'd rather do the research up front and avoid problems later) -(Makes you wonder what I'm doing in the tech industry :p  )

Just a thought, but you may wanna check out [Virtual Box]("http://www.virtualbox.org/") if you want a bit more control over the VM. Server is limited, I'd only recommend VMware for the workstation line which is more powerful. Virtual Box is very good though and at least partially open source. Will give you more options too and version 1.4 can now read VMDK files (Vmware files, I assume thats what converter makes). Just putting choices out there.

---

### Post by captlogic on 2007-06-07
Thanks, the amount of choice in the  *nix environment is a little overwhelming at first, but a welcome change from the M$ world.

---

### Post by starcraft.man on 2007-06-07
> **captlogic said:**
> Thanks, the amount of choice in the  *nix environment is a little overwhelming at first, but a welcome change from the M$ world.

Indeed, [go to this site]("http://linuxappfinder.com/"). Your mind will be blown! :p Great place to see all the choices and see which one you like...

Disclaimer: I take no responsibility for cleaning the mess left after it does blow.

---

