---
title: "Creating a bootable 12.04 usb for MacBook 2,1"
date: 2012-07-29
forum: Apple Hardware Users
---

### Post by reggiehg on 2012-07-29
Hi,

After searching this site for my particular problem, apart from googling all over web, I'm still stuck. I'm looking for a straight forward install, as much as possible, with maybe a handful of manual steps at most. Using unetbootin says the created usb works on pcs but not macs. Using startup disk creator, I can't select the usb to be booted from.

At the wiki pages, I find entries only until 10.10 for the MacBook 2,1. Does that mean what I'm looking for isn't possible?

Tia!

---

### Post by baloo101 on 2012-07-30
Hi reggiehg. First of all, the only "Apple" answer is : You can't boot Legacy OS from external devices (read anything than OSX)

My answer is : It's possible with a mix of rEFIt, Grub aver many command line (this is how I successful installed Precise from external CD because my internal superdrive is broke)

Maybe it's possible to boot from USB with the same thing with changing some line of code.

Best regards. If you want to go forward with this I can try to find my documentation or to help you as much as i can.

Cheers.

---

### Post by markzero on 2012-08-03
Hi, Reggie. I was struggling with a fix for this issue myself, overnight, when installing a new drive in my black Macbook 2,1. I tried creating bootable USB sticks and CDs, both on the PC and on the Macbook, and nothing would boot up to install. (This was complicated by the fact that I was using an external DVD drive because the internal one is broken, and Apple won't let us boot "legacy" OS stuff from an external drive)

Sadly, I didn't find a fix for this problem, but **I did find a workaround** just to get Ubuntu booting on the Macbook (which is the ultimate goal, anyway): I ended up pulling the hard drive sled back out and connecting it directly to a desktop PC, and installing Ubuntu on it that way. I was using the alternate ISO, and since it was a new drive, wasn't trying to save an existing OSX install, so figured, why not? Anyway, I then slid the drive back into the Macbook (stupid rubbery rails keep coming off the sides, be careful) and at first it wouldn't boot, so then I blessed it using 

*bless --device /dev/disk0s1 --setBoot --legacy*

from a terminal window after booting from my Snow Leopard install DVD, and tried again, and... after a few long seconds with a dark screen, it came up! Ubuntu leaves enough generic drivers lying around that it was able to make the hardware switch okay.

I hope baloo101 can get back to you with a good fix, but if not, and you have a working, normal-BIOS (not EFI) PC on hand, this should at least get you running.

p.s. the drive blessing command was from [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by reggiehg on 2012-08-05
Thanks for the reply, MarkZero. What I'm trying to do right now is just create an Ubuntu 12.04 usb that I can boot pcs or macs (or well, at least my MacBook 2,1) with. I can already create a usb to boot pcs with, but it won't boot my mac. I can boot my mac off an 12.04 internal cd. Eventually, I will want to repartition my internal osx harddisk to be able to dual boot with 12.04 too, but I want to learn more about these stuff before actually doing it, including creating a said 12.04 usb. I have already repartitioned my internal pc drives to dual boot 12.04. But could you enlighten me on this:

> **markzero said:**
> ...(...Apple won't let us boot "legacy" OS stuff from an external drive)


I keep running into these "legacy" references while googling, but I can't quite understand it. Does it mean non-OSX? 

Or does it mean FAT drives? The 12.04 usb I created was FAT. I tried creating an ext3 usb but that wouldn't work on my mac. I haven't tried using an ext3 usb with my pcs yets though. Or will my mac boot only on hfs usbs?

---

### Post by pindar on 2012-08-05
> **reggiehg said:**
> Hi,

After searching this site for my particular problem, apart from googling all over web, I'm still stuck. I'm looking for a straight forward install, as much as possible, with maybe a handful of manual steps at most. Using unetbootin says the created usb works on pcs but not macs. Using startup disk creator, I can't select the usb to be booted from.

At the wiki pages, I find entries only until 10.10 for the MacBook 2,1. Does that mean what I'm looking for isn't possible?

Tia!
If you insist on performing "a handful of manual steps at most," yes, you may be out of luck. If you want a USB that boots both on your Macbook and on generic PC hardware, I think this is definitely impossible. If, however, you're just looking for a way to make USB stick that will boot your Macbook: I have found two methods which work pretty reliably.
[LIST=1]
[*]The method described [in this post]("http://www.devslashzero.com/node/160") has worked pretty well for me.
[*]Something that's a bit more involved, but very useful: produce a USB stick which is able to boot from an iso image. I have a small USB disk which does that. This means for ubuntu-based (and some other) distributions, I can simply copy the iso to the main partition of the disk and boot from it. But preparing the USB disk/stick is a bit involved and needs more than "a handful of manual steps at most."  You will need to format your USB disk or stick with a GUID partition table; modern Apple hardware will not boot from anything partitioned with a DOS partition scheme. This stick needs a small UEFI partition as partition #1, and you need to install GRUB to this first partition.
[/LIST]

Good luck!

---

### Post by reggiehg on 2012-08-07
Thanks for your reply, Baloo101. 

> **baloo101 said:**
> Hi  reggiehg. First of all, the only "Apple" answer is : You can't boot  Legacy OS from external devices (read anything than OSX)

Ok, so this is where I got that idea about legacy OS meaning non OSX :-) Sometimes, it just doesn't click the 1st time.

> **baloo101 said:**
> My answer is : It's possible with a mix of  rEFIt, Grub aver many command line (this is how I successful installed  Precise from external CD because my internal superdrive is broke)

Maybe it's possible to boot from USB with the same thing with changing some line of code.

Best regards. If you want to go forward with this I can try to find my documentation or to help you as much as i can.

Cheers.

Cool! Given that my ideal isn't possible, I'd appreciate going forward with your suggestion!

Cheers!

---

### Post by reggiehg on 2012-08-07
Thanks for the reply, Pindar!

> **pindar said:**
> If you insist on performing "a handful of manual steps at most," yes, you may be out of luck. If you want a USB that boots both on your Macbook and on generic PC hardware, I think this is definitely impossible. If, however, you're just looking for a way to make USB stick that will boot your Macbook: I have found two methods which work pretty reliably.
[LIST=1]
[*]The method described [in this post]("http://www.devslashzero.com/node/160") has worked pretty well for me.
[*]Something that's a bit more involved, but very useful: produce a USB stick which is able to boot from an iso image. I have a small USB disk which does that. This means for ubuntu-based (and some other) distributions, I can simply copy the iso to the main partition of the disk and boot from it. But preparing the USB disk/stick is a bit involved and needs more than "a handful of manual steps at most."  You will need to format your USB disk or stick with a GUID partition table; modern Apple hardware will not boot from anything partitioned with a DOS partition scheme. This stick needs a small UEFI partition as partition #1, and you need to install GRUB to this first partition.
[/LIST]

Good luck!

Ok, I checked the link for #1, & it seems similar to the #2 procedure. What's the difference? From what I understand, #1 used vfat, while #2 uses guid/uefi? What makes #2 better? They both seem to use iso images though I don't really appreciate the implications of that.

Btw, you've tested this on MacBook 2,1 right?

TIA!

---

### Post by First Taste Hooks You on 2012-08-11
I can say that I used unetbootin to make a bootable USB with Ubuntu 12.04 on my MacBook 3,1 and it worked great, just put the USB in the MacBook and hold the alt button when booting.

---

### Post by aventrax on 2012-08-24
> **pindar said:**
> If you insist on performing "a handful of manual steps at most," yes, you may be out of luck. If you want a USB that boots both on your Macbook and on generic PC hardware, I think this is definitely **impossible**. If, however, you're just looking for a way to make USB stick that will boot your Macbook: I have found two methods which work pretty reliably.



Impossible? I think is not.
After long night**s** in front of a macbook 2,1 i found a way to have am awesome Debian system (NOT live, that would be really easy) installed on a external usb disk, boooting on my mac and also on my  desktop.

I will write a guide about it.
Two words: refind + recompiled GRUB 2.00 + custom kernel(s).

M

---

### Post by aventrax on 2012-09-03
Nobody seems to be interested, so I'm going to write a small guide here.

1) Partition you externat USB disk using MBR (not GUID) with 2 partitions (or more).
2) Format the first partition using FAT16 (128MB is more than enough).
3) Download and compile grub2. 
4) On your <grub-2-compile-dir>/grub-core/, issue the following command:

../grub-mkimage -O i386-efi -d . -o grub.efi -p "" part_gpt part_msdos ntfs ntfscomp hfsplus fat ext2 normal chain boot configfile linux multiboot efi_uga loopback usb udf iso966

5) The previous step creates a file named grub.efi: rename it to bootIA32.efi and copy it to your disk on the FAT16 partition under /EFI/boot/

note: I compiled grub with "-O i386-efi" option, because my macbook has a 32bit EFI. Change it if your mac has a 64bit EFI. You also must use bootX64.efi in place of bootIA32.efi.
note2: I compiled grub with "efi_uga" module con my macbook has a Universal Graphic Accelerator", on newer macs you probably has to use the "efi_gop" module.

At this point you should be able to boot into your grub hanging on the option key on your mac.
In this is happening, you can go ahead.

7) Format the second partition of the usb disk using ext2/3/4 or whatever.
8) Label your partition as you want using the e2label command. Mine is labeled "usbrootfs".
9) Use debootstrap to populate the filesystem with your linux installation. (or copy your ubuntu installation on it)
10) Copy a working kernel and his initrd to the FAT16 partition
11) Configure /EFI/boot/grub.cfg to load the kernel from it. Pass to the kernel the root= option to indicate where is the root partition. This can be done using root=/dev/sdXX or (better) using root=LABEL=usbrootfs (using LABEL require the use of an initrd )

At this point you should be able to boot in you linux installation from your Macbook.

To boot the same disk on a normal desktop/laptop:

12) Install grub or LILO (apt-get install lilo)
13) Indicate to your lilo.conf the kernel to load and the required initrd, then run lilo -v


That's all. Now you have a disk able to boot on your macbook and also an your laptop without touching anything else than the disk itself.




Bye.
:popcorn:

Here my /EFI/boot/grub.cfg 

```
menuentry "Debian Squeeze 6.0" {
	set root=(hd0,1)
	linux	/vmlinuz-3.4.10 ro
	initrd	/initrd.gz
}
```

---

### Post by pindar on 2012-09-10
> **aventrax said:**
> Nobody seems to be interested, so I'm going to write a small guide here.

No no, I'm really interested in these questions of how to boot apple hardware. I found your guide interesting (though I have no need of such a setup myself), and I have just a few small questions:

[LIST=1]
[*]Is it still necessary to compile grub2? I did this myself and now have a USB drive which will boot my iMac, and won't touch a running system, but shouldn't it now be possible to simply apt-get it and then produce the boot image?
[*]One drawback of your method is that the partition where the actual kernel resides and the /boot directory of the linux installation are different, which means you'll have to manually copy over the kernel and the initrd every time it is updated.
[*]Does this method limit the user to 4 partitions, or would it be possible to use extended partitions on the linux part of the drive? 
[/LIST]
There should be more on this problem in the Ubuntu wiki; there is so much outdated information floating around on the web... So thanks for your guide!

---

### Post by aventrax on 2012-09-15
> **pindar said:**
> 
[LIST=1]
[*]Is it still necessary to compile grub2? I did this myself and now have a USB drive which will boot my iMac, and won't touch a running system, but shouldn't it now be possible to simply apt-get it and then produce the boot image?
[*]One drawback of your method is that the partition where the actual kernel resides and the /boot directory of the linux installation are different, which means you'll have to manually copy over the kernel and the initrd every time it is updated.
[*]Does this method limit the user to 4 partitions, or would it be possible to use extended partitions on the linux part of the drive? 
[/LIST]
There should be more on this problem in the Ubuntu wiki; there is so much outdated information floating around on the web... So thanks for your guide!

Hi... well.. I think is not necessary to compile grub, but is necessary to use the command to make that .efi executable.

2) Once you boot a kernel, you do not need to have the /boot partition mounted. If you want you can put a line in your /etc/fstab that mount the FAT partition in /boot, but it's not necessary.
Once loaded, the system works even if you delete the kernel and the initrd. The modules are on /lib/modules/3.x.x/, so if the system needs a module is not using the initrd anymore.

3) I think you can use extended partition as well. Use that setup only if you need more than 4 partitions, and use a primary partition for the FAT partition.

M

---

### Post by zancudo on 2012-09-25
> **aventrax said:**
> Nobody seems to be interested, so I'm going to write a small guide here.

HERE! am absolutely interested as this is almost what am trying to achieve right now.
I try to dual boot a MacBook2,1 with efi to Snow Leopard and Trisquel an Ubuntu derivate. Right now i use rEFInd as boot manager. and it perfectly loads the grub2 boot loader for Trisquel (Ubuntu). when choosing to start up Trisquel with the boot loader the MacBook goes black screen and reboots after a few seconds... (:

So for now i try to follow your guide for an usb pen to boot the MacBook, hoping i can adopt the technique afterwards and install that grub-efi thing to my hard disk. 

Just to make sure i got it right. The idea is to boot the linux distribution installed to the usb pen, or that at the hard disk?

I followed up to step 11.
when reboot with the option key hit, i can select the usb pen to boot from.
then it loads the grub menu and offers the one menu item from within grub.cfg.
selecting it, results in the same behavior as from my efi boot loader at the hard disk.
after a couple of seconds black screen the MacBook reboots.
there is no error message or something on the screen.

Have you got any idea what it is that i am missing?

any idea is much appreciated!

---

### Post by aventrax on 2012-09-27
> **zancudo said:**
> HERE! am absolutely interested as this is almost what am trying to achieve right now.
I try to dual boot a MacBook2,1 with efi to Snow Leopard and Trisquel an Ubuntu derivate. Right now i use rEFInd as boot manager. and it perfectly loads the grub2 boot loader for Trisquel (Ubuntu). when choosing to start up Trisquel with the boot loader the MacBook goes black screen and reboots after a few seconds... (:

So for now i try to follow your guide for an usb pen to boot the MacBook, hoping i can adopt the technique afterwards and install that grub-efi thing to my hard disk. 

Just to make sure i got it right. The idea is to boot the linux distribution installed to the usb pen, or that at the hard disk?

I followed up to step 11.
when reboot with the option key hit, i can select the usb pen to boot from.
then it loads the grub menu and offers the one menu item from within grub.cfg.
selecting it, results in the same behavior as from my efi boot loader at the hard disk.
after a couple of seconds black screen the MacBook reboots.
there is no error message or something on the screen.

Have you got any idea what it is that i am missing?

any idea is much appreciated!


When I'm going to try things like this, i prefer to go step-by-step.
I do not know your distribution but watching the screen without see anything isn't good to debug what's happening. One thing I don't like about ubuntu is the ******-things that makes impossible to watch the boot process.

In my attempts to make my usb-linux, I do the following:

1) I found  a way to choose the boot device (done using refit or holding OPTION key)
2) I have been able to load grub (you did it too)
3) On the grub console, you can specify a couple of commands :

to "load" a disk or partition  
set root=(hd0,1) 
where hd0 is the first disk, 1 is the first primary partition.

to watch what is inside it:
ls /

here you should see your kernel and eventually your initrd.

to specify the kernel you want to boot:
linux /where/is/it/vmlinuz-3.x.x
initrd /where/is/it/initrd-3.x.x

and, if the steps before was done, issuing the command to boot:
boot

4) If you're here, you are probably in front of your black/blank screen (or maybe not) waiting for your unexpected reboot. Bu you do not know why the system reboots.
So, at step 3, when you was typing the command linux /where/is/it/vmlinuz-3.x.x, is possible to add additional parameters to this command line. For example try all the commands to avoid the splash screens or other non-vga modes (you should search for them).
maybe:

linux /where/is/it/vmlinuz-3.x.x vga=normal nosplash noefi noapic nolapic

all the option listed before are only what I would try in your situation. I don't remember if all of them exists or not. As I said, you should google a lot! =)

5) If you still can't see anything useful for debugging your problem, I would compile my own kernel (I prefer not to use a initrd).

If you need it, I can send you the configuration file for a kernel 3.4.11 that I'm using with my macbook 2,1 (32bit).



Ok. That post is not a solution, It's just a small hit for trying to solve your problem.
I hope you can boot linux on your damn macbook :P

Bye

---

### Post by aventrax on 2012-09-27
I forgot: you can specify to grub if your mac is using efi_uga or efi_gop. Search for it, my mac is efi_uga. I dont know what happens grub is using the wrong module: maybe the system dont show anything and reboots :p

I found it on the proprieties of my mac under OSX somewhere if I remember...

---

### Post by skipperczt on 2012-09-29
I've used this a few times to make a bootable usb....... it's worked every time

[http://penguintosh.com]("http://penguintosh.com")

---

### Post by nobodyfamous on 2012-09-29
> **skipperczt said:**
> I've used this a few times to make a bootable usb....... it's worked every time

[http://penguintosh.com]("http://penguintosh.com")

I second this, works great. Just hold down atl/option while you boot!

---

