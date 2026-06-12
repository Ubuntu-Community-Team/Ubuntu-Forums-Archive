---
title: "Keyboard &amp; mouse become unusable after trying ndiswrapper for AirPort on MacBook C2D"
date: 2007-03-24
forum: Apple Intel Users
---

### Post by miguev on 2007-03-24
Hello all,

I have a rather weird post to begin with ;-)

Actually, I have just reported [bug 95376]("https://bugs.launchpad.net/ubuntu/+bug/95376") in launchpad.net but unfortunately the issue doesn't seem to be possible to fix from Ubuntu's side, I have reported it to warn people of what can happen.

No I would like you to tell me if this has already happened to you. And if it has, how have you managed to fix it (if you have).

**Please don't try to reproduce the error, I don't want you to hate me!**

From my experience, this issue seems to me located somewhere in the MacBook C2D firmware, or perhaps in rEFIt, because the only fix I have found is to apply the Mac OS X 10.4.2 update [[http://docs.info.apple.com/article.html?artnum=301722]](http://docs.info.apple.com/article.html?artnum=301722]), which updates the firmwares and disables rEFIt.

To reproduce this issue:
1. Install Ubuntu or Kubuntu (6.04 or 6.10) in a MacBook using LILO for booting (not tested in Grub because root partition is /dev/sda5)
2. Optionally, because makes no difference, upgrade your kernel (tested with last kernel in Ubuntu 6.10 and kernel 2.6.20.3 from kernel.org, making sure you enable ATA and ATA_PIIX for kernel 2.6.20.3)
3. Install ndiswrapper from source (v1.39) or from Ubuntu 6.10 repository --ndiswrapper version also makes no difference.
4. Install the Windows driver from [ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7iwc21ww.exe](ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7iwc21ww.exe) by uncompressing it and doing ndiswrapper -i WINXP_2K/NET5416.INF and modprobe ndiswrapper.
5. Reboot to see the efect, although the kernel 2.6.20.3 will not boot.
5.a. If using kernel 2.6.20.3, reboot with previous kernel, uninstall kernel-image-2.6.20.3, uninstall ndiswrapper (make uninstall from its sources) and make sure to delete ndiswrapper.ko (/lib/modules/<version>/misc). Reboot, it should boot now.

Now we are there. Try to use the integrated keyboard in LILO and you will not be able to do anything. Try with an external USB keyboard and you will be able to use it if *and only if* you plug it in the second USB port (the one nearest to the Shift key).
When you boot the system and GDM or KDM starts, try to use the touchpad or any external USB mouse. Except with an external mouse in the second USB port, the cursor will move weirdly, as it were only receiving a small percentage of the signals. Same issue with keyboard, half of the keys you press will be lost, the other half may be randomly repeated. The effect makes it unusable, this is the same sentence using the integrated keyboard:

Thecmasii uunnssbb,,hhsstthh aaee sseeeeee uussiing ttetkebrd.
T efmae tusabl,tthhii eemmsseeeeee hhtteedd keeyybb.
Thffeecc mmiusaabbee, ts h ssaammeuitinrtedebrd

The efffffffffect iss stiilll vverryy nnaasstt iiffyyuu ttyyppee sslloowwllyy nntt ttoo mmii kkyysttrrooeess, yoo wwillllllll ssttillllllllmiis them or getthem repeated.

I mean, the effect is still very nasty if you type slowly not to miss keystrokes, you will still miss them or get them repeated.

This happened to me one, just after trying to make the C2D Airport work with ndiswrapper, and then I was depressed until I updated Mac OS X. The updated make me reinstall rEFIt and Ubuntu, everything worked very fine until I tried again to make the C2D Airport work with ndiswrapper.

Of course, every external keyboard and mouse, plus the integrated ones, work perfectly in Mac OS X. This is why I think the problem is somewhere between the MacBook firmware but it is the ndiswrapper (plus the Airport windows driver) what makes make issue arise.

Any troubleshooting advise will be appreciated and probaby performed, because apparently the only way to reflash the MacBook firmware is erasing the whole hard drive and reinstalling Mac OS X from its DVD, which is not an option.

Thanks a lot for your support.

---

