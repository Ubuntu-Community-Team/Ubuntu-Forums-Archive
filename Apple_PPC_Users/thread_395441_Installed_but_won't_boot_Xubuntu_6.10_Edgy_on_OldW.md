---
title: "Installed but won't boot: Xubuntu 6.10 Edgy on OldWorld Mac w/ BootX"
date: 2007-03-28
forum: Apple PPC Users
---

### Post by SubGothius on 2007-03-28
I finally managed to get Xubuntu 6.10 Edgy installed on my "Old World" Power Mac clone, a Umax S900 dual-200MHz PowerPC 604e w/ stock ixMicro/IMS TwinTurbo 128+ video card -- i.e., an OldWorld Power Macintosh 9500/9600 clone w/ the same stock video card as Apple supplied, so those with PowerMac 9500/9600 tips/experience should be able to help me here.

However, now that I have completed the initial installation session and copied my newly-installed kernel (vmlinux) and ramdisk (initrd.img) files over to my MacOS System Folder:Linux Kernels where BootX can use them, I cannot seem to boot into my virgin Xubuntu system!  All I get is a black screen and apparent system freeze (no audible HD activity), requiring a forced-reboot (Ctrl-Cmd-Power).  Is there somewhere I could look for a boot log file (by executing a shell from the installer), to at least see where it might be hanging?

I am reasonably sure the new vmlinux kernel file is fine, as I can use that kernel to boot with the installer's initrd.gz ramdisk file (just not with the post-install initrd.img).  I have tried:[list][*]Moving the new initrd.img out of Linux Kernels into the System Folder "loose";
[*]Renaming the ramdisk file to initrd.gz or ramdisk.image.gz (in both locations above);
[*]With and without the "root=/dev/sdb4" kernel arg. in BootX;
[*]W/ & w/o every combination of the "No video driver" and "Force video settings" options in BootX;
[*]W/ & w/o various permutations of the "video=imsttfb:vmode:6,cmode:8,mclk:66" kernel arg. (FWIW, the installer required no video arg. nor options, tho' display was erratic/distorted)
[*]Is there some "magic combination" of the above I might have missed? :-k [/list]
**Gruesome install details for the curious:**
I had already managed to net-install Debian 3.1 "Sarge" and booted into that base installation to start D/Ling and installing the full suite of desktop workstation packages, when the partition I was using ran out of free space partway thru.  However, after deciding to start over with a bigger drive, I then realized how I could apply the lessons learned towards installing (X)ubuntu instead.

A [net-install of Ubuntu](http://ftp.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/) might have worked, but I preferred to try my hand at the leaner Xubuntu distro first. I had to D/L and burn the Xubuntu Edgy PPC Alternate Install CD, but the "vmlinux" kernel and "initrd.gz" ramdisk files on that CD would not seem to boot with my BootX 1.2.2 bootloader when I copied them over to my System Folder:Linux Kernels.  Instead, I D/L'd [the version of those files for Edgy CD installation from the Ubuntu FTP site](http://ftp.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/cdrom/).  Those files seemed to work with the Xubuntu CD just fine, which led me to my present installed-but-not-booting state. ](*,)

---

### Post by pxwpxw on 2007-03-31
This might be the answer:

 6.10 on oldworld macs: can´t get installed vmlinux and intrd.img

[http://www.ubuntuforums.org/showthread.php?p=2137453#post2137453](http://www.ubuntuforums.org/showthread.php?p=2137453#post2137453)

---

### Post by SubGothius on 2007-04-08
Thx, I did find that thread, took me a bit to distill from it that all I had to do was add 'mesh' to my initrd.img and recopy that file over to the MacOS side.

Here's my summary of how I installed Xubuntu **8.04 Hardy** on my OldWorld PowerMac clone, using a dedicated 4 GB physical SCSI drive completely separate from the one holding my MacOS (so I did not need to address the issue of backing-up my existing MacOS and data nor partitioning a place for them on the same drive as Linux):
[LIST=1]
[*]Download the .iso of [Xubuntu PowerPC Alternate Install]("http://cdimage.ubuntu.com/xubuntu/ports/releases/hardy/") and burn that to a CD-R (details on how to do this are outside the scope of this guide ;) );
[*]Download and install the [BootX bootloader]("http://penguinppc.org/bootloaders/bootx/");
[*]Download the [Ubuntu 8.04 Hardy CD-install "vmlinux" (kernel) and "initrd.gz" (boot ramdisk) files]("http://ports.ubuntu.com/dists/hardy/main/installer-powerpc/current/images/powerpc/cdrom/"), and place them both (named as-is, no changes required) inside a "Linux Kernels" folder inside the MacOS System Folder;
[*]Optional: Instead of burning a CD and using the CD-installer kernel+ramdisk, if you're plugged into Ethernet with a DHCP'd broadband uplink (and have a *lot* of time for a more leisurely install process!) you can just use the [Ubuntu 8.04 Hardy Network-install "vmlinux" (kernel) and "initrd.gz" (boot ramdisk) files]("http://ports.ubuntu.com/dists/hardy/main/installer-powerpc/current/images/powerpc/netboot/") to download installation packages on-the-fly;
[*]Launch the BootX App and select:[LIST][*]The "vmlinux" kernel;
[*]"Options..." to select "Use Ramdisk..." with the "initrd.gz" file;
[*]Save to prefs;
[*]Click "Linux" to boot into the installer (or click "Linux" when BootX appears at Mac startup).[/LIST][*]Follow the Ubuntu Installer prompts;
[*]At the Partitioner step, I went with this partitioning scheme:[LIST][*]2.8 GB ext3 partition as "/" (I had tried 2 GB earlier and ran out of space on my /);
[*]Optional: 64.0 MB ext**2** partition as /boot (necessary if you ever want to try the [quik bootloader]("http://penguinppc.org/bootloaders/quik/") instead of relying on BootX) -- you can get by with only 32.0 MB here, but that's a bit tight for routine future kernel upgrades or initrd.img updates;
[*]Optional: 64.0 MB ext3 partition as /tmp (nice to keep runaway processes from dumping enough in /tmp to fill your / partition);
[*]512.0 MB swap partion (this can be set as double your expected physical RAM);
[*]"max" ext3 partition as "/home" (max available in my case was ~1 GB).[/LIST][*]Follow further Ubuntu Installer prompts;
[*]"Continue" at the bootloader warning that "root=/dev/sdb4" (in my case) will be required as a kernel argument in order to boot the new system;
[*]"***Go back***" at the prompt about finishing installation/rebooting (***do not*** continue!);*
[*]This brings up an Installer menu showing all the steps so far and a few extra options;
[*]Scroll down to select "Execute a Shell";
[*]"Continue" into the shell and type the following commands (omit comments after the "#"):```
# See where all your partitions are
# (only works accurately after install, before rebooting):
df
# Mount newly-installed system at installer's /mnt point
#   (e.g. /dev paths from my case appear below):
mount /dev/sdb4 /mnt
# Switch shell "into" using the newly-installed system as root:
chroot /mnt
# Create mount point in new system for MacOS partition:
mkdir /mac
# Load kernel module to read/write Mac HFS+
#   (aka "HFS Extended") partitions:
modprobe hfsplus
# (...or substitute "hfs" for "hfsplus" re: HFS Standard
#   partitions here and below)
# Mount MacOS partition at /mac:
mount -t hfsplus /dev/sda4 /mac
# Verify that recognizable MacOS files/folders are in
#   the partition just mounted:
ls /mac
# Optional: set MacOS partition to always mount at /mac:
echo '/dev/sda4 /mac hfsplus defaults' >> /etc/fstab
# Add 'mesh' to modules loaded at boot:
echo 'mesh' >> /etc/initramfs-tools/modules
# Verify 'mesh' is in there:
cat /etc/initramfs-tools/modules
# Update boot ramdisk image file to reflect changes:
update-initramfs -u
# (note: the above may take a while to complete!)
# Optional: if your installer found the network, do all
#   your initial upgrades (unnecessary if you used the
#   network-install method):
aptitude update
aptitude full-upgrade
# Copy new kernel and boot ramdisk files to MacOS:
cp /boot/vmlinux* /boot/initrd* /mac
# (note: this will wind up copying two of each file --
#   I boot with the plain-named ones and keep the
#   version-named ones as backups.)
# Force disk writes to finish before continuing:
sync
# Unmount MacOS from /mac:
umount /mac
# Exit chroot session from new system:
exit
# Exit Installer shell and return to Installer menu:
exit
```[*]Now it is finally okay to Finish Installation and Reboot;
[*]When MacOS is back up, copy your new "vmlinux" and "initrd.img" files into your System Folder:Linux Kernels folder;
[*]Launch the BootX App and select:[LIST][*]The new "vmlinux" kernel;
[*]"Options..." to select "Use Ramdisk..." with the new "initrd.img" file;
[*]Type new "/" partition path in kernel arguments line (root=/dev/sdb4 in my case);
[*]Optional (may be unnecessary): Type video kernel arguments after that (video=imsttfb:vmode:17,cmode:32 *should* work for me, but I got a distorted 800x600 in Edgy instead... :confused: see more below);
[*]TAB key toggles which OS is the default for BootX;
[*]Save to prefs;
[*]Click "Linux" to boot into the new system.[/LIST][*]Be patient while Xubuntu boots up for the first time, login, and enjoy! \\:D/[/LIST]
*If you have already installed your (X|K)Ubuntu and exited the installer by rebooting, rest assured that you do not have to restart installing from scratch; just reboot into your Installer kernel/ramdisk again and follow it up to the Partitioner stage, "Go Back" out of the Partitioner, then select "Execute a Shell" from the Installer menu and follow the shell command sequence outlined above (note that the "df" step may not be helpful, and I would advise against doing the optional "aptitude update/upgrade" steps as well).

**Teething issues from Edgy preserved below for purely historical interest :)**

Right now, I only have a few minor issues left to polish off:

For one thing as noted above, I don't think my video karg is right, or maybe I need to edit my xorg.conf, as Xubuntu boots into a 800x600 rez that's shrunken and squeezed off the left side of the screen, appearing the same as when I select 800x600 in MacOS, and I can't select anything but 800x600 and 640x480 in the Xfce Display settings panel (even tho' I specified 1024x768 in the Installer as the only valid rez for X), so I think it's defaulting to a generic video driver and resolution instead of the imsttfb driver. ([Please post any ideas/suggestions in this separate thread]("http://ubuntuforums.org/showthread.php?t=404204").)

Also, after running all available Updates using the Xubuntu GUI Update Manager and customizing some Xfce panels and windowing options, now I can't seem to launch any applications from the Applications menu.  Whenever I try, my drive chatters briefly like it's going to do something, but then nothing happens.  Only Xfce utilities like the Settings Manager and Process Manager will open, and the Process Manager doesn't list any new processes when I try to launch an app. ([Please post any ideas/suggestions in this other dedicated thread]("http://ubuntuforums.org/showthread.php?t=404196").)

---

### Post by Huffalump on 2008-02-25
Thanks very much for these detailed instructions.  I'd been getting nowhere for about 3 weeks when I was trying to get Dapper onto an oldworld powermac.  Your notes simplified what I was trying to do... and then it worked!

Now that I see you got Edgy to work, even though I read nothing past Dapper would work, I am going to start all over and install Edgy instead.  I may even waste a few minutes trying Gutsy, since your straightforward notes pretty much streamline the install process.

Thank you.

---

### Post by SubGothius on 2008-04-19
Thx! Glad you appreciate and found this useful. This same basic process has worked for me with every release up thru Hardy so far; my only lingering issues have to do with getting Xorg to work properly for me, but I suspect this has more to do with my oddball vidcard, rather than anything to do with the Oldworld PowerPC Mac hardware itself. Without having tested on other PowerMacs myself, I'd conjecture that anyone running a more common vidcard (e.g.nVidia or ATI) or prolly even the on-board video should be able to follow this process to get any release running on an Old World beige PPC Mac.

BTW, Xubuntu/XFCE4 is totally the way to go on this old hardware. I tried installing Debian Etch with its default Gnome desktop on this hardware, and (aside from the stuttering-keyboard issue I never could solve there) *man* was that interface *slow*!

---

