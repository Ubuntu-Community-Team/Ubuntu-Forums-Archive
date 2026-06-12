---
title: "[SOLVED] how do you repair gutsy?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by unebaguettesvp on 2007-10-22
so, during an upgrade (from synaptic) to gutsy yesterday, my computer froze. i was forced to restart and now i can't even boot linux.

is there a repair cd for gutsy? does the download for the gutsy iso have a repair option to fix the broken installation?

when i install from the gutsy cd, should i reformat the partition first using gparted? and install it on a clean partition?

or can i install gutsy on the broken installation and all my programs and settings will still be there?

thanks for any help.

---

### Post by dhruva023 on 2007-10-22
i think you should just reformat the drive and do the fresh install.

boot up the live cd and backup your data on usb or on the internet.

---

### Post by AndyCooll on 2007-10-22
To do a normal install you don't need to use GParted and partition first, the partitioning process is all part of the install. Some folk, when they get to the partitioning stage choose "Manual" and then create a separate partition for their /home partition. This means that when problems happen like the one you're having, they can just do a clean re-install in the knowledge that all their settings will be maintained.

In your case however, if you don't have a separate /home partition you have a few options:
- you could boot the live cd, mount your home partition, copy it for backup purposes, then do a reinstall.
- or IIRC the Alternate CD comes with a "repair" option
- or you could try booting from something like the System Rescue CD (a Linux distro with tools to do what it says on the tin)

:cool:

---

### Post by unebaguettesvp on 2007-10-22
how do you mount /home frome the live cd?

i thought you couldn't do that. i think i tried to mount the root directory "/" from the live cd once but i could never get it to work. how do you do it?

---

### Post by az on 2007-10-22
> **unebaguettesvp said:**
> so, during an upgrade (from synaptic) to gutsy yesterday, my computer froze. i was forced to restart and now i can't even boot linux.

is there a repair cd for gutsy? does the download for the gutsy iso have a repair option to fix the broken installation?

when i install from the gutsy cd, should i reformat the partition first using gparted? and install it on a clean partition?

or can i install gutsy on the broken installation and all my programs and settings will still be there?

thanks for any help.

I don't think you need to reinstall.

What happens when you try to boot Ubuntu?  Do you get to the bootloader?  Can you select which OS to boot? (HGit escape to reveal the boot menu)?  Does it boot, but your X server is broken?

Any of those three is a two-minute fix.

0.  I assume your hard disk is not borked because you do not say that your computer no longer boots, but only that Ubuntu does not boot.

1.  If your bootloader is screwed up, you can reinstall grub by booting the live cd.  There is a help.ubuntu.com page about that.

2.  If your bootloader works, but your Ubuntu got stuck installing packages, you can select the recovery mode and run

apt-get -f install
and then

dpkg --configure-a

to fix any half-installed or otherwise broken packages.

3.  If your X server is misconfigured, boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

and then

init 2

---

### Post by unebaguettesvp on 2007-10-22
the bootloader works. i can press escape and i get a choice of which os to boot. the default, the newest linux is not working. so i choose the one from feisty. and that gets me to the login screen. i type in my username and password and then it does a lot of number crunching and then just stops working leaving me in a beige window.

where do i type:

apt-get -f install
dpkg --configure-a

or does this sound like x is broken?

---

### Post by az on 2007-10-22
> **unebaguettesvp said:**
> the bootloader works. i can press escape and i get a choice of which os to boot. the default, the newest linux is not working. so i choose the one from feisty. and that gets me to the login screen. i type in my username and password and then it does a lot of number crunching and then just stops working leaving me in a beige window.

where do i type:

apt-get -f install
dpkg --configure-a

or does this sound like x is broken?

Perhaps your upgrade to Gutsy was interrupted?  Boot into recovery mode using the Feisty kernel.  That will drop you into a shell where you can run those commands to complete the upgrade procedure.  

If that's not the problem, give more details about what happened before you could no longer boot into Ubuntu.

---

### Post by unebaguettesvp on 2007-10-23
yes! that was it! thank you!

i logged into the kernel that feisty uses in recovery mode. then i typed in:

dpkg --configure-a

after that was done, i restarted and i have gutsy now! thanks!

---

### Post by Mr_Ada on 2008-04-07
Well my gutsy version got honked up when I was having crashes in my system.  Don't know what from.  I have looked at memory, graphics cards.  I know my system is still there as I can see it from Windows.  What happens is that I get into the (recover) mode and watch things being done then it gets to something called Busybox and initramfs and from there it doesn't do anything.  I don't know what to type.  I think some files are missing but I'll have to write them down next time.  I figured I upgrade to Hardy Heron but if using the Live CD helps that might be useful.

chris

---

