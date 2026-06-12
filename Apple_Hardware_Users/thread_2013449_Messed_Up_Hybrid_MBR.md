---
title: "Messed Up Hybrid MBR"
date: 2012-06-30
forum: Apple Hardware Users
---

### Post by medman826 on 2012-06-30
I have a MacBook Pro 8,2 and I successfully installed Ubuntu 12.04. I realized that I did not have swap space afterwards, so I made a new partition for swap space using disk utility. Now, my partitions are all messed up.

When I attempt to boot into Ubuntu I get "Error: No such partition" and then "grub rescue >" I can still boot into Mac OS X Lion, so I was able to get information about the disks.

diskutil list gives me this:

[B]/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS HD                      465.0 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:                 Linux Swap                         9.2 GB     disk0s4
   5: 0FC63DAF-8483-4772-8E79-3D69D8477DE4               20.0 GB    disk0s5[/B]

and printing my partition list from the gdisk command line tool gives me this:

[B]GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): p
Disk /dev/disk0: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00003AD5-6824-0000-2112-0000DD520000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 9831517 sectors (4.7 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       908612759   433.1 GiB   AF00  Customer
   3       908612760       909882295   619.9 MiB   AB00  Recovery HD
   4       919713792       937711615   8.6 GiB     8200  SWAP
   5       937711616       976773119   18.6 GiB    8300  UBUNTU[/B]

As you can see, the partitions are not reading correctly in gdisk. I want it to be the way diskutil list shows it. What can I do to fix my hybrid MBR?

---

### Post by DJ_Max on 2012-07-01
Don't use OS X's Disk Utility again, you'll just run into problems like you have now.

Boot the Ubuntu disc, and re-install Grub

---

### Post by medman826 on 2012-07-02
I appreciate your reply. On the ubuntu live cd I see the incorrect partition scheme that gdisk printed. I understand what has gone wrong, I think, but I do not know how to fix it.

The easy thing to do would be to simply erase all my partitions but mac os x, and then reinstall ubuntu properly. Is there an easy way to backup my ubuntu partition to an image file for restoring from (like mac os x disk utility can) or a good/better way to back up and restore all of my ubuntu settings and files?

Thanks.

edit: I forgot to mention that i attempted to re-install grub and got the message

> /usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

edit 2: ubuntu is not currently capable of mounting my ubuntu partition, although mac os x seems to still know it's proper size and location. I hope there is some way to work around that.

edit 3: interestingly enough, the installation assistant for ubuntu on the live cd sees the partitions correctly. what the heck is that about?

---

### Post by DJ_Max on 2012-07-03
Boot the the CD, I normally use the Alternative disc. But regardless, choose "Rescue Install" or whatever it's called, and go through, it will ask you questions similar to a install, but it will come to a point where it will ask you if you want to re-install GRUB along with other options.

---

### Post by medman826 on 2012-07-03
I have already erased everything but my mac partition and reinstalled ubuntu, letting the installer do the partitioning. Config took a little bit but I think I have everything back the way I need it. All is well.

For future reference, though, what is a good program for backing up ubuntu?

---

### Post by animalk on 2012-07-03
Ubuntu 12.04 has a backup utility built into it. You can find it in System Settings. I haven't tried it yet so I can't comment on how good it is.

---

