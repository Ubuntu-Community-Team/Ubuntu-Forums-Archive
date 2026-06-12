---
title: "I keep loosing Grub"
date: 2011-05-14
forum: Apple Hardware Users
---

### Post by c@ssie on 2011-05-14
I was running ubuntu and MacOSX as a dual boiot for a while with no problems, a few days ago I added Debian, and since then every time I boot into debian I loose grub the next time I boot, And have to reinstall grub from a livecd.
My setup:
```
   sda1: VFAT EFI                    209.7 MB  
   sda2: HFS+ Mac OS X                89.1 GB   
   sda3: HFS+ Data                   880.7 GB  
   sda4: EXT4 Ubuntu                  15.1 GB   
   sda5: EXT4 Debian                  13.9 GB   
   sda6: Swap                          1.2 GB    

```

From Mac OS X,I have installed rEFIt

Ffrom the live CD I did:
```
$ su -
# apt-get install gptsync
# mkdir /media/ubuntu
# mkdir /media/debian
# mount -t ext4 /dev/sda4  /media/ubuntu
# mount -t ext4 /dev/sda5  /media/debian
# gptsync /dev/sda
# grub-install --boot-directory=/media/debian/boot /dev/sda5
# grub-install --boot-directory=/media/ubuntu/boot /dev/sda4

```

When I reboot and select Linux from the rEFIT menu I get a grub menu, but if I select Debian, the next time I boot, when I select Linux from the rEFIt menu I just get "missing operating system" and not the grub menu.  I then have to repeat the above steps.   If I boot into Ubuntu, this doesn't happen, only when I boot into Debian

---

### Post by JohnAtilano on 2011-05-16
I am no expert but don't you have to run

```
sudo update-grub
```

After you do all of this?

---

### Post by pindar on 2011-05-16
> **c@ssie said:**
> I was running ubuntu and MacOSX as a dual boiot for a while with no problems, a few days ago I added Debian, and since then every time I boot into debian I loose grub the next time I boot, And have to reinstall grub from a livecd.
My setup:
```
   sda1: VFAT EFI                    209.7 MB  
   sda2: HFS+ Mac OS X                89.1 GB   
   sda3: HFS+ Data                   880.7 GB  
   sda4: EXT4 Ubuntu                  15.1 GB   
   sda5: EXT4 Debian                  13.9 GB   
   sda6: Swap                          1.2 GB    

```

From Mac OS X,I have installed rEFIt

Ffrom the live CD I did:
```
$ su -
# apt-get install gptsync
# mkdir /media/ubuntu
# mkdir /media/debian
# mount -t ext4 /dev/sda4  /media/ubuntu
# mount -t ext4 /dev/sda5  /media/debian
# gptsync /dev/sda
# grub-install --boot-directory=/media/debian/boot /dev/sda5
# grub-install --boot-directory=/media/ubuntu/boot /dev/sda4

```

When I reboot and select Linux from the rEFIT menu I get a grub menu, but if I select Debian, the next time I boot, when I select Linux from the rEFIt menu I just get "missing operating system" and not the grub menu.  I then have to repeat the above steps.   If I boot into Ubuntu, this doesn't happen, only when I boot into Debian

I'm not 100 % certain, but I think your problem might be the setup of your hard disk: to double-boot linux and OS X on intel architecture, you need a hybrid GPT partitioning scheme. This, however, is unable to address more than 4 partitions. So everything after your ubuntu partition will effectively be invisible for grub. But please don't take my word for it, just google hybrid gpt mbr, you'll find tons of information.

pindar

---

### Post by srs5694 on 2011-05-16
> **pindar said:**
> I'm not 100 % certain, but I think your problem might be the setup of your hard disk: to double-boot linux and OS X on intel architecture, you need a hybrid GPT partitioning scheme. This, however, is unable to address more than 4 partitions. So everything after your ubuntu partition will effectively be invisible for grub. But please don't take my word for it, just google hybrid gpt mbr, you'll find tons of information.

No, this is incorrect. See [this page,](http://www.rodsbooks.com/ubuntu-efi/index.html) for example. Linux is able to boot on an Intel-based Mac using GPT only (without an ugly hybrid MBR). If a hybrid MBR *is* present, Linux uses the GPT side rather than the MBR side. Furthermore (but not really relevant for this discussion), the limit on real partitions on the MBR side of a hybrid disk is *three*, not four. The fourth partition (normally the first in the list) is reserved for the protective EFI partition, which can't be used to store user data; its purpose is to identify the disk as a GPT disk and, on legal GPT disks (vs. hybrid disks, which violate the spec) to keep GPT-unaware utilities from messing with the disk.

That said, c@ssie clearly has a hybrid MBR. This fact almost certainly does not cause the problem. Before proceeding, it's probably best to get more information by running the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) which will more clearly identify the partitions and boot loader configurations. Unfortunately, Boot Info Script will omit some of the EFI/Mac-specific information that may be relevant, such as the rEFIt configuration; but at least it's a start. My suspicion is that the problem is at least related to the fact that you're merging two different GRUB configurations, for Ubuntu and for Debian. It would probably be better to keep and maintain these separately, and use rEFIt to choose between them; or perhaps to install GRUB 2 for EFI in the EFI System Partition (your /dev/sda1) and use EFI-mode booting. (That will enable you to do away with your hybrid MBR.)

---

### Post by c@ssie on 2011-05-17
ok I think I came upon a solution that seems to be working, though I will have to give it more time to know for sure.   I uninstalled grub from both partitions.  Then from  ubuntu,  I installed grub into the MBR (yes I do have a hybrid partition table) with the root being in my ubuntu partition.  I left grub uninstalled in debian.  Now I do update-grub in ubuntu, after debian updates the kernel.

---

