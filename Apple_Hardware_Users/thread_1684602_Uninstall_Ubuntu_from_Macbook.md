---
title: "Uninstall Ubuntu from Macbook"
date: 2011-02-09
forum: Apple Hardware Users
---

### Post by philperrin on 2011-02-09
Hi all,
Thanks in advance for any insights on this. I'm posting this here instead of on a mac forum since I believe you mostly know more about managing this than many mac forum posters would. I installed a Linux swap on my macbook and used rEFIt for booting between the two. I'm not at a stage where I'll have separate hardware for my mac and linux and would like to clean up my macbook's disk. I assume the steps to do so are as follows:
-backup everything first.
-boot up with mac install disk
-use terminal/disk utility to unmount/remove/repartition the linux partitions.
-enjoy having one machine for mac, and one machine for linux.

Below are the partitions - I'd like any help on removing the suspicious mbr behavior as well.
Thanks.







```
pmac:~ philperrin$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *80.0 GB    disk0
   1:                       0xEE                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            63.4 GB    disk0s2
   3:                       0xEE                         63.6 GB    disk0s3
   4:                      Linux                         15.7 GB    disk0s4
pmac:~ philperrin$ sudo gpt -r show /dev/disk0
Password:
gpt show: /dev/disk0: Suspicious MBR at sector 0
      start       size  index  contents
          0          1         MBR
          1          1         Pri GPT header
          2         32         Pri GPT table
         34          6         
         40     409600      1  GPT part - C12A7328-F81F-11D2-BA4B-00A0C93EC93B
     409640  123731968      2  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
  124141608       2008         
  124143616       2048      3  GPT part - 21686148-6449-6E6F-744E-656564454649
  124145664   30713856      4  GPT part - EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
  154859520    1441792      5  GPT part - 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F
  156301312        143         
  156301455         32         Sec GPT table
  156301487          1         Sec GPT header

```

---

### Post by srs5694 on 2011-02-09
Your basic procedure is sound. Unlike an installation on a PC, an installation on a Mac doesn't render the computer dependent upon the Linux partitions to boot. In a worst-case scenario, you could hold down the Command key while booting to select OS X. You might want to uninstall rEFIt unless you plan to install Windows or have multiple OS X versions running on the computer.

One comment: Your hybrid MBR is odd at best, corrupt at worst. Specifically, it's got two 0xEE partitions. Some versions of the Ubuntu installer tend to create this type of setup, which often causes problems. I'm not sure how Disk Utility will react to it. At best, it'll fix it automatically when you delete the Linux partitions. At worst, it'll flake out and corrupt your disk. Thus, I recommend you take care of this before you do anything else. It's possible that Apple's gpt utility has an option to write a fresh protective MBR, but if so I don't know what the option is. My own GPT fdisk (gdisk) utility can do the job. You can download a copy from its [Sourceforge download page,](http://sourceforge.net/projects/gptfdisk/files/) then use the "n" option on the experts' menu:

```
$ **sudo gdisk /dev/disk0**
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): **x**

Expert command (? for help): **n**

Expert command (? for help): **o**
MBR disk identifier: 0x00000000
MBR partitions:
Number     Boot     Start (sector)     Length (sectors)    Type
   1                        1            3981311     0xEE

Disk size is 3981312 sectors (1.9 GiB)

Expert command (? for help): **w**

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.

```

The "x" command enters expert mode, "n" creates a new protective MBR, "o" displays the MBR data (so you can verify you've done what you expected to do), and "w" saves your changes. With this done, there'll be no chance that unusual MBR data will confuse a GPT-aware partitioning tool.

---

### Post by philperrin on 2011-02-09
Thanks - I was worried about there being some deep rooted problems in there. I'll test out some options on a clone and try the gdisk utility.

If anyone reading this has had a similar experience, I'd appreciate hearing from them.

Cheers.

---

### Post by joopbraak on 2011-04-18
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/757201](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/757201)

---

