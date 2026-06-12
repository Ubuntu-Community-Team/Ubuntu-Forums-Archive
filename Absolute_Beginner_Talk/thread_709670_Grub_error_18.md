---
title: "Grub error 18"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by imanoob on 2008-02-27
Hello Ubuntu-Linux members,

I have a problem when trying to install Ubuntu 6.10 on my computer... Whenever I boot up it gives me a Grub Error 18. Now being a noob at linux I have no idea what this means. I cannot load into windows xp (I chose the duel boot method) and now I'm stuck with the live cd. If anyone is willing to help me I gladly appreciate it!

By the way these are  my computer specs:
```
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1519MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.2
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage 128 Pro Ultra TF
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=8
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: 00:04:23:15:97:e5
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=69.70.248.123 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```

I got them using the "$sudo lshw" command in terminal. (I'm not a complete noob)

---

### Post by warbird on 2008-02-27
Read this:
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

---

### Post by imanoob on 2008-02-27
I was wondering how to install it (using duel boot method) but partioning the disk in a way that it will start up without an error or at least start up windows xp again... Because I've read somewhere else that on older computers like mine the BIOS might have a hard time supporting GRUB or something like that. But thanks for replaying so fast.

---

### Post by chris.a.barker on 2008-02-27
Do you happen to have a mixture of SATA hard drives and IDE hard drives? If so hold on to your seat it's going to be a fun ride. Post back with the answer to this question please.

---

### Post by imanoob on 2008-02-27
I believe I have two IDE drives, but I'm not entirely sure how to check.

---

### Post by imanoob on 2008-02-27
Please help... (bump)

---

### Post by dstew on 2008-02-27
You will have to create a small (100 Mb) partition at the front of your drive, and install Ubuntu again, designating that partition with the mount point **/boot**. There is no other way to overcome this particular problem.

---

### Post by imanoob on 2008-02-27
Ok, how would I do this? And will my files be deleted...

---

### Post by dstew on 2008-02-27
Boot an Ubuntu Live CD, open a terminal window, enter the command **sudo fdisk -l** and post the result to the forum. Then we can tell you what you will need to do. You will probably need to make a [gparted live CD]("http://gparted-livecd.tuxfamily.org/") to partition the disk, so look into that also. If you don't want to make that gparted disk you can try to install gparted into your Edgy Live CD system using synaptic, but it will disappear when you close the Live CD, and you will have to install it again if you need it again.
EDIT: If you do this properly, your files will not be deleted. You can try to use the partitioner in the installer, but I think it is a little clunky.

---

### Post by imanoob on 2008-02-28
Alright sorry I took so long, these are my results.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebb5ebb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11968    96132928+  83  Linux
/dev/sda2           23270       24321     8450190    5  Extended
/dev/sda3   *       11969       23269    90775282+  83  Linux
/dev/sda5           23755       24321     4554396   82  Linux swap / Solaris
/dev/sda6           23270       23754     3895699+  82  Linux swap / Solaris
```

---

### Post by imanoob on 2008-02-28
Please help! (bump) <-- I hope bumping isn't illegal here...

---

### Post by dstew on 2008-02-28
That fdisk output does not show a Windows partition. The first partition is too big to avoid the grub error 18.

If you don't have any files on your Linux installation that you want to save, the easiest way to do this is to delete all the partitions and create new ones that will allow you to boot. If you have files you want to save, you can try to shrink and move the partitions using gparted from a Live CD boot.

If you decide to delete all the partitions, then create new ones like this:

1. 100 Mb, format ext3, mount point /boot
2. 15 Gb, format ext3, mount point /
3. 1 Gb, swap, no mount point (use as swap)
4. The rest ext3, mount point /home

You can make four primary partitions if you think you will not be needing any more partitions. If you want more flexibility, make the fourth partition an extended partition, and make a logical partition out of that for /home.

Note that the first partiton is 100 **mega**bytes, not 100 **giga**bytes.

---

### Post by imanoob on 2008-02-28
Ok, so how would I go about doing this: I didn't save anything on my live cd and never got ubuntu running in the first place (after installation) so I just want to delete the ubuntu portions and keep the windows xp ones, then I want to reinstall ubuntu avoiding the Grub error 18. Can you please give me a detailed explenation.
Thanks for helping me out, I really apreciate this.

---

### Post by dstew on 2008-02-28
I am afraid that you do not have any Windows partitions left on that disk. Hopefully you had backed up your files before you tried to install Ubuntu the first time. You probably accidentally deleted the Windows partition when you did your partitioning.

If you want a dual boot system, it is always easiest to install Windows first (or re-install in your case). When you install Windows, it will claim the whole disk for itself usually. After Windows is installed, you can install Ubuntu. You will probably have to shrink the XP partition, and create new partitions out of the unallocated space.

For surgery such as this, it is best in my opinion to do the partitioning before you start the installation. If you can make a gparted live CD, that is the best way. Then, when you run the installer, the partitions will already be there. You only have to format them and assign them their mount points.

I think the installer in the Live CD sometimes confuses people, because of the "use whole disk" and other such options. People don't realize that that means the whole disk will be wiped, including Windows. I prefer to partition manually, with gparted. Then you know what is going on at each step.

---

### Post by imanoob on 2008-02-28
Well I chose the first option which is Guided and then asked me how big I wanted the partition to be so I should still have all my old files...

---

### Post by imanoob on 2008-02-28
Bumpaty bump bump! Please answer.

---

### Post by dstew on 2008-02-28
What question do you have? Your Windows partition is gone. If you want to make a dual-boot Windows-Ubuntu system, you will need to re-install Windows and Ubuntu.
Do you have another disk drive that is not plugged in maybe?

---

### Post by imanoob on 2008-02-28
Are my files gone? (The ones I had in windows xp) If I install my drive on another computer will I be able to recover files? I really need them, I had some important documents on there.

---

### Post by dstew on 2008-02-28
> Are my files gone? I am very sorry, but the evidence of the fdisk output shows that you no longer have a WIndows partiton on that drive. I don't know what happened during your attempted Ubuntu installation. If you used Guided it should have saved your files, but if you did Use Entire Disk it may have deleted the WIndows partition.> If I install my drive on another computer will I be able to recover files? I don't think so, but you can certainly try that.

Sometimes, if you delete a partition, you can recover it with certain types of disk rescue software. One that I have heard about is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). However, this only works if you delete a partition, but leave the space on the disk unallocated. From your fdisk output, it looks like all the space on the disk is accounted for by the partitions that are there. If you create a new partition where the WIndows partition used to be, and format it to ext3, then I don't think you can recover the partition.

If the data was very important (doctoral thesis without any backup) you might be able to get professional help to recover some of the data, even if the partition was re-formatted. This is expensive though.

---

### Post by imanoob on 2008-02-28
Well when I tried to access my C;\ drive on the live disk it wouldn't let me, it would just load the content on the disk. So maybe, for some reason... I dunno, all I know is my dad's going to be pissed.

---

### Post by warbird on 2008-02-28
It is easy to say this now, but... Always backup stuff you can't afford to lose, especially when messing around with HD partitions... If there is something critically important there, your best bet is to get professional help recovering the files... Else, try search around for some freeware recovering tools.

---

