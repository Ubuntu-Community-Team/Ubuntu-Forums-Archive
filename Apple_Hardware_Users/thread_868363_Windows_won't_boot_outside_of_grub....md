---
title: "Windows won't boot outside of grub..."
date: 2008-07-23
forum: Apple Hardware Users
---

### Post by kdb424 on 2008-07-23
I have a macbook pro 3rd gen that I use, with Mac OS X Leopard, Windows XP (Bootcamped), and Ubuntu linux. When I installed ubuntu, I could still boot from the rEFIt boot menu into windows, but after an update, now I can only boot into windows from the grub boot loader, where as before, I could boot either way. Any ideas?

Another problem is that windows will no longer start in VMware fusion. It says no operating system found. I was also wondering if I could boot my Ubuntu partition in VMware fusion like I did before (hack).

Nothing is actually broke here, except little annoyances, because I can still use all 3 operating systems, but I'd like to get it all fixed. Thanks.

---

### Post by cyberdork33 on 2008-07-24
> **kdb424 said:**
> I have a macbook pro 3rd gen that I use, with Mac OS X Leopard, Windows XP (Bootcamped), and Ubuntu linux. When I installed ubuntu, I could still boot from the rEFIt boot menu into windows, but after an update, now I can only boot into windows from the grub boot loader, where as before, I could boot either way. Any ideas?Windows' bootloader gets installed onto the MBR. By default, Ubuntu installs grub to the MBR as well, overwriting your windows bootloader. Normally this is OK as you would want the grub menu to choose between windows or ubuntu on startup, but on the Mac we have a little different situation with EFI and rEFIt. IDK why this changed for you all the sudden, but it sounds like this is the issue.

[LIST=1]
[*]Boot into Ubuntu and install grub onto the Ubuntu root partition. [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)
[*]Then boot from the Windows Recovery Console (on the Install disc) and use the FIXMBR command to repair the windows bootloader.
[*]after you reboot, you should get all three OS options in rEFIt and choosing Windows will boot directly into windows, choosing Linux will boot into GRUB.
[/LIST]
> **kdb424 said:**
> Another problem is that windows will no longer start in VMware fusion. It says no operating system found. I was also wondering if I could boot my Ubuntu partition in VMware fusion like I did before (hack).
You will probably get better help in the virtualization forum, or from VMWare support. If you get everything figured out on how to do this, please share and I will link to it in the FAQ.

---

### Post by kdb424 on 2008-07-24
I found some guides on the net for just ubuntu, but that was with a dual boot. I'm workin on it. I had grub installed on the linux partition, and now I'll do that fix the windows thing. Thanks!

---

### Post by kdb424 on 2008-07-25
Sorry for the double post, bbut now I have a bigger problem. When I boot from the linux drive I get the grub boot loader, which is good. But when I boot the windows partition, I get grub also. So I can't boot into windows XP because it loads the same grub boot loader that was on the linux partition. If I edit one, they both get modified. (BTW, I did the FIXMBR, and I think that is what caused it.)

---

### Post by cyberdork33 on 2008-07-25
> **kdb424 said:**
> Sorry for the double post, bbut now I have a bigger problem. When I boot from the linux drive I get the grub boot loader, which is good. But when I boot the windows partition, I get grub also. So I can't boot into windows XP because it loads the same grub boot loader that was on the linux partition. If I edit one, they both get modified. (BTW, I did the FIXMBR, and I think that is what caused it.)
It sounds like you have GRUB on both the MBR and on the Ubutnu root partition now. FIXMBR should copy over the install in the MBR. I don't know why else you would get that problem.

---

### Post by kdb424 on 2008-07-25
I tried FIXMBR again, and still nothing. I have no idea why this would happen.

---

