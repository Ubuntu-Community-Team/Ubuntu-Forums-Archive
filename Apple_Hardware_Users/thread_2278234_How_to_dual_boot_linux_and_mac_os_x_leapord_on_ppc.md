---
title: "How to dual boot linux and mac os x leapord on ppc?"
date: 2015-05-14
forum: Apple Hardware Users
---

### Post by shoop2 on 2015-05-14
I want to run ubuntu on my imac g5..... but i also want to keep mac os x 10.5.8 leapord... dual booting seems like a good idea but does anybody know how i would go about doing this?
(P.S. does adobe flash player work with ubuntu??)

---

### Post by oldfred on 2015-05-15
I do not know Mac, but have a few links.

 [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
[http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)

---

### Post by este.el.paz on 2015-05-15
@oldfred:

Thanks for your help in the apple hardware sub-forum . . . you should have the links to the "PowerPCFAQ" and the "Powerpc Known issues" . . . web wiki's . . . .

@OP:

Simple answer, yes, dual boot is a good way to go  . . . and then find a flavor of Ubuntu spun for "powerpc" . . . right now Lubuntu 14.04 might be the best supported spin for PPC.  I just tried an install of Ubuntu-MATE 15.04 and have to say "it ain't ready for primetime" . . . .  Still, most simple install and best all-around for PPC would be one of the 12.04 flavors . . . should have "powerpc" in the file name.

e..

---

### Post by shoop2 on 2015-05-18
@este.el.paz How can i dual boot?

---

### Post by este.el.paz on 2015-05-18
> **shoop2 said:**
> @este.el.paz How can i dual boot?

@shoop:

You have to do some reading . . . been awhile, but possibly the Ubuntu PowerPCFAQ will offer detailed instructions.  The first step is maybe the hardest, as in PPC I don't believe the HD can be re-partitioned "on the fly" . . . .  What I did is clone my OSX install to an ext HD connected by firewire using Carbon Copy Cloner . . . then re-boot into the ext HD . . . and re-partition the int HD using Disk Utility in the ext HD.  You could boot the install disk and use DU to do the same thing, but then you would have to do a fresh install back into the int HD.  Cloning the system is easier.

Let's say you pick two partitions, one for OSX . . . and whatever you want for linux . . . possibly at least 12 GB . . . or depending . . . might be 6 or 8GB if you use Lubuntu . . . set that space as "Free space" or if not available, then as "FAT32."   Re-install or clone OSX in ***first****.  Then boot up the linux installer of choice . . . run through the first few windows, then hopefully you will see the "what do you want to do?" window . . . hopefully it will show "install alongside OSX"  option, to use "automatic" install.  See if it runs through OK and installs Yaboot.  Some people say shut down the computer, then hard boot and see if Yaboot window opens . . . it should auto-select "linux" . . . see what happens.

Alternatively you can select "something else" . . . which is "manual" . . . my latest 15.04 U-MATE install did not go well using this method, but previously it was the best way . . . partition 10MB for "new world boot partition" which is for Yaboot; 8 or more GB for "/" formatted as "ext4;" and 1 - 2x RAM set up as "swap."

Enjoy.  But first read through PowerPCFAQ and PowerPC Known issues.  Generally these days wifi is not set up and sound doesn't work out of the box.

e..

---

