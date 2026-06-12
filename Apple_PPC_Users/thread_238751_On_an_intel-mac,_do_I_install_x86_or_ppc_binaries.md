---
title: "On an intel-mac, do I install x86 or ppc binaries?"
date: 2006-08-18
forum: Apple PPC Users
---

### Post by ramvi on 2006-08-18
On an intel-mac, do I install x86 or ppc binaries? So, do I install using the ppc-cd or the intel x86-cd? I'm buying a new laptop, and I only buy a mac if it runs x86 :P

---

### Post by APU on 2006-08-18
Use the x86 CD. And you will have to look around the net a bit to learn how to get everything working. But since the new Apple laptops are normal Intel Centrino hardware essentially this should not be much of a problem.

APU

---

### Post by hajk on 2006-08-18
> **APU said:**
> Use the x86 CD. And you will have to look around the net a bit to learn how to get everything working. But since the new Apple laptops are normal Intel Centrino hardware essentially this should not be much of a problem.

APU

Whoa there! Core Duo processor, and the mobo doesn't use BIOS anymore but EFI. One way to proceed is to install the Boot Camp Beta from Apple to make a "Windows partition", then start the Ubuntu liveCD by restarting and holding down the Option key. Once in the installer, you then delete the "Windows partition" and install Ubuntu Linux in the resulting unallocated space. You'll also find that GRUB doesn't work with Boot Camp, so you'll have to use LILO instead, install it in a chroot to the new root partition. Finally, back in OS X, you could download rEFIt from SourceForge and install it to give you a boot menu with OS X and Linux. As the previous poster said, there are more detailed recipes available, such as my own on
[http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk") which just pulls together a lot of info from the forums.

But be aware that some things don't work very well: frequent kernel panics on boot (bug filed), requiring rebooting with the off/on switch; no temperature info with ACPI (bug filed), possibly causing MacBook to run very hot under Ubuntu Linux; and very slow activation of wireless ath0 interface (bug filed), requiring several "sudo ifup ath0" commands.

But otherwise it runs fine.:rolleyes:

---

### Post by APU on 2006-08-18
> **hajk said:**
> Whoa there! Core Duo processor, and the mobo doesn't use BIOS anymore but EFI.....

Yes this is true. But this only means that you will have some troubles installing Ubuntu at the moment. On the other hand all hardware "should" run just fine. And everything that doesn´t right now, will definitly do so in a very short period of time.

And I would also suspect that EFI will not be a big problem anymore very soon because it is really supported and pushed by Intel. The only reason why current non-Apple Intel (Centrino) Notebooks do not use EFI is because Windows XP can´t handle it.

I would definitely look for a MacBook if i had to by a new laptop right now.

APU

---

