---
title: "Installing Ubuntu only on Intel Imac (wiping OS X)"
date: 2007-10-14
forum: Apple Intel Users
---

### Post by IMcD23 on 2007-10-14
Is it possible to put JUST Ubuntu Fiesty on an Intel iMac(1GB ram, 17 inch screen)?  And how???

---

### Post by IMcD23 on 2007-10-14
Anyone???

---

### Post by wigglydiggly on 2007-10-14
I believe it is with rEFIt.  Just install refit boot live cd, install ubuntu replacing osx partition.  Just make sure you don't remove efi partion.  You will not be able to update firmware anymore, to my knowledge.  I have both osx and ubuntu on macbook c2d and just use osx for video skype, updating firmware, and as a backup in case I hose my system while on the road.

Enjoy

---

### Post by hajk on 2007-10-15
Installing just Linux on the internal HD of an Intel Mac is easy, I've done it on my MacBook and it would be very similar on an iMac. There's no need for rEFIt or Boot Camp, as you will partition the HD with an old-fashioned MBR-style scheme (not the newer GPT-style). Just insert your Linux install CD and hold down C when booting, then install Linux as per usual (taking the whole HD) and install GRUB to the MBR. When rebooting and ever after, at the familiar chime sound, a folder logo appears (instead of the Apple logo), upon which EFI hands off to GRUB to boot Linux.

Now, I keep Mac OS X around on an external FireWire HD (moved it there with Carbon Copy Cloner). This way I can install the odd Apple firmware updates. Booting with this drive plugged in starts Mac OS X, or (with Alt-Option held down) gives a choice of booting Mac OS X or "Windows" (meaning Linux). A full report on this at my site [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk")

---

### Post by IMcD23 on 2007-10-15
> **hajk said:**
> Installing just Linux on the internal HD of an Intel Mac is easy, I've done it on my MacBook and it would be very similar on an iMac. There's no need for rEFIt or Boot Camp, as you will partition the HD with an old-fashioned MBR-style scheme (not the newer GPT-style). Just insert your Linux install CD and hold down C when booting, then install Linux as per usual (taking the whole HD) and install GRUB to the MBR. When rebooting and ever after, at the familiar chime sound, a folder logo appears (instead of the Apple logo), upon which EFI hands off to GRUB to boot Linux.

Now, I keep Mac OS X around on an external FireWire HD (moved it there with Carbon Copy Cloner). This way I can install the odd Apple firmware updates. Booting with this drive plugged in starts Mac OS X, or (with Alt-Option held down) gives a choice of booting Mac OS X or "Windows" (meaning Linux). A full report on this at my site [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk")

I also have OS X on a 500GB external hd.  You have exactly what I want, except I want Ubuntu instead of Debian.  Shouldn't be too much different, because Ubuntu is built off of Debian

---

### Post by hajk on 2007-10-15
> **IMcD23 said:**
> I also have OS X on a 500GB external hd.  You have exactly what I want, except I want Ubuntu instead of Debian.  Shouldn't be too much different, because Ubuntu is built off of DebianRight, I had it working with Dapper initially (summer 2006), but at that time support for MacBook was still a bit of a problem (especially ALSA). All of that has been resolved in the 2.6.22 kernel, and that should hold for your older 17" Intel iMac as well. Go to it, I'd say!

---

### Post by eldepeche on 2007-10-15
> **hajk said:**
> Installing just Linux on the internal HD of an Intel Mac is easy, I've done it on my MacBook and it would be very similar on an iMac. There's no need for rEFIt or Boot Camp, as you will partition the HD with an old-fashioned MBR-style scheme (not the newer GPT-style). Just insert your Linux install CD and hold down C when booting, then install Linux as per usual (taking the whole HD) and install GRUB to the MBR. When rebooting and ever after, at the familiar chime sound, a folder logo appears (instead of the Apple logo), upon which EFI hands off to GRUB to boot Linux.

Now, I keep Mac OS X around on an external FireWire HD (moved it there with Carbon Copy Cloner). This way I can install the odd Apple firmware updates. Booting with this drive plugged in starts Mac OS X, or (with Alt-Option held down) gives a choice of booting Mac OS X or "Windows" (meaning Linux). A full report on this at my site [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk")

The reason to use rEFIt/Boot Camp is that in order to have hardware-accelerated graphics, you need to enable the legacy BIOS compatibility mode. 

Technically, it would be possible to enable hardware-accelerated graphics without the BIOS compatibility mode (i.e. using only EFI), but Apple doesn't have any reason to tell us how to do it, and no one seems to have figured out a good way to do it just yet.

---

### Post by hajk on 2007-10-15
> **eldepeche said:**
> The reason to use rEFIt/Boot Camp is that in order to have hardware-accelerated graphics, you need to enable the legacy BIOS compatibility mode. 

Technically, it would be possible to enable hardware-accelerated graphics without the BIOS compatibility mode (i.e. using only EFI), but Apple doesn't have any reason to tell us how to do it, and no one seems to have figured out a good way to do it just yet.
That's interesting. I was under the impression that the legacy BIOS mode is, in the absence of a GPT partitioning scheme,  enabled by default -- that's why Grub installed in the MBR can boot Linux. It would be helpful, I believe, if you could explain precisely what the presence of rEFIt/Boot Camp can add to this, especially as it relates to enabling hardware-accelerated graphics for Linux.

---

### Post by jamieno10 on 2007-10-15
Hi,

I was under the impression that you can indeed wipe out OS X, not have bootcamp or rEFIt etc, but my efforts on a mac pro (desktop) proved otherwise.

I have only been able to install ubuntu and boot it up properly after installing rEFIt. Just ubuntu alone doesn't work; GRUB hangs.

Not sure if its broadly applicable, but that's what I've experienced.

---

### Post by eldepeche on 2007-10-15
> **hajk said:**
> That's interesting. I was under the impression that the legacy BIOS mode is, in the absence of a GPT partitioning scheme,  enabled by default -- that's why Grub installed in the MBR can boot Linux. It would be helpful, I believe, if you could explain precisely what the presence of rEFIt/Boot Camp can add to this, especially as it relates to enabling hardware-accelerated graphics for Linux.

I am not entirely sure. I got my information [here](http://refit.sourceforge.net/myths/), on the rEFIt website.

The [Gentoo wiki site](http://gentoo-wiki.com/HARDWARE_Apple_MacBook) also has a lot of information.

---

### Post by cyberdork33 on 2007-10-15
You do not need rEFIt to enable the BIOS mode. You should be able to boot the install cd, tell the installer to use the entire disc, and boot into your system from the hard drive. All that rEFIt is useful for is having a menu appear at startup everytime when you are multibooting (and syncing partition tables if that is needed).

Note that removing the EFI partition and OSX will not allow you to update firmware in the future.

---

### Post by hajk on 2007-10-15
> **cyberdork33 said:**
> You do not need rEFIt to enable the BIOS mode. You should be able to boot the install cd, tell the installer to use the entire disc, and boot into your system from the hard drive. All that rEFIt is useful for is having a menu appear at startup everytime when you are multibooting (and syncing partition tables if that is needed).

Note that removing the EFI partition and OSX will not allow you to update firmware in the future.OK, that's what I advised the OP. He would do firmware updates by booting OS X from an external FireWire drive; I've done it that way on an original MacBook since summer 2006.

---

### Post by cyberdork33 on 2007-10-15
> **hajk said:**
> OK, that's what I advised the OP. He would do firmware updates by booting OS X from an external FireWire drive; I've done it that way on an original MacBook since summer 2006.
but you still need the efi partition as that is the official position apple is taking about its existance. In fact, on the previous firmware update, I now have files on that partition.

---

### Post by hajk on 2007-10-15
The external FireWire HD, from which I boot OS X,  is GPT formatted, so has the added EFI partition. Firmware updates for my MacBook have all been successful with this setup. Are you saying that on the new iMacs this EFI partition cannot be on an external HD, but *must* be on the internal HD? A deliberate change in Apple update policy? Frankly, I doubt that this is so.

The above should not be confused with Boot Camp: it is well-known that this can only be used on the internal HD, even on my original white MB...

---

### Post by cyberdork33 on 2007-10-15
> **hajk said:**
> The external FireWire HD, from which I boot OS X,  is GPT formatted, so has the added EFI partition. Firmware updates for my MacBook have all been successful with this setup. Are you saying that on the new iMacs this EFI partition cannot be on an external HD, but *must* be on the internal HD? A deliberate change in Apple update policy? Frankly, I doubt that this is so.

The above should not be confused with Boot Camp: it is well-known that this can only be used on the internal HD, even on my original white MB...

No, no, sorry, I am sure that if you have the partition on your external drive that is fine. I was not trying to say otherwise.

---

### Post by slick666 on 2007-10-15
I've been able to install Ubuntu on to my 1st gen MacBook straight from the install CD. It installed fine with no problems but I'm finding an inconsistency at boot up. Most of the time the system will boot find but 30 percent of the time the system will go to a black screen and simply hang there.

has anyone else had this problem with a direct install?

---

### Post by hajk on 2007-10-16
The problem will likely go away if you use the kernel boot option ```
lpj=7333000
```which corrects an estimate of Bogomips that may be way off. This option does not affect performance once the system has booted.

---

### Post by IMcD23 on 2007-10-16
> **hajk said:**
> Right, I had it working with Dapper initially (summer 2006), but at that time support for MacBook was still a bit of a problem (especially ALSA). All of that has been resolved in the 2.6.22 kernel, and that should hold for your older 17" Intel iMac as well. Go to it, I'd say!

I am having trouble with booting off the live cd.  It boots the first time after I burn, then when I boot off of it the next time, It will not load the user interface.  I believe it is called X.  Is there any way to fix that, other than burning again??? I have redownloaded the ISO off the Ubuntu website.  Any help?:confused:

---

### Post by slick666 on 2007-10-16
I had this problem myself for a little bit. Make sure your holding down the the c key at boot up to force it to boot off of the CD. It almost seems at if th system doesn't want to boot off of it after it see's it's a rival os :)

Hope this helps

---

### Post by cyberdork33 on 2007-10-16
> **IMcD23 said:**
> I am having trouble with booting off the live cd.  It boots the first time after I burn, then when I boot off of it the next time, It will not load the user interface.  I believe it is called X.  Is there any way to fix that, other than burning again??? I have redownloaded the ISO off the Ubuntu website.  Any help?:confused:

So you are seeing the bootloader and the Ubuntu Logo, but then nothing? You will probably continually get this issue, but if you install Ubuntu (where you can actually make changes to the config files, then it is likely correctable. You should be able to use CTRL+ALT+F1 (or F2, F3 and so on) to get to a console.

---

### Post by IMcD23 on 2007-10-16
> **cyberdork33 said:**
> So you are seeing the bootloader and the Ubuntu Logo, but then nothing? You will probably continually get this issue, but if you install Ubuntu (where you can actually make changes to the config files, then it is likely correctable. You should be able to use CTRL+ALT+F1 (or F2, F3 and so on) to get to a console.

Here's what happens.

It boots...ubuntu logo...then code running down screen...bluetooth loading, etc...Blue Screen...then message saying x won't load and asking me if i want to see the error, etc...select no...get command line.

---

### Post by slick666 on 2007-10-16
What type of system are you trying to install this on?

Also
>  The problem will likely go away if you use the kernel boot option
```
lpj=7333000
```

which corrects an estimate of Bogomips that may be way off. This option does not affect performance once the system has booted.


I added this just to see but it does not help. The problem I'm having is the system hangs between the initial Apple screen and GRUB stage 1.5. Has anyone had problems like this with booting directly into Ubuntu?

---

### Post by IMcD23 on 2007-10-17
> **slick666 said:**
> What type of system are you trying to install this on?

Also


I added this just to see but it does not help. The problem I'm having is the system hangs between the initial Apple screen and GRUB stage 1.5. Has anyone had problems like this with booting directly into Ubuntu?

I have an intel imac 17 inch with a 2.0 GHz intel core 2 duo with 1 gig of ram

---

### Post by slick666 on 2007-10-17
Does this also happed when you boot into the in the safe mode as well? there should be a "Start ubuntu in safe graphics mode"

---

### Post by IMcD23 on 2007-10-17
I don't know...My keyboard never works at that stage...sorry

IMcD23

---

### Post by cyberdork33 on 2007-10-17
> **IMcD23 said:**
> I don't know...My keyboard never works at that stage...sorry

IMcD23
You need to install a firmware update. That fixes the keyboard issue in bootloaders

---

