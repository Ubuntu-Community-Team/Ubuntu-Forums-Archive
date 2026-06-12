---
title: "XP Installed fine; Ubuntu now missing from rEFIt"
date: 2007-11-05
forum: Apple Intel Users
---

### Post by BarcSsarc on 2007-11-05
Got a new Macbook Pro.
Firstly, partitioned hard drive into:
Mac HD:70GB (I resized this down, then added the others)
WINDOWS:23GB
LINUX:23GB
SHARED:70GB (MS-DOS file format, for multi-OS data (music, etc))
Secondly, manually upgraded to Leopard.
Installed rEFIt,
Installed Ubuntu, configured it to general usability

At this point, everything seemed to be working fine.  Computer booted into rEFIt, where I could choose OS, Mac OSX being default (left option).

I rebooted to the XP CD and ran the install.  I told XP to install to WINDOWS(23GB,seen as D: ).  Everything seemed to work smoothly and I now have XP installed.

The verdict:
1.XP installed the boot loader on SHARED(70GB, seen as C: )
-this is fine, I guess.  I can work around that.
2.rEFIt no longer sees Ubuntu;  it has gone missing!

*****
My question is, how do I reconfigure rEFIt to show Ubuntu?

Any help is greatly appreciated.  I tried to find other posts about this before adding to forum clutter, so apologies if my failure was personal!

---

### Post by cyberdork33 on 2007-11-05
> **BarcSsarc said:**
> Got a new Macbook Pro.
Firstly, partitioned hard drive into:
Mac HD:70GB (I resized this down, then added the others)
WINDOWS:23GB
LINUX:23GB
SHARED:70GB (MS-DOS file format, for multi-OS data (music, etc))
Secondly, manually upgraded to Leopard.
Installed rEFIt,
Installed Ubuntu, configured it to general usability

At this point, everything seemed to be working fine.  Computer booted into rEFIt, where I could choose OS, Mac OSX being default (left option).

I rebooted to the XP CD and ran the install.  I told XP to install to WINDOWS(23GB,seen as D: ).  Everything seemed to work smoothly and I now have XP installed.

The verdict:
1.XP installed the boot loader on SHARED(70GB, seen as C: )
-this is fine, I guess.  I can work around that.
2.rEFIt no longer sees Ubuntu;  it has gone missing!

*****
My question is, how do I reconfigure rEFIt to show Ubuntu?

Any help is greatly appreciated.  I tried to find other posts about this before adding to forum clutter, so apologies if my failure was personal!

You likely replaced Grub with the Windows bootloader. You should install grub to the Ubuntu partition.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

---

### Post by cuvtixo on 2007-11-05
Boot into OS X and run an app called Partition Inspector.  This app automatically attempts to reconcile the entries in the GPT and entries in the MBR. If that doesn't work ... I'm not sure...I don't even know if its a pseudo-master boot record or what the hybrid entries are? The rEFIt site might have more on the particulars of its functioning- but I don't understand it.  OSX and WIN SP2 and above understand the GPT partitions, but Linux doesn't (yet?)  So the rEFIt has to find and boot Ubuntu on the MBRecord for booting.  
In fact- if there are newbie GUI  tools for configuring EFI and dealing with the hybrid format from linux I'd like to hear about it!

---

### Post by cyberdork33 on 2007-11-05
> **cuvtixo said:**
> OSX and WIN SP2 and above understand the GPT partitions, but Linux doesn't (yet?)  So the rEFIt has to find and boot Ubuntu on the MBRecord for booting.

This is incorrect. Linux reads GPT just fine. It is windows (ALL versions) that cannot.

---

### Post by cuvtixo on 2007-11-05
> **cyberdork33 said:**
> You likely replaced Grub with the Windows bootloader. You should install grub to the Ubuntu partition.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

This part is very confusing to me.  Can I/Should I use Grub2 (which seems to be named Grub 1.97) or only the original GRUB?  Do I configure GRUB to boot Mac OSX (mach microkernel) and how do I do this?    I found directions for booting alternate linux kernels, but not OS X.  rEFt people seem to be sticking to the original GRUB bootloader- but I don't know why

---

### Post by cyberdork33 on 2007-11-05
> **cuvtixo said:**
> This part is very confusing to me.  Can I/Should I use Grub2 (which seems to be named Grub 1.97) or only the original GRUB?  Do I configure GRUB to boot Mac OSX (mach microkernel) and how do I do this?    I found directions for booting alternate linux kernels, but not OS X.  rEFt people seem to be sticking to the original GRUB bootloader- but I don't know why

Use the normal grub that comes with Ubuntu.

There are still issues with booting directly from EFI (elilo or grub2). This requires a custom kernel anyway, and doesn't yet support 3D graphics.

You do not configure grub for OSX, it boots from EFI (via rEFIt).

---

### Post by BarcSsarc on 2007-11-06
Got it sorted out:

I ended up going with this and it worked like a charm, adding my Ubuntu back into rEFIt.  I'm now totally triple-booting.  Apparently it just needed a quick reconfigure; no reinstall or anything crazy.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Thanks for the responses!

---

### Post by cyberdork33 on 2007-11-06
> **BarcSsarc said:**
> Got it sorted out:

I ended up going with this and it worked like a charm, adding my Ubuntu back into rEFIt.  I'm now totally triple-booting.  Apparently it just needed a quick reconfigure; no reinstall or anything crazy.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Thanks for the responses!
Those are the same instructions I posted. Just from the actual GRUB manual.

---

