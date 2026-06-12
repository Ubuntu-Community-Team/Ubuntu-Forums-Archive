---
title: "Edgy Boot Time Issue"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-11-02
From what I've read Edgy should have shorter boot times than Dapper...
But that doesn't works for me:
For a simple boot I sometimes need up to 3 minutes.

Basically, I get the message "Starting up" (when I switch from the graphical bootloader to the non-graph) for 2.5 minutes, then I get this:

> [1717968281600]ali15x3-smbus 0000:00:15.1: ALI15x3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[1717968281600]ali15x3 not detected, module not inserted 

And then, following very fast:
> *Activating swap...
*Checking root file system...
fsck 1.39(29-may-2006)
/dev/sda5: clean 149206/5144576 files, 1119039/10283600 blocks
*Checking filesystems
fsck 1.39 (29-may-2006)
####And then all my other partitions marked as clean and how many files/blocks####

So now I wonder:
*Is there anything I can do to make it start up faster (like the force_addr=0xaddr mentioned )
*Is it the bios who makes this long or is it the checking of my disks (which didn't seem to take long, just flashed a sec, didn't seemed to be a full check to me)

---

### Post by Ecthelion on 2006-11-02
Maybe I should mention that I have installed Edgy 32bit on my computer, which has an AMD64 processor.
I've heard that this shouldn't cause any trouble, and I was hoping to avoid the flash etc problems that I had with dapper 64bit

Could it be that this causes the delay?

---

### Post by dannyboy79 on 2006-11-03
> **Ecthelion said:**
> From what I've read Edgy should have shorter boot times than Dapper...
But that doesn't works for me:
For a simple boot I sometimes need up to 3 minutes.

Basically, I get the message "Starting up" (when I switch from the graphical bootloader to the non-graph) for 2.5 minutes, then I get this:

 

And then, following very fast:


So now I wonder:
*Is there anything I can do to make it start up faster (like the force_addr=0xaddr mentioned )
*Is it the bios who makes this long or is it the checking of my disks (which didn't seem to take long, just flashed a sec, didn't seemed to be a full check to me)

I can' tell you anything about the force_addr=0xaddr thing but I can tell you about why it takes 2 or 3 mins to boot possibly. if you have a fat32 partition, ubuntu probably added a 1 at the end it's fstab entry which means to perform the fsck upon every boot. Check out this thread for all the info you can digest regarding fsck running at boot etc etc. [http://ubuntuforums.org/showthread.php?t=104890&highlight=change+fsck+frequency](http://ubuntuforums.org/showthread.php?t=104890&highlight=change+fsck+frequency)

---

### Post by Ecthelion on 2006-11-03
> I can' tell you anything about the force_addr=0xaddr thing but I can tell you about why it takes 2 or 3 mins to boot possibly. if you have a fat32 partition, ubuntu probably added a 1 at the end it's fstab entry which means to perform the fsck upon every boot. Check out this thread for all the info you can digest regarding fsck running at boot etc etc.

I found a thread where this was suggested, but it didn't seemed to make any difference...
I even commented out the line with the fat32 and the line with NTFS in /etc/fstab
but the boot time didn't changed...:-k

---

### Post by Tamil on 2006-11-03
See [http://www.ubuntuforums.org/showpost.php?p=1707220&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1707220&postcount=8)

---

### Post by Ecthelion on 2006-11-03
> See [http://www.ubuntuforums.org/showpost...20&postcount=8](http://www.ubuntuforums.org/showpost...20&postcount=8)

Ya I know... that's what they say in dannyboy79's link too...

But that's really not the problem here...
I've booted again after uncommenting the vfat & NTFS and changing the 1 to 0...

But the boot time is still the same...

The problem is more

> Basically, I get the message "Starting up" (when I switch from the graphical bootloader to the non-graph) for 2.5 minutes, then I get this:

[QUOTE]
[1717968281600]ali15x3-smbus 0000:00:15.1: ALI15x3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[1717968281600]ali15x3 not detected, module not inserted 
[/QUOTE]

What I would want to know is:
Is there any way to let Ubuntu start up whitout paying attention to the "ALI5x3", something like forcing...
OR
Is there a way to Initialize that "ALI5x3" so that there isn't any problem anymore...

Of course I prefer option 2,...
                ...but I prefer short boot times the most...

Any help or comments are welcome!

---

### Post by macnerd on 2006-11-03
I'm having the same delay at startup, right after the kernel loads.  I changed the fstab entry to 0 and it still takes about 4 minutes for my system to start booting normally.

---

### Post by dannyboy79 on 2006-11-03
have you guys tried upgrading your bios? or maybe disabling apci or acpi in your bios?

---

### Post by Ecthelion on 2006-11-03
> have you guys tried upgrading your bios? or maybe disabling apci or acpi in your bios?

Nope...
... Sounds dangerous...

How should I do that?

---

### Post by Cynical on 2006-11-03
Its only dangerous if your computer loses power during the upgrade. It takes about a minute and its not very difficult. If you'd like to try it let us know your motherboard model so we can find the utility for you.

---

### Post by Ecthelion on 2006-11-03
My motherboard model is:

Asrock 939SLI32-eSATA2 S939 ULi M1695 FSB 1000MHz PCIe ATX 

I must say I would be rather surprised if I could update it...
...it's not very outdate yet (or that's what I would think...)

But then again, half a year is maybe older than I would first think...

> or maybe disabling apci or acpi in your bios?

What about that?
I just wouldn't take any risk if it's possible otherwise...

Although I would give that upgrading a try if it's the only solution...

---

### Post by pbaehr on 2006-11-03
> **Ecthelion said:**
> My motherboard model is:

Asrock 939SLI32-eSATA2 S939 ULi M1695 FSB 1000MHz PCIe ATX 

I must say I would be rather surprised if I could update it...
...it's not very outdate yet (or that's what I would think...)

But then again, half a year is maybe older than I would first think...


A lot of motherboards can actually be out of date by the time they leave the box if the manufacturer has made changes to the firmware since it was manufactured.

> 
What about that?
I just wouldn't take any risk if it's possible otherwise...

Although I would give that upgrading a try if it's the only solution...

Upgrading your BIOS is not really that risky. Just don't unplug your computer half way through. The utilities that update the BIOS now a days are pretty friendly, though. You shouldn't have much trouble. At worst it will be a matter of booting to a disk and letting an automated program do it's thing. At best, you can run a program without even restarting the computer.

EDIT:

Here is the page where you'll find the BIOS updates for your computer.
[http://www.asrock.com/support/download.asp?Model=939Dual-SATA2](http://www.asrock.com/support/download.asp?Model=939Dual-SATA2)

MAKE SURE I GOT THIS RIGHT. IF YOU DOWNLOAD THE UPDATE FOR THE WRONG BOARD BECAUSE I SCREWED UP THINGS COULD GO UGLY ON YOU. DON'T DO IT BLIND BASED ON MY LINK. DOUBLE CHECK MY WORK.

Anyway, now that my disclaimer is out of the way, it looks like they only have support for Windows and DOS updates. It may be that the DOS version is a bootable disc, but maybe if you're "lucky" you have a dual boot.

Again, DOUBLE CHECK MY CHOICE FOR YOUR MB. Other than that, good luck, and let us know if the update fixes the problem.

---

### Post by Ecthelion on 2006-11-04
> EDIT:

Here is the page where you'll find the BIOS updates for your computer.
[http://www.asrock.com/support/downlo...=939Dual-SATA2](http://www.asrock.com/support/downlo...=939Dual-SATA2)

MAKE SURE I GOT THIS RIGHT. IF YOU DOWNLOAD THE UPDATE FOR THE WRONG BOARD BECAUSE I SCREWED UP THINGS COULD GO UGLY ON YOU. DON'T DO IT BLIND BASED ON MY LINK. DOUBLE CHECK MY WORK.




Good that I did check...
Your link is to 939Dual-sata 2

My motherboard is 939SLI32-eSATA2 

> Anyway, now that my disclaimer is out of the way, it looks like they only have support for Windows and DOS updates. It may be that the DOS version is a bootable disc, but maybe if you're "lucky" you have a dual boot.

Again, DOUBLE CHECK MY CHOICE FOR YOUR MB. Other than that, good luck, and let us know if the update fixes the problem.


How do I have to upgrade it now?
I don't have a floppy disk...
Is just making a bootable cd of it also good?

Yes I have a dual boot so does that mean I can use the dos version?


Thanks a lot for your aid this far!

---

### Post by Ecthelion on 2006-11-06
... Still no answer...


In meanwhile, does anyone know if this should be reported as bug?
The reason why I think this should be reported is because you can't expect an average user to have the latest bios updates when he want's to install edgy...

Reason while I would not report it is because I seem to be the only one who has this problem...
If it's so isolated then it wouldn't be worth it to have a developer using his time on it...

Any advice is welcome

---

### Post by dannyboy79 on 2006-11-06
> **Ecthelion said:**
> Good that I did check...
Your link is to 939Dual-sata 2

My motherboard is 939SLI32-eSATA2 




How do I have to upgrade it now?
I don't have a floppy disk...
Is just making a bootable cd of it also good?

Yes I have a dual boot so does that mean I can use the dos version?


Thanks a lot for your aid this far!

Once you have downloaded the latest bios file (maybe you'd want to use the latest stable version, not the latest beta) then you should gogle something like, how do i flash my bios. actually I am surprised asus doesn't have a tool on there website under support. look there first, better to use the tools they provide to be on the safe side. i know I have an older Asus P4P800 or something like that and I downloaded the flashing tool from there website. You can use a cd I believe, if you make it bootable, it won't matter what operating system since you are booting to the floppy or cd. prior to performing the actual flash make sure that the outlet you're using isn't overloaded with stuff so that you can be sure it doesn't pop a breaker and then you're screwed, don't do it during a lighting storm and once you hit ok, or perform the command, don't touch the computer, don't let your pets near the power button or anything, you need to make sure the flash completes it's thing, then you'll restart your computer and you should have the latest bios. i would always save you're old bios first, and also, note what bios that is by entering your bios and looking for the version of your bios prior to flashing it that way, if the new flash doens't work, you can always revert back to the original one whether because you saved it before you flashed or because you noted what version it was and then you could download it from asus's website. Good luck

---

### Post by Ecthelion on 2006-11-06
> Once you have downloaded the latest bios file (maybe you'd want to use the latest stable version, not the latest beta) then you should gogle something like, how do i flash my bios. actually I am surprised asus doesn't have a tool on there website under support. look there first, better to use the tools they provide to be on the safe side. i know I have an older Asus P4P800 or something like that and I downloaded the flashing tool from there website. You can use a cd I believe, if you make it bootable, it won't matter what operating system since you are booting to the floppy or cd. prior to performing the actual flash make sure that the outlet you're using isn't overloaded with stuff so that you can be sure it doesn't pop a breaker and then you're screwed, don't do it during a lighting storm and once you hit ok, or perform the command, don't touch the computer, don't let your pets near the power button or anything, you need to make sure the flash completes it's thing, then you'll restart your computer and you should have the latest bios. i would always save you're old bios first, and also, note what bios that is by entering your bios and looking for the version of your bios prior to flashing it that way, if the new flash doens't work, you can always revert back to the original one whether because you saved it before you flashed or because you noted what version it was and then you could download it from asus's website. Good luck
1 Hour Ago 01:34 PM

Tx for the help...

I succesfully upgradet my bios to the latest version (1.40)

BUT...

that didn't solved the problem...

[QUOTE=Ecthelion][1717968281600]ali15x3-smbus 0000:00:15.1: ALI15x3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[1717968281600]ali15x3 not detected, module not inserted[/QUOTE]

The problem is still there and the boot times are still soo long...

Anyone who has any other idea?

Ps. dannyboy79, again tx for your help so far
Tx also to all other folks who helped me this far

---

### Post by Ecthelion on 2006-11-09
> or maybe disabling apci or acpi in your bios?

Does anyone know how to do it?

Also, I've found some more things about the "force_addr=0xaddr":
Only [it seems]("http://www.mjmwired.net/kernel/Documentation/hwmon/sis5595") that it has to be changed in the kernel.

Does this mean that I should recompile my kernel after inserting it?

I have no idea how I should do that...

---

### Post by Ecthelion on 2006-11-09
Two other solutions to my problem... (If I only knew how to do what they mention so easily...)

[http://archives.andrew.net.au/lm-sensors/msg29331.html]("http://archives.andrew.net.au/lm-sensors/msg29331.html")

[QUOTE=http://archives.andrew.net.au/lm-sensors/msg29331.html]Why don't you pick the exact same address in 2.4 that was automatically
detected in 2.6? I'd assume this would be the safest choice. Or, like
Mark said, just any free address (i.e. from a range not listed as used
in /proc/ioport) should do.
[/QUOTE]

I don't really understand... Which address should I modify?
How? The only way to display the /proc/ioport is using cat...
Doesn't go with gedit etc...
I don't know how to modify files with cat

I'm feeling I'm getting closer to the solution...
Plz help me on the last steps!


Anyone who knows how to do this...

---

### Post by Ecthelion on 2006-11-10
I don't know I this could help, but I'm still trying and I will do so till I get a decent boot time [-(  :twisted: 

I've been searching my system to find that ali15x3 thing:

> ecthelion@ElvenLounge:~$ locate ali15x3
/lib/modules/2.6.17-10-generic/kernel/drivers/i2c/busses/i2c-ali15x3.ko
/usr/src/linux-headers-2.6.17-10/include/config/blk/dev/ali15x3.h
/usr/src/linux-headers-2.6.17-10/include/config/i2c/ali15x3.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/blk/dev/ali15x3
/usr/src/linux-headers-2.6.17-10-generic/include/config/blk/dev/ali15x3/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/blk/dev/ali15x3/module.h~
/usr/src/linux-headers-2.6.17-10-generic/include/config/i2c/ali15x3
/usr/src/linux-headers-2.6.17-10-generic/include/config/i2c/ali15x3/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/i2c/ali15x3/module.h~
/usr/src/linux-headers-2.6.17-10-generic/include/config/wdc/ali15x3.h
/usr/src/linux-headers-2.6.17-10-386/include/config/blk/dev/ali15x3
/usr/src/linux-headers-2.6.17-10-386/include/config/blk/dev/ali15x3/module.h
/usr/src/linux-headers-2.6.17-10-386/include/config/wdc/ali15x3.h
/usr/src/linux-headers-2.6.17-10-386/include/config/i2c/ali15x3
/usr/src/linux-headers-2.6.17-10-386/include/config/i2c/ali15x3/module.h


Thats what I found..

I tried to read the first on the list

> ecthelion@ElvenLounge:~$ cat /lib/modules/2.6.17-10-generic/kernel/drivers/i2c/busses/i2c-ali15x3.ko 

#####################################################################
 I deleted what was written here since it where all unreadable signs
#####################################################################

             &#65533;m&#65533;SMBus ALI15X3 adapter at %04x<3>%s %s: SMBus Timeout!
ali15x3_smbus<3>%s %s: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
<3>%s %s: ALI15X3_smb region 0x%x already in use!
<6>%s %s: forcing ISA address 0x%04X
<3>%s %s: force address failed - not supported?
<6>%s %s: enabling SMBus device
<6>%s %s: enabling SMBus controller
<3>%s %s: ALI15X3 not detected, module not inserted.
<3>%s %s: Idle wait Timeout! STS=0x%02x
<3>%s %s: I2C_SMBUS_PROC_CALL not supported!
<6>%s %s: Resetting entire SMB Bus to clear busy condition (%02x)
<3>%s %s: SMBus reset failed! (0x%02x) - controller or device on bus is probably hung
<3>%s %s: Error: device error
&#65533;parmtype=force_addr:ushortparm=force_addr:Initialize the base address of the i2c controllerauthor=Frodo Looijaard <frodol@dds.nl>, Philip Edelbrock <phil@netroedge.com>, and Mark D. Studebaker <mdsxyz123@yahoo.com>description=ALI15X3 SMBus driverlicense=GPLvermagic=2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1depends=i2c-corealias=pci:v000010B9d00007101sv*sd*bc*sc*i*srcversion=5B987BC7A0FAE9A7289F816t&#65533;C&#65533;struct_module*&#65533;Tparam_get_ushort&#65533;P&#65533;&#65533;param_set_ushort&#65533;&#65533;&#65533;&#65533;msleep&#65533;J&#65533;P__pci_register_driver&#65533;n&#259;i2c_add_adapterp&#65533;]snprintf&#65533;NTZpci_bus_write_config_byte&#65533;1&#65533;pci_bus_write_config_word        O__request_regiont@}printk"&#65533;&#65533;pci_bus_read_config_word
                 b&#65533;&#65533;pci_bus_read_config_byte&#65533;&#65533;&#65533;__release_region&#892;^&#65533;ioport_resourceei2c_del_adaptere&#65533;  pci_unregister_driver

#####################################################################
 I deleted what was written here since it where all unreadable signs
#####################################################################

i2c-ali15x3.cali15x3_funci2c_ali15x3_exitali15x3_driverali15x3_removeali15x3_adapterali15x3_smbaali15x3_probeforce_addri2c_ali15x3_initali15x3_access__param_force_addr__param_str_force_addr__mod_force_addrtype129__mod_force_addr131__mod_author525__mod_description526__mod_license527ali15x3_idssmbus_algorithmi2c-ali15x3.mod.c__mod_vermagic5____versions__module_depends__mod_alias43__mod_srcversion45param_set_ushort__this_modulesnprintf__pci_register_drivercleanup_modulepci_bus_write_config_bytepci_unregister_driver__release_regioninit_modulepci_bus_read_config_wordparam_get_ushorti2c_del_adapter__mod_pci_device_tableprintkioport_resourcei2c_add_adapterpci_bus_write_config_wordmsleeppci_bus_rea

This file looks unchangeable to me since the only reader I could find that can read it is cat...

Most of those .h files only have 1 line like that of

> ecthelion@ElvenLounge:~$ cat /usr/src/linux-headers-2.6.17-10/include/config/i2c/ali15x3.h
#undef CONFIG_I2C_ALI15X3


Anyone else who could help?
I'll keep trying but if anyone has a comment, suggestion, link, anything really, I would greatly appreciate it

---

### Post by Swatje on 2006-11-11
It doesn't seems to be an essential module (Linux kernel modules for hardware monitoring) so maybe you can blacklist the module. Say to the system not to load this module.

You can do it with the following command:

```

sudo echo "blacklist i2c-ali15x3" >> /etc/modprobe.d/blacklist
```

This command adds a line to the blacklist file.

---

### Post by Ecthelion on 2006-11-12
Well done...
Using your trick maybe didn't solved my problem, but still it made it go away.
So that's good.

But still... it doesn't make a faster boot...
But we are making progress and I feel that this time I've got the right error.

I found out that somehow my pc had problems mounting my sata disk...
Since Linux is on the Sata disk, that would explain the delay in the whole startup...
When looking in my system logs I found this:

> Nov 12 18:59:08 ElvenLounge kernel: [17179580.280000] ahci 0000:00:16.1: flags: ncq ilck pm led clo pmp pio slum part 
Nov 12 18:59:08 ElvenLounge kernel: [17179580.280000] ata1: SATA max UDMA/133 cmd 0xF882E900 ctl 0x0 bmdma 0x0 irq 66
Nov 12 18:59:08 ElvenLounge kernel: [17179580.280000] ata2: SATA max UDMA/133 cmd 0xF882E980 ctl 0x0 bmdma 0x0 irq 66
Nov 12 18:59:08 ElvenLounge kernel: [17179580.280000] ata3: SATA max UDMA/133 cmd 0xF882EA00 ctl 0x0 bmdma 0x0 irq 66
Nov 12 18:59:08 ElvenLounge kernel: [17179580.280000] ata4: SATA max UDMA/133 cmd 0xF882EA80 ctl 0x0 bmdma 0x0 irq 66
Nov 12 18:59:08 ElvenLounge kernel: [17179581.200000] ata1: SATA link down (SStatus 0)
Nov 12 18:59:08 ElvenLounge kernel: [17179611.220000] ata1: qc timeout (cmd 0xec)
Nov 12 18:59:08 ElvenLounge kernel: [17179611.220000] ata1: dev 0 failed to IDENTIFY (I/O error)
Nov 12 18:59:08 ElvenLounge kernel: [17179611.220000] scsi0 : ahci
Nov 12 18:59:08 ElvenLounge kernel: [17179612.140000] ata2: SATA link down (SStatus 0)
Nov 12 18:59:08 ElvenLounge kernel: [17179642.160000] ata2: qc timeout (cmd 0xec)
Nov 12 18:59:08 ElvenLounge kernel: [17179642.160000] ata2: dev 0 failed to IDENTIFY (I/O error)
Nov 12 18:59:08 ElvenLounge kernel: [17179642.160000] scsi1 : ahci
Nov 12 18:59:08 ElvenLounge kernel: [17179643.080000] ata3: SATA link down (SStatus 0)
Nov 12 18:59:08 ElvenLounge kernel: [17179673.096000] ata3: qc timeout (cmd 0xec)
Nov 12 18:59:08 ElvenLounge kernel: [17179673.096000] ata3: dev 0 failed to IDENTIFY (I/O error)
Nov 12 18:59:08 ElvenLounge kernel: [17179673.096000] scsi2 : ahci
Nov 12 18:59:08 ElvenLounge kernel: [17179673.472000] ata4: SATA link up 3.0 Gbps (SStatus 123)
Nov 12 18:59:08 ElvenLounge kernel: [17179673.472000] ata4: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:3c01 87:4023 88:407f
Nov 12 18:59:08 ElvenLounge kernel: [17179673.472000] ata4: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
Nov 12 18:59:08 ElvenLounge kernel: [17179673.472000] ata4: dev 0 configured for UDMA/133

It are those timeout that make the whole thing take so long.
So that would be the real problem after all. But for this I don't have a lot of hope making it a lot faster...

Someone of you guys know anything?

---

### Post by Ecthelion on 2006-12-20
Nevermind, there has been a kernel update and since then the problem is gone.

Good work developers!

---

