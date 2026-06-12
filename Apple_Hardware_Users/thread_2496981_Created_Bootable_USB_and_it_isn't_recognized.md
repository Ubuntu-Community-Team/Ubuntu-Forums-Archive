---
title: "Created Bootable USB and it isn't recognized"
date: 2024-04-18
forum: Apple Hardware Users
---

### Post by w00die2 on 2024-04-18
Downloaded latest Ubuntu ISO
Downloaded Etcher
Installed etcher just fine on my Mac Mini Running Catalina 10.15.7
Ran Etcher
Installed a USB drive and Flashed it just fine

Installed the USB into my iMac late 2006 model running 10.6.8 currently
Rebooted holding the Opt key
The only boot option showing is the Hard drive and no USB shown 
Stuck

Any suggestions?

---

### Post by TheFu on 2024-04-18
Your idea of "latest Ubuntu ISO" is unlikely to be the same as others.  Right now, that could be at least 3, if not 15 different ISOs.  Please be specific. Use the release numbers and specify the DE used.

You might find more helpful replies if this were posted in the Apple HW subforum.  I have no idea which CPU an iMac from 2006 had.  In general, computers from 2006 are mostly too old to run {Ubuntu, unless they were top end at the time.  But if that has a 64-bit Intel Core2 Duo CPU 4+GB of RAM and you stay with a very light DEs/GUIs, then it shouldn't be too bad an experience.  If you want a better experience, go for Lubuntu or Xubuntu with 22.04 release number ... for now.  Avoid Gnome - it won't be great or it might be terrible.

Do you happen to know the GPU?  nVidia GPUs from that time have all lost nVidia support by now.  The best you can hope for is to use a F/LOSS GPU driver, not the proprietary nVidia driver. I wish I could say this happens automatically, but since I don't use 22.04 as a desktop, I don't know.

For people really new to Linux, 24.04 shouldn't be used, nor should 23.10. Those are unstable at this point.  I've been using Linux since 1993 and I won't bother with odd-year releases at all and the earliest I'll use 2024's upcoming release will be June, if I'm forced and August if I have a choice.  I want to avoid all the early release bugs that always happen, but stay on an LTS release with 3 yrs of standard support.  Odd year releases have 9 months of support, from their release date, so 23.10 support will end in June '24.

Of course, if you like reinstalling OSes, just to see what's up, feel free and check out all the releases you like.

Can an iMac boot from a flash drive?  I know computer of that time had some USB ports that wouldn't boot and some flash drives that wouldn't boot, so the trick was to get a working port with a working flash drive.  On my Dell laptops of that era, about 50% of my flash drives didn't work for booting any OS.  Newer computers, say less than 10 yrs old (2015) and later tend to support booting from almost any port and any flash storage.  As time moves forward, stuff gets better support and hardware followed standards better.

Anyways, that's all the suggestions I have. Hopefully, a moderator will move this thread to the Apple sub-forum, if that really is a better place for it. IDK.

---

### Post by ajgreeny on 2024-04-18
As suggested by TheFu, moved to Apple  Hardware where you might get a much better response.

---

### Post by w00die2 on 2024-04-18
This version, which is the latest: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
What does GPU have to do with making a bootable USB?
This is the instruction for installation: [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
I'm assuming the issue is the installation instruction is flawed or what I'm doing is flawed.
I don't know which yet.

---

### Post by d018398 on 2024-04-22
Hi,

I have the same machine and had the same problem. Some USB worked - but most were not recognized.

You can fix this by creating your stick via [YUMI]("https://pendrivelinux.com/yumi-multiboot-usb-creator/#Download_YUMI") . You can put multiple ISOs on the stick and test them one-by-one.

The YUMI usb stick is always recognized by the iMAc 5.1 (late 2006).

Going through the GRUB boot loader option adding "nosplash noefi nomodeset" will help, in case the normal start-up per distro gets stuck.

This way I managed to live-boot: Lubuntu 22.04, Fedora, Mint, Elementary OS and some others.

But I get stuck after installation on hard disk is complete. When booting without USB, the system does not start properly.

Most of the time I get a black screen.

Good luck.

Jochen

---

### Post by TheFu on 2024-04-22
> **w00die2 said:**
> This version, which is the latest: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

That link doesn't answer the question. There are 2 versions there and to some people, neither of them is "the latest", hence why I specifically asked what version.  Any day now, there will be a "new" new version and the download servers will be busy with people trying the newest LTS release, 24.04.  I expect it this week, sometime.

Apple hardware is "different".  When creating instructions, the target audience for simple instructions is for the most likely hardware someone will bring. As a guess, that would be hardware that is 1-5 yrs old.  I don't really know the actual make up of hardware used by people new to Ubuntu since my experience is warped by University students usually with new or 1 yr old laptops trying to install Ubuntu (or any flavor of Linux they choose).

Other apple users will need to help.

---

### Post by oldfred on 2024-04-22
Is this Mac a core2duo (64bit) & 32 bit UEFI boot?
The standard installer does not include the 32 bit UEFI boot files.

Old Mac with core2duo & 32 bit UEFI
[https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)

Old Mac  Late 2006 iMac (iMac6,1) 18.04 with patched nVidia 304
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)
Mac 2007 delete gfxmode $linux_gfx_mode
[https://ubuntuforums.org/showthread.php?t=2420243](https://ubuntuforums.org/showthread.php?t=2420243)


How much RAM? 
New Ubuntu expects lots more RAM than those old systems. 
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I was able to use Kubuntu with my 2006 PC with only 1.5GB of RAM, Ubuntu would not install.

---

