---
title: "Checking of hard drives periodically"
date: 2014-05-02
forum: Any Other OS
---

### Post by RGMoonen on 2014-05-02
Hi there,

It just happened to me again today, I start the machine and half way through booting up it goes off to check hard drive(s).
Now, I have set the checking periods to not overlap, as that causes even worse problems, but even though it is only checking 1 out of the 3 installed drives, the same thing always happens when it is not the primary boot drive being checked. I finishes checking the drive and then displays the prompt "Checking your drives this may take some time", but this prompt never disappears. Why is this problem still persistent in the distribution?
I have never noticed this behaviour on single drive systems, they always just work, but on systems with multiple drives it still persists.

cheers

Robert

---

### Post by QIII on 2014-05-02
Hello!  

I've never had this issue, so I would probably not say that the problem "persists in this distribution" or with multiple drives.

Could you tell us about your machine and the version of Ubuntu you are running?

Cheers.

---

### Post by oldfred on 2014-05-02
Also post fstab:

cat /etc/fstab

Unless you have drive issues it should only run fsck every 40 or 60 reboots and that is a settable parameter.

man fsck

> The  root
              filesystem  should be specified with a fs_passno of 1, and other
              filesystems should have a fs_passno of 2. 

But fsck only works on ext2, ext3, ext4 family of formats. Other checks may be used on other formats but you cannot run chkdsk on NTFS partition so 0 would be correct for those.

---

### Post by RGMoonen on 2014-05-03
robert@robert-p4p800e ~ $ cat /etc/lsb-release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=9
DISTRIB_CODENAME=isadora
DISTRIB_DESCRIPTION="Linux Mint 9 Isadora"

Yes I know it is Mint, but it is built using a Ubuntu base 'lucid lynx' 10.04

robert@robert-p4p800e ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0466d63c-d89b-4063-aca2-a9aa4159acb5 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=ebfd4d50-90ba-4152-b801-9a4756b020bd /home           ext3    defaults,user_xattr        0       2
# swap was on /dev/sdb1 during installation
UUID=43238ab6-b24e-4c4f-9248-fca1416beb01 none            swap    sw              0       0
# Video recording disk /dev/sdc1
UUID=fedcd34c-00e0-4dce-8a57-c454306297ae /home/mythtv    ext3    defaults,user_xattr        0       2

I have set the 'mount count' values to stop them all being checked at once with tune2fs -C /dev/sd?? et al.

The one machine I have that is sort of up to date, 12.04 has only one drive installed, so I haven't noticed this behaviour on it.
But on an older machine that I had previously with about 8.04 on it and multiple drives, I had the same problem. So I was really wondering what the current state of affairs is.

cheers

Robert

---

### Post by oldfred on 2014-05-03
Moved to Other OS since Mint. Not sure of differences.
The desktop version of 10.04 is not supported. Server version until April 2015. So Is Mint supporting desktop?

A lot of improvements to system since 10.04 and ext4 is now a much better format.
Does Disk Utility show drive is ok. It can run tests, but all I know is passed is good.

---

