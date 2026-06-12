---
title: "Warning, installing the Nvidia drivers will bork your Arch Linux install!"
date: 2009-02-03
forum: Arch and derivatives
---

### Post by RJARRRPCGP on 2009-02-03
If you do a "pacman -S nvidia" and reboot, you will get:


ERROR: root fs cannot be detected. Try using the rootfstype= kernel parameter.

ERROR: Unable to create/detect root device '/dev/disk/by-uuid/xxxxx

Dropping to a recovery shell... type 'exit' to reboot

________________________________________________________

Thus, you will be stuck in a reformatting and reinstalling trap!

With this bug, you would be wondering if it should still be in alpha! :evil:

---

### Post by mips on 2009-02-03
Which version of the nvidia driver and on which arch, i686 or AMD64?

Maybe try
```
yaourt -S nvidia-utils-beta
yaourt -S nvidia-beta
```

Which will install 180.27-1

---

### Post by fwojciec on 2009-02-03
> **RJARRRPCGP said:**
> If you do a "pacman -S nvidia" and reboot, you will get:


ERROR: root fs cannot be detected. Try using the rootfstype= kernel parameter.

ERROR: Unable to create/detect root device '/dev/disk/by-uuid/xxxxx

Dropping to a recovery shell... type 'exit' to reboot

________________________________________________________

Thus, you will be stuck in a reformatting and reinstalling trap!

With this bug, you would be wondering if it should still be in alpha! :evil:

I don't think this has anything to do with nvidia drivers.  I don't see how nvidia would affect recognition of filesystems by the boot image.

I also have two Arch machines that use nvidia drivers and I never had any problem like this.

In either case, this kind of problem is not something that requires either reformatting or reinstalling.  Just make sure that the uuid identifiers are correct in menu.lst/fstab.  Alternatively you can ditch uuids and use the old style /dev/sdX designations for filesystems.

See this for how to deal with kernel panics (which are usually easy to fix): [http://wiki.archlinux.org/index.php/Kernel_panic]("http://wiki.archlinux.org/index.php/Kernel_panic")  First thing you should try when you boot into your system, aside from checking that grub and fstab configurations are OK, is regenerating boot images with "mkinitcpio -p kernel26".

---

### Post by Rumor on 2009-02-03
I've got nvidia 180.22-1 installed with no issues here.

As fwojciec pointed out, installing nvidia doesn't do anything to your file system. It plugs a module into your kernel, but that's about as invasive as it gets.

---

### Post by RJARRRPCGP on 2009-02-03
> **mips said:**
> Which version of the nvidia driver and on which arch, i686 or AMD64?

Maybe try
```
yaourt -S nvidia-utils-beta
yaourt -S nvidia-beta
```

Which will install 180.27-1


Just typing "pacman -S nvidia" will install 182.xx, 182.22 or later IIRC. 

And BTW, it's i686. With an Athlon XP 3000+.

---

### Post by RJARRRPCGP on 2009-02-03
> **fwojciec said:**
> I don't think this has anything to do with nvidia drivers.  I don't see how nvidia would affect recognition of filesystems by the boot image.

I also have two Arch machines that use nvidia drivers and I never had any problem like this.

In either case, this kind of problem is not something that requires either reformatting or reinstalling.  Just make sure that the uuid identifiers are correct in menu.lst/fstab.  Alternatively you can ditch uuids and use the old style /dev/sdX designations for filesystems.

See this for how to deal with kernel panics (which are usually easy to fix): [http://wiki.archlinux.org/index.php/Kernel_panic]("http://wiki.archlinux.org/index.php/Kernel_panic")  First thing you should try when you boot into your system, aside from checking that grub and fstab configurations are OK, is regenerating boot images with "mkinitcpio -p kernel26".

!The fstab was valid before "pacman -S nvidia"!

---

### Post by RJARRRPCGP on 2009-02-03
> **fwojciec said:**
> 

See this for how to deal with kernel panics (which are usually easy to fix): 

It wasn't a kernel panic, because it didn't display "Kernel panic:not syncing" and the caps lock light didn't start blinking.

And with a kernel panic, it wouldn't even give you a prompt. LOL.

---

### Post by fwojciec on 2009-02-03
> **RJARRRPCGP said:**
> It wasn't a kernel panic, because it didn't display "Kernel panic:not syncing" and the caps lock light didn't start blinking.

And with a kernel panic, it wouldn't even give you a prompt. LOL.

It doesn't matter -- the procedure for fixing it is the same: kernel panic ~= non-booting system.

And my guess is that when you installed nvidia pacman pulled some dependencies alongside with it, or something entirely different happened.  Like I said, there is no way installing nvidia driver would affect the boot routine.

---

### Post by mips on 2009-02-03
> **RJARRRPCGP said:**
> Just typing "pacman -S nvidia" will install 182.xx, 182.22 or later IIRC. 


pacman -S nvidia will install 180.22-1, there are no 182.xx drivers. yaourt will pull in the latest (180.27-1) from AUR.

---

### Post by crimesaucer on 2009-02-03
I'm using the official NVIDIA 180.25 and my graphics have never been better.

---

### Post by smartboyathome on 2009-02-03
> **mips said:**
> yaourt will pull in the latest (180.27-1) from AUR.

It won't unless you specify in yaourt that you want it from AUR instead of the main repos.

---

### Post by Grant A. on 2009-02-03
I am using the latest NVIDIA drivers from the stable repositories with no problems... FUD?

---

### Post by mips on 2009-02-04
> **smartboyathome said:**
> It won't unless you specify in yaourt that you want it from AUR instead of the main repos.

Sorry I should have been more clear like I was in post#2. 
yaourt -S nvidia-utils-beta
yaourt -S nvidia-beta

---

### Post by RJARRRPCGP on 2009-02-04
> **fwojciec said:**
> It doesn't matter -- the procedure for fixing it is the same: kernel panic ~= non-booting system.

And my guess is that when you installed nvidia pacman pulled some dependencies alongside with it, or something entirely different happened.  Like I said, there is no way installing nvidia driver would affect the boot routine.

I agree. LOL. Still horrible that I got a initial RAM disk prompt.

I guess I can call it the dreaded "RAM disk prompt of death"! LOL!:D

It's looking like I need to do "pacman -Sy udev" to update udev. 
I'm going to try that.

Because before getting the above errors, when installing the Nvidia drivers before rebooting, I saw this error message scroll by:

resolve-modalias: command not found

---

### Post by smartboyathome on 2009-02-04
This is what was happening to me when I get a borked kernel. Did you happen to update your kernel recently, by chance? If so, you might want to revert back to a previous version of the kernel to see if that helps.

---

### Post by RJARRRPCGP on 2009-02-04
> **smartboyathome said:**
> This is what was happening to me when I get a borked kernel. Did you happen to update your kernel recently, by chance? If so, you might want to revert back to a previous version of the kernel to see if that helps.

Yes. 

Unlike apt-get, it apparently upgrades the kernel without giving me an option to keep the same kernel version.

It appears to have snuck a higher version of the kernel. Instead of telling me in advance! :evil:

---

### Post by smartboyathome on 2009-02-04
> **RJARRRPCGP said:**
> Yes. 

Unlike apt-get, it apparently upgrades the kernel without giving me an option to keep the same kernel version.

It appears to have snuck a higher version of the kernel. Instead of telling me in advance! :evil:

You are supposed to *look* at the stuff before you upgrade it. Arch doesn't babysit you to keep you from messing up your system, it goes against their philosophy. ;)

---

### Post by namegame on 2009-02-04
> **RJARRRPCGP said:**
> 

It appears to have snuck a higher version of the kernel. Instead of telling me in advance! :evil:

Output of my "pacman -Syu"

```
[root@arch ~]# pacman -Syu
:: Synchronizing package databases...
 testing is up to date
 kdemod-core is up to date
 core is up to date
 extra                    389.7K   56.4K/s 00:00:07 [#####################] 100%
 community                359.4K   57.1K/s 00:00:06 [#####################] 100%
 archlinuxfr is up to date
:: Starting full system upgrade...
resolving dependencies...
looking for inter-conflicts...

Targets (5): device-mapper-1.02.30-1  imagemagick-6.4.8.10-1  
             kernel26-2.6.28.3-1  lvm2-2.02.44-1  psiconv-0.9.8-4  

Total Download Size:    31.26 MB
Total Installed Size:   100.93 MB

Proceed with installation? [Y/n] 
```

It always shows the upgrade targets, so what you are claiming really didn't happen...

On a somewhat sidenote, I have been running [testing] for over 2 months now with no issues at all. I just haven't been motivated to install that new kernel today...it would require a restart. :P

---

### Post by RJARRRPCGP on 2009-02-05
It looks like the problems are worse now, when I reinstalled and installed KDE, it now claims it cannot open some graphical file called "soft-grey" or something close to that and when I click "OK" KDE brings me back to the command line.

---

### Post by RJARRRPCGP on 2009-02-05
> **RJARRRPCGP said:**
> If you do a "pacman -S nvidia" and reboot, you will get:


ERROR: root fs cannot be detected. Try using the rootfstype= kernel parameter.

ERROR: Unable to create/detect root device '/dev/disk/by-uuid/xxxxx

Dropping to a recovery shell... type 'exit' to reboot

________________________________________________________

Thus, you will be stuck in a reformatting and reinstalling trap!

With this problem, you would be wondering if it should still be in alpha! :evil:

It looks like the roots of the problem is a forced major version upgrade to the kernel. 

I WANTED TO KEEP 2.6.25, but it didn't obey, it installed 2.6.28!

It seemed that's the cause!

---

### Post by smartboyathome on 2009-02-05
> **RJARRRPCGP said:**
> It looks like the roots of the problem is a forced major version upgrade to the kernel. 

I WANTED TO KEEP 2.6.25, but it didn't obey, it installed 2.6.28!

It seemed that's the cause!

It didn't force it on you. If you wanted to keep it from upgrading, you should have used this:
```
pacman -Sy --ignore kernel26
```

---

### Post by RJARRRPCGP on 2009-02-05
> **smartboyathome said:**
> It didn't force it on you. If you wanted to keep it from upgrading, you should have used this:
```
pacman -Sy --ignore kernel26
```

I wanted to just have the Nvidia driver added to the original 2.6.25 kernel. 

And that problem occurred with just a simple ```
pacman -S nvidia
```

---

### Post by RJARRRPCGP on 2009-02-05
I also should have waited for a 2009 release! 

Arch GNU/Linux seems to not like it when the real important components suddenly get a version change! 

!Especially when you don't upgrade packages in baby steps!


I should be less likely to get borked updates when newer stuff is already on the CD. :(

It appears to have thrown a fit because of jumping from 2.6.25 to 2.6.28
instead of 2.6.25.0 > 2.6.25.9  and then 2.6.25.9 > 2.6.27.0

---

### Post by fwojciec on 2009-02-05
Arch is a distro designed to be updated on regular basis.  Also, before installing any package you should always make sure that the system is up to date -- otherwise unpredictable things can happen.  This is a characteristic of a rolling release model.

---

### Post by RJARRRPCGP on 2009-02-05
But, because it's been a while since the last release, that could be the problem, because lots of new packages appeared that weren't there in June, 2008.

---

### Post by andrek on 2009-02-06
I had exactly the same error yesterday. In my case, it was caused by removing either "filesystems" or "ide" hook from /etc/mkinitcpio.conf :)

So I suggest you to check your mkinitcpio.conf file and use 
```
# mkinitcpio -p kernel26
```
once again.

---

### Post by RJARRRPCGP on 2009-02-15
But will that undo the Nvidia support? 

And someone reported this being caused by a problem with klibc and thus to do: ```
pacman -Sy klibc
```

I NEED the Nvidia kernel module enabled and I have the feeling that mkinitcpio -p kernel26 will undo it.

I didn't get Arch, to run my PC without 3D like it's 1996! That's so gay! :evil:

---

### Post by cardinals_fan on 2009-02-15
> Warning, installing the Nvidia drivers will bork your ***LIFE***!
Fixed that for you ;)

---

### Post by SkonesMickLoud on 2009-02-16
> **RJARRRPCGP said:**
> I also should have waited for a 2009 release!

> **RJARRRPCGP said:**
> But, because it's been a while since the last release, that could be the problem, because lots of new packages appeared that weren't there in June, 2008.

Arch doesn't work like that.  It's not on a release schedule like Ubuntu.  Theoretically, you could have installed Arch in 2002 and still be running the same install.  There is no "Version 2008".  No "Version 2009".

The different "versions" that you saw when you downloaded an iso are just snapshots of package state at that particular time.

---

### Post by RJARRRPCGP on 2009-02-16
> Warning, installing the Nvidia drivers will bork your LIFE!

> **cardinals_fan said:**
> fixed that for you ;)

lol

---

