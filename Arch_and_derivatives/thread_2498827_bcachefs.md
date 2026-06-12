---
title: "bcachefs"
date: 2024-06-29
forum: Arch and derivatives
---

### Post by #&amp;thj^% on 2024-06-29
A new comer to filesytems bcachefs.

Features

Bcachefs is a copy-on-write (COW) file system for Linux-based operating systems.[3] Features include caching,[4] full file-system encryption using the ChaCha20 and Poly1305 algorithms,[5] native compression[4] via LZ4, gzip[6] and Zstandard,[7] snapshots,[4] CRC-32C and 64-bit checksumming.[3] It can span block devices, including in RAID configurations.[5]

Earlier versions of Bcachefs provided all the functionality of Bcache, a block-layer cache system for Linux, with which Bcachefs shares about 80% of its code.[8] As of December 2021, the block-layer cache functionality has been removed.[7]

On a data structure level, bcachefs uses B-trees like many other modern file systems, but with an unusually large node size defaulting to 256 KiB. These nodes are internally log-structured, forming a hybrid data structure, reducing the need for rewriting nodes on update.[9] Snapshots are not implemented by cloning a COW tree, but by adding a version number to filesystem objects.[10] The COW feature and the bucket allocator enables a RAID implementation which is claimed to not suffer from the write hole nor IO fragmentation.[7]
Stability.

Bcachefs describes itself as "working and stable, with a small community of users".[11] When discussing Linux 6.9-rc3 on April 7, 2024, Linus Torvalds touched on the stability of bcachefs, saying "if you thought bcachefs was stable already, I have a bridge to sell you".[12]

I like the last line by the Man himself....LOL

There is one show stopper ATM it will not load on grub/efi, it needs rEFInd or systemd-boot. That might confuse some, and call it bad names...lol.
```
inxi -p|grep fs 
  ID-1: / size: 215.24 GiB used: 41.69 GiB (19.4%) fs: bcachefs dev: /dev/sdc3
  ID-2: /boot size: 1.9 GiB used: 369.3 MiB (19.0%) fs: ext4 dev: /dev/sdc2
  ID-3: /boot/efi size: 511 MiB used: 1.3 MiB (0.3%) fs: vfat dev: /dev/sdc1

```

Snapshots are fairly straight forward. The best part is they get stored in "/"
```
ls /snap1
bin   dev  home  lib64       mnt  proc  run   srv  tmp  var
boot  etc  lib   lost+found  opt  root  sbin  sys  usr

```
And they also can be removed with just the "rm or rm -rf" command.

Filesystem checks work like normal except syntax is different:
```
sudo bcachefs fsck /dev/sdb3
[sudo] password for me: 
bcachefs (sdb3): check_alloc_info... done
bcachefs (sdb3): check_lrus... done
bcachefs (sdb3): check_btree_backpointers... done
bcachefs (sdb3): check_backpointers_to_extents... done
bcachefs (sdb3): check_extents_to_backpointers... done
bcachefs (sdb3): check_alloc_to_lru_refs... done
bcachefs (sdb3): check_snapshot_trees... done
bcachefs (sdb3): check_snapshots... done
bcachefs (sdb3): check_subvols... done
bcachefs (sdb3): check_subvol_children... done
bcachefs (sdb3): delete_dead_snapshots... done
bcachefs (sdb3): check_root... done
bcachefs (sdb3): check_subvolume_structure... done
bcachefs (sdb3): check_directory_structure... done

```
And Status of Data:
```
bcachefs fs usage
Filesystem: fad6e580-bf0e-4338-b693-8b17958ae7e4
Size:                   233097060864
Used:                    32438931456
Online reserved:             2398720

Data type       Required/total  Durability    Devices
reserved:       1/0                [] 36840448
btree:          1/1             1             [sdb3]             430964736
user:           1/1             1             [sdb3]           29985519104

(no label) (device 0):          sdb3              rw
                                data         buckets    fragmented
  free:                 220581855232          841453
  sb:                        3149824              13        258048
  journal:                1979187200            7550
  btree:                   430964736            1644
  user:                  29985519104          115854     384911872
  cached:                          0               0
  parity:                          0               0
  stripe:                          0               0
  need_gc_gens:                    0               0
  need_discard:               524288               2
  capacity:             253366370304          966516

```

So I've been using this now for a few months and seems stable enough currently, but I'm not going to push it to a production machine just yet.

---

### Post by TheFu on 2024-07-10
Any known issues with high transaction rates or VM workloads?

---

### Post by #&amp;thj^% on 2024-07-10
None on my end, but some folks who built and formatted themself have had problems with high transaction rates.
And I suspect user errors on that.

VM workloads are just like what we see now with any formatted options.

I'm still not ready to throw this into a production system though. (It's just to new ATM and so far has a very small user base)

---

### Post by TheFu on 2024-07-10
BTRFS had issues with VM storage for a few years.  The work around was to disable something that seemed like a main reason to use BTRFS, so I never installed it anywhere.  Life has enough problems with data corruption already that I don't need a new file system that hasn't been used 5+ yrs in production around the world to cause more.

For example, this morning, I saw a SMARTd warning about 2 errors in one of my RAID1 arrays.  About a year ago, I moved off that RAID1 array, only to have the disk I'd moved onto (WD-Black) fail within 8 months.  The RMA for that WD took 6 weeks (they actually lost it inside their shipping location for 8 days!).  Now I have a new WD black and the RMA WD black has been returned/replaced (I haven't looked inside to see which) that I need to move all the 3.8+ yr old old RAID1 data onto ... er ... again.  Most of the RAID disks in that array are over 10 yrs old.

```
The following warning/error was logged by the smartd daemon:

Device: /dev/sdd [SAT], ATA error count increased from 0 to 2

Device info:
Hitachi HUA723020ALA641, S/N:xxxxxxxxxxx, WWN:5-000cca-223c1ac77, FW:MK7OA840, 2.00 TB

For details see host's SYSLOG.

```
The last weekly SMART test on that HDD doesn't show any issues, unless Power_On_Hours 33985 is something you consider a problem. ;)  It isn't even getting very hot - 40°C typically.
I run weekly short tests and monthly long tests.
```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     33985         -
# 2  Extended offline    Completed without error       00%     33822         -
# 3  Short offline       Completed without error       00%     33649         -
# 4  Short offline       Completed without error       00%     33481         -
# 5  Short offline       Completed without error       00%     33313         -
# 6  Extended offline    Completed without error       00%     33150         -
...
#18  Short offline       Completed without error       00%     31188         -
#19  Extended offline    Completed without error       00%     31026         -
#20  Short offline       Completed without error       00%     30853         -
#21  Short offline       Completed without error       00%     30685         -
```
So these are definitely new errors.

I waited 5 yrs from when ext4 was put as the default file system before I started using it.  I was on JFS and ext3 before then.

---

### Post by #&amp;thj^% on 2024-07-10
Yep I remember a few early posts of yours showing your use with JFS with ext3.

I find hard to believe that BTRFS is so flaky still on some Distros.

I'll try to keep this updated as time progresses, is there anything particular you would be interested in seeing?

Like you for me to add this new comer to my systems, is not going to happen right away if ever for that matter....needs more time to grow into a stable system.
EDIT: Oh this may help some understand a bit better: [https://bcachefs-docs.readthedocs.io/en/latest/index.html](https://bcachefs-docs.readthedocs.io/en/latest/index.html)

---

### Post by TheFu on 2024-07-10
> **1fallen said:**
>  I'll try to keep this updated as time progresses, is there anything particular you would be interested in seeing?


Just the normal stuff ....

How stable is the file system for general use?
How stable is it for hosting VMs?
How well does it integrate with LVM, if at all?
How are the snapshots used for quick recovery and backups?
And I have a slight interest in the performance compared to the top 5 other file systems.  Nobody wants one that is slower unless the extra features make up for it.  

The built-in encryption and compression are only slightly interesting to me.  For my large data storage, those files are already compressed, so doing it again won't help.  I suppose on a chromebook with 16GB of eMMC storage, compression would be very important with all the new bloat added since 18.04.  I still use a 64MB Linux sometimes and that OS comes with a bloated browser, so I know there's zero need to have 5G, 25G, 35G for an desktop OS.

I'm a simple man.  Overall, it has to actually be "better", not just "new".

---

### Post by 1fallen on 2024-09-13
Just trying to keep up with all the noise over Bcachefs:
Might be fun to give it a listen: [https://youtu.be/-w4H2-LLVdY](https://youtu.be/-w4H2-LLVdY)
> **TheFu said:**
> Just the normal stuff ....

How stable is the file system for general use?
How stable is it for hosting VMs?
How well does it integrate with LVM, if at all?
How are the snapshots used for quick recovery and backups?
And I have a slight interest in the performance compared to the top 5  other file systems.  Nobody wants one that is slower unless the extra  features make up for it.  

The built-in encryption and compression are only slightly interesting to  me.  For my large data storage, those files are already compressed, so  doing it again won't help.  I suppose on a chromebook with 16GB of eMMC  storage, compression would be very important with all the new bloat  added since 18.04.  I still use a 64MB Linux sometimes and that OS comes  with a bloated browser, so I know there's zero need to have 5G, 25G,  35G for an desktop OS.

I'm a simple man.  Overall, it has to actually be "better", not just "new".
Well I gave up on it, it won't work with my back-up strategy.
If at all I won't try it again for at least a year or more.

---

