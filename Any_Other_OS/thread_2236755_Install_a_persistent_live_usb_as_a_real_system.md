---
title: "Install a persistent live usb as a real system"
date: 2014-07-28
forum: Any Other OS
---

### Post by phoenixofnightfall on 2014-07-28
Hello,

I am currently running Ubuntu on a persistent live usb and I would like to go for a full install on my hard drive. However, I'd like to keep the installed applications, documents and settings from the persistent live usb, is there a way to do that ?

I know the persistent live usb is the squashfs union the casper-rw partition. Wouldn't it be possible to overwrite the full installation with everything in the casper-rw to get the same result as my current persistent live usb session, provided I keep the same username as the live session one ?

Thank you,
David

---

### Post by yancek on 2014-07-28
>  am currently running Ubuntu on a persistent live usb and I would like  to go for a full install. However, I'd like to keep the installed  applications, documents and settings from the persistent live usb, is  there a way to do that ?

Remastersys is an application you could install on Ubuntu and remaster to create an iso file with an installer which you could use to do exactly what you want.  That would be from an installed system.  It's no longer maintained and I don't know if it will work on Ubuntu newer than 12.04.  

> Wouldn't it be possible to overwrite the full installation with  everything in the casper-rw to get the same result as my current  persistent live usb session, 

Might be possible, I've never tried it but would not really expect it to work.  What full installation are you referring to?  The install on the flash drive?  An installation currently on your hard drive?  You won't be able to use the installer on the flash drive to install and save all your settings, at least I would not expect that to happen.  If you currently have a system on your hard drive, I would definitely not install over it.

If you want to save the configurations on the flash, why not just continue using it?  You can create a data partition on your hard drive to store additional data.  What format did you use for the flash drive?  ext2, fat32?

---

### Post by ian-weisser on 2014-07-28
> **phoenixofnightfall said:**
> I'd like to keep the installed applications, documents and settings from the persistent live usb, is there a way to do that ?

It's a lovely idea, and you're certainly welcome to try...but the Live system is simply not designed to be transferrable like that. You are likely to hit unexpected roadblocks, and lose your customizations anyway.

For example, the Live system uses a different bootloader, and a customized initramfs and fstab to load the system snapshot into RAM, decompress it, and mount it read/write in RAM. That means you'll need to partition the disk manually, install grub, edit the initramfs and fstab settings and generate a fresh initramfs binary...and hope(!) they all work the first time, because you won't get a chance to test most of them before you reboot.

So I recommend you make a plan to recreate your customizations from a safer and more reliable form of install. You will need it.

---

### Post by phoenixofnightfall on 2014-07-29
Thank you for your replies,

> **yancek said:**
> Remastersys is an application you could install on Ubuntu and remaster to create an iso file with an installer which you could use to do exactly what you want.  That would be from an installed system.  It's no longer maintained and I don't know if it will work on Ubuntu newer than 12.04.  

I just happen to be running 12.04 ! (Actually it's Elementary OS Luna, based on 12.04)


> **yancek said:**
> Might be possible, I've never tried it but would not really expect it to work.  What full installation are you referring to?  The install on the flash drive?  An installation currently on your hard drive?  You won't be able to use the installer on the flash drive to install and save all your settings, at least I would not expect that to happen.  If you currently have a system on your hard drive, I would definitely not install over it.

I was referring to the future installation I would like to have on my hard drive. What I meant was:
1. Make a standard install on the hard drive (so clean install)
2. Copy everything from the casper-rw partition to the clean install, overwriting the clean install files when needed (trying to mimic unionfs)


> **yancek said:**
>  If you want to save the configurations on the flash, why not just continue using it?  You can create a data partition on your hard drive to store additional data.  What format did you use for the flash drive?  ext2, fat32?

I only have two USB ports on this computer so paralyzing one of them at all time is really a limitation. Plus, I have an SSD so I would gain in speed with a standard installation. The flash drive as a 1gb fat32 partition for the live system, and a 15gb ext4 partition for casper-rw.


[QUOTE=ian-weisser] It's a lovely idea, and you're certainly welcome to try...but the Live  system is simply not designed to be transferrable like that. You are  likely to hit unexpected roadblocks, and lose your customizations  anyway.

For example, the Live system uses a different bootloader, and a  customized initramfs and fstab to load the system snapshot into RAM,  decompress it, and mount it read/write in RAM. That means you'll need to  partition the disk manually, install grub, edit the initramfs and fstab  settings and generate a fresh initramfs binary...and hope(!) they all  work the first time, because you won't get a chance to test most of them  before you reboot.

So I recommend you make a plan to recreate your customizations from a safer and more reliable form of install. You will need it.[/QUOTE]

I don't really understand how the bootloader, initramfs and fstab would be a problem if I plan to do a full install on my hard drive ? I think you both misunderstood my question, I don't want to do a full install on the flash drive, I want to go from a persistent live usb to a standard installation on the hard drive. 

I realize I wasn't precise enough in my problem description, that's my fault, sorry. I corrected it.

---

### Post by ian-weisser on 2014-07-29
> **phoenixofnightfall said:**
> I don't really understand how the bootloader, initramfs and fstab would be a problem if I plan to do a full install on my hard drive ? I think you both misunderstood my question, I don't want to do a full install on the flash drive, I want to go from a persistent live usb to a standard installation on the hard drive.

Ah, well certainly do try. The problems you run into will merely be different.
It will be interesting to discover what those problems are.

---

### Post by phoenixofnightfall on 2014-08-09
Well it actually went really smoother than I expected !

So for the recall, I had an Elementary OS Luna (based on Ubuntu 12.04 precise) persistent live USB with a lot of things and configurations and I wanted to install Elementary OS on my computer hard drive AND keep all the data's and configurations.

What I did is:
1. Install Elementary OS Luna from the LiveUSB using the same username as the live session user (it was "elementary" for elementary os)
2. Mount the system partition of the hard drive to /sdd (I had to mkdir /sdd first indeed)
3. Mount the casper-rw partition of my persistent LiveUSB to /mnt
3. sudo cp -rv /mnt/* /sdd
4. Reboot
5. Lightdm won't let me open my session, I went to tty1 (ctrl+alt+F1) and ran "sudo chown -R -v elementary:elementary ." (replace elementary by your username)
6. sudo stop lightdm; sudo start lightdm
7. Return to graphical interface (ctrl+alt+F7) and login !

I lost postgresql, I don't know why, I had to purge it completely and reinstall it, see [http://stackoverflow.com/questions/2748607/how-to-thoroughly-purge-and-reinstall-postgresql-on-ubuntu](http://stackoverflow.com/questions/2748607/how-to-thoroughly-purge-and-reinstall-postgresql-on-ubuntu).
Beware, this will make you lose all your postgresql databases, but you should still be able to export them from your persistent LiveUSB, though.

It seems that postgresql was not the same package that was installed, is marked as installed, but is not actually installed, because when reinstalling it, dpkg complained about packages in the same strange state with output like this:
dpkg: warning: files list file for package `libgtkmm-2.4-1c2a' missing, assuming package has no files currently installed.

Looking that message on google, I found a webpage ([http://serverfault.com/questions/430682/dpkg-warning-files-list-file-for-package-x-missing](http://serverfault.com/questions/430682/dpkg-warning-files-list-file-for-package-x-missing)) where someone designed a special command to install --reinstall all the package for which dpkg is complaining, but it didn't work for me because it was calling apt-get upgrade which waited for input so I edited it a bit:
for package in $(apt-get install --reinstall gparted 2>&1 | grep "warning: files list file" | sed "s/.*\`//; s/'.*//"); do apt-get install --reinstall "$package"; done

This command is to be run from a sudo -s terminal. Because I read a lot of errors regarding initramfs in the output, I ran the following command after the previous one was done: "update-initramfs -k all -u".
After a reboot I was still getting initramfs errors when using apt or dpkg, so I tried to install --reinstall initramfs-tools, but it didn't work well. I was then unable to install initramfs-tools because it couldn't find update-initramfs, which is provided by ... initramfs-tools ! (seriously ?)
I commented the part of the /var/lib/dpkg/info/initramfs-tools.postinst file which was complaining about update-initramfs, ran dpkg --configure -a which now worked because it did not try to call update-initramfs anymore, then decommented the lines and ran update-initramfs -k all -u manually.

I rebooted, did a dist-upgrade, rebooted again, and everything seems fine ! It was not very complicated after all ! ;-)

I even created a new user now that I saw that everything was working  well, copied all the files and chowned over again, and I have now my own  user with my own name instead of the live user account name.

EDIT: However there is a security issue with all this, because all the tty's are automatically logged into the live session user without any password, even though i'm logged on another user in the graphical interface. Because the live session user can use sudo without providing a password, this gives total root access to the computer... This can be fixed by editing all the /etc/init/ttyX.conf files, where X is a number from 1 to 6, and replacing the last line:
exec /bin/login -f elementary </dev/tty1 > /dev/tty1 2>&1
By the following, with the X replaced by the tty number of course, here it's the 1:
exec /sbin/getty -8 38400 tty1

---

### Post by howefield on 2014-08-09
Thread moved.

---

