---
title: "GRUB disappeared"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-04-04
OK, so where did my boot loader go?

We had a storm come through last night -- power outage. Not a problem because I've got a fairly decent UPS in place. Did a NORMAL shutdown. Now, I try to startup and have problems. The POST runs, no problem, but then there is no boot loader. So, restart with the boot CD in place (it runs OK) and select boot from first hard disk -- which it does without incident.

What happened to my boot loader?

---

### Post by Kobalt on 2007-04-04
Quite strange indeed...
You can always restore Grub from a LiveCD, following the instructions at the beginning of this page : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by lwalper on 2007-04-04
Thanks for the direction --

Tried the first option to retain my Win2K loading option. No joy. At least the system boots to Ubuntu now without the CD.

Hmmm??

For some reason I also seem to have lost my printer. I've tried to uninstall / reinstall as I did [http://ubuntuforums.org/showthread.php?t=384279](http://ubuntuforums.org/showthread.php?t=384279) to no avail. No communication to the printer. The print job goes to the queue but no farther. It's an HP 3600n connected through a DSL modem/router. It was working yesterday.

---

### Post by Kobalt on 2007-04-04
Ok, one thing at a time.
Now that you can access your Ubuntu regularly, you need to edit the /boot/grub/menu.lst file in order to add Windows back to the boot list. Open up a Terminal and enter this command line : 
```
gksudo gedit /boot/grub/menu.lst
```
This will open a text file that contains, at the end, the list of kernels/operating systems you can boot on. You need to add a part that looks like this at the end of the file :
> title           Windows
root            (**hd0,3**)
makeactive
chainloader     +1
You just need to change what's bold in that example : hd0,3 (for example here) being the partition on which your windows is installed on. To know that, enter the following line in a terminal and look for your windows partition and the label in front of it : 
```
sudo fdisk -l
```
After that save & close the file, and reboot to test.

---

### Post by lwalper on 2007-04-04
I have this already in the menu.lst file
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=62ec8b86-1074-4984-abab-7f1407211d63 ro
# kopt_2_6=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=785 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
This is my fdisk -l list
```
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825       10011    49697077+   7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3569    28667961   83  Linux
/dev/hdb2            3825       24321   164642152+   7  HPFS/NTFS
/dev/hdb3            3570        3824     2048287+  82  Linux swap / Solaris
```

---

### Post by lwalper on 2007-04-04
My Win2K installation is on /dev/hda1 with a second primary partition for Windows data on /dev/hda2.

---

### Post by drs305 on 2007-04-04
When I was just getting started with Linux I experimented a lot and probably installed Ubuntu more than a dozen times. When I screwed things up really badly, I would resort to the Super Grub Disk. It bailed me out of many booting problems and either let me restore or recreated my boot setup.

More information and the download link can be found here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Kobalt on 2007-04-05
What happens when you select "Microsoft Windows 2000 Professional" in your boot list ? What error message do you get ?

---

### Post by lwalper on 2007-04-05
That's just it. The boot loader never displays. Somethin's seriously messed up somwhere. It may be a hardware problem. I recently (two weeks ago) replaced the hda1 drive due to a failure. The new one may now be going bad following a few hundred hours burn in. I've tried downloading Super Grub Disk and can't seem to get the file to "save" to the drive -- either one. That raises concerns for me about a possible I/O failure or HDD controller failure -- writing bad data.

I ran the CD installer, looking at the manual partitioning options and got some kind of error relating to no boot sector defined (or some such thing -- I forget right at the moment what the error said exactly). Anyhow, with the curent problems I elected to delete the partition on hdb1 (which contains/ed the Ubuntu install) and see if I could do a re-install. Will unplug hd0 (to avoid confusion about what is doing what -- I believe that is a "good" HD) to see how that goes.

---

### Post by Kobalt on 2007-04-05
You don't even see for a couple of seconds, before you see the Ubuntu logo, a line stating "Grub Boot loader, press Esc to enter the menu" or something like that ? 
You should definitely have this installed if you can boot into Ubuntu..

---

### Post by lwalper on 2007-04-05
So, I've unplugged hd0, reinstalled Ubuntu on hd1 (now hd0) with the GRUB installed in the MBR. Some crazy stuff going on. About halfway through the partitioning/formatting process the system shuts down, restarts. This time the install goes without a hitch.

The system will not read my M$ Win2K install CD so on bootup I try to enter the BIOS to check for "boot from CD." All I get is a white stripe down the middle of the screen. Looks bad. May be motherboard problems?? Or may be related to this thread

[http://ubuntuforums.org/showthread.php?t=388937](http://ubuntuforums.org/showthread.php?t=388937)

where I noted some change in my video performance after installing Ubuntu. Can't imagine what's happened?? Maybe a chain of unrelated events??

---

### Post by Verbatim9 on 2007-04-05
(Hmm...I see you posted again in the interim...I'm afraid I don't know what to do in your current situation, or what might be causing it. Looks like I'm a little late with this suggestion...but for future reference...)

Taking a look at the instructions you followed...I don't know enough about GRUB to be certain, but I think they created a *new* version of GRUB in your MBR...so the version of GRUB on your Linux partition isn't used at all, and your menu.lst file isn't being read...there's a different menu.lst file in the MBR, and that's the file that's being used to boot your system.

The easiest way to get your original GRUB re-installed is using the [alternate install disk](http://ftp.ale.org/mirrors/ubuntu-releases/6.10/) (scroll down the page to the "alternate install" section, and choose the 32-bit or 64-bit version, whichever matches your Ubuntu install).

Once you've burnt yourself an alternate install disk, boot from it, and choose "rescue a broken system" It will ask you a bunch of questions, it doesn't particularly matter how you answer them, except for the keyboard one (which may impact how well your keyboard works during the restore process...it's not particularly critical either for this process)...you'll want to say "no" to the autodetect question (the autodetect is a very confusing and not very automatic process, and always decides you have a freakishly weird keyboard in my expierience), and then choose US ENGLISH on the next two screens.

Eventually, it will ask you which partition you want to use as root, and give you a list of /dev names. Highlight your Ubuntu OS partition in the list, and hit enter.

It will offer you several choices as to how you could start rescuing the system, choose "Reinstall GRUB boot loader"...that will set up your computer to boot using the GRUB that already exists in your Ubuntu partition.

---

### Post by confused57 on 2007-04-05
> **lwalper said:**
> So, I've unplugged hd0, reinstalled Ubuntu on hd1 (now hd0) with the GRUB installed in the MBR. Some crazy stuff going on. About halfway through the partitioning/formatting process the system shuts down, restarts. This time the install goes without a hitch.

The system will not read my M$ Win2K install CD so on bootup I try to enter the BIOS to check for "boot from CD." All I get is a white stripe down the middle of the screen. Looks bad. May be motherboard problems?? Or may be related to this thread

[http://ubuntuforums.org/showthread.php?t=388937](http://ubuntuforums.org/showthread.php?t=388937)

where I noted some change in my video performance after installing Ubuntu. Can't imagine what's happened?? Maybe a chain of unrelated events??
Maybe you can just add an entry to your menu.lst to boot Windows:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Set your system up to boot first to your Ubuntu drive, then edit your /boot/grub/menu.lst following the directions in the link I gave you, then try adding the Window's entry.

---

### Post by lwalper on 2007-04-06
Seems that I may have a MB problem. The 80Gb drive in question will not even boot Windoze now -- nor will the system boot from my Win2K install disk. I have now taken the drive out, twested it on another machine -- it seems to work OK there, but when I install it back in the same machine -- problems. So, have deleted (overwritten) the first 63 sectors of the drive to make sure the is no MBR problem.

Will try again on another machine, different drives, and etc.

Thanks for your input/advice. I may be looking at getting a new 'pooter (or MB or something?).

---

