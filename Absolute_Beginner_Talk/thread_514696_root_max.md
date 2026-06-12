---
title: "root max"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by overownt on 2007-08-01
i go to move large files to root and it said my root drive is full, yet i am on a 60gb drive with only 2.5 gbs full... i am using slax

---

### Post by overownt on 2007-08-01
any answers to make this work/commands

---

### Post by aysiu on 2007-08-01
Can you post the output of this terminal command? ```
df -h
```

---

### Post by overownt on 2007-08-01
root@slax:~# df -h
Filesystem            Size         Used           Avail      Use% Mounted on

tmpfs                 488M         251M           237M     52% /

/dev/sda1              56G       3.8G             53G        7% /mnt/sda1


sorry bout the unessary bump, i forgot i can edit posts * apologies*:mad:

---

### Post by aysiu on 2007-08-01
Uh, that looks weird. Why is it *tmpfs*? In any case, your root partition *is* almost full. It has only 237 MB free. Are you using a live CD?

---

### Post by overownt on 2007-08-01
hmm i think i figured out why, im not using a live cd but i used the pendrivelinux install, i reallized it did not state anything about it having a persistants feature (running like a live cd) 

can i make the partition the size of the hard disc?

---

### Post by overownt on 2007-08-01
alright so i have desided to scrap slax and us ubuntu 6.10

i am using this guide:[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610]("http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610")

and i had 2 questions about what i put in the terminal:
         
          * type p to show the existing partition and d to delete it
          * type p again to show any remaining partitions (if partitions exist, repeat step 3)
          * type n to make a new partition
          * type p for primary partition
                o type 1 to make this the first partition
                o hit enter to use the default 1st cylinder
                o type +750M to set the partition size
           
         the casper partition is what holds all the rest of the data for persistents, but if i wanted to put games (in root)on here i would have to make it way bigger than +750M?

                o type a to make this partition active
                o type 1 to select partition 1
                o type t to change the partition filesystem
                o type 6 to select the fat16 file system
    
       now here is my other question, no system will boot for me on fat 16, do you have any other suggestions? on what other hex code i should use?

o type w to write the new partition table
   6. Type umount /dev/sdx1 to unmount the partition
   7. Type mkfs.vfat -F 16 -n usb /dev/sdx1 to format the first partition
          * “Alternately you can try mkfs.vfat -F 32 -n usb /dev/sdx1 (doesn’t always work)”

---

