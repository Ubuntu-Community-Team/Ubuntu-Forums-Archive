---
title: "iMac G3 400 Won't Boot Ubuntu"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by Gokussj5okazu on 2009-01-18
Alright, I've got a troublesome Mac on my hands. I bought it with a wiped hard drive, no OS. Well, I don't have a copy of any Mac OS so I thought I'd throw Ubuntu onto it. I got Ubuntu PPC Alternative on my XP machine, burnt the image (yes, as an image, not data), but I can't get the darn Mac to boot it. I've tried clearing the P-RAM and everything.

I've burnt to 3 different types of CD-Rs, and everytime hold down 'C'. I can hear the disc spin but it always ends up at the folder with the flashing question mark. Any ideas? I've heard the iMac G3's can have quirky drives that won't read much, any way to get aroudn that? I don't have a second Mac to do a firewire install or anything.

---

### Post by Audacitor on 2009-01-18
If it has a USB port (I can't remember if so), you could try it with a flash drive.

---

### Post by SNAFU0062000 on 2009-01-18
I have the same thing going on But i do have os X on here. But when  evey i try to boot the same happend i hold down C i hear the cd drive spin but it just will not boot i got the Cd from my girl friend room mate and he has it installed on his computer. so i know  the disk is fine. My Imac spec ImacG3 powerPC 750@ 700mhz 1g ram and 60g HD i need help to installing.

---

### Post by Gokussj5okazu on 2009-01-18
Thanks Audacitor. It does have USB ports, but I only have a 256mb flash drive. What would be a small enough distro that's not too hard to install? I tried for DSL, but it's not PPC based.

---

### Post by oswaldkelso on 2009-01-18
> **Gokussj5okazu said:**
> Alright, I've got a troublesome Mac on my hands. I bought it with a wiped hard drive, no OS. Well, I don't have a copy of any Mac OS so I thought I'd throw Ubuntu onto it. I got Ubuntu PPC Alternative on my XP machine, burnt the image (yes, as an image, not data), but I can't get the darn Mac to boot it. I've tried clearing the P-RAM and everything.

I've burnt to 3 different types of CD-Rs, and everytime hold down 'C'. I can hear the disc spin but it always ends up at the folder with the flashing question mark. Any ideas? I've heard the iMac G3's can have quirky drives that won't read much, any way to get aroudn that? I don't have a second Mac to do a firewire install or anything.

If it can boot the osx disk (so the drive is ok) a bad iso is the main culprit. Did you check the md5sum and burn slowly imac drives are very picky, only minus -discs usualy also. check.

---

### Post by Gokussj5okazu on 2009-01-18
I don't have a Mac OS, but I'm certain the Iso burned fine. I burned it the same way I burnt my copy for my PC, 1x on a good quality CD-R. 

In the iMac's Open Firmware, I was able to find and detect my flashdrive, so it seems that way would be plausible. I just don't know how to go about that method.

---

### Post by marshag63 on 2009-01-18
When I put Ubuntu on my G4 iMac, I had to old the "C" key down clear up until I got to the command prompt - I had to hold it until it even started typing the letter "c" at the command prompt, then I could backspace to delete the extra "c"s and then press tab to pick boot options.  

Mg

---

### Post by Montblanc_Kupo on 2009-01-18
Many "old world" macs, which this one might be depending on the motherboard inside, won't boot anything but mac os. The way around this is you have to install mac os on it, then use bootx to take care of the linux boot (newer machines will use yahboot). Basically what happens is that something like mac os 9 will start to boot the machine, then it will load bootx as an extension which will immediately pop up and give you a little graphical bootloader to choose which os to load. It requires you to install a mac os because of the mac hardware lockdown, and drop a couple of the kernel files onto the drive so that it can handle the loading process.

Take a peek at these links:
[http://www.ppcnux.com/?q=node/7024](http://www.ppcnux.com/?q=node/7024)
[http://penguinppc.org/bootloaders/bootx/](http://penguinppc.org/bootloaders/bootx/)

Also... with the imacs and ibooks... you often have to experiment to get a video mode that works for you... it's... less than fun... although you might get lucky and just have it work right off.

---

### Post by pxwpxw on 2009-01-18
> **Gokussj5okazu said:**
> I don't have a Mac OS, but I'm certain the Iso burned fine. I burned it the same way I burnt my copy for my PC, 1x on a good quality CD-R. 

In the iMac's Open Firmware, I was able to find and detect my flashdrive, so it seems that way would be plausible. I just don't know how to go about that method.

I think you have a New World g3 there.
Then if you have a network connection on the g3

[http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/netboot/](http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/netboot/)
(or if you dont want intrepid, there are other ubuntu versions available there)

On the usb stick put

vmlinux 
initrd.gz
yaboot
yaboot.conf

The usb should best be formatted hfsplus, but other formats can work, if you are seeing it with open firmware.

Then boot from open firmware
```

0> boot usb:,yaboot

```
except you will have to substitute the correct usb device by finding it with the 'dir' command.

Then it loads the full installer from the internet.

---

### Post by Montblanc_Kupo on 2009-01-18
> I think you have a New World g3 there.

From what I can tell the cutoff was halfway through the fishbowl imacs (the bright colored crt ones). If it's slot loading... it's new world... if it's tray loading it's old world.

If you're running old world... you pretty much need mac os to boot linux. If it's new world, yahboot should be able to pick up and load linux. You might grab an mac os disc from a friend if you don't have one and just see if it boots with mac os... that would rule out some weird hardware problem preventing booting. Macs are pissy about the batteries inside too. If you can't get it to boot from mac os install, you might try nuking the pram, nvram, and do the power management reset. That's all pretty "worst case scenario" though... macs are pretty bullet proof (heh.. in fact the original imacs were made of bullet proof polycarbonate.... I saw this proved with a .38 revolver once).

If you're sure you have a new world rom in the mac... and it still won't boot... possibly try an older distro of ubuntu or another ppc distro of linux entirely. I had some work better than others when I was playing around with My old G3 powerbook.

[http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active](http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active)

---

### Post by Gokussj5okazu on 2009-01-18
Alright, I got somewhere! Woo!

Turns out my dvd drive was shot, soo I managed to temporarily hook up another drive and got Ubuntu installer running. It all finished up and restarted after I took out the cd.

So, according to [THIS]("http://ubuntuforums.org/showthread.php?t=405934"), my next step is to login and run

sudo apt-get update

sudo apt-get upgrade

However, I don't get a prompt to even log in. Several screens go by, without giving me time to interact with them. It stops on a screen that says;

```
Loading, please wait...
[38.461143] ohci1394: fw-host0: SelfId received outside of bus reset sequence

Check root= bootarg cat /proc/cmdline
tab or missing modules, devices: cat /proc/modules 1s /dev
Alert! dev/hda3 does not exist. dropping to a shell!

BusyBox v1.1.3(Debian 1:1.1.3-5Ubuntu7) Built-In Shell(ASH)
Enter 'help' for a list of build-in commands.

(initramfs)
```

Any ideas? I'm lost.

---

### Post by Gokussj5okazu on 2009-01-19
Slight update, kinda. I re-did the install, and it changed a bit. Now it goes to the Ubuntu loading screen, but the loading bar doesn't move. If I let it sit for about 5 minutes, it goes to a black screen saying;

```
BusyBox v1.1.3(Debian 1:1.1.3-5Ubuntu7) Built-In Shell(ASH)
Enter 'help' for a list of build-in commands.

(initramfs)
```

Help?

---

### Post by Gokussj5okazu on 2009-01-19
Ugh!! This keeps getting worse. I burnt a copy of Ubuntu Live to see if that would work. I put it in and it tries to boot and everything, but when it comes up saying;

Loading, please wait....

The computer shuts off there. It's the same spot that the already-installed copy was having problems. If I boot the Live CD as "live-nosplash" then it comes up with that exact same BusyBox error! Ugh!

---

### Post by stream303 on 2009-01-19
With busybox coming up, it sounds like you are tying to install Gutsy 7.10.  This has a known problem that needs to get fixed - check out this wiki for the solution about half-way through the doc about *modprobe ide-core*:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

Don't confuse this with Intrepid's bug, where you need to use *modprobe ide-scsi* in a virtual terminal to help it find the cdrom. :)

Also, you will have to manually edit your /etc/X11/xorg.conf file to get graphics up properly:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

What can make this difficult is that in newer releases, xorg.conf may be unpopulated or very slim as compared to the older releases, so if you aren't familiar with the xorg.conf syntax, it can be a hair-pulling experience.

One option is to use Debian "stable" 4.0r6.  It doesn't have any of the busybox or cdrom detection bugs, has a full xorg.conf file for one to easily modify, and you can use everything you've learned here to get it running.  You can apply the graphics fixes to xorg.conf from these wiki's to it.

Highly recommended for a first-time install!

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Just be sure to get the powerpc "stable" version.  Once you get your feet wet with that, and have a working xorg.conf, you can later decide if you want to tackle Debian Lenny, or perhaps go back to Ubuntu Hardy or Intrepid.

---

### Post by Gokussj5okazu on 2009-01-19
Ok, well I tried that just now and it didn't help. I started with typing

```
modprobe ide-core
exit
```

at the BusyBox prompt, and it just said "no such file or directory" over and over.

Soo, I tried adding 

```
break=top
```

at the Yaboot prompt. This still brought up the BusyBox prompt, but it disabled my keyboard! Any more ideas?

---

### Post by nogoldformarfa on 2009-01-20
I have an ibook g3 dual usb with 500mhz processor and i am running into the exact same problem word for word. I am going to try to use the debian install.

I have had nothing but trouble with this crazy mac

ive tried loading xubuntu with the no-spalsh powerpc commond and i get nothing but busy bo and when i try to probe the ide to find the cdrom drive it fails and just cant find the disk or invalid disk or something 

Any help would be greatly appreciated

---

### Post by stream303 on 2009-01-20
Is that external dvd drive disconnected when you try to boot after the installation?

It looks like it can't find /dev/hda3, which should be the root partition.  When you installed it, did you let guided partitioning "use the whole disk" ?  I'm wondering if you tried to install to some dinky left-over partition on that suspect drive.

We also don't know if the previous owner may have installed a non-oem replacement drive that is larger than 128gb.  If so, you'll have to keep the / root partition below 128, make it 125 or so to keep it off the boundary when you do custom partitioning to keep / root below 128gb.  Possibly - we just don't know about that hard drive either.

---

### Post by Gokussj5okazu on 2009-01-20
The new DVD drive, through a longer IDE than stock, stays connected even after the install is done. When installing, I told it to use the whole disk, which is a brand new WD40GB drive.

---

### Post by Gokussj5okazu on 2009-01-22
Bump! 

Anyone? I'm trying Debian next.

---

### Post by noriek on 2009-01-22
Hi.

Nothing but grief for me with PPC *ubuntu too (iMacDV G3 400Mhz). Installed Debian 40r4a using the PPC Net install disc.

Installation without a hitch, no work-arounds etc.

Could then possibly install ubuntu linux kernel and desktops using apt but unsure if that's possible currently. Will let you know if I try. Otherwise Debian works out of the box with only the fewest of annoyances. (40r4a PPC net install)

---

