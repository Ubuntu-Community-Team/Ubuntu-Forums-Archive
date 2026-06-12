---
title: "G5 Dual boot problem with OS X on separate hard drive"
date: 2016-12-01
forum: Apple Hardware Users
---

### Post by danfcavs on 2016-12-01
I have a G5 powerpc with 2 hard drives, so I installed Lubuntu 14.04 on one (/dev/sda), and OS X Leopard on the other (/dev/sdb). I've recently updated to Lubuntu 16.04 and everything seemed ok. However I can't boot into macosx from yaboot, I'm assuming there must be a problem with my yaboot.conf file. to compound things I can no longer boot into OS X when holding down the option key, the system just goes to the grey screen with the apple logo in the middle then crashes. this was working previously so I'm unsure what has happened. This is my yaboot.conf file. 

```

boot="/dev/disk/by-id/ata-ST1000DM003-9YN162_Z1D1KB0Z-part2"
device=/ht@0,f2000000/pci@7/k2-sata-root@c/@ffffffffffffffff/@0
partition=3
root="UUID=c997367a-41f0-41da-96ba-957488f725ba"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx="/dev/disk/by-id/ata-Maxtor_6Y120M0_Y4D5PMEE-part3"
## macosx="/dev/sdb3"

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda5.
image=/ht@0,f2000000/pci@7/k2-sata-root@c/@ffffffffffffffff/@0:5,/boot/kernel-4.1.15-gentoo-r1
    label=Gentoo-Linux
    root="UUID=316d5016-e78c-4f1a-ba95-ebdb026d9471"
    append=" ro"

```

any help appreciated.

---

### Post by ernsteiswuerfel on 2016-12-03
So you have Ubuntu and Gentoo on /dev/sda and /dev/sdb is all OS X? Best to check out your partitions first with **sudo blkid **via terminal. Afterwards have a look at your yaboot.conf if the /dev/sdXY paths are correct.

I had some funny issues with that OpenFirmware paths like *macosx="/dev/disk/by-id/ata-Maxtor_6Y120M0_Y4D5PMEE-part3"*. Better use the /dev/sdXY notation.

Also don't forget to write out your yaboot.conf to disk via **sudo ****ybin -v.** ybin has additional parameters to specify the boot-partition directly, etc.

---

### Post by danfcavs on 2016-12-05
Hi ernsteiswuerfel thanks for your reply 

> [COLOR=#000000]So you have Ubuntu and Gentoo on /dev/sda and /dev/sdb is all OS X? [/COLOR]

Yes this is correct but the Gentoo install is faulty, either I have stuffed something up during install (which is likely since I've never done it before), or yaboot.conf which was generated automatically by the Lubuntu install is not configured right for the Gentoo partition. 

Happily after multiple attempts I was able to boot into OS X by holding the alt/opt key, and after performing a software update (it was a fresh install of OS X Leopard) it seems more robust/reliable now. booting into OS X from yaboot however still doesn't work.

the sudo blkid command gives the following output: 

```
sudo blkid

/dev/sda2: LABEL="bootstrap" TYPE="hfs" PARTLABEL="bootstrap"
/dev/sda3: UUID="c997367a-41f0-41da-96ba-957488f725ba" TYPE="ext4" PARTLABEL="ubRoot"
/dev/sda4: UUID="74b30fd2-e8b4-427b-8516-2fa29715f8f9" TYPE="swap" PARTLABEL="swap"
/dev/sda5: UUID="316d5016-e78c-4f1a-ba95-ebdb026d9471" TYPE="ext4" PARTLABEL="root"
/dev/sdb3: UUID="8166dd4d-7442-394c-925e-f5bc3cff4959" LABEL="leopard-backup" TYPE="hfsplus" PARTLABEL="Untitled"
/dev/sda1: PARTLABEL="Apple"
/dev/sda6: PARTLABEL="Extra"
/dev/sda7: PARTLABEL="Extra"
/dev/sdb1: PARTLABEL="Apple"
```

and those UUIDs match whats in the yaboot.conf file. When I try and boot Gentoo I get "Invalid memory access/Bad Bus info" errors which sounds bad. Then my system crashes. I get the same result whether I specify root by UUID or by /dev/sd5. with the macosx variable, I get the same result whether I use the open firmware path or /dev/sdb3, which is it fails to load then returns me back to the yaboot menu screen. I'm reluctant to experiment with the Lubuntu settings, as it is working and I don't want to break it. 

I executed sudo ybin -v after making changes to yaboot.conf.

---

### Post by ernsteiswuerfel on 2016-12-07
Whats the output of ybin -v? It should give you some info what it is doing.

The error gentoo throws just sounds like a kernel which is not fit to run your system, nothing more. My G5 started to run reliably with kernel 4.7.x, I had problems with older kernels.

If I do understand you correctly yaboot succeeds in booting Linux, but fails in booting OS X? I think I misread your first post, thinking yaboot does not work at all and you didn't even get the yaboot boot prompt.

---

### Post by danfcavs on 2016-12-10
> Whats the output of ybin -v?
holy penguin pee aside it appears to be ok 
```

ybin: Finding OpenFirmware device path to `/dev/sda2'...
ybin: Finding OpenFirmware device path to `/dev/sdb3'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda2...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda2...
ybin: Installing /etc/yaboot.conf onto /dev/sda2...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda2 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...

```
sda2 is my bootstrap partition, sdb3 is my macosx partition. 

the kernel version of my gentoo system is 4.1.15, my working lubuntu 16.04 system is 4.4.0-53-powerpc64-smp.

> yaboot succeeds in booting Linux, but fails in booting OS X?

yes this is correct, when I need to boot into OS X I hold down the alt/opt key during startup. then I get an OS9 style gui that allows me to select either OS X or Linux.

---

### Post by ernsteiswuerfel on 2016-12-12
Hmm ok, according your ybin ouptut everything seems to be ok... I am afraid I am out of guess what you could do next.
> **danfcavs said:**
> the kernel version of my gentoo system is 4.1.15, my working lubuntu 16.04 system is 4.4.0-53-powerpc64-smp.
Never had 4.1.x running on my G5, but 4.8.x serves me very well! You could try my config: [https://forums.gentoo.org/viewtopic-t-1055626.html](https://forums.gentoo.org/viewtopic-t-1055626.html)

---

### Post by danfcavs on 2016-12-16
> You could try my config: [https://forums.gentoo.org/viewtopic-t-1055626.html](https://forums.gentoo.org/viewtopic-t-1055626.html)

Thanks ernsteiswuerfel for this. For the moment I'm going to work with Lubuntu as its functional and I'm trying to get my firewire audio interface up and running. but I take it your .config file is a list of selected options made during manual kernel configuration? I spent many hours pouring over each option, trying to figure out whether I needed it or not. I will definitely use this as a reference next time I try and install gentoo.

---

### Post by ernsteiswuerfel on 2016-12-23
> **danfcavs said:**
> [...] I take it your .config file is a list of selected options made during manual kernel configuration? I spent many hours pouring over each option, trying to figure out whether I needed it or not. I will definitely use this as a reference next time I try and install gentoo.
Yes, I took my time  to refine the config a few times to get the hardware of my G5 7,3 and G5 11,2 running and to set the appropriate options for running systemd. The rest is basic network functionality and a few filesystems I need (btrfs, nfs, CIFS, AFS).

---

