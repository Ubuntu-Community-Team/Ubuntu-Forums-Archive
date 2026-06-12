---
title: "Ubuntu won't start up"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-05-22
Hi all.

I have just re-installed ubuntu 7.04 (a fresh install as opposed to previous upgrade from 6.10) but it won't start up. I get the ubuntu loading screen (logo and orange loading bar) but the loading bar does not move at all. I am a bit stumped as to why.

Does anybody have any ideas please.

---

### Post by jerrylamos on 2007-05-22
Well we do need some more information.
1. What computer, display, disk drives, memory size, network card do you have?
2. Does CD Live 7.04 work fine, you can get the internet, run open Office, click on Places, etc?  Have you ever run a previous version of CD Live Ubuntu?  Do you have Windoze on the system anywhere?
3. What size partitions did you think Installation used?
4. When it stops, push Alt-Ctrl-F1.  What lines do you see on the screen?
Later in the day let me try a couple things on CD Live to see what the commands should be to get into this a bit more.
Cheers, Jerry

---

### Post by V-600 on 2007-05-22
Sorry. I wasn't thinking due to annoyance of a non working pc. 

> 1. What computer, display, disk drives, memory size, network card do you have

My computer was self built and worked with the ubuntu install that was I was using before I removed it to do a fresh install. I have one 80GB hard disk. Hda3 is a 50GB partition that was set as "/home", hda5 is the swap partition. Currently hda1 23GB has the non-working ubuntu 7.04 install on it. It is an active partition (i.e. it boots). I have 384 MB of memory and a pci network card (god knows what but it works with the live cd i am using to write this). The computer has a geforce 4 graphics card.

> 2. Does CD Live 7.04 work fine, you can get the internet, run open Office, click on Places, etc? Have you ever run a previous version of CD Live Ubuntu? Do you have Windoze on the system anywhere?

Yes the live cd runs fine and no there is no MS Windows anywhere in the system.

> 3. What size partitions did you think Installation used?

At the minute the whole install is on 23GB hda1. I have not altered fstab to use the old /home partition. I have however removed hda4 (the installed created a new swap partiton) and pointed fstab towards the old swap.

> 4. When it stops, push Alt-Ctrl-F1. What lines do you see on the screen?

I will have to check but I get the feeling that nothing will happen. I will reboot and try it now.

Sorry again about the length of this.

---

### Post by lamalex on 2007-05-22
do you have quiet splash enabled? go to the grub screen and edit boot flags. take out quiet and splash and see where it stops booting.

---

### Post by V-600 on 2007-05-22
I have turned off splash and quiet.

The startup stops at the following point.

Begin: Mounting root file system
/init: /init: 148: syntax error 0xhda1
[   17.403734 ] Kernel panic - not syncing: Attempted to kill init
[   17.403796 ] 

At this point there is a flashing cursor.

I have included the grub entry as it seems relevant...maybe.

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=hda1 ro
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I have tried using the command "sudo vol_id -u hda1" as well as variations round this to get the UUID for the partitions but it always returns the error "hda: error open volume"

EDIT: A bit of research later I tried "sudo vol_id -u /dev/hda1". Success. Do I add that in place of hda1 in the grub entry?

---

### Post by V-600 on 2007-05-22
I have reset the UUID in grub.

The startup gets a bit further but stops at the following line

[21.323297] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

This is odd as to the best of my knowledge I have neither a SCSI or SATA hard drive.

---

### Post by jerrylamos on 2007-05-22
Thanks for the info on your computer system.  

As I gather, Linux has a HAL (Hardware Abstraction Layer) where it treats all devices as SCSI, which includes IDE, CD R/W, Floppy, USB, SATA, and I don't know what  else.  As more and more devices are invented the code to figure out what characteristics they all have gets more and more complex, i.e. longer to check if all possible devices are present.

At the same time, Ubuntu Feisty is trying to speed up boot by doing more things in parallel.  The risk is, some function may start before the SCSI simulation has gotten to the correct point, example CD Live "persistent" feature of Dapper and Edgy fails on Feisty because it looks for the USB pen drive but the SCSI simulation code hasn't made the USB device available yet.

One of the results we as users see is sometimes things work and sometimes they don't, and we can't tell what affects this time dependent code.  A few weeks ago I saw the "DPO or FUA".  I jumped to the conclusion the SCSI simulation code marks down what features each of the devices has, and that one didn't have those features. I don't remember the situation other than I was likely trying to define a bug.

Some people drop back to Edgy 6.10.  Some people like me persevere until their particular computers are running (there are 5 on this LAN), others luck out and Feisty works fine.  For what it's worth, one of the goals of release Gutsy Gibbon 7.10 is "more polish" whatever that means to them.

If Ubuntu is hanging in boot there are some things that can be tried.  Here's an excerpt from my post "Workarounds" in forum "Installation & Upgrades":

[https://bugs.launchpad.net/ubuntu/+s...20/+bug/106864](https://bugs.launchpad.net/ubuntu/+s...20/+bug/106864)
There was a "fsck failed, see /var/log/checkfs" buried in the middle of the messages that roar up the screen. My interpretation, the bug came in when hard drive code was changed to support both IDE and SATA. Along with this came change of device name from hda to sda, complex UUID's, and all that. fsck failed to process the IDE hard drive.
My fix: put in an extra cable to put the IDE hard drive on IDE2, while the CDROM is on IDE1. Ubuntu booted right up, no "can't access tty" errors.
Ben Collins said on 2007-04-18: (permalink)

The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"
For installing a system, add break=top to the kernel cmdline via the bootgfx menu. Once at a busybox prompt, run "modprobe piix". Then "exit" the shell. Once the system is installed, the above work around will also be needed.

From another post in bug 106864: Adding piix in /etc/initramfs-tools/modules allowed to advance more in the startup but the kernel was not able to finish the startup. I've added this in /etc/initramfs-tools/modules:
piix
i2c_piix4
i2c_core
Now the problem is solved in my system.

"Feisty does not recognise CD burner"
The workaround mentioned in the previous thread (break=top + modprobe piix)
fixed the xfermode error problems described in bug #96826 for me on a
Dell OptiPlex GX100 system. The two problems seems to be connected.

---

### Post by V-600 on 2007-05-23
I would like to give your idea a go but I am not sure how to go about it. I have to boot the computer from the live cd. I can access the hard drive from /media/disk/etc/initramfs-tools/modules but I am not sure how to run the update. Surely it would update the live cd version rather than the installed one.

Also how would I "add break=top to the kernel cmdline via the bootgfx menu" and what is a busybox prompt?

Thanks

---

### Post by jerrylamos on 2007-05-24
The bootgfx I think is just the initial CD Live boot screen.  You would push F6 and add break=top to the boot options just after quiet splash.  This is for booting the CD Live which in your case works, so you don't do that one.  If you were doing the suggestions for CD Live (which you don't need) the break=top stops the boot at a command line then you would do "modprobe piix" and then "exit"

There's another user's post which makes some more sense.  You would do from a CD Live boot:
sudo gedit /media/disk/etc/initramfs-tools/modules
then add these to the list, as is, no # which is a comment:
piix
i2c_piix4
i2c_core

Then shutdown CD Live and try to boot the install again.  I don't have any idea what the other two lines after piix are, but they helped someone, so they may or may not be useful for you.

I'm no developer(!) but I'd assume if those were in the list and you booted up, then the modules would be loaded as part of boot.  Perhaps what the developer was thinking is if you were at least at a functioning command line, adding the piix etc. to the list wouldn't take effect unless you did a sudo update-initramfs -u.

Sometimes "can't access tty" ends up in a usable command line so you would do
modprobe piix
exit

On occasion on a hang, Ctrl-Alt-F1 does get you to a command line.  If it seems like we're probing in the dark, that's right; I don't get the identical hang you did, so I'm trying to figure out something worth trying.

Good luck, Jerry

---

