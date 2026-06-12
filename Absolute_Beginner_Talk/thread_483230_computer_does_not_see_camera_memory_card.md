---
title: "computer does not see camera memory card"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by connieward on 2007-06-24
I'm using Ubuntu Edge Elf, and the camera memory card says "1.0 GB SanDisk".

I insert the camera memory and open the "Computer - File Browser" The only unknown thing there says "Smart Media Drive" so I think that means the slot with the camera card.  But when I click on it, the message says, "Unable to mount the selected volume."

Under "Show more details" is:

mount: no medium found
mount: no medium found
error: could not execute pmount

The slot itself cannot be the problem because it works fine on xp--on the other side of the partition-- and it worked for suse 9.3, which was here until I installed ubuntu. 

I went into xp when ubuntu couldn't see the memory.  xp saw it immediately.  Without taking the card out, I booted back into ubuntu, but ubuntu still couldn't see it.

I googled the error message but could not find anyone with this problem.  I went to ubuntuwiki and couldn't find anything there either.  Help, please?

---

### Post by ukripper on 2007-06-24
try this link -
[http://ubuntuforums.org/archive/index.php/t-906.html](http://ubuntuforums.org/archive/index.php/t-906.html)

---

### Post by connieward on 2007-06-25
Thank you, ukripper, for showing me where to find the solution in the archives, but I am not good enough to follow the directions.

I tried the different commands that the page suggested:

"/dev/sda1 /media/usbdisk auto rw,user,noauto 0 0" 
"/dev/sda1 /mnt/memorystick vfat user,noauto,rw 0 0 uid=1000 gid=1000"
"sudo mkfs.msdos /dev/sda1"

None of these worked.  The computer just said that the device didn't exist or that it wasn't a command.  Maybe I was in the wrong part of the computer when I typed? 

That top line said it should be added to /etc/fstab, but I don't know how to add things to /etc/fstab.  The slashes mean I need to be in terminal, I know that much, but I don't know *where* in terminal or how to get there. 

I can cd to /etc but the computer won't let me cd /fstab.  It says fstab is not a directory.

Oh, and I found out that I don't have Edgy Elk, I have Dapper Drake.

---

### Post by Seisen on 2007-06-25
To open the terminal go to Applications>Accessories>Terminal

To open your fstab file do this in the terminal

```
gksudo gedit /etc/fstab
```

gksudo gives you super user rights to change the file and gedit is like notepad in Windows.

---

### Post by ukripper on 2007-06-25
> **connieward said:**
> Thank you, ukripper, for showing me where to find the solution in the archives, but I am not good enough to follow the directions.

I tried the different commands that the page suggested:

"/dev/sda1 /media/usbdisk auto rw,user,noauto 0 0" 
"/dev/sda1 /mnt/memorystick vfat user,noauto,rw 0 0 uid=1000 gid=1000"
"sudo mkfs.msdos /dev/sda1"

None of these worked.  The computer just said that the device didn't exist or that it wasn't a command.  Maybe I was in the wrong part of the computer when I typed? 

That top line said it should be added to /etc/fstab, but I don't know how to add things to /etc/fstab.  The slashes mean I need to be in terminal, I know that much, but I don't know *where* in terminal or how to get there. 

I can cd to /etc but the computer won't let me cd /fstab.  It says fstab is not a directory.

Oh, and I found out that I don't have Edgy Elk, I have Dapper Drake.

Just go to terminal and type below:

as described above 
```
sudo gedit /etc/fstab
```

and amend as suggested in that link. It doesn't matter whether you using Edgy or Dapper because fstab is same

---

### Post by connieward on 2007-06-25
Thanks, Seisen and Ukripper, I got into the fstab and added the line

/dev/sda1 /media/usbdisk auto rw,user,noauto 0 0

Then I typed mkdir /media/usbdisk into the terminal.

usbdisk appeared on the list in Computer, but when i tried to open it, I received this error:

mount: /dev/sda1 is not a block device

I changed "auto" to "vfat" in the fstab (as suggested on the solutions page), but the error stayed the same.

---

### Post by VChief on 2007-06-26
/bump

---

### Post by PaulFr on 2007-06-26
Maybe /dev/sda1 is the wrong device, can you try the following ?

1. Reboot your machine without the memory card installed. Then insert the card, and run the command **dmesg** in a terminal. Look at the last few lines. For reference, my output under Feisty Fawn is: 
> [218833.968000] tifm_core: MMC/SD card detected in socket 0:1
[218834.532000] mmcblk0: mmc1:80ca SD01G 992000KiB 
[218834.532000]  mmcblk0: p1

Then my card shows up as /dev/mmcblk0p1 (vfat type). Do you see any lines like this ?
2. Also, what does your /etc/fstab contain ?
3. Can you run the following command **lspci** in a terminal and post the output here.

---

### Post by connieward on 2007-06-26
Thank you, PaulFr, for helping me!

1.  dmesg command gave me no lines that looked anything like yours.  None of my lines start with tifm or mmcblk0.  But further up the list there were lines about sd:

[bunch of numbers] Driver 'sd' needs updating - please use bus_type methods
[17179600.264000] sd 1:0:0:0: Attached scsi removable disk sda
[17179600.448000]   Vendor: Generic   Model: USB Storage-SMC   Rev: 500A
[17179600.448000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17179600.452000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179600.464000] sd 0:0:0:0: Attached scsi removable disk sdb
[17179600.464000] sd 0:0:0:0: Attached scsi generic sg1 type 0

2. /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           reiserfs defaults        0       2
/dev/hda1       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1 /media/memorystick vfat rw,user,noauto 0 0

3.  lspci command gave me this:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:08.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

### Post by PaulFr on 2007-06-26
1. First, check output of **ls -l /dev/sd*** - can you see /dev/sda<n> and /dev/sdb<n>, where <n> is 0-9 (for example, /dev/sda0 or /dev/sdb0 or /dev/sda1 or /dev/sdb1) ?
2. Then for every such entry, run the command **sudo fdisk -l <device_name>**. So for example, if /dev/sdb1 shows up, run the command ```
sudo fdisk -l /dev/sdb1
``` This will show you the partition table on the device.
3. If you find a partition with type FAT, that is probably your device (I suspect it is /dev/sdb1 for you based on your dmesg).
Now, you can edit your fstab to match the device you found above. Hope this helps.

---

### Post by connieward on 2007-06-26
I hope you guys haven't given up on me yet.  
Are you ready for another round?  Okay, here goes!

1. Both /dev/sda and /dev/sdb are listed, but neither have a number

connie@connie-desktop:~$ ls -l /dev/sd*
brw-rw---- 1 root plugdev 8,  0 2007-06-26 09:02 /dev/sda
brw-rw---- 1 root plugdev 8, 16 2007-06-26 09:02 /dev/sdb

2. I did the sudo fdisk to both of them, but the computer didn't write anything.

connie@connie-desktop:~$ sudo fdisk -l /dev/sda
Password:
connie@connie-desktop:~$ sudo fdisk -l /dev/sdb
connie@connie-desktop:~$

3.  I couldn't do this part.

---

### Post by PaulFr on 2007-06-27
Okay, lets try a number of things to see where the problem may lie:

1. Comment out the entry / entries you may have introduced in /etc/fstab for /dev/sda or /dev/sdb.
2. Reboot the machine **without** your card inserted. Check your dmesg for sda or sdb messages - also check for any lines / errors regarding 'hotplug'.
3. Login as yourselves, and start a terminal. Run the command **getent group | egrep '(hal|plug)'** and paste its output here.
4. I presume you have updated your system to the latest versions of Dapper. If not, please do so by **sudo apt-get update; sudo apt-get upgrade**.
4. Run **sudo fdisk -l** (that's right, not on sda or sdb) to show all filesystems recognized by system. Can you post the output of this ?
5. Now introduce the camera card. Check the last few dmesg lines for sda/sdb references. Again run **sudo fdisk -l** and compare it with earlier output.
6. Another command's output to check is **sudo lshw** to see the details of the hardware on your system - save the output to a file, and paste only the lines relevant to your MMC / SD card controller.
This should give us something to work with :D

---

### Post by connieward on 2007-06-27
Thank you, PaulFr, for your patience.  I used gedit to copy/paste all the terminal messages, hoping that a small application would not effect the results.


2 & 5.  There was only one line different on dmesg before and after inserting card: a space within the word "revision"

BEFORE [17179598.776000]   Type:   Direct-Access                      ANSI SCSI revision: 00
---AFTER [17179598.776000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00

None of the sd lines are at the end of list.  They are about 2/3 of the way down.


3.  getent group | egrep '(hal|plug)'

cdrom:x:24:haldaemon,connie
floppy:x:25:haldaemon,connie
plugdev:x:46:haldaemon,connie
haldaemon:x:108:


4.  fdisk -l  memory card OUT

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2659    21358386    c  W95 FAT32 (LBA)
/dev/hda2            2660        2707      385560   82  Linux swap / Solaris
/dev/hda3            2708        4097    11163594   83  Linux
/dev/hda4            4098        4865     6168960   83  Linux

5.  fdisk -l is exactly the same as when memory card is IN.  No differences whatsoever.


6.  sudo lshw  I hope I didn't include too much.  I looked for mmc or sd, and controller.

 *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-28-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: USB Storage Device
                   vendor: Generic
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi0
                   version: 1.00
                   serial: 0AEC305000001A000
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: USB Storage-SMC
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sdb
                      version: 500A
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
              *-usb:1
                   description: Mass storage device
                   product: TEAC FD-05PUB
                   vendor: TEAC
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi1
                   version: 0.00
                   capabilities: usb-1.00 floppy emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: FD-05PUB
                      vendor: TEAC
                      physical id: 0.0.0
                      bus info: scsi@1:0.0.0
                      logical name: /dev/sda
                      version: 1026
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sda

---

### Post by PaulFr on 2007-06-28
Hi Connie, Just trying to help. So let's review:
1. Your memory card reader is USB Storage-SMC. Is your memory card reader removable (and you have it plugged into one of the USB slots) ?
2. The logical device corresponding to your memory card is /dev/sdb (from your lshw output **logical name: /dev/sdb**).
3. /dev/sda corresponds to the device TEAC FD-05PUB which is your floppy drive.
4. But your fdisk -l is not changing after you insert your memory card into the card reader.

First possibility: Follow steps suggested by Seisen and ukripper and add line to /etc/fstab, but use **/dev/sdb1** rather than /dev/sda1. Reboot machine and issue **sudo fdisk -l** to see if you can see a FAT/VFAT entry. If there is such an entry, you should be able to use the card storage as usual.

If this does not succeed, 

1. If your card reader is an external USB device (removable), I would suggest that you try booting with it removed from the USB slot, then insert it and see if dmesg messages appear for it (if yes, please paste here). Be aware that the logical name **/dev/sdb** may change if you plug it in later, so you have to check **sudo lshw** again to verify the logical name assoicated with "USB Storage-SMC" device.
2. Check you have udevd running (**ps -ef|grep udevd**) udevd is the one that monitors your removable devices for insertion and is supposed to create devices for it.
3. Check your dmesg for messages from 'udev' : **dmesg | grep udev** - are there any error lines indicated? Please paste here.

---

### Post by connieward on 2007-06-29
I changed the fstab to /dev/sdb1 and rebooted, but there was no new FAT/VFAT entry listed in the fdisk -l.  When I changed "fat" to "auto" in this line

 /dev/sdb1 /media/usbdisk auto rw,user,noauto 0 0

I still don't have another item listed in the fdisk, but I do have a different error message when I insert the card.  

mount: i could not determine the filesystem type, and none was specified


If this did not succeed I was to do three other things:

#1 was to remove the card reader.  I would have to open the box to do that, so I don't think it is an external USB device.  

#2.  Check if I have udevd running.  I did the command, but I don't know what the results mean.
connie@connie-desktop:~$ ps -ef|grep udevd
root      2238     1  0 07:52 ?        00:00:00 /sbin/udevd --daemon
connie    5186  5181  0 08:01 pts/0    00:00:00 grep udevd

#3.  Looking for error messages from udev.  Nothing at all showed up.
connie@connie-desktop:~$ dmesg | grep udev
connie@connie-desktop:~$


Thinking about opening the box to unplug the card reader reminds me of an incident a few weeks ago, I put the memory in the wrong slot and it fell into the computer.  Husband had to open the computer and dig it out.  I didn't think it mattered because the card works in xp, but could Linux be more sensitive to poking around inside the box?

Which brings me to this: I think I am hurting my ubuntu by making all these changes because the last time I rebooted, ubuntu got stuck *twice* on "checking all filesystems".  I used the switch to turn off the computer both times and start it again before I could finally get in.  I was afraid that I had lost ubuntu for sure and would have to re-install.  Maybe I just don't know enough about Linux to be doing this right, and I don't want to lose my Linux while trying to get a camera card to work correctly.  I used computers before memory cards were invented, so it won't hurt me to do without one now.  (Heck, I used computers before floppies were invented--we used a cassette recorder to save our programs.)

Thank you, PaulFr, for trying to help the helpless.  You Linux guys are so sweet.

---

### Post by PaulFr on 2007-06-30
Hi Connie, Last attempt for me.

1. Remove your camera memory card. Start a terminal to type the following commands.

2. Verify that your /etc/fstab looks like the following:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda4 /home reiserfs defaults 0 2
/dev/hda1 /windows vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda2 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
**/dev/sdb1   /media/memorystick   vfat   rw,user,noauto  0  0**
- The key line here is the last one - do not change any other lines.
- Make sure there are no spaces in "rw,user,noauto"
- Please make sure there are no blank lines in the middle of /etc/fstab
- Add one blank line at the very end.

Use **gksudo gedit /etc/fstab** to edit the file and fix any issues.

3. Next verify that /media/memorystick exists by **ls -l /media/memorystick**. You should not get any error. If you do, please run **sudo mkdir -p /media/memorystick**.

4. Reboot your machine. Login and start a terminal for the following commands:

5. Insert your camera memory card. Run **dmesg** to see if any error messages appear.

6. If the error message mentioned in your last message (**mount: i could not determine the filesystem type, and none was specified**) appears, then it appears your card may be unformatted.

7. Are you willing to format the memory card (and lose any files on it) ? If you are, then issue the command ```
sudo  mkfs.vfat  /dev/sdb1
``` to format your memory card. If any errors here, this is the end of the line for me - and some one else will have to diagnose the problem :-(

8. If the above step succeeded, now pull out your card - ignore any error messages. And then insert it back again.

9. Check whether card has been mounted properly **sudo fdisk -l** and see if any line has FAT or FAT16 or FAT32 or VFAT in it. This line should have /dev/sdb1 at the beginning.

10. If it does, you can begin to use the card (through the Places menu - I am not sure whether that is there in Dapper). You may also receive a notification indicating a memory card has been inserted. All good to go.

11. If it does not, final command: ```
sudo  mount  /media/memorystick
``` If this gives errors, again this is the end of the line for me - and some one else will have to diagnose the problem :-(

Best of luck.

---

