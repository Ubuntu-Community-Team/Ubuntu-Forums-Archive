---
title: "All mounts empty on install"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by walding on 2007-11-03
Hi,

I have just done a fresh install of Gutsy (Ubuntu) from the LiveCD on a PC with two HDDs.  Previously only Windows XP was on the PC, although we did partition the drive when installing Windows XP.

During the Gutsy install, I requested the other partitions to be mounted in /media.  The fstab looks OK to me, but all of the other partitions (including the ones with all files & documents on) are empty when I try to browse them.

fstab output below.  Can anyone help, please?

Ta.

AW

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=a9a49879-73b8-4796-8fbb-b286460702e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=25598b7a-7eb7-47bf-8709-9bb3b8c82c81 /home           ext3    defaults        0       2
# /dev/hda5
UUID=9A84FDBC84FD9AC9 /media/files    ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
UUID=04E4DB94E4DB8678 /media/old_drive ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda1
UUID=18C89D2DC89D0A60 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=6d97b4d6-b83d-4c1c-a9ce-7661491fc588 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by walding on 2007-11-03
I think I know the source of the problem...the ntfs partitions are marked as "in use" by Windows.  However, Windows has failed (terminally, I think - it won't boot in any mode.  shame.)

Is there a way to unmark the partitions as in use?  I don't want to add a force command to fstab, in case I get Windows up and running again.

AW

FYI, I ran ntfs-config to try to mount these, and got the following message:

Mounting /media/files failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda5 /media/files -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda5 /media/files ntfs-3g defaults,force

---

### Post by walding on 2007-11-03
OK - I have a solution, in case anyone else has this problem....  I've now force mounted in a terminal window, as suggested by ntfs-config (just copied and pasted the force-mount line, adding sudo at the front), and backed up my files to somewhere safe!  I'll now format the windows drive and reinstall it.  

Of course, Windows being an expensive commercial product, it will only take 30 minutes to install, like Ubuntu, right?  ;-)

My weekend is cancelled....

AW

---

