---
title: "part_nowrite check:: No such file or directory"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by phyx on 2006-02-16
**OS: Ubuntu 5.10, 64-bit**

Hi, I'm having a big problem with lilo. I'm trying to install a boot loader on 1 partition of a USB device, but it's not working out. Whenver I run lilo, I get a "part_nowrite check:: No such file or directory" message. Now, since my OS is on SCSI sda, the USB device ends up getting /dev/sdb. So I mount the first USB device partition with devdir (a folder with my file system).

*# mount -t ext3 -v /dev/sdb1 devdir*

Within devdir, I have my own lilo configuration file etc/newlilo.conf. Now, when I run lilo on my configuration file, I get that "part_nowrite check:: No such file or directory". I've spent the last 2 days looking on google and linuxquestions, but they have not been helpful. 

*# /sbin/lilo -C /etc/newlilo.conf -r devdir*

Reading boot sector from /dev/sdb
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/sda4' -> '/dev/sda4'
part_nowrite check:: No such file or directory

The warning about '/dev/sda4' -> '/dev/sda4' concerns me a bit too. Even more is that the exact same setup is executed on _SuSe 32-bit_ and it worked with "Added 2.4.28 *". I'm beginning to think it's something with Ubuntu/Debian or whatnot.

Below is my lilo configuration file. This seemed to fail on my Ubuntu 5.10 64-bit, but worked on SuSe 32-bit (not sure the version).

[I]newlilo.conf:
# new lilo config file
boot = /dev/sdb      # where the MBR will be written
disk = /dev/sdb       # tell bios this is going to be the first dist
        bios = 0x80     # on boot in a new machine
vga = 0x311
backup =/dev/null
compact                  # makes disk access faster
lba32                       # access disks with > 1023 cylinders
image = /boot/bzImage   # the linux kernel to boot
              label = 2.4.28
        root=/dev/hda1       # on boot, this is going to be mounted as hda
                                        # and contain the root filesystem
        append="console=/dev/tty2"  # redirect the console

[/I]

---

