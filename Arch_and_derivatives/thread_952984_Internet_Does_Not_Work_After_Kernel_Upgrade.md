---
title: "Internet Does Not Work After Kernel Upgrade"
date: 2008-10-19
forum: Arch and derivatives
---

### Post by Opeth115 on 2008-10-19
Ok well i posted this on the arch forums this morning but i have yet to recieve a reply so i decided to post it in the subforum here =) 

I have been reading all of the other threads and have tried everything possible to downgrade my kernel to 2.6.26 rather then 2.6.27.  I have found a package for kernel 2.6.26.2-1 and nvidia 173.14.12-2 but they do not mix and wont let me start x when i downgrade both of them.  Is there some way i can get past this as not having internet is frustrating =)

Edit:

I have tried using this

```
echo 0 >/proc/sys/net/ipv4/tcp_sack
echo 0 >/proc/sys/net/ipv4/tcp_dsack
```

Edit again:

When downgrading both the kernel and nvidia with those two packages i found, my computer boots up fine up untill i get to the command line to type "startx".  The i get this error message after typing "startx" :


```
Error: API mismatch: the nvidia kernel module has version 173.14.12, but thus nvidia driver component has version 177.80.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

```

After i got this i went and reinstall kernel 2.6.27 and the latest nvidia to look at the nvidia package i had installed.  I extracted it and all the was in it was a hierarchy of folders "/lib/modules/2.6.26-ARCH/kernel/drivers/video/nvidia.ko"  and that nvidia.ko file.  Is it possible that i'm not installing the driver jsut a kernel module?

Also i found a package for nvidia-utils and installed it with nvidia and the kernel and i can "startx", but it freezes everytime and i have to manually restart the computer with the rest button.

---

### Post by handy on 2008-10-19
This bug has caused a lot of us to have to jump through a few hoops.

With the current kernel installed, remove your nvidia drivers, reboot & then reinstall the previous version.

After which the kernel downgrade, as you already know is quite simple.

---

### Post by crimesaucer on 2008-10-19
> **Opeth115 said:**
> Ok well i posted this on the arch forums this morning but i have yet to recieve a reply so i decided to post it in the subforum here =) 

I have been reading all of the other threads and have tried everything possible to downgrade my kernel to 2.6.26 rather then 2.6.27.  I have found a package for kernel 2.6.26.2-1 and nvidia 173.14.12-2 but they do not mix and wont let me start x when i downgrade both of them.  Is there some way i can get past this as not having internet is frustrating =)

Edit:

I have tried using this

```
echo 0 >/proc/sys/net/ipv4/tcp_sack
echo 0 >/proc/sys/net/ipv4/tcp_dsack
```

Edit again:

When downgrading both the kernel and nvidia with those two packages i found, my computer boots up fine up untill i get to the command line to type "startx".  The i get this error message after typing "startx" :


```
Error: API mismatch: the nvidia kernel module has version 173.14.12, but thus nvidia driver component has version 177.80.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

```

After i got this i went and reinstall kernel 2.6.27 and the latest nvidia to look at the nvidia package i had installed.  I extracted it and all the was in it was a hierarchy of folders "/lib/modules/2.6.26-ARCH/kernel/drivers/video/nvidia.ko"  and that nvidia.ko file.  Is it possible that i'm not installing the driver jsut a kernel module?

Also i found a package for nvidia-utils and installed it with nvidia and the kernel and i can "startx", but it freezes everytime and i have to manually restart the computer with the rest button.



If you can't fix it with handys way, you can try to do it this way for the time being:



A way to fix the nvidia issue is to install the NVIDIA driver from the NVIDIA site.


First, pacman the 177.80 nvidia-utils:

```
pacman -S nvidia-utils
```


next, go to this site for x86_64: [http://www.nvidia.com/object/linux_display_amd64_177.80.html](http://www.nvidia.com/object/linux_display_amd64_177.80.html)
or this site for i686: [http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)

and download this x86_64 NVIDIA 177.80 driver: [http://us.download.nvidia.com/XFree86/Linux-x86_64/177.80/NVIDIA-Linux-x86_64-177.80-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/177.80/NVIDIA-Linux-x86_64-177.80-pkg2.run)

or this i686 driver: [http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run)

When you run the NVIDIA installer, it should replace any driver module that you had before from any version number.

So log into a virtual console (tty1) and run this command as root or sudo, in the directory that you downloaded the driver into:

```
sh NVIDIA-Linux-x86_64-177.80-pkg2.run
```

or for i686:

```
sh NVIDIA-Linux-x86-177.80-pkg1.run
``` 



select ok and yes for everything then reboot after it's installed.


As for your kernel, you could always build any of the kernel's from the AUR, or you could even build the stock -ARCH kernel from the ABS, just edit the PKGBUILD to have the old 2.6.26-5 version numbers to it..... basically all it does is download the vanilla kernel from [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/) that matches the version number in your PKGBUILD, patch it with the -ARCH patch that matches the version numbers on your PKGBUILD, and then it builds it, depmods it, and then you just have to install it..... hopefully that will work.


Now. I'm not sure if the old 2.6.26-5 "-ARCH" patch will still be there, but hopefully it will. If that doesn't work, you can try one of the zenmm kernels from the AUR.... they work pretty good, install easily, and it will create a kernel that doesn't replace your -ARCH one, all you have to do is add it on to your /boot/grub/menu.lst and you can use that one while you fix your -ARCH kernel.

---

### Post by handy on 2008-10-20
***@crimesaucer:***  I new you would come through with the detailed explanation. :-)

& they are much appreciated too. :KS

By the way I'm just in the process of learning about ABS, with the intention of submitting the simple but incredibly useful to Mac owners backlight program which allows control of LCD screen brightness, as opposed to fudging it with gamma as I & many/most other Mac users have been doing for some time.

Hopefully it is not beyond my meager Linux based knowledge.

---

### Post by crimesaucer on 2008-10-20
> **handy said:**
> ***@crimesaucer:***  I new you would come through with the detailed explanation. :-)

& they are much appreciated too. :KS

By the way I'm just in the process of learning about ABS, with the intention of submitting the simple but incredibly useful to Mac owners backlight program which allows control of LCD screen brightness, as opposed to fudging it with gamma as I & many/most other Mac users have been doing for some time.

Hopefully it is not beyond my meager Linux based knowledge.

Sounds like a cool thing to do for other mac users. I'm not sure if what I posted would work that well.... I think it should help with the nvidia thing, and I was thinking that the only way to get the old version of the -ARCH 2.6.26-5 kernel (if you don't have one in the cache) would be to build it from source (or have someone with the old 2.6.26-5 i686 or x86_64 .tar.gz package copy it and share it).


I know building a kernel is not everyones favorite thing, but ABS and AUR make it pretty easy to do.

---

### Post by handy on 2008-10-20
***@crimesaucer:*** For future & present reference, do you know where the kernel source can be sourced?

[***_The Linux Kernel Archives_***]("http://www.kernel.org/") have too limited a range to be of any help from my observations.

This kernel bug has certainly taught me to keep a backup of previous packages in case of emergency.  Thankfully I had never cleared the cache.

I would email a copy out, but I think it is just a bit too big for my account at least, without breaking it up into pieces.  You would think that someone would have the previous Arch kernel available.

---

### Post by MisfitI38 on 2008-10-20
Check out [this wiki article.]("http://wiki.archlinux.org/index.php/Downgrade_packages") It includes URLs of repos containing old package versions.
Useful if you cleared you cache at an inopportune time..

---

### Post by handy on 2008-10-20
> **MisfitI38 said:**
> Check out [this wiki article.]("http://wiki.archlinux.org/index.php/Downgrade_packages") It includes URLs of repos containing old package versions.
Useful if you cleared you cache at an inopportune time..

Thanks Misfit138, I checked out the sites on the wiki only two had a previous kernels & the following site had the most recent both 32/64bit which were:

i686/kernel26-2.6.26.2-1-i686.pkg.tar.gz

***_[http://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/](http://ftp.tu-chemnitz.de/pub/linux/sunsite.unc-mirror/distributions/archlinux/)_***

If I ever decide to clear my /pacman/pkg/ it will be carefully hand picked thinning out of the fruits. :-)

---

### Post by Opeth115 on 2008-10-20
Thank you everyone so much for helping me out with this i finally got it sorted after a couple of days without internet thanks to crimesaucer and handy!  I had to use the 2.6.26.2-1 kernel so it's not the last i had installed but my internet is now working =)  Thank you everyone again!

---

### Post by handy on 2008-10-20
> **Opeth115 said:**
> Thank you everyone so much for helping me out with this i finally got it sorted after a couple of days without internet thanks to crimesaucer and handy!  I had to use the 2.6.26.2-1 kernel so it's not the last i had installed but my internet is now working =)  Thank you everyone again!

That's great to hear. :-)

I have just read the bug report here:

***_[http://bugzilla.kernel.org/show_bug.cgi?id=11721](http://bugzilla.kernel.org/show_bug.cgi?id=11721)_***  

& found way down in the read that the following command as root, worked for the poster of the bug on the current kernel:

***_echo 0 > /proc/sys/net/ipv4/tcp_timestamps_***

I have done a yaourt -Syu & tested it & it worked for me too.

You might like to try it, if it doesn't work it is easy to downgrade, now that you have the kernel in your /var/cache/pacman/pkg/

[I]**[Edit:]**
I'll make a new thread on this here & on the Arch forum, which already has valuable information added to the initial post regarding this workaround.[/I]

***_[http://ubuntuforums.org/showthread.php?t=954112](http://ubuntuforums.org/showthread.php?t=954112)_***

---

### Post by crimesaucer on 2008-10-21
> **MisfitI38 said:**
> Check out [this wiki article.]("http://wiki.archlinux.org/index.php/Downgrade_packages") It includes URLs of repos containing old package versions.
Useful if you cleared you cache at an inopportune time..

Thanks, that might be very useful in the future.

---

### Post by handy on 2008-10-21
> **crimesaucer said:**
> Thanks, that might be very useful in the future.

I've just made a simple web site with the intention continually carrying a very recent copy of a known good kernel both 32/64bit.

I'm sure the list will grow over time.

Here is the address:

***_[www.users.on.net/~thehands/](www.users.on.net/~thehands/)_***

I need assistance with permissions on the files that I serve?

---

### Post by Opeth115 on 2008-10-21
> **handy said:**
> That's great to hear. :-)

I have just read the bug report here:

***_[http://bugzilla.kernel.org/show_bug.cgi?id=11721](http://bugzilla.kernel.org/show_bug.cgi?id=11721)_***  

& found way down in the read that the following command as root, worked for the poster of the bug on the current kernel:

***_echo 0 > /proc/sys/net/ipv4/tcp_timestamps_***

I have done a yaourt -Syu & tested it & it worked for me too.

You might like to try it, if it doesn't work it is easy to downgrade, now that you have the kernel in your /var/cache/pacman/pkg/

[I]**[Edit:]**
I'll make a new thread on this here & on the Arch forum, which already has valuable information added to the initial post regarding this workaround.[/I]

***_[http://ubuntuforums.org/showthread.php?t=954112](http://ubuntuforums.org/showthread.php?t=954112)_***

just did a -Syu and tried the command and it worked!  thanks for that!  I added the line to my /etc/sysctl.conf and my internet is up and running with the latest kernel!  Thanks again for everyones help!

---

### Post by crimesaucer on 2008-10-21
> **handy said:**
> I need assistance with permissions on the files that I serve?

I'm not sure I understand this, but if you mean "Do you need permission for Arch files (like PKGBUILDS)?", then you should check with the people at Arch. I think they wouldn't care.

---

### Post by handy on 2008-10-21
> **crimesaucer said:**
> I'm not sure I understand this, but if you mean "Do you need permission for Arch files (like PKGBUILDS)?", then you should check with the people at Arch. I think they wouldn't care.

I've got it covered now thanks, actually from what I've learned there is no need to carry the kernels, only the need for people to know how to source the redundant ones.

There will be a sticky on it soon. :-)

---

