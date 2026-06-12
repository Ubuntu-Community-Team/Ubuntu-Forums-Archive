---
title: "MBP 5.1, Lion, Headache :("
date: 2012-06-23
forum: Apple Hardware Users
---

### Post by markthekdeguy on 2012-06-23
I was happily triple booting, Snow Leopard, win7, Kubuntu 10.04 last year, without issues. been Linuxing since Redhat 5.1 back in the 90s, so i'm pretty used to installing Linux/Solaris/BSD/Win/QNX etc..

I knew something was wrong when Mac OS failed several times to mount and or burn sucessfully any .iso from Ubuntu.
I had to use another Linux PC to do this. this was noticed with  Mac specific ISO .. what are Canonical thinking ?
its very poor. especially as its less likely to suceed than the regular x64 / i386 .iso's ... maybe its just my MBP 5.1

The MBP 5.1 loves Kubuntu 12.04 when its the only OS on the disc.

Tried all this, didn't work for me on my Macbook Pro 5.1,
during install, it recommended seperate (min 20mb) boot bios-efi thingy, so i did as advised (which it mentioned is not same as a seperate /boot partition) I also made the usual swap, installed grub onto its sdax ext4 partition. 
at reboot, Linux failed.
It failed with the exact same looking error.
 
tried Kubuntu 12.04 Mac .iso ... failed several tries
tried Kubuntu 12.04 x64      ... failed to boot after install.

tried another guide which said run 'sudo grub' off the live CD
it said 'not found' so i installed grub to HD while on live CD, ok, ran sudo update grub, it complained it could not see
'menu.1st, can create one for you y/n ' (or something)
i said yes. it never found the kernel. ran sudo update grub
again, same result, it found memtest++ and menu.1st and that was about it. 
I wondered why prev guide expected grub to be installed & it wasnt, coz so did i. attempted to install grub2, no such package, but it did recommend gub-efi, do i thought 'why not' it installed.
it failed.

I'm not a huge fan of OS X, but i guess i'm going back to Kub 10.04 and letting it update, but this all worked ok alongside Snow Leopard, which leads me to beleive its related to Lion and its evil backup partition :)
Any help / painkillers greatfully received..

Mark

---

