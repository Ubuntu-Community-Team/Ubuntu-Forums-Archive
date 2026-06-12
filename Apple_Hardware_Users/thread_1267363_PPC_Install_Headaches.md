---
title: "PPC Install Headaches"
date: 2009-09-15
forum: Apple Hardware Users
---

### Post by Outinthedark on 2009-09-15
I'm not new to Ubuntu in the slightest but this install on a G5 Desktop PPC is just absolutely frustrating the hell out of me. So much I have decided to ask for help :grin:

I have tried both versions of 9.04 release and have successfully been able to launch Ubuntu off a live cd about 2 weeks or so ago. Since then I have finally cleared off and backed up the hard drive for the intended install. Now the live cd wont boot at all. OSX does not recognize it and will constantly eject it upon trying to boot up.

Thought it was the CD so I download a new iso and try again. 3 CD's later still nothing using 2 different types of media using Disk Utility the first time, then toast, then using an entirely different windows machine w/ iso burn. Still no dice, it always will eject.

I try the Alternate cd and I get it to boot first time only to run into "debootstrap error failed to determine the codename for the release" and finding only a bad burn causes this? Still unsure what the actual solution to that issue is but now I cannot even boot that cd and again OSX does not recognize the disk at all.

So I'm now burning 8.04 to see if it is just an issue w/ 9.04 but I cannot even fathom why I was able to 2 short weeks ago and not at all now regardless of how many different ways I burn the disk.

Any help would be greatly appreciated and very much so needed!

[I could not post in the Install forums probably because I registered today]

*Figured I would post this here as well. I see another PPC thread and you guys are suggesting he just go w/ debian. Is that my only option rather than banging my head against a wall w/ the Ubuntu installers?*

---

### Post by sweetleaf on 2009-09-15
> **Outinthedark said:**
> I see another PPC thread and you guys are suggesting he just go w/ debian. Is that my only option rather than banging my head against a wall w/ the Ubuntu installers?*

You could also try Yellow Dog, Fedora (very large installation), or Gentoo (time-consuming). Since you're already familiar with Ubuntu, Debian might be the best bet. 

However, I don't know that there's any particular reason to think that using a different distro will solve your cd-booting woes.

---

### Post by Outinthedark on 2009-09-15
> **sweetleaf said:**
> You could also try Yellow Dog, Fedora (very large installation), or Gentoo (time-consuming). Since you're already familiar with Ubuntu, Debian might be the best bet. 

However, I don't know that there's any particular reason to think that using a different distro will solve your cd-booting woes.

I have a bootable DVD of openSUSE and it works fine and will boot up w/ no issues what so ever. I just really don't know what the problem is w/ these Ubuntu distros. They work once in my system then not at all again.

Do you have a link to Debian's PPC distro? Seems to be a maze to find the download :D

*edit*
Is this the correct one for a G5 PPC? [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/multi-arch/iso-cd/debian-testing-amd64-i386-powerpc-netinst.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/multi-arch/iso-cd/debian-testing-amd64-i386-powerpc-netinst.iso)

---

### Post by oswaldkelso on 2009-09-17
Take your pick
[http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/)

If you have a internet connection you only need CD1 (no name is default gnome) but you have kde CD1 xfce-lxde CD1 net-install or business card install.  Don't worry about the rest. Do a md5sum check.

---

