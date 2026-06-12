---
title: "Triple boot problem Ubuntu 10.04, Windows 7, Snow Leopard"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by Divine_Evil on 2010-04-30
Ok guy I'm having trouble starting up Ubuntu 10.04 on a Macbook Pro 13" mid 2009. My setup is as follow:
2 Hard Drives:

160 GB in the original HDD slot:
80 GB Mac OS (HFS+)
80 GB Windows 7 (NTFS)

500 GB via Sata caddy in the Superdrive's place:
60 GB Documents (HFS+)
25 GB Ubuntu (Ext3)
25 GB Ubuntu Home Directory (Ext3)
8 GB Swap space
Rest for other Data (HFS+)

Before I installed Ubuntu those Ubuntu partitions were one partition that I didn't use at all so I wanted to try Ubuntu again. Now that I have plenty of space for 3 OSes. One more thing I use rEFIt 0.14 as a boot menu. So far it has worked great with Mac OS and Windows dual booting.

Anyway I installed Ubuntu with the Advance setup in the Gparted tool... Created the Swap partition, The Ubuntu Partition with mount point "/", the home directory partition with mountpoint "/home". I didn't see any options to config grub... so after the install grub messed up my Windows MBR. I fixed it by booting windows bootrec.exe /fixmbr etc... Now I can boot Mac OS and Windows correctly. I have a Linux option, but when I choose it, Windows starts up :(. Any suggestions on how to fix it? How can I (re)install grub on the Ubuntu partition so that when I boot in rEFIt all 3 OS to start and no other boot menus to show up. Thank in advance.

---

### Post by Divine_Evil on 2010-05-01
Any suggestions guys? I read somewhere that it might be a SATA bus driver bug... but nobody has info on how to solve it.
I boot the live CD from the "now portable" Superdrive via USB and I'm able to see all the drives NFS, HFS+, Ext3, ext4 whatever... But how do I repair it? What should I edit in the grub config files...

---

### Post by vasi on 2010-05-01
rEFIt doesn't really support booting from a second internal disk, see: [http://refit.sourceforge.net/help/multiple_disks.html](http://refit.sourceforge.net/help/multiple_disks.html) . You might want to contact the author of refit and offer your help.

Two potential workarounds I can think of:

* Hold Option while booting to get Apple's boot selection screen, and choose your secondary drive, or

* Create a small partition on your primary disk to hold grub.

---

### Post by Divine_Evil on 2010-05-01
10x for the info. It worked I'm now typing this from my Ubuntu :D.

Btw any info on how to remove grub from the secondary HDD to the primary HDD?
I know how to shrink a partition after that what should I do?
I have a 100 MB allocated space that is between Mac OS and the Windows Partition which Windows created as a safety blabla... Can I use that one or I might mess my Windows installation?

---

### Post by gnudung on 2010-05-30
> **vasi said:**
> 
Two potential workarounds I can think of:

* Hold Option while booting to get Apple's boot selection screen, and choose your secondary drive, or

* Create a small partition on your primary disk to hold grub.

I'm a beginner, so teach me manners if I need that. This is the only post I could find that is about the exact thing I want to do. I have essentially identical hardware, but my MacBook Pro 13inch unibody is from last month. It has Mac OS 10.6.3 & Windows 7 32bit on Bootcamp (with no extra little partitions, because I was less clever last month). 

The second drive is GUID partition table, with a single HFS+j volume, with no OS on it. I will figure out how to make the Ubuntu partitions (three) be on it, and install Ubuntu, at least that is my goal. (This is not a request for help with that-- I have the Beginner's Guide, I can read, and I do read).

But, when I get to this point - the boot struggle, I"d like to know:

Divine_Evil, 

How did you do it? Where *did* GRUB end up? Are you using rEFIt, or booting holding down the option key?

Thanks.

---

### Post by Ryupower on 2010-05-30
Why not just install Wubi on your Windows partition? Seems a lot less stressful.

---

### Post by gnudung on 2010-05-30
For many, WUBI, which if I understand it correctly, is a form of virtualization, would be good.

I barely know how to find my way around Windows 7, and I don't want to increase the complexity of that side in any way. So, I want to do what Divine_Evil has done, and to learn how his/her problem was overcome.

Ha ha, besides, as I just found out, I'll have a while to think all this over since my chipset is not supported yet. 

[https://bugs.launchpad.net/linux/+bug/576601](https://bugs.launchpad.net/linux/+bug/576601)

So, Divine_Evil, please disclose the secret in the next month or two.

---

