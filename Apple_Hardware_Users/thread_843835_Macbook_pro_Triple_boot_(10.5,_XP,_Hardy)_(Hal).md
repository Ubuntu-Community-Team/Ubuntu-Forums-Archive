---
title: "Macbook pro Triple boot (10.5, XP, Hardy) (Hal?)"
date: 2008-06-28
forum: Apple Hardware Users
---

### Post by Quipacorn on 2008-06-28
I am trying to get a triple boot to work on my macbook pro, revision 3 (Santa Rosa), 2.4 Ghz
I have followed most of the guides available on the web in various places to no avail with one particular issue.

First, I install os X to the drive as usual
second, Separate out 23 Gb for Bootcamp
third, install windows in the partition created
fourth, boot Hardy from live cd, scale down XP partition to 13 Gb, and allocate 10 for hardy
and create ext3 partition.
Install hardy, with grub in installed on /dev/sda4 (The hardy partition)
then, no matter what, on reboot and selection of XP with rEFIt i get the hal.dll is missing, and therefore will not boot
ubuntu works fine
and if i restore the xp partition to the full 23Gb it will boot
ive also tried fixing the MBR (via windows), and backing up the mbr before hand
i understand this issue may not be possible to be easily covered in this discussion board
but could anyone offer any suggestions? similar issues?

thank you in advance

regards

---

### Post by DonnieP on 2008-06-29
No answers but a couple of suggestions:

1. Wipe XP's previously scaled down partition and reinstall XP there, or
2. Boot to a CD like SystemRescueCD and use gparted to create the two non-Mac partitions (in other words, forget Bootcamp).  Then install XP and Ubuntu.

---

### Post by promodus on 2008-06-29
Are you able to boot Windows XP by holding down the option key and getting the bootcamp menu?

For me, if I hold option after the boot chime I get the bootcamp menu. My options are OSX or Windows.
if I select OSX I then get the rEFIt menu.

My install order was
rEFIt, Bootcamp, windows xp. I haven't done the Ubuntu portion, yet.
What version of Ubuntu? Is all your hardware supported?

---

### Post by DonnieP on 2008-06-29
Actually, promodus, you're supposed to get the rEFIt menu when you *don't* hold down the option key - you just boot normally and you get the rEFIt menu.  At least, that's the way mine works.  I have Ubuntu Hardy and openSUSE 11 installed in addition to OSX.  They both work fine, except for the webcam, and also I had to do some digging to find a Linux driver for my all-in-one printer.

---

### Post by Quipacorn on 2008-06-29
Thanks for the suggestions
i was able to finally get it to work, i was off a little on the partition scheme, and after fixing that i wouldn't get the HAL message with XP but it would crash immediately after the splash screen, so i used a norton Ghost backup and fixed that and now everything is just fine.
however, in ubuntu...i can't enable desktop effects for some reason, and also with the touchpad, i used the script from [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) but i cannot figure out how to make it so that two fingers plus the main button performs a right-click...i can't really stand the sensitivity of the tap (which two-finger tapping works) so i turned that off and i can't find a solution

regards

---

### Post by cyberdork33 on 2008-06-29
> **Quipacorn said:**
> i can't enable desktop effects for some reason
You have to get 3d acceleration working first. (i.e. install the proprietary drivers).
> **Quipacorn said:**
> also with the touchpad, i used the script from [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) but i cannot figure out how to make it so that two fingers plus the main button performs a right-click...That functionality is not possible with the default touchpad driver. There is a patched version available in the forum that allows this.
[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

---

### Post by Quipacorn on 2008-06-29
The proprietary drivers are installed, and in use (as says the Driver pane) but i'm still getting the Desktop effects could not be enabled dialogue box.

Thanks for the driver link, hope it works

Regards

---

### Post by DonnieP on 2008-06-29
> **Quipacorn said:**
> The proprietary drivers are installed, and in use (as says the Driver pane) but i'm still getting the Desktop effects could not be enabled dialogue box.


Is the proprietary driver checked 'enabled' in the hardware driver box?

---

### Post by Quipacorn on 2008-06-29
Yep, it is...and it says in use to
it's not really that critical
it still just bugs me though
i'm going to try reinstalling the GTx packages and see if it works

---

### Post by Quipacorn on 2008-06-30
okay, so by getting the GTX packages desktop effects works perfectly now
however, the touchpad still wont work with the two finger + button clicking even with Volanin's Driver
also, for some odd reason the bluetooth keyboard (apple standard) will not stay connected...it just keeps connecting and disconnecting..w.orks fine with windows and 10.5...batteries are new too

---

### Post by cyberdork33 on 2008-06-30
> **Quipacorn said:**
> okay, so by getting the GTX packages desktop effects works perfectly now
however, the touchpad still wont work with the two finger + button clicking even with Volanin's Driver
also, for some odd reason the bluetooth keyboard (apple standard) will not stay connected...it just keeps connecting and disconnecting..w.orks fine with windows and 10.5...batteries are new too

Please post problems with the touchpad driver in that thread as it is off-topic here.

I have not had any luck at all with my Bluetooth Apple Keyboard in Hardy. The Bluetooth system was completely overhauled in Hardy, and it messed everything up. Again though, this is off-topic.

---

### Post by promodus on 2008-07-01
> **DonnieP said:**
> Actually, promodus, you're supposed to get the rEFIt menu when you *don't* hold down the option key - you just boot normally and you get the rEFIt menu.  At least, that's the way mine works.  I have Ubuntu Hardy and openSUSE 11 installed in addition to OSX.  They both work fine, except for the webcam, and also I had to do some digging to find a Linux driver for my all-in-one printer.

I believe the bootcamp loader is stored as an extension to the EFI.
while rEFIt is stored on the OS X partition.

---

### Post by DonnieP on 2008-07-01
> **promodus said:**
> I believe the bootcamp loader is stored as an extension to the EFI.
while rEFIt is stored on the OS X partition.
Well, "alls I know" is that when I boot the machine it goes directly to the rEFIt menu.  Which can be verified by the Apple "Genius" who last night informed me that I had voided my warranty because of installing rEFIt.

---

### Post by cyberdork33 on 2008-07-01
> **DonnieP said:**
> Well, "alls I know" is that when I boot the machine it goes directly to the rEFIt menu.  Which can be verified by the Apple "Genius" who last night informed me that I had voided my warranty because of installing rEFIt.That is a bunch of crap. Your warranty is not void. Uninstall rEFIt if you want... The directions are on rEFIt's website.

The "bootcamp" menu has nothing to do with bootcamp at all... This menu has existed long before there was an Intel Mac. Holding the Option Key on bootup give you a choice of bootable partitions.

rEFIt is an EFI executable. The EFI system scans the available partitions for a folder named 'efi' and will look for efi executables in that folder to run. This is common across all EFI systems.

---

### Post by DonnieP on 2008-07-04
> **cyberdork33 said:**
> That is a bunch of crap. Your warranty is not void. Uninstall rEFIt if you want... The directions are on rEFIt's website.

The "bootcamp" menu has nothing to do with bootcamp at all... This menu has existed long before there was an Intel Mac. Holding the Option Key on bootup give you a choice of bootable partitions.

rEFIt is an EFI executable. The EFI system scans the available partitions for a folder named 'efi' and will look for efi executables in that folder to run. This is common across all EFI systems.
It wasn't just rEFIt that he blamed - that was just the tip-off.  It was that I had installed any OS - other than OSX or Windows - into its own partition.  According to this 'Genius', any installation of Linux that is not virtualized voids the Mac warranty.  So according to him the only way to run any non-OSX/Windows OS on a Mac without voiding the warranty is in OSX using (again according to him) "something like Parallels".

---

### Post by fastertyper on 2008-07-04
Hello, this is my first post here on these forums...

I also have a Santa Rosa Macbook Pro...I followed the instructions on this forum

I have all 3 operating systems on my computer and refit...Refit sees all operating systems on the boot menu...but when I try to boot into windows it shows the splash page for a couple of seconds then crashes and automatically restarts my computer...I can boot into OSX and Ubuntu

Any help would be appreciated!

Kevin

---

### Post by DonnieP on 2008-07-04
> **fastertyper said:**
> 
I have all 3 operating systems on my computer and refit...Refit sees all operating systems on the boot menu...but when I try to boot into windows it shows the splash page for a couple of seconds then crashes and automatically restarts my computer...I can boot into OSX and Ubuntu

Any help would be appreciated!

Kevin
Check out this thread, it might help:
[http://ubuntuforums.org/showthread.php?t=826673]("http://ubuntuforums.org/showthread.php?t=826673")

---

### Post by Quipacorn on 2008-07-04
> **fastertyper said:**
> 
when I try to boot into windows it shows the splash page for a couple of seconds then crashes and automatically restarts my computer...I can boot into OSX and Ubuntu

Any help would be appreciated!

Kevin


I had the same issue as well, for me it started after creating the partition for ubuntu in the first place, what may help is restoring the OSX partition to a single volume, creating windows with bootcamp, then creating ubuntu's. Then install windows, and then ubuntu...or you could do what i did and use a utility like Norton Ghost and backup the windows parition after its up and working the first time, then after installing ubuntu restoring it...I think Partedmagic ([http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)) has a parition backup/recovery utility as well (note: you will need some form of backup storage such as a usb external HD or an extra parition)
hope that helps

Cheers

---

### Post by fastertyper on 2008-07-05
thanks for the replies...I actually got it my windows partition working

all i did was reinstall windows xp onto the same partition it was on initially.  now it boots fine..not sure what happened?

---

