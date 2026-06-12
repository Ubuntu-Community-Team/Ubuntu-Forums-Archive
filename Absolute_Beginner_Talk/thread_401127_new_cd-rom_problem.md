---
title: "new cd-rom problem"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by benner on 2007-04-04
just connected a new cd-rom and am not sure if the computer is seeing it or not.  it is connected to a PCI card that has 2 IDE ports on it.  my motherboard only has a spot for one ide cable to connect and i already had 2 devices so i bought this card.  when i boot up i don't see any evidence of it and in the bios it don't see it either.  because it's a pci card, i'm not sure if it is supposed to be there or not.  the device manager seems to see the card, i think.  I see the following listed as PCI:

IT/ITE8212 Dual channel ATA RAID

but i don't see the CD-rom listed anywhere

in /dev I didn't see anything that was obviously a new CD-rom either, but I am still new to all of this...


can anyone offer a suggestion?  thanks in advance...

---

### Post by benner on 2007-04-04
btw i'm running feisty with an amd4200+ the motherboard is called 'spark'

---

### Post by Skrynesaver on 2007-04-04
Is it an IDE CD-ROM?
If so you can attach it to the drive cable of one of the existing devices, making setting the original Master and the CD-ROM slave, check the stickers on the case for something outlining the correct jumper positions
see here, [http://rtvpatch.sourceforge.net/jumpers.html](http://rtvpatch.sourceforge.net/jumpers.html)

---

### Post by benner on 2007-04-04
thanks.  it is IDE.  the jumpers are ok.  the cd-rom was just working in another machine this morning.  how would it normally go if there were no hardware problems?  should ubuntu see it right away?  do you think it should appear in the bios even though it is connected to a pci card?

---

### Post by benner on 2007-04-04
it is getting power and the lights go on the cd goes for a spin when i boot up.  the machine is set to boot first from hard disk though.

---

### Post by benner on 2007-04-05
i still haven't solved the problem 23 hours later.  the device manager seems to have it in the list but i don't understand all of the information there under the 'advanced' tab to know what is going on.

on the cd that came with it, there is a folder of linux drivers.  one is called iteraid.o  and the other is iteraid.smp 

the instructions that came with the card are pretty complicated and are written for mandrake and redhat.  also, the info seems a bit old so i don't know how feisty would deal with them.. before i mess around with anything, i thought i would ask here.  i will post the complete instructions from the guide.  sorry if it's long...  i don't know how to make it fit in a little box like some people do.


Linux
Mandrake Installation Guide and Release Notes
1.  Component Name(s) and Version #:
    Components           : For Mandrake 9.0
    Kernels Tested       : 2.4.19-16mdk
    Driver Version       : v1.0
    Release Date         : Jan 16, 2003
2.  Files Listing (in linux directory)
     redhat.txt                 This file
     mandrake.txt                      Mandrake installation guide
     driver
      |
      |
      +- md90                   Mandrake 9.0 directory
      | |- iteraid.o                   Driver module for Mandrake 9.0
      |
      +- rh73                          RedHat 7.3 directory
          |- modinfo                   Module info file
          |- modules.cgz               Compressed driver modules
          |- modules.dep               Module dependence file
          |- pcitable                  IT8212 pci info
          |- rhdd-6.1           Driver disk label
          |- iteraid.o                 Driver module for RedHat 9.0
3.  Installation Procedures
    3.1     Install IT8212 Linux Driver into an EXISTING SYSTEM
            3.1.1      Boot Linux system and login as root.
                                            68
          RAIDExpress 133 RAID USER MANUAL
3.1.2 Copy the IT8212 driver module (/linux/driver/md90/iteraid.o) to
      any directory you want, and then go to that directory.
3.1.3 You can test out the module to ensure that it works by the
      following commands:
      # insmod scsi_mod
      # insmod sd_mod
      # insmod iteraid.o
      To ensure the modules have been loaded successfully, you can
      check the driver status by using the "dmesg" command.
      # dmesg
      Then you will see the following messages.
      ...
      ...
      Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
      SCSI device sda: 120103200 512-byte hdwr sectors (61493
      MB)
      ...
      ...
3.1.4 The following commands are only for your reference.
      You can create the partition when the IT8212 driver module is
      ready.
      # fdisk /dev/sda
      If you create two partitions on /dev/sda such as /dev/sda1 and
      /dev/sda2, you can use the mkfs to make the filesystem.
                           69
   RAIDExpress 133 RAID USER MANUAL
# mkfs /dev/sda1            <-- Make /dev/sda1 ext2 filesystem
# mkfs -j /dev/sda2 <-- Make /dev/sda2 ext3 filesystem
After this you can create two directories for mount point. For
example:
# mkdir /mnt/hd0
# mkdir /mnt/hd1
# mount -t ext2 /dev/sda1 /mnt/hd0/
# mount -t ext3 /dev/sda2 /mnt/hd1/
                     70
                         RAIDExpress 133 RAID USER MANUAL
Red Hat Installation Guide and Release Notes
1.  Component Name(s) and Version #:
    Components           : For Redhat Linux 7.3
    Kernels Tested       : 2.4.18-3
    Driver Version       : v1.1
    Release Date         : Feb 7, 2003
2.  Files Listing (in linux directory)
     redhat.txt                 This file
     mandrake.txt               Mandrake installation guide
     driver                     driver directory
      |
      |
      +- md90                   Mandrake 9.0 directory
      | |- iteraid.o            Driver module for Mandrake 9.0
      |
      +- rh73                   RedHat 7.3 directory
          |- modinfo            Module info file
          |- modules.cgz        Compressed driver modules
          |- modules.dep        Module dependence file
          |- pcitable           IT8212 pci info
          |- rhdd-6.1           Driver disk label
          |- iteraid.o          Driver module for RedHat 9.0
3.  Installation Procedures
    3.1     Installing IT8212 Linux Driver into an EXISTING SYSTEM
            3.1.1      Boot Linux system and login as root.
            3.1.2      Copy iteraid.o to any directory you want, and then go to that
                                            71
          RAIDExpress 133 RAID USER MANUAL
      directory.
3.1.3 You can test out the module to ensure that it works by the
      following commands:
      # insmod scsi_mod
      # insmod sd_mod
      # insmod iteraid.o
      To ensure the modules have been loaded successfully, you can
      check the driver status by using the "dmesg" command.
      # dmesg
      Then you will see the following messages.
      ...
      ...
      Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
      SCSI device sda: 120103200 512-byte hdwr sectors (61493
      MB)
      ..
      ..
3.1.4 Most likely, you will not want to type in "insmod iteraid.o" each
      time you boot up the system. Therefore you must install the
      module and tell the system about it. To install the module, type
      in the following commands (first change directory to where the
      proper iteraid.o can be loacted):
      On Red Hat 7.3, use
      # install -d /lib/modules/2.4.18-3/kernel/drivers/scsi
                            72
    RAIDExpress 133 RAID USER MANUAL
# install -c iteraid.o /lib/modules/2.4.18-3/kernel/drivers/scsi
Then you should inform the system when to load the module.
You can add the driver to the existing RAM disk image (In
RedHat 7.3, it will be /boot/initrd-2.4.18-3.img). Use the
following commands:
# gzip -dc /boot/initrd-2.4.18-3.img > /tmp/initrd.ext2
# mkdir /mnt/initrd
# mount -o loop /tmp/initrd.ext2 /mnt/initrd
# cp iteraid.o /mnt/initrd/lib/
# cp /lib/modules/2.4.18-3/kernel/drivers/scsi/scsi_mod.o
/mnt/initrd/lib/
# cp /lib/modules/2.4.18-3/kernel/drivers/scsi/sd_mod.o
/mnt/initrd/lib/
Now, add the following lines to the file /mnt/initrd/linuxrc and you
can use the editor that you are familiar with like vi. Example of
linuxrc:
# vi /mnt/initrd/linuxrc
================================================
#!/bin/sh
echo "Loading scsi_mod module"             <-- new insert line
insmod /lib/scsi_mod.o                     <-- new insert line
echo "Loading sd_mod module"               <-- new insert line
insmod /lib/sd_mod.o                       <-- new insert line
echo "Loading IT8212 module"               <-- new insert line
                        73
                   RAIDExpress 133 RAID USER MANUAL
              insmod /lib/iteraid.o                      <-- new insert line
              ...
              ...
              ================================================
              # umount /mnt/initrd
              # gzip -c /tmp/initrd.ext2 > /boot/initrd-2.4.18-3.img
              If you are using Lilo to boot your system, you also need to run
              lilo:
              # lilo
              Then reboot your system and the driver will be loaded.
    3.1.5     Configure system to mount volumes during startup.
              Now you can inform the system to automatically mount the
              array by modifying the file /etc/fstab. E.g. You can add the
              following line to tell the system to mount /dev/sda1 to location
              /mnt/raid after startup:
              /dev/sda1        /mnt/raid     ext2 defaults     00
3.2 Installing Red Hat Linux on IT8212 Controller.
    3.2.1     Prepare your hardware for installation.
              After attaching your hard disks to IT8212 controller, you can use
              IT8212 BIOS to configure your hard disks as RAID 0, RAID 1,
              RAID 0/1 or JBOD arrays, or just use them as single disks.
              Remember to set the BOOT disk in the IT8212 BIOS
              configuration menu.
              Before installation, you must remove all the disk drives, which
                                      74
          RAIDExpress 133 RAID USER MANUAL
      are not physically attached to IT8212 controller, from your
      system.
3.2.2 Check system BIOS setting.
      In your system bios setup menu, change Boot Sequence in
      such a way that system will first boot from CDROM, and then
      from SCSI. Refer to your BIOS manual to see how to set boot
      sequence.
3.2.3 Prepare the driver diskette.
      Copy all the files under /linux/driver/rh73/ directory to a new dos
      formatted disk.
3.2.4 Install Red Hat 7.3.
             Start installing Red Hat 7.3 by booting with the CDROM.
             On "welcome to Red Hat Linux 7.3!" installation screen, a
             prompted label "boot:" will appear at the bottom of the
             screen. Then type in "expert" and press enter.
             Then you will be asked "Do you have a driver disk?".
             Select "Yes".
             When "Insert your driver disk and press "OK" to continue"
             is prompted, insert the driver disk in the floppy driver and
             then select "OK". Then the IT8212 driver will be loaded.
             Continue the installation as normal. You can refer to the
             Red Hat Linux installation guide.

thanks everyone...

---

### Post by benner on 2007-04-09
anyone?  i still haven't got it sorted and i would like to use this pci ide card to add some new hardware to my machine.

---

