---
title: "How to transfer an existing XP install to VM in Ubuntu?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Crakie on 2007-01-24
I run a dualboot system with XP and Ubuntu.

I succesfully set up a virtual XP install with VMware Server in Ubuntu. From several sources on the internet, I read it was possible to transfer an existing, real install to the VM using NTbackup. So I ran NTbackup on XP (files and systemstate), transfered the backup file to the VM using Samba, ran NTbackup (or rather: NTrestore ;)) in the VM and... got a BSOD upon rebooting.

In hindsight, I am not surprised. After all, the hardware of the real install is completely different than that emulated by VMware. And by restoring the system state, I am restoring all sorts of drivers that are not appropriate. 

So, what IS the right way of going about this, using free software only (as I am aware there are ghost utilities, but they all are commercial)? 

Just to be clear, specifically I am looking to transfer the applications installed on my real XP install to the Ubuntu VM in one go - without actually installing them manually that is. I have a nagging suspicion that if I only restore the files (and not the system state), the files will be there in the VM but they will not work because their registry entries etc. are not entered.

---

### Post by lamego on 2007-01-24
Have you tried to boot into safemode ? Restoring into a different hardware (on this case VM) requires some manual hacking for the drivers.

---

### Post by annda on 2007-01-24
are you transferring the win install from another machine? if so, this will be no help, but still i found the link interesting (even if it's gentoo, but mostly about vmware, not very distro-specific)

[http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm)

hope it has useful info for you. if not, it may help some other people trying to abandon dual booting but not windows itself.

---

### Post by Crakie on 2007-01-24
My first reaction looking at your posts (and the given link) was: argh! This is going to be more complicated than I thought. 

However, there are two elements that look interesting:
1) Booting into safe mode, as suggested by lamego
2) The info in annda's link, which is rather complicated for me but interestingly shows the possibility of creating another hardware profile.

Perhaps it would work to boot into safe mode, create another hardware profile and boot into that. Trouble is, restoring the backup takes an awful lot of time, so I want to as sure as I can get it will work before trying it again (I deleted the VM, unfortunately).

---

