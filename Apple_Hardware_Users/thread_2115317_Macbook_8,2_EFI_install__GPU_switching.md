---
title: "Macbook 8,2 EFI install / GPU switching"
date: 2013-02-12
forum: Apple Hardware Users
---

### Post by SilverOne on 2013-02-12
Dear Ubuntu Community,

I have a macbook 8,2 and want to install ubuntu 12.10. I need both GPUs to work, since i need external display support and decent battery life. 

I've found tutorials to : 

enable EFI to work on 12.10: [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)  

Full install with switching kinda working?: [http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/) However, this one seems to be made for debian (ubuntu?) Oneiric and seems a little bit out of date, i'm not exactly an experienced user and i'm wondering if it'll work. 

Full gentoo linux install with switching: [http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011) well this one is for a completely diferent linux distribution and seems a little bit dated as well, i'm not sure this will work too. 

So i'll probably end up trying the first tutorial.

i might also remove rEFInd through this tutorial : [http://glandium.org/blog/?p=2830](http://glandium.org/blog/?p=2830)

Unfortunately there seems to be very little information on "graphic switching" and i'm not sure on how to switch between both GPUs.
The [https://help.ubuntu.com/community/MacBookPro8-2/Quantal](https://help.ubuntu.com/community/MacBookPro8-2/Quantal) says switching doesn't work. So how do i choose which GPU to boot and use ? i don't mind rebooting each time i need a different GPU. 

Best Regards,
SilverOne

---

### Post by Chav on 2013-02-12
Hopefully this will help you get on your way.

[http://ubuntuforums.org/showthread.php?t=2103743](http://ubuntuforums.org/showthread.php?t=2103743)

---

### Post by SilverOne on 2013-02-12
> **Chav said:**
> Hopefully this will help you get on your way.

[http://ubuntuforums.org/showthread.php?t=2103743](http://ubuntuforums.org/showthread.php?t=2103743)

Dear Chav, 

Thank you! I've been searching for tutorials for days now!! :).
I've never compiled a Kernel before but i'm sure with the help of some tutorials i'll figure out a way to do it :popcorn:.

Best Regards,
Silver

---

### Post by Chav on 2013-02-12
Glad I could help.

I used this guide to learn how to compile the kernel from a git repository. 

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

If I had to choose a repository to build from I would use the raring ubuntu kernel here: git://kernel.ubuntu.com/ubuntu/ubuntu-raring.git


One caveat is that after you dpkg -i your kernel it will sym link /lib/modules/(your kernel)/build and /lib/modules/(your kernel)/source to your build directory. After you install your kernel header package you can manually fix the sym link. It's not a huge problem but it will become an issue if you need to build kernel modules such as Virtual Box or any other DKMS and you've removed or cleaned your build directory.

---

### Post by SilverOne on 2013-02-12
> **Chav said:**
> Glad I could help.

I used this guide to learn how to compile the kernel from a git repository. 

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

If I had to choose a repository to build from I would use the raring ubuntu kernel here: git://kernel.ubuntu.com/ubuntu/ubuntu-raring.git


One caveat is that after you dpkg -i your kernel it will sym link /lib/modules/(your kernel)/build and /lib/modules/(your kernel)/source to your build directory. After you install your kernel header package you can manually fix the sym link. It's not a huge problem but it will become an issue if you need to build kernel modules such as Virtual Box or any other DKMS and you've removed or cleaned your build directory.

Dear Chav,

Thanks for the links :). i'll follow the tutorial you posted and i'm not sure i need those kernel modules?

Anyway I'll try it out during the weekend and report back! 

Best Regards,
Silverone

---

### Post by SilverOne on 2013-02-17
Hello :) 

I kinda veered off track here ... those tutorials seemed really complex when ubuntu 12.10 supports U(EFI) booting from the start. so i loaded up the "regular" iso and not the mac one.
At first it didn't work, the screen was black but i did happen to hear the "turck" sound when selecting "Try Ubuntu", that's when i figured i should add the following to the grub 2 selection menu : 
```

outb 0x728 1
outb 0x710 1
outb 0x740 2

```

it installed just fine but gave me a "linux will run in low graphics mode" or something like that each time i tried to boot. 
i added
```

outb 0x750 0

``` 
and it works great now, except for the amd support. Could you tell me where i can edit the grub.cfg ? i saw it on some directory but it had so many things inside i didn't know where to start.

anyway i've been trying some commands i've found on these websites :

[http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011)
[http://ubuntuforums.org/showthread.php?t=2103743](http://ubuntuforums.org/showthread.php?t=2103743) ( your thread )
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

if i add :```
outb 0x750 1
``` - i can hear the turck sound but the screen goes black. 

i feel like i'm really close here but writing all the commands every time takes a long time.

---

### Post by SilverOne on 2013-02-18
Okay, so i've managed to get a  custom grub option by following this tutorial : 
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

it's not the default option but it'll do for now, keep in mind i'm not using refind or refit... geez... that really saved me allot of time :popcorn:

mac os x booting from grub doesn't work though, i'll look into it later since i can always press option while booting up. 

Mr. Chav, i trust the next step would be to build the kernel per your tutorial ?

UPDATE:

after booting back into the OS x partition i can't seem to get back in. I only see a "windows" partition and that kinda loads bios mode. 


i'll have to install refind and then follow this tut: 
[http://glandium.org/blog/?p=2830](http://glandium.org/blog/?p=2830)

---

### Post by Chav on 2013-02-18
Yes, the next step (once you can boot back into Ubuntu) is to compile your kernel. 

I'm not sure how your machine is setup. Are you using a hybrid Master Boot Record (Boot camp)? That would explain the "Windows" boot option. 

Can you still boot into OSX? If you can please post the output of the following:

```
diskutil list
```

Hopefully you've already got this sorted and nothing too important was on the harddrive!

---

### Post by SilverOne on 2013-02-18
> **Chav said:**
> Yes, the next step (once you can boot back into Ubuntu) is to compile your kernel. 

I'm not sure how your machine is setup. Are you using a hybrid Master Boot Record (Boot camp)? That would explain the "Windows" boot option. 

Can you still boot into OSX? If you can please post the output of the following:

```
diskutil list
```

Hopefully you've already got this sorted and nothing too important was on the harddrive!

Hello , well... i have no idea what i'm using : 

```

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *121.3 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh SSD           88.5 GB    disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:       Microsoft Basic Data                         32.0 GB    disk0s4
silver-mbp:~ silverone$ 

```

Nothing ever broke ;) i just had to reinstall refind and launch ubuntu from there instead of the default EFI.

---

### Post by Chav on 2013-02-19
Excellent! I was worried that your partition table and/or EFI partition got trashed. I was about to go into a long, complicated, and risky set of steps on how to repair it.

---

### Post by SilverOne on 2013-02-19
> **Chav said:**
> Excellent! I was worried that your partition table and/or EFI partition got trashed. I was about to go into a long, complicated, and risky set of steps on how to repair it.

hehe i was worried too. what happens if i delete that EFI partition up there ? guess i'd have to reinstall from scratch.

the first time i installed ubuntu i did it without "manual" configuration of the partitions, and it deleted the recovery partition. luckily, if you press CMD R it'll load one from the internet. 

as you see i only have an ssd so i didn't make a swap partition. How much ram do you need to compile a kernel? i've got 8gigs but wondering if its enough.
also, have you managed to adjust the trackpad sensitivity?

---

### Post by Chav on 2013-02-19
For me the entry for the EFI partition was deleted while the files were left intact. I was lucky enough to be able to recreate the partition using the original position and size and not have to reinstall EFI grub. 

Yes, the internet recovery saved me a few times as well.

I've compiled the kernel several times with 4GB of RAM. You will see in the kernel compile instructions a concurrency level.

```
make -j `getconf _NPROCESSORS_ONLN` deb-pkg LOCALVERSION=-custom
```

You may set this value lower to consume less RAM. For example:

```
make -j 4 deb-pkg LOCALVERSION=-custom
```

I'm happy with the default trackpad sensitivity on Ubuntu 12.10, but there is a place to adjust the sensitivity and acceleration in the settings.

---

### Post by SilverOne on 2013-02-19
> **Chav said:**
> For me the entry for the EFI partition was deleted while the files were left intact. I was lucky enough to be able to recreate the partition using the original position and size and not have to reinstall EFI grub. 

Yes, the internet recovery saved me a few times as well.

I've compiled the kernel several times with 4GB of RAM. You will see in the kernel compile instructions a concurrency level.

```
make -j `getconf _NPROCESSORS_ONLN` deb-pkg LOCALVERSION=-custom
```

You may set this value lower to consume less RAM. For example:

```
make -j 4 deb-pkg LOCALVERSION=-custom
```

I'm happy with the default trackpad sensitivity on Ubuntu 12.10, but there is a place to adjust the sensitivity and acceleration in the settings.

Hi ;) 

i've tried that, but nothing changes on my end.

---

### Post by SilverOne on 2013-02-19
> **Chav said:**
> Glad I could help.

I used this guide to learn how to compile the kernel from a git repository. 

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

If I had to choose a repository to build from I would use the raring ubuntu kernel here: git://kernel.ubuntu.com/ubuntu/ubuntu-raring.git


One caveat is that after you dpkg -i your kernel it will sym link /lib/modules/(your kernel)/build and /lib/modules/(your kernel)/source to your build directory. After you install your kernel header package you can manually fix the sym link. It's not a huge problem but it will become an issue if you need to build kernel modules such as Virtual Box or any other DKMS and you've removed or cleaned your build directory.

Hello! i've cloned the raring git, but i'm not so sure how to apply the radeon-load-bios patch. 

i did the following: 

```

silverone@silver-mbp:~/kernel$ ls
radeon-bios-firmware.patch  ubuntu-raring
silverone@silver-mbp:~/kernel$ cd ubuntu-raring
silverone@silver-mbp:~/kernel/ubuntu-raring$ ls
arch     debian         firmware  Kbuild       Makefile        samples   ubuntu
block    debian.master  fs        Kconfig      mm              scripts   usr
COPYING  Documentation  include   kernel       net             security  virt
CREDITS  drivers        init      lib          README          sound
crypto   dropped.txt    ipc       MAINTAINERS  REPORTING-BUGS  tools
silverone@silver-mbp:~/kernel/ubuntu-raring$ patch -pl < '/home/silverone/kernel/radeon-bios-firmware.patch' 
patch: **** strip count l is not a number
silverone@silver-mbp:~/kernel/ubuntu-raring$ patch -p1 < '/home/silverone/kernel/radeon-bios-firmware.patch' 
patching file drivers/gpu/drm/radeon/radeon_bios.c
Hunk #1 succeeded at 30 with fuzz 1.
Hunk #2 succeeded at 58 (offset 1 line).
Hunk #3 succeeded at 68 (offset 1 line).
Hunk #4 succeeded at 77 (offset 1 line).
Hunk #5 succeeded at 649 with fuzz 2 (offset 128 lines).
silverone@silver-mbp:~/kernel/ubuntu-raring$ 

```

i suppose that did it? i've already taken care of the vbios configs, and am now looking on how to apply the following: 

```

5. (This is key) Compile the kernel with the following options.
CONFIG_DRM=Y
CONFIG_DRM_I915-Y

DRM_RADEON=m

# This was the hardest one for me to figure out. 
# Without this the system will boot to a blank screen after 
# splash

# CONFIG_FB_EFI is not set

# These options allow your kernel to load the radeon bios before 
# the filesystem is mounted. Otherwise you will have to delay 
# loading the radeon module.
CONFIG_FW_LOADER=y
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE="radeon/vbios.bin"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware/"

```
how do i apply these?

---

### Post by Chav on 2013-02-20
With the patch command it's -p1 (the number one). You're second try worked. 

After copying your current config and running 
 ```
yes '' | make oldconfig
```

```
CONFIG_DRM=Y
CONFIG_DRM_I915-Y

DRM_RADEON=m

# CONFIG_FB_EFI is not set
```

These config settings can be set in the menuconfig.

```
make menuconfig
```

Once menuconfig starts you can use the '/' key to search for the configuration option and find where it is set. 

```
CONFIG_FW_LOADER=y
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE="radeon/vbios.bin"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware/"
```

Those settings I could not find in the menuconfig and set manually by opening '.config' and setting the value. This is not recommended for other settings since many configuration options have dependencies.

---

### Post by SilverOne on 2013-02-20
Oh okay... that makes sense :). Didn't knew you could perform a search.

Alright so i've asked for the CONFIG_DRM :

[http://d.pr/i/fjUR](http://d.pr/i/fjUR) 

so now all i have to do, is to press 8 : 

[http://d.pr/i/9nWY](http://d.pr/i/9nWY)

and then Y ?

okay, i think i got this :P

---

### Post by SilverOne on 2013-02-20
Okay! it's compiling ! 

thank you for your help :) i have no idea how you figured all this stuff ! 

it's been quite the adventure so far and i hope to see this done. 
i'm also surprised that my computer isn't scorching hot running 100%: 

[http://d.pr/i/neIs](http://d.pr/i/neIs)

at first i thought there was some downclock but seems not:

```

silverone@silver-mbp:~$ cat /proc/cpuinfo | grep "cpu MHz"
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000

```

i'll let you know ;)

edit: 

error :( 
```

  LD [M]  sound/soc/generic/snd-soc-simple-card.ko
  LD [M]  sound/soc/snd-soc-core.ko
  LD [M]  sound/soundcore.ko
  LD [M]  sound/synth/emux/snd-emux-synth.ko
  LD [M]  sound/synth/snd-util-mem.ko
  LD [M]  sound/usb/6fire/snd-usb-6fire.ko
  LD [M]  sound/usb/caiaq/snd-usb-caiaq.ko
  LD [M]  sound/usb/misc/snd-ua101.ko
  LD [M]  sound/usb/snd-usb-audio.ko
  LD [M]  sound/usb/snd-usbmidi-lib.ko
  LD [M]  sound/usb/usx2y/snd-usb-us122l.ko
  LD [M]  sound/usb/usx2y/snd-usb-usx2y.ko
  LD [M]  ubuntu/aufs/aufs.ko
  LD [M]  ubuntu/dm-raid4-5/dm-raid45.ko
make[3]: *** No rule to make target `firmware/bnx2x/bnx2x-e1-7.8.2.0.fw', needed by `__fw_modbuild'.  Stop.
make[2]: *** [modules] Error 2
make[1]: *** [deb-pkg] Error 2
make: *** [deb-pkg] Error 2
silverone@silver-mbp:~/kernel/ubuntu-raring$ ^C
silverone@silver-mbp:~/kernel/ubuntu-raring$ 

```

i'll try another kernel git other than the raring.

---

### Post by Chav on 2013-02-20
Oh so close! And an easy fix :)

When you ran clean before building it deleted the firmware folder. The firmware folder is still in the git repository so it's easy to get those files back. Just make sure that you don't clean again before building and you'll be set.

1. Don't panic. ;)

2. Do a clean. 
If you built with make do: 
```
make clean
```
If you build with make-kpkg do:
```
make-kpkg clean
```

3. Clean the build folder and get the firmware files back:
This will show all the changes to the build folder:
```
git status
```

You will see something like the following:

```
#	deleted:    firmware/bnx2x/bnx2x-e1-7.8.2.0.fw
#	deleted:    firmware/bnx2x/bnx2x-e1h-7.8.2.0.fw
#	deleted:    firmware/bnx2x/bnx2x-e2-7.8.2.0.fw
#

```

We need to get those files back before compiling. 
Remove all the extra files/folders that were created:
```
git clean -df
```
Restore all the deleted files:
```
git reset --hard
```

Now you are ready to build.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Oh so close! And an easy fix :)

When you ran clean before building it deleted the firmware folder. The firmware folder is still in the git repository so it's easy to get those files back. Just make sure that you don't clean again before building and you'll be set.

1. Don't panic. ;)

2. Do a clean. 
If you built with make do: 
```
make clean
```
If you build with make-kpkg do:
```
make-kpkg clean
```

3. Clean the build folder and get the firmware files back:
This will show all the changes to the build folder:
```
git status
```

You will see something like the following:

```
#	deleted:    firmware/bnx2x/bnx2x-e1-7.8.2.0.fw
#	deleted:    firmware/bnx2x/bnx2x-e1h-7.8.2.0.fw
#	deleted:    firmware/bnx2x/bnx2x-e2-7.8.2.0.fw
#

```

We need to get those files back before compiling. 
Remove all the extra files/folders that were created:
```
git clean -df
```
Restore all the deleted files:
```
git reset --hard
```

Now you are ready to build.

Hello ! :) 

I changed the raring git to : git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git 

and it seems to have worked. However, since we're on ubuntu i suppose the raring would be a better choice :) 

i'll let this one finish and compile that one after! 

thank you again :)

---

### Post by SilverOne on 2013-02-20
Hello! 

I've successfully compiled a kernel and installed it! :) . However I'm booting to a dark screen after splash 

```

# This was the hardest one for me to figure out. 
# Without this the system will boot to a blank screen after 
# splash

# CONFIG_FB_EFI is not set
```


I did not make this step, i suppose this is what's causing the issue :p? 

Also, could you kindly test if cpu scaling works on your end? mine are always at :

```
silverone@silver-mbp:~$ cat /proc/cpuinfo | grep "cpu MHz"cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
cpu MHz		: 2201.000
silverone@silver-mbp:~$ ^C
silverone@silver-mbp:~$ 


```

---

### Post by Chav on 2013-02-20
Yes, this is an important one. :)
```
# CONFIG_FB_EFI is not set
``` 

Scaling is working:
```
~$ cat /proc/cpuinfo | grep "cpu MHz"
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000

```

I also have Jupiter installed and it is setting the cpu governor to ondemand.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Yes, this is an important one. :)
```
# CONFIG_FB_EFI is not set
``` 

Scaling is working:
```
~$ cat /proc/cpuinfo | grep "cpu MHz"
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000

```

I also have Jupiter installed and it is setting the cpu governor to ondemand.

I've installed jupiter and it seems to be downclocking but CPU Turbo Boost doesn't seem to work.
Compiling the new kernel now.

---

### Post by SilverOne on 2013-02-20
Alright, i've got it running :). However, it would appear vgaswitcheroo is not installed? 

```

bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
root@silver-mbp:/home/silverone# echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
root@silver-mbp:/home/silverone# exit
exit

```

---

### Post by Chav on 2013-02-20
Vgaswitcheroo wont load unless two graphics drivers are present. 

If, for example, the radeon driver failed to load then you wont see vgaswitcheroo. 

First off is to see if both cards are connected:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Serie
```

This shows that both cards are present and not hidden.

See if the radeon driver is loaded:

```
lsmod | grep radeon
```

I'm guessing that wont show anything meaning that the radeon driver failed to load. You can look at dmesg for errors to figure out why. Again, I'm guessing, that it has to do with the vbios.bin not being found or the patch not being applied.

Ah ha! As I was typing that I realized the issue. 

When we did 
```
git reset --hard
```

That undid the radeon load bios patch. Sorry!

So the steps are (off the top of my head):
make clean
git clean -df
git reset --hard
apply the radeon patch
build the kernel

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Vgaswitcheroo wont load unless two graphics drivers are present. 

If, for example, the radeon driver failed to load then you wont see vgaswitcheroo. 

First off is to see if both cards are connected:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Serie
```

This shows that both cards are present and not hidden.

See if the radeon driver is loaded:

```
lsmod | grep radeon
```

I'm guessing that wont show anything meaning that the radeon driver failed to load. You can look at dmesg for errors to figure out why. Again, I'm guessing, that it has to do with the vbios.bin not being found or the patch not being applied.

Ah ha! As I was typing that I realized the issue. 

When we did 
```
git reset --hard
```

That undid the radeon load bios patch. Sorry!

So the steps are (off the top of my head):
make clean
git clean -df
git reset --hard
apply the radeon patch
build the kernel

Hello! 

I didn't do those steps since i'm still on the 3.8.0 kernel, this git: 
git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git

this git doesn't present me with the problem raring did :P got lucky i suppose :P 

however here are the commands you've ran: 

```

silverone@silver-mbp:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series]
silverone@silver-mbp:~$ lsmod | grep radeon
radeon                941684  0 
ttm                    83361  1 radeon
silverone@silver-mbp:~$
```

seems like both cards are online.

---

### Post by Chav on 2013-02-20
Hmm, next step is to look at dmesg to see if there are errors regarding the graphics drivers or vgaswitcheroo.

---

### Post by SilverOne on 2013-02-20
```

silverone@silver-mbp:~$ dmesg | grep vga
[    2.322717] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    2.322722] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    2.322724] vgaarb: loaded
[    2.322725] vgaarb: bridge control possible 0000:01:00.0
[    2.322726] vgaarb: no bridge control possible 0000:00:02.0
[    4.933224] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    4.933226] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    5.180151] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    8.281258] vga_switcheroo: enabled
[    8.282478] vga_switcheroo: disabled

```

seems like it turned off vga_switcheroo pretty early.

```

silverone@silver-mbp:~$ dmesg | grep radeon
[    8.281040] [drm] radeon defaulting to kernel modesetting.
[    8.281042] [drm] radeon kernel modesetting enabled.
[    8.281290] radeon 0000:01:00.0: Invalid ROM contents
[    8.281352] radeon 0000:01:00.0: Invalid ROM contents
[    8.281376] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[    8.281400] radeon 0000:01:00.0: Fatal error during GPU init
[    8.281422] [drm] radeon: finishing device.
[    8.282568] radeon: probe of 0000:01:00.0 failed with error -22

```

i've checked and vbios is where it should be.

---

### Post by Chav on 2013-02-20
Weird. Have you opened your .config and checked that the config options are set to the same as mine?

edit: I've attached my config for reference.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Weird. Have you opened your .config and checked that the config options are set to the same as mine?

sigh i edited the wrong post .... 

anyway, here's what i found : 

i checked the .config, and the 
CONFIG_FW_LOADER=y
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE="radeon/vbios.bin"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware/"

isn't there. maybe i didn't save the file before quitting. i'll try recompiling.

---

### Post by SilverOne on 2013-02-20
Hello! 

no joy, i'm getting the same errors. 
Can you get me an md5 on your vbios.bin? maybe its corrupted somehow? 

```

silverone@silver-mbp:~/kernel/linux$ cat .config | grep CONFIG_EXTRA_FIRMWARE
CONFIG_EXTRA_FIRMWARE="radeon/vbios.bin"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware/"
silverone@silver-mbp:~/kernel/linux$ md5sum '/lib/firmware/radeon/vbios.bin' 
b42bc234ca257f1710ad81a23390b220  /lib/firmware/radeon/vbios.bin
silverone@silver-mbp:~/kernel/linux$ 

```

i haven't exactly compared your .config to mine. I looked where your extra_firmware stuff was and placed mine there. I'll take a look at it now.

also here's my grub2:

```

menuentry "Ubuntu - IG" {
record fail
        insmod gzio
        insmod part_gpt
        insmod ext2
        set gfxpayload=keep
        outb 0x728 1
        outb 0x710 2
        outb 0x740 2
        set root='hd0,hpt4'
        search --no-floppy --fs-uuid --set=root 36a95a24-b710-43f7-9cec-d2ed409a4f5f
        linux   /boot/vmlinuz-3.8.0-custom root=UUID=36a95a24-b710-43f7-9cec-d2ed409a4f5f ro   quiet splash i915.lvds_use_ssc=0 
        initrd  /boot/initrd.img-3.8.0-custom
}

```

---

### Post by Chav on 2013-02-20
```
$ md5sum /lib/firmware/radeon/vbios.bin 
c1f3ee4dce553a009ab1599e18146f35  /lib/firmware/radeon/vbios.bin

```

That doesn't necessarily mean that yours is corrupt. The other vbios.bin I found online had a different md5sum than mine. 

The radeon load bios patch was applied before compiling? That's the only thing I can think of.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> ```
$ md5sum /lib/firmware/radeon/vbios.bin 
c1f3ee4dce553a009ab1599e18146f35  /lib/firmware/radeon/vbios.bin

```

That doesn't necessarily mean that yours is corrupt. The other vbios.bin I found online had a different md5sum than mine. 

The radeon load bios patch was applied before compiling? That's the only thing I can think of.

oops ](*,)

also i was comparing your config to mine and noticed you have CONFIG_APPLE_GMUX=y  where i have m. i'll reboot now and recompile.

---

### Post by Chav on 2013-02-20
Since your next build will work ;), here's something for you to read over while the kernel is compiling.

[https://bugs.freedesktop.org/show_bug.cgi?id=49981](https://bugs.freedesktop.org/show_bug.cgi?id=49981)

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Since your next build will work ;), here's something for you to read over while the kernel is compiling.

[https://bugs.freedesktop.org/show_bug.cgi?id=49981](https://bugs.freedesktop.org/show_bug.cgi?id=49981)

mother of god that is high... realllyyy high, higher than anything on the 6750m overclocking thread: 
[http://forums.macrumors.com/showthread.php?t=1142028](http://forums.macrumors.com/showthread.php?t=1142028)

i have no idea how to revert commits and apply patches :( , maybe it's best i stick to os x for now? and how can that bug be reported as "medium" when it can effectively brick your mac O.o?

---

### Post by Chav on 2013-02-20
Those clock speeds and voltages are being set from a table stored in vbios.bin (which is provided by ATI). I haven't read through your link but I don't think any voltages are being set that are out of spec. 

Regardless I have run with those settings for months without issue (knock on wood).

Anyway, reverting a commit is as easy as doing the following:

```
git revert 27810fb2d2edacf2961dbedfe9e9f8d2e5080ea5
```

Edit: Wow, maybe our card is different from OEM 6750m?
Edit Again: It's from the Apple section, but those posts are from before my laptop was announced. I'm using a late 2011 macbook pro 8,2 (released in Oct)

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Those clock speeds and voltages are being set from a table stored in vbios.bin (which is provided by ATI). I haven't read through your link but I don't think any voltages are being set that are out of spec. 

Regardless I have run with those settings for months without issue (knock on wood).

Anyway, reverting a commit is as easy as doing the following:

```
git revert 27810fb2d2edacf2961dbedfe9e9f8d2e5080ea5
```

Edit: Wow, maybe our card is different from OEM 6750m? This is scary.

those do seem quite a bit high however. Alright so it's working now :P

```

silverone@silver-mbp:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
[sudo] password for silverone: 
-rw-r--r-- 1 root root 0 Fev 21 02:30 /sys/kernel/debug/vgaswitcheroo/switch

```

so it is indeed working, however, i'm not being able to switch graphics to the DIS: 

```
 
root@silver-mbp:/home/silverone# cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS-Audio: :Off:0000:01:00.1
2:DIS: :Off:0000:01:00.0
root@silver-mbp:/home/silverone# echo ON > /sys/kernel/debug/vgaswitcheroo/switch
root@silver-mbp:/home/silverone# cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS-Audio: :Pwr:0000:01:00.1
2:DIS: :Pwr:0000:01:00.0
root@silver-mbp:/home/silverone# echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
root@silver-mbp:/home/silverone# cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS-Audio: :Pwr:0000:01:00.1
2:DIS: :Pwr:0000:01:00.0
root@silver-mbp:/home/silverone# 

```

it is detecting the screen in "displays" but no output.

---

### Post by Chav on 2013-02-20
X is stopped, right?

If it is already stopped then you can tail /var/log/syslog to see the error.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> X is stopped, right?

If it is already stopped then you can tail /var/log/syslog to see the error.

What do you mean X is stopped? i gotta stop the "unity" "desktop" to change ? 
i suppose you open up a terminal and do "stop x" ? i'll try that :P

---

### Post by Chav on 2013-02-20
Unfortunately, the switch will only happen when X is not running. 

1. Open a virtual terminal (Ctrl + Alt + F1)
2. Login
3. sudo service lightdm stop (or gdm stop)
4. Perform the switch
5. sudo service lightdm start (or gdm start)

You can queue switches from within an X session by echoing 'DDIS' or 'DIGD' to switch then restarting X by:
```
gnome-session-quit --no-prompt --logout
```

---

### Post by SilverOne on 2013-02-20
well that did it. it's working ;). thank you  :)

---

### Post by SilverOne on 2013-02-20
Hello again! 

Everything is working great! Thank you for walking me all the way :). 

i'm studying computer engineering and hope that one day i'll understand as much as you ;). 

):P:popcorn:

---

### Post by Chav on 2013-02-20
> **SilverOne said:**
> Hello again! 

Everything is working great! Thank you for walking me all the way :). 

i'm studying computer engineering and hope that one day i'll understand as much as you ;). 

):P:popcorn:

You're welcome!

I also studied computer engineering. 

I'm convinced that most people will take a look at my guide and give up (for good reason). You were able to get through it without having compiled a kernel before and that's impressive. Best of luck to you! I'm sure you'll do well.

---

### Post by Chav on 2013-02-20
Oh, one last thing.

I've found that even with X stopped vgaswitcheroo will refuse to switch. I've narrowed the issue down to the audio system, but I've only found a brute force way to fix it by running: 

```
pulseaudio -k && sudo alsa force-reload
```

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Oh, one last thing.

I've found that even with X stopped vgaswitcheroo will refuse to switch. I've narrowed the issue down to the audio system, but I've only found a brute force way to fix it by running: 

```
pulseaudio -k && sudo alsa force-reload
```

it switches here. 

I'm not on gnome but here's what i do: 

sudo service lightdm stop

echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch

service lightdm start 


if you try to do DDIS and then restarting lightdm it'll fail. 

last time i did this i couldn't reboot ( it'd take me back to the login screen ) let me try now.

edit: it seems any shutdown / reboot takes you back to the screen. i'll try sudo shutdown now

---

### Post by Chav on 2013-02-20
I should clarify. The switch will work most of the time, but occasionally it wont. That's when I have to run the above command.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> I should clarify. The switch will work most of the time, but occasionally it wont. That's when I have to run the above command.

How exactly do you turn off your computer afterwards ? 

mine gets stuck here : 

[http://d.pr/i/EChW](http://d.pr/i/EChW)
and that was a shutdown now otherwise it'd have landed on the login screen again. 

pressing the power button doesn't cut it.

---

### Post by Chav on 2013-02-20
Hmm, I haven't seen that issue. Both 
```
sudo shutdown -P now
```
and using shutdown from gnome shell/cinnamon/unity work for me.

---

### Post by SilverOne on 2013-02-20
> **Chav said:**
> Hmm, I haven't seen that issue. Both 
```
sudo shutdown -P now
```
and using shutdown from gnome shell/cinnamon/unity work for me.


well, that worked. but i've just ran afew reboots and it happens each time i switch gpu.

---

### Post by supermario87 on 2013-05-04
Hi, I'm here to ask for help!
I used the procedure from **Chav**, with latest linux 3.9.0 kernel from linux mainline.
With no radeon-bios patch applyed I can boot but then is kernel panic! I can attach a log because the system hangs, I can post a photo of the screen at my best!
Do the patch is necessary with linux 3.9 kernel?

Thanks

---

### Post by marcosnils on 2013-05-29
Hi, 

As supermario asked, by using the latest 3.9 kernel do we still need to apply any manual patches before booting with the corresponding parameters?.

Thx,

Marcos.

---

### Post by whatsamac on 2013-08-12
By the way, for people that are satisfied with switching between i915 and radeon at boot time while using vanilla 3.8 kernel I made a tutorial that should be understandable even for Ubuntu newbies: [http://ubuntuforums.org/showthread.php?t=2157775&p=12707618#post12707618](http://ubuntuforums.org/showthread.php?t=2157775&p=12707618#post12707618)

---

