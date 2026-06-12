---
title: "[SOLVED] Feisty won't boot!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-06-04
Hi,
I'm running a dual boot system (Ubuntu/WinXP) on an AMD Sempron 3400+ 2gHz.  I had problems with Edgy Eft which a friend solved by setting up a different kernel.  Unfortunately, he was unable (or unwilling) to explain what he did.  When he finished, it "just worked."  Recently, I installed recommended upgrades to Ubuntu, which upgraded my system to Feisty Fawn.  And now, it won't boot and my friend is nowhere to be found.
Here's what happens:  When I try to boot to Ubuntu, I get the Ubuntu logo on a black background with a progress bar below it (splash screen?)  The progress bar shows a tiny sliver of orange, and freezes there.  My GRUB loader gives me several options, the first being kernel 2.6.17-11 generic.  When I try the second option, kernel 2.6.17-11 recovery, I get several pages of text ending with "Begin: Waiting for root file system... ..."  The third option, kernel 2.6.17-10 generic, actually gets me to a login screen.  When I log in, however, I only get as far as a blank tan screen.  Option 4, kernel 2.6.17-10 recovery, gives me a [fail] message after "mount: wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error  In some cases useful info is found in syslog - try dmesg | tail or so"
Needless to say, this is all Greek to me.  At any rate, the last line on the screen is a prompt that looks like this:
root@speedoo-desktop:~#

Typing dmesg | so returns "bash: so: command not found.  dmesg | tail returns 9 lines of code that seem to indicate I have 4 removable scsi disks attached, sda, sdb, sdc & sdd.  I have no scsi disk as far as I know, just a 160GB NTFS for WinXP and the boot system, and an 80GB for Linux (formatted in whatever way Ubuntu does it.)

Is there a known problem with the current linux kernel running on the AMD Sempron processor?  How would I recover the working kernel I was using in Edgy Eft? I thought it was 2.6.17-10, but that no longer seems to work.   WinXP still works fine, but I'm really trying to ditch Microsoft and switch to Linux.  So far, it's been a less than rewarding experience..

Thanks for any help!  Trying to learn this stuff,
Speedoo

---

### Post by phr0ze on 2007-06-04
Since I don't know what your friend has done, I must suggest to do a fresh install of Feisty.

---

### Post by Speedoo on 2007-06-04
Duh!
To quote a popular TV ad, "That was easy."
Thanks, all is well for now.

---

