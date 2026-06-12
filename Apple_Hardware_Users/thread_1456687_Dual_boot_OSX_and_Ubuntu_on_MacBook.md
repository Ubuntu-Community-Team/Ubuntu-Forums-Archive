---
title: "Dual boot OSX and Ubuntu on MacBook"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by kornelix on 2010-04-17
Dual boot OSX and Ubuntu on MacBookPro

A friend asked me if he could add Ubuntu to his MacBook in a dual-boot configuration with shared files. I did not know, but I agreed to try. This took me about a day, with most of the time spent reading various forums and documents. I have zero experience with OSX and reasonable experience with Ubuntu. I hope this document is enough for others to be useful. Add postings to correct errors or expand on what is missing.
```

This case, starting conditions:
   MacBookPro with OSX 10.5.7
   Ubuntu 9.10 on bootable CD-ROM
   Gparted on bootable CD-ROM

1. Boot up OSX and do the following:
   - Install all available updates for OSX (works like Windows).
   - Back-up personal files on OSX disk.
   - Do the following 2 commands in a terminal window:
     $ id -u      # get your user ID (in my case 501)
     $ id -g      # get your group ID (in my case 20)

2. Boot Gparted:
   - insert the bootable CD-ROM.
   - power up while holding down the ALT key.
   - when the "windows" disk image appears, click it to boot.
     (OSX calls all other bootable media "Windows")

3. Using Gparted, shorten the OSX partition and add two new 
   partitions: 10 GB for Ubuntu and 2 GB for Linux swap.
   In my case, partitions are now as follows:
      sda1     small boot partition called "EFI"
      sda2     OSX partition with hfs+ file system
      sda3     new partition for Ubuntu, ext3 file system
      sda4     new partition for Linux swap
   In OSX, these are named disk0s1 ... disk0s4.

4. Boot the Ubuntu CD-ROM (same as in step 2).
   Install Ubuntu on sda3 (usual procedure).

5. Boot to the newly installed Ubuntu:
   - power up while holding down the ALT key.
   - when the "windows" disk image appears, click it to boot.

6. Do Ubuntu software updates and personal configurations
   (a LAN cable to your internet router is required at first).
   Install hardware drivers for WLAN and graphics chip.
   Remove the cable, reboot, check that WLAN is working.

7. Change your Ubuntu IDs to match OSX.
   This will give you access to your files on OSX.
   - uuuu and gggg are the OSX IDs from step 1.
   - "uname" is your Ubuntu login user name
   - In my case group 20 was already assigned to "dialout", 
     so I assigned dialout to group 199 to free up group 20.
   - Add a root account: $ passwd root (provide passwords)
   - $ su (supply password, become root)
   - $ usermod -u uuuu -g gggg uname   # assign uuuu:gggg to uname
   - $ chown -R uname:uname /home/uname   # fix file ownerships

8. Mount the OSX partition and check that you have read access to 
   the files in /users/oname, where oname is your OSX login name.    
   - $ sudo mkdir /zmac     # directory to mount OSX partition
   - $ sudo mount /dev/sda2 /zmac     # mount it
   - $ ls /zmac/users/oname/*         # check read access

9. Add OSX partition to /etc/fstab so it will mount at boot:
      /dev/sda2  /zmac  hfsplus  default  0  1
    
10. To get write access from Ubuntu to the files on OSX, 
    journaling for the OSX file system must be turned off.    
    - boot to OSX and open a terminal window
    - $ diskutil disableJournal disk0s2     # OSX partition

11. Boot to Ubuntu and check write access to your OSX files:
   - $ cd /zmac/users/oname
   - $ echo "test" > temp
   - $ rm temp


```

---

