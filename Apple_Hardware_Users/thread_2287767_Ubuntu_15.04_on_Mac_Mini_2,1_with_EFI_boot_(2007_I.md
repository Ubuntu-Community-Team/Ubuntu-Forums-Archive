---
title: "Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)"
date: 2015-07-22
forum: Apple Hardware Users
---

### Post by bench on 2015-07-22
I am posting this for the benefit of the community, in case it helps someone else along the way.  I've had some problems getting Linux to install or even boot on this machine.  At some point I did manage to install a version of Ubuntu Server (I think it was 12.04) alongside Mac OS X, booting in BIOS emulation mode, using rEFInd.  However that install never worked correctly to my satisfaction.  Requiring the use of the Mini as a server once more, I turned to the challenge of installing 15.04 Server, single-boot (no OS X), in pure EFI mode, using only the Mac EFI boot loader.

The technical background is available at the [rEFInd Boot Manager]("http://www.rodsbooks.com/refind/") site.

The guide which I followed and which, with a few tweaks, got me up and running, is by [Jason Heeris]("http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/").

On my Mac, I started with a reasonably fresh but basic install of OS X 10.5 with the rEFInd boot manager installed.

I downloaded the Ubuntu Server 15.04 server ISO and then created a bootable USB drive on my Windows 8.1 laptop with [Rufus]("https://rufus.akeo.ie/") for Windows (although I suspect the Universal USB Installer on Windows and the Startup Disk Creator on Ubuntu would have worked as well).

I soon realised (by repeated attempts) that I was never going to be able to boot the USB either via the Mac boot manager or rEFInd.

The first thing to note about the Mac Mini 2,1 is that while it has an x64 processor (Core 2 Duo), it has a 32-bit EFI implementation. It took me a while to figure this out but once I did, I then knew what I need to do to get the Ubuntu Server installer to boot.

I found an article by [sturmflut]("https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/") detailing how to install Ubuntu on BayTrail tablets, which apparently also have a 32-bit EFI. Specifically, it talks about downloading a 32-bit bootia32.efi (for GRUB).  This file is necessary because the Ubuntu installer only supports booting GRUB in EFI mode for 64-bit EFI implementations.

After reading this, I did the following:

1. Removed rEFInd from my Mac so it booted only using the Mac boot loader.
2. Downloaded the bootable CD image of rEFInd from [here]("http://sourceforge.net/projects/refind/files/0.8.7/refind-cd-0.8.7.zip/download") and used Rufus (on Windows) to create a second bootable USB stick.
3. Downloaded the bootia32.efi from [John Wells]("https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi").
4. Placed the bootia32.efi in the /EFI/BOOT folder on the Ubuntu Server installer USB stick.
5. Placed both USB sticks in the Mac, rebooted it, held down the ALT key on my keyboard to bring up the Mac boot manager, clicked "EFI Boot" which was the rEFInd boot image and rEFInd loaded. I then selected the option which included the words "bootia32.efi" in the options (it was an Ubuntu graphic) and selected it. The Ubuntu Installer USB stick then booted, presenting the GRUB menu, from which I could select "Install Ubuntu Server".
6. I then installed Ubuntu server to the internal hard drive, using the partitioning option "Guided - use entire disk", which blew away the existing OS X install. At the end when it tries to install GRUB to /dev/sda, this failed (no matter, it would be re-installed later).

I then manually booted using the same process as before with the rEFInd USB stick, broadly following Jason Heeris' guide.

When I got to this line on installing extra packages:

```
sudo apt-get install mactel-boot hfsprogs gdisk grub-efi-amd64
```

I instead ran:

```
sudo apt-get install mactel-boot hfsprogs gdisk grub-efi-ia32
```

When I got to this line on installing grub:

```
sudo grub-install --target x86_64-efi --boot-directory=/boot --efi-directory=/boot/efi --bootloader-id="$(lsb_release -ds)"
```

I instead ran:

```
sudo grub-install --target i386-efi --boot-directory=/boot --efi-directory=/boot/efi --bootloader-id="$(lsb_release -ds)"
sudo update-grub
```

The second line is necessary to actually add the boot menu entries. Not sure why it was not required by Jason Heeris, possibly because his GRUB installed during the installation successfully?

I then rebooted and my system booted straight into Ubuntu Server 15.04, in pure EFI mode. The system appears to be more stable than my last installation and will reboot headless (which the the 12.04 installation wouldn't).

I have one outstanding issue (unrelated to the install) which I will post in another thread.

This process should work on any Intel Mac which has a 64-bit processor and a 32-bit EFI (and for any variant, Desktop, Kubuntu, etc).

Happy to answer any questions!

Regards

---

### Post by Hindrik_Hettema on 2016-01-04
In addition to the above procedure, I had only a problem when at a certain point in [Jason Heeris]("http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/") explanation you need in GRUB to start-up using the UUID of the just created boot partition - how to obtain that UUID.

After some googling I found the response of [terminator14]("http://ubuntuforums.org/showthread.php?t=2140115&p=12628843#post12628843") from which I copy the essential part below:
> 
I suppose the other option is to just run it without the 'root=' part, instead adding 'break' to the kernel like so:

```

    set root=(hd0,msdos1)
    linux /boot/vmlinuz... break
    initrd /boot/initrd...
    boot
``` 
This will stop the boot process at an initrd shell, at which point you can use:

     ```
ls /dev/sd*
```
to see the available partitions, and mount them to a temp  directory to see which is the right one. Once you find the right one,  you can also use:

     ```
ls -l /dev/disk/by-uuid/
``` 
to find the disk's UUID if you are concerned that the device name  might change after a reboot, which you will have to do to get back to  the grub menu.


---

### Post by Hindrik_Hettema on 2016-01-04
In addition - I have tested the procedure with [linux mint 17.3]("http://www.linuxmint.com/edition.php?id=204") and that works as well - note that linux mint does not have the signed EFI vmlinuz executable, but that was no problem.

---

### Post by bench on 2016-01-08
As I recall, I didn't bother with that step regarding the UUID in the initial manual boot of grub. I have only one disk in my machine so I just used "root=/dev/sda2" as a kernel parameter. Of course my /etc/fstab has the UUIDs for the filesystems but I seem to think Ubuntu entered those correctly anyway.

---

### Post by Peter_R._Wood on 2016-06-18
> **bench said:**
> 
4. Placed the bootia32.efi in the /EFI/BOOT folder on the Ubuntu Server installer USB stick.


I'm trying to install Ubuntu on my Mac mini 1,1. I'm building the necessary boot/install USB sticks on a Macbook 4,1 which is already running Debian, and when I try to do the above step on this machine, I'm not able to write to the USB stick - it tells me that it's read-only, which I'm assuming is because it was formatted using an ISO. Did you have to do anything special to make the USB stick writable?

---

### Post by emielleon on 2016-11-05
Hi,
I installed it succesfully and it kinda works now. I'm not sure what exactly is wrong, but the video performance sometimes is very good, but other times it just stands still with nothing happening. I don't understand what went wrong. Can somebody help me out? I think it has something to do with the video drivers, but I don't know how to check since 'Additional Drivers' is nowhere to be found. I btw have the same model as you do, but I'm using elementary os, since it has a lot in common with Ubuntu and it looks so good.

---

### Post by petermacrobert on 2017-01-15
The Ubuntu installer ISO is slightly non-standard so it doesn't mount cleanly on OSX or Ubuntu. I found that OSX would flatly refuse to mount it, and Ubuntu would mount it read-only.

The workaround is to create a new ISO from the base Debian ISO, plus the extra file bootia32.efi in /EFI/BOOT, and then write the new ISO to a USB drive. 

I used ISO Master on Ubuntu (inside Parallels on my Mac) to add the file and create the new ISO, but there might be other apps out there.

---

### Post by petermacrobert on 2017-01-15
Very helpful guide, worked a treat on my 2007 MacMini 2,1. Thank you!

---

### Post by kevin160 on 2017-05-22
A few months back I used this little guide to install 16.04 Server on my macpro 1,1 and it has worked like a charm.  Even openvswitch with DPDK hums along on an 11 year old machine!  

I upgraded today to 17.04 (via 16.10) and the upgrade went fine, but I can only boot with the 4.4 kernel.  The 4.10 kernel gets to the point where it loads the initrd and then the screen blanks and the keyboard locks up.  

The only obvious difference is that the new kernel boot scripts default to the signed version.  Macs don't need secure boot, so I adjusted the boot setting in grub to boot the ordinary kernel, but no joy.  

Is anybody with a 32bit EFI mac able to run a kernel above 4.4?

SORTED:  I added "noefi" to my kernel boot parameters and I'm running 4.10.

---

### Post by bench on 2017-05-26
@kevin160, thanks for this information.  I am currently running the same installation as I detailed above 2 years ago, but I have upgraded through to 16.10.  I think I will hold off upgrading to 17.04 for the time being and do some research into this, seems it maybe a bug - the noefi parameter has been around a long time but has never been necessary before.

Would you mind sharing any source information which pointed you to this kernel parameter?

---

### Post by salem-ok on 2017-05-30
Hi There,

I have been working on installing Lubuntu 17.04 alongside OS X on my Macmini 2.1 and just completed the project.

Here is what I did:

1- Partition the main HD (Shrink the OS X partition and and leave 20Gb Free Space for Linux)
2- Install REFind (not sure I needed to do that but it felt reassuring)
3- Download the amd64 distro of Lubuntu 17.04
4- Modify it using the little C program provided by Matt Gadient: [https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)
5- Burn it on a DVD
6- Boot Lubuntu from the DVD (will not work if  step 4 is not done, as Matt explains very well on his page)
7- Run the normal Lubuntu Install - it detects the free space on the main HD and installs Lubuntu gracefully alongside Mac OS X

Now when I boot I have the REFind menu and then the GRUB menu, which seems redundant, but apart from that everything works fine and most importantly, I didn't break the OS X installation.

I hope this helps, it took me a lot of trial and error (goose chase to try and boot from a USB Key, trying to boot several distros from DVD, etc.) to get to a simple path to install this dual boot.

Thanks,

---

### Post by bench on 2017-05-30
@salem-ok,

Thanks for your write up.  I checked out the link you provided in (4).  The process describes in this article converts the install media so that it boots and installs in BIOS emulation mode.  I should have been clearer in my original post that the install process I describe results in a system which is installed in pure EFI mode, with a GPT format drive, and with no OS X.  I think my original 12.04 install which I described was installed in this way (dual boot, hybrid MBR/GPT drive, BIOS emulation mode - except I had the benefit of the "mac" ISO images in those days) - but it never worked satisfactorily in my opinion (issues with hanging on boot for instance).

Thanks.

---

### Post by kevin160 on 2017-06-02
> **bench said:**
> 
Would you mind sharing any source information which pointed you to this kernel parameter?

Ah, yes, I should have provided the source:  [Sergey's Blog]("http://blog.sergem.net/how-to-install-ubuntu-14-04-on-macpro-11-efi-boot-mode/") 

I haven't tried it, but I imagine that passing "noefi" would allow installing 17.04 fresh.  

As an additional note, I have found [Super Grub2]("http://www.supergrubdisk.org/super-grub2-disk/") on a USB stick to be very helpful installing and troubleshooting Linux installs on mac hardware.  It boots on efi32 macs and automagically finds installed linux and existing grub configs.

---

### Post by kevin160 on 2017-06-02
> **bench said:**
>  I think my original 12.04 install which I described was installed in this way (dual boot, hybrid MBR/GPT drive, BIOS emulation mode - except I had the benefit of the "mac" ISO images in those days) - but it never worked satisfactorily in my opinion (issues with hanging on boot for instance).

Agreed.  When I installed Ubuntu in BIOS aka Bootcamp mode, I found that my SATA drives were only available in SATA-I (1.5 Gb/s) mode and some devices seemed to be missing.  EFI is the way to go IMHO.

---

### Post by salem-ok on 2017-06-18
Hi guys,

Here is some feedback after a few weeks of running the setup I described above: zero issues to report. The Mac Mini boots fine, both in OS X and Lubuntu I shortened the GRUB wait time and now the bot time is satisfying. I have not noticed any of the issues you describe.

The mac mini original internal drive is detected as follows: Not sure if that is what you would expect.

[IMG]https://lh3.googleusercontent.com/3OA7GNW764sroOTCGdg93QbFfv1Bjgj-yVmbAR-AinsuczUyNlIeQWXLfTH_b1CQ_r2r19VB1-PUw1S61d63OGOk1KcX2Ouer73tXyXob8gr2syG1PmBv5rgLTt9abi6qYcuAw=w784-h601-no[/IMG]


On a side note: I use this box as a Plex Server and the performance, image and sound quality is far superior to what I used to get streaming from the same Plex server on Snow Leopard. 

Being more confident with Linux running on this box now, I might give a try to the full EFI installation method for future OS upgrades.

---

### Post by kevin160 on 2017-06-20
Hey, as long as it's doing what you need it to, it's all good!  ;-)  

I think your HD is SATA-I (1.5 Gbps) anyway, so it doesn't matter, but for future reference, if you do a "dmesg | grep -i sata" you'll see lines like 

[    2.173156] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.173175] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

that show you the connection speed between your disk controllers and disks.

---

### Post by Trav1s on 2017-08-22
Thanks for all the great documentation in this thread.  I just picked up a Core 2 Duo 2.0 Mini (I think it is 1.1) at a local recycler.  I am going to upgrade it to a Samsung 128GB SSD, 2.66 processor, and 4gb of ram (if I have have the DDR2 in the tech stash) and plan to run Ubuntu Mate (not sure if I will go LTS or 17.04)  I am not sure if it is 1,1 or 2,1 but it will get upgraded to 2,1 if it is the older version.

---

### Post by simonr12 on 2017-11-09
@bench thanks for these instructions, I've just followed them to install 16.04 and with some minor changes everything has worked out great..

@Trav1s I've just done the same thing with an old 1,1 MacMini, it's well worth the effort..

Here's my notes on installing 16.04:

[LIST=1]
[*]Burned rEFInd to a disc to boot from (on macOS)
[*]Mounted the Ubuntu server ISO on a Ubuntu VM, copied the contents, added the bootia32.efi and then created a new bootable ISO (see: [http://bencane.com/2013/06/12/mkisofs-repackaging-a-linux-install-iso/](http://bencane.com/2013/06/12/mkisofs-repackaging-a-linux-install-iso/))
[LIST]
[*]```

mkdir -p /mnt/ubuntu
mount -o loop [/path/to/ubuntu.iso] /mnt/ubuntu
cd /mnt/
tar -cvf - ubuntu | (cd /tmp/ && tar -xf - )
cd /tmp/ubuntu
# make your changes
mkisofs -o ../your-new.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -R -V Ubuntu .

```
[*]Note: I named the ISO "Ubuntu", this *may* have been the source of some issues later in the process..
[/LIST]

[*]Cloned my ISO to a key on macOS (see [http://osxdaily.com/2015/06/05/copy-iso-to-usb-drive-mac-os-x-command/](http://osxdaily.com/2015/06/05/copy-iso-to-usb-drive-mac-os-x-command/))
[*]Booted into and started the Ubuntu install as per the instructions
[*]During the install I had two issues possibly related to the name of the ISO (I'm not sure) but I found workarounds pretty quickly:
[LIST=1]
[*]First issues was a problem with the installation disc being found (see: [https://cloudnull.io/2016/11/install-ubuntu-16-04-x-from-usb-media/](https://cloudnull.io/2016/11/install-ubuntu-16-04-x-from-usb-media/)):
[LIST]
[*]```

# when asked if you want to "Retry mounting the CD-ROM?" select No, return to the install menu and choose "Execute a shell" and run:
blkid
# look for the partition LABEL="Ubuntu.." and note the path (e.g. /dev/sdc1) and mount this manually - changing [sd*] to the correct path
mount -t iso9660 /dev/[sd*] /cdrom -o ro
exit

```
[*]This should allow you to continue the install
[/LIST]

[*]Second issue was when the install was at "Configure the Package Manager", it was just silently failing at around 20% and returning to the main menu - to get passed this:
[LIST]
[*]```

# on the install menu choose "Execute a shell" and run:
umount /cdrom

```
[*]Then select "Configure the Package Manager" to continue
[/LIST]
[/LIST]

[*]After install, during the instructions to first boot the drive from the Grub console, I found ```
ls -l
``` wouldn't work, so I used ```
cat /etc/fstab
``` to find the UUID of the drive(s)
[*]After finishing the setup as per the instructions, the system booted, I saw the Ubuntu server splash, but would then be presented with a black screen (the system was booting however, as as services were up, also booting in recovery mode would work fine. To resolve this I booted in recovery mode and edited ```
/etc/default/grub
``` removing ```
quiet splash
``` from ```
GRUB_CMDLINE_LINUX_DEFAULT
``` No more splash screen, but a perfectly booting system..
[/LIST]

Hope these help someone..

---

### Post by ratell on 2017-11-09
I did a fresh install of 17.10 onto a 2007 intel Imac which I believe has the same 32bit EFI. The only difficulty I had was needing to use nomodeset for the video card. I think the difficulties described in this thread may no longer be an issue.

---

### Post by Trav1s on 2017-12-19
Finally getting back here for an update...

I finally upgraded my 2,1 Mini T7200 process/4GB DDR that I picked up at the local recycler.  After sitting on their shelf for over 6 months, a little cash lowered the price a fair amount.  For the upgraded, I purchased a t7600 processor from eBay for under $18 and a used 128GB Samsung SSD (from the same local recycler where I got the Mini) for $20 cash.  The upgrade process was relatively painless other than broken plastic spring pins hold the heatsink in place.  Replaced them with some 1"xM3 screws and it went back together.  

Here's the fun stuff of the project:  The 128GB was previously installed in a Dell Optiplex i5 machine and was completely up-to-date with Mate 17.10.  I simply removed the drive from the Dell and reinstalled it in the Mini.  When I powered it up for the first time, the Mini booted into the Mate install from the Dell without a problem.  I have forced additional updates, installed new programs, and used the previously installed programs without any problem.  Currently the machine resides on the workbench in my garage and is used for music streaming, social media, and other online stuff.  I am very impressed how responsive this machine is for its specs.

---

### Post by mörgæs on 2017-12-20
The method of moving a hard disc containing a complete operative system is also a good workaround if the computer neither boots from USB nor DVD.

---

### Post by vctls on 2018-01-01
After a day trying to install Lubuntu 17.10 x64 on a spare Samsung 840 Pro 128GB used as a replacement, here's what worked for me:


[LIST=1]
[*]Copy the installation iso on a flash drive. 
[*]Copy the 32 bit efi file into /efi/boot. 
[*]Hold Alt, boot on the flash drive. 
[*]Select "Try Lubuntu". 
[*]Change the resolution to something like 1280*1024. 
[*]Zero the drive (sudo dd if=/dev/zero of=/dev/sda). 
[*]Connect to an internet connection. 
[*]Launch the installer, select « guided, use entire disk ». 
[*]Select « Download updates during install ». 
[/LIST]

A few explanations:
Apparently, rEFInd wasn't even necessary. Simply putting the 32 bit efi file in /efi/boot allowed me to boot on the flash drive.
I had actually tried to boot through rEFInd before, but all I got was [this series of errors]("https://i.imgur.com/Jdi5YHP.jpg") (« Not Found from LocateDevicePath », among others).

The mac mini was really struggling with the native resolution of my only monitor at hand, which is 3440*1440.
Actually, LXDE was the only usable desktop at that resolution.
Gnome lagged like hell, Unity straight out crashed.
So to prevent any funny behavior, I lowered the resolution as soon as I could boot on the installer.

On previous attempts, I got errors about the installer not being able to copy files on the drive, which is why I zeroed it. Might not be necessary.

Lastly, connecting to the internet and downloading the updates during installation was apparently a critical step.
As stated in [this askubuntu answer]("https://askubuntu.com/a/400676"), that resolved the bootloader installation error.

After that, I was able to immediately boot on the newly installed OS without any issues.

---

### Post by guga-a on 2018-01-06
[COLOR=#111111][FONT=Menlo]Hi guys, hope you could help me because I am going crazy!

I have a [2.0GHz Macbook late 2006 (MA700LL/A)]("https://support.apple.com/kb/SP23?viewlocale=en_US&locale=en_US") with OSX 10.6 on, and I would like to install Lubuntu, so I can use this machine as a Plex Server.
I need to boot from a USB Key but I tried and failed! After few days browsing, finally I found out the solution on this thread but I am not sure how to proceed.

I tried to boot Lubuntu 17.10 (LXDE) (64-bit Mac) – 921 MB from [Matt Gadient's page]("https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/") 
My actual [Macbook]("https://support.apple.com/kb/SP649?viewlocale=en_US&locale=en_US") recognises the USB but I cannot boot from old Macbook. I reckon that is due to the 32-bit EFI but, even after I installed rREFit, I still fail!

As you know I am not an expert. Could you please help me to solve the problem?
Is Lubuntu the best option for the Plex server? 
How do I copy the 32 bit efi file into /efi/boot without using Ubuntu VM?

Thank you so much for your help and time.

G.[/FONT][/COLOR]

---

### Post by doublek66 on 2018-05-11
Hi everyone,

I am beginner in Ubuntu and trying to install on a Mac Mini2,1, when I come to this step,
sudo apt-get install mactel-boot hfsprogs gdisk grub-efi-ia32

it said cannot locate the the mactel-boot and hfsgprogs package, I am trying 14.04 and 16.04 desktop not server version, is it only available in server?

Also tried to use this [boot-repair tools]("https://askubuntu.com/questions/142750/after-installing-ubuntu-from-usb-grub2-cant-be-installed"), but it said my version do not support but this [blog]("http://digiecologist.blogspot.hk/2015/12/installing-ubuntu-on-2007-mac-mini-a1176.html") said that it can fix the problem on Mac Mini, I confirm the model I have is Mac Mini2,1 but all the result is different from what I see on Internet and feeling frustrated.

---

