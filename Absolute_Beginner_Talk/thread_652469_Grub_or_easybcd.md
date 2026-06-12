---
title: "Grub or easybcd?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2007-12-28
I'm about to dual boot my laptop tonight, so I want some advice so this goes smooth.

I've read here [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")
that you should manually adjust the primary partition, install Ubuntu and it will install Grub, and everyone is happy.

I read here [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
to let Vista have the MBR and use EASYBCD - no Grub required?  

What's the correct way so that I have a trouble free install? 

Thanks,
Brian

---

### Post by mejy on 2007-12-28
I haven't actually used Vista recently - I played around with the Beta and didn't like what I saw (it refused to install while I had a linux partition, claiming it was an 'incompatible legacy OS', so I chucked it on and old PC).  However I have heard of Vista messing up peoples' Grub MBRs, so I'd suggest taking the easybcd root here.

---

### Post by Joeb454 on 2007-12-28
I use GRUB, as long as you have free space on the drive it should be ok :)

---

### Post by meierfra on 2007-12-28
> to let Vista have the MBR and use EASYBCD - no Grub required? 


EasyBCD stills requires Grub. Only that Grub isn't  installed on the MBR.

So I would go with Grub. (And  if Grub in the MBR causes a problem, just install  EasyBCD later)

---

### Post by parts-man73 on 2007-12-29
Thanks guys!

I let the Ubuntu install put Grub in the MBR and everything works fine! I now have portable Ubuntu! 

Brian

---

### Post by blueridgedog on 2007-12-29
My opinion is that grub is the way to go, you can edit it (using the boot cd if needed), it is easily configured and can be reinstalled simply.  Not to mention, most of the dual boot/multi boot support you can get here will be grub-centric.

---

