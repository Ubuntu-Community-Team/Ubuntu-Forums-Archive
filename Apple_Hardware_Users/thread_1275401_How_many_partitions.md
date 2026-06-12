---
title: "How many partitions?"
date: 2009-09-25
forum: Apple Hardware Users
---

### Post by Nottawa on 2009-09-25
I am a new/soon to be user of Linux.  I am going to put it on my MacBook.  How many partitions should I put on my harddrive?  I know I need at least one for OSX and two for linux.  Is it worth while putting more in place.  I would like to be able to see my data files from both OS's, if that is possible.

Thanks.

---

### Post by pandanuma on 2009-09-25
3 partitions...
root partition: /    about 8gig
swap partition: /swap  about 2 times the size of your ram
home partition: /home  as big as you like

check out
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by the_squircle on 2009-09-25
What is suggested above is impossible, as your mac comes with two partitions on it: a 100-200MB partition for the EFI data, and the OS X partition. I partitioned my drive with one ext3 partition for Ubuntu, and one for swap. That equaled the maximum permittable partitions; 4.

---

### Post by gwydionwaters on 2009-09-25
there is no limit, i currently have five.
```

rob@ubox009:~$ sudo parted
GNU Parted 1.8.9
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ST980815A (ide)
Disk /dev/hda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: mac

Number  Start   End     Size    File system  Name      Flags
 1      512B    32.8kB  32.3kB               Apple          
 2      32.8kB  10.0MB  10.0MB  hfs          yaboot    boot 
 3      10.0MB  4010MB  4000MB  ext3         rescue         
 4      4010MB  79.2GB  75.2GB  ext3         untitled       
 5      79.2GB  80.0GB  816MB   linux-swap   swap      swap 

(parted)                          

```

---

### Post by sweetleaf on 2009-09-25
-

---

### Post by MacUsers on 2009-09-28
> **the_squircle said:**
> What is suggested above is impossible, as your mac comes with two partitions on it: a 100-200MB partition for the EFI data, and the OS X partition.This is not true: I presently have 7
```
maci:~ ss$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS OSX                     28.9 GB    disk0s2
   3:                  Apple_HFS Programs                21.0 GB    disk0s3
   4:                  Apple_HFS DataVault               75.0 GB    disk0s4
   5:                  Apple_HFS Projects                99.9 GB    disk0s5
   6:       Microsoft Basic Data                         22.9 GB    disk0s6
   7:                 Linux Swap                         1.0 GB     disk0s7
```

---

### Post by bluTaz on 2009-09-28
i remember reading that you can have a max of 4 primary partitions on one drive... however, you can make one of those an exteded partion and break it down into smaller partions

---

### Post by oldfred on 2009-09-29
EFI partitioning or GUID *partition* table (GPT) *partition* does not have the MBR limits. All new drives over 2TB will have to be EFI and apple & some Windows servers use EFI now. Old grub was not EFI aware but some old grubs have been modified to see the EFI correctly. New grub2 is efi aware.

---

