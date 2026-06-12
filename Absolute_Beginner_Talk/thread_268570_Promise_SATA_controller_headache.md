---
title: "Promise SATA controller headache"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by xela321 on 2006-09-30
I'm pretty desperate at this point.  I have a Promise TX4310 SATA II controller.  It has partial open source linux drivers.  I tried getting the card to be recognised by just 

```
modprobe sata-promise
```

But, after checking dmesg, it didn't seem to find the card (there was no change to dmesg before and after modprobe sata-promise).

So, I tried to compile the linux drivers from Promise. I followed the README the best I could, symbolically linking the proper directories so 'make' could find everything.  It spit out ftsata2.ko and ftsata2.o.  I cp'd ftsata2.ko to /lib/modules/2.6.15-27-386/kernel/drivers/scsi/.  Then I insmod ftsata2.ko.  That returned a segmentation fault, and when I check dmesg I saw:

```
[17225767.180000] Promise 4310/579/779 Serieal Device Driver 2.6.1.0320 (Feb 07, 2006)
[17225767.180000] Warning: PCI driver fasttrak has a struct device_driver shutdown method, please update!
[17225767.180000] Required extension size: max: 2379296 Min: 1537300
[17225767.180000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 225
[17225767.180000] fasttrak 0000:01:07.0: Found FastTrak Controller with IRQ: 225
[17225767.184000] Unable to handle kernel paging request at virtual address 00003515
[17225767.184000]  printing eip:
[17225767.184000] f8e933ee
[17225767.184000] *pde = 00000000
[17225767.184000] Oops: 0002 [#1]
[17225767.184000] PREEMPT 
[17225767.184000] Modules linked in: ftsata2 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec af_packet md_mod aes dm_crypt fuse sr_mod cdrom sbp2 lp rsrc_nonstatic pcmcia_core r1000 tsdev nvidia r8169 it821x analog floppy gameport rtc parport_pc parport pcspkr psmouse serio_raw shpchp pci_hotplug snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc nvidia_agp agpgart i2c_nforce2 i2c_core evdev sg ipv6 ext3 jbd dm_mirror dm_mod ide_generic ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore ide_disk generic amd74xx sata_nv sd_mod sata_sil libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[17225767.184000] CPU:    0
[17225767.184000] EIP:    0060:[<f8e933ee>]    Tainted: P      VLI
[17225767.184000] EFLAGS: 00010282   (2.6.15-27-386) 
[17225767.184000] EIP is at EXP_CAM_ComponentGetDMASafeMemoryRequirement+0x1e/0x30 [ftsata2]
[17225767.184000] eax: 00000794   ebx: 00003515   ecx: 00003515   edx: f8e933d0
[17225767.184000] esi: 00000000   edi: 00000000   ebp: 105a3515   esp: d1bfbe58
[17225767.184000] ds: 007b   es: 007b   ss: 0068
[17225767.184000] Process insmod (pid: 29822, threadinfo=d1bfa000 task=ee520030)
[17225767.184000] Stack: 1e000200 35180012 00000794 0000ac44 00000550 18000004 00000001 f8e75f70 
[17225767.184000]        f8eb7c40 f8e769f4 105a3515 105a3515 d1bfbe90 105a3515 00000000 00000000 
[17225767.184000]        00000000 dff69400 f938c00c 00244e20 f8e7606e f938c00c dff69444 dff694e0 
[17225767.184000] Call Trace:
[17225767.184000]  [<f8e75f70>] fasttrak_probe+0x150/0x530 [ftsata2]
[17225767.184000]  [<f8e769f4>] linux_GetUncachedMemoryRequirement+0x44/0x80 [ftsata2]
[17225767.184000]  [<f8e7606e>] fasttrak_probe+0x24e/0x530 [ftsata2]
[17225767.184000]  [<c01e6ea5>] pci_match_device+0x15/0x110
[17225767.184000]  [<c01e6ffc>] __pci_device_probe+0x3c/0x60
[17225767.184000]  [<c01e703f>] pci_device_probe+0x1f/0x40
[17225767.184000]  [<c024457b>] driver_probe_device+0x3b/0xc0
[17225767.184000]  [<c0244670>] __driver_attach+0x0/0x40
[17225767.184000]  [<c02446ab>] __driver_attach+0x3b/0x40
[17225767.184000]  [<c0243c58>] bus_for_each_dev+0x48/0x80
[17225767.184000]  [<c02446c5>] driver_attach+0x15/0x20
[17225767.184000]  [<c0244670>] __driver_attach+0x0/0x40
[17225767.184000]  [<c02440f9>] bus_add_driver+0x69/0xc0
[17225767.184000]  [<c01e728a>] __pci_register_driver+0x6a/0xa0
[17225767.184000]  [<f8da704a>] fasttrak_init+0x4a/0x66 [ftsata2]
[17225767.184000]  [<c013820f>] sys_init_module+0x9f/0x1d0
[17225767.184000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17225767.184000] Code: 00 68 44 01 00 00 b9 40 14 00 00 eb e0 53 89 cb 83 ec 20 85 c0 74 04 85 d2 75 05 83 c4 20 5b c3 89 e0 e8 36 20 00 00 8b 44 24 08 <89> 03 8b 44 24 0c 01 c0 89 43 04 83 c4 20 5b c3 90 90 c3 eb 0d 
[17225767.184000]  
```

Now, I don't know what any of that means, but it looks like perhaps the driver crashed and caused a memory dump?

Either way, if there's anything anyone out there could suggest, I'd really appreciate it.  You can assume I don't know anything about linux.  I could have compiled the drivers wrong.  I could have cp'd things to the wrong directories.  I'm very new to this.

I searched google and couldn't find any English pages that had anything to do with the TX4310 in linux.  The Promise website is no help.  And, I'm afraid to post in the kernel.org forum, because I'm afraid of not understanding the replies.  I don't know if this is the right section to post in.  I can repost in another section if any of the mods prefer.

"Help me Ubuntu Forums.  You're my only hope!"

---

### Post by kevin24 on 2006-10-21
Hi Xela,


I have the same controller - and problems - as you do. I mentioned the issue earlier in this forum, but I didn't got any reply. You can read about my experiences at [http://ubuntuforums.org/showthread.php?t=232345](http://ubuntuforums.org/showthread.php?t=232345).

I found a message mentioning that this problem might affect every debian based distribution ([http://kanotix.com/PNphpBB2-viewtopic-t-20525.html);](http://kanotix.com/PNphpBB2-viewtopic-t-20525.html);) I can't affirm this, since I only tried Debian Sid and Ubuntu.

I also read somewhere, that the Promise Partial Open Source Driver from their official website can only be compiled with Linux Kernel 2.4, because they are using deprecated headers and function calls. I don't know if this is true either, since I don't have any 2.4 systems around. But as I mentioned in my post - and as you have experienced - the driver can be compiled, but loading it doesn't change anything.

At this moment I'm posting a bug report for Edgy Eft - maybe someone can solve this issue. Please let me know if you have written to the kernel.org forum or even got it working.


kevin

---

### Post by kevin24 on 2006-10-23
Today I installed Edgy Eft RC. The controller is now recognized and its disks can be listed, but not accessed. There is still no raid functionality at all. I've written to the Promise Technical Support Team (I really had to boot windoze 'cause these "§$% only support Intern Exploder on their website); I will post any answers here.

kevin

---

### Post by spitenmalice on 2006-10-23
Hope this helps, I have the Promise TX4310, it did not work under 6.06 (Dapper) but it is working under 6.10 (Edgy) beta.

---

### Post by kevin24 on 2006-10-23
Really, it works?? Do you have a raid 0/1/5/10 configuration or JBOD? Did it work out of the box or did you do anything to get it running?

thx,kevin

---

### Post by spitenmalice on 2006-10-23
Hey Kevin,

Currently I have just one HD attached as JBOD, when I get back to work I will connect two drives and try to mirror and see what happens. I'll post my findings in a couple hours. Edit* I forgot to mention, this was just a straight install, I didn't do anything special.

---

### Post by spitenmalice on 2006-10-23
Okay so I am using the amd64-server version of Edgy Beta, and the SATA controller works as it should. JBOD and Mirror works, also not setting up any drives on the controller will still allow me to see the drives and install to them. I do not have a copy of Edgy RC, I will download that tonight and install that next to see if it still works.

---

### Post by kevin24 on 2006-10-23
spitenmalice,

thanks for your efforts! I'm looking forward to your experiences with Edgy RC!

I also tried to install the AMD64 version of Edgy RC, but it crashed on every installation attempt. I'm not familiar with kernel drivers - is it possible that the 64bit driver, which is integrated in the AMD64 version of the kernel, works and the 32bit version does not? I will download the image again and will try that tomorrow.

Thanks again for helping me,
kevin

---

### Post by spitenmalice on 2006-10-24
Hello Kevin, 

Yes modules can be compiled both in 32 and 64 bit versions, you'll notice on the promise site they have both versions available for download. Anyway last night I downloaded edgy-rc the 64bit and 32 bit versions. They both work fine for me. Can you post the type of motherboard you have and hard drives? It could be a problem with one of them.

---

### Post by kevin24 on 2006-10-24
Okay, I've got an answer from the Promise technical support team, but it sounds more like a joke than an answer (I mentioned in my request that I have a TX4310 card):

> we are sorry the card is discontinued. the drivers indeed only work with kernel 2.4 our TX4310 has support for kernel 2.6.

So it seems that they aren't reading the support requests very well..


So it works for you, so maybe you are right and my computer is causing the problem. Here's my configuration:

Mainboard: Asus A8N-E, nForce 400 Ultra Chipset
CPU: AMD64 3000+ Socket 939
RAM: Dual Corsair DDR400 (2x512)
Disk for OS (SATA onboard controller): Western Digital WD1200JB
SATA Raid Disks: 2x Seagate Barracuda 7200.8, 2x Seagate Barracuda 7200.9 (ST3250620AS/ST3250823AS) á 250 GB


Another idea crossed my mind: is it possible that the kernel integrated driver is not capable of all raid modes? You have tried JBOD and mirroring, but I'm running a raid 5 configuration with 4 disks. I will try to get 2 unused disks to try raid 1 somewhere, but I don't have them at the moment.

And another thing: Were you able to install on the raid disks, or did you install the OS on a separate disk?

kevin


EDIT: some info from proc
```
$ sudo cat /proc/scsi/scsi
Attached devices:
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3250620AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3250823AS      Rev: 3.03
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3250620AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3250823AS      Rev: 3.03
  Type:   Direct-Access                    ANSI SCSI revision: 05
```

btw: the required modules are loaded (or do I need more than them?)
```
$ lsmod|grep -i promise
sata_promise           12292  0
libata                 73228  2 sata_promise,sata_nv

```


UPDATE:
I've downloaded "dmraid", which can be found in the ubuntu universe. This program claims to support different software raids, including Promise Fasttrack (PDC). Well, it doesn't work, but, however, here is the error message:
```
$ sudo dmraid -r
ERROR: pdc: identifying /dev/sda, magic_0: 0x52b33485/0x410522, magic_1: 0x52b33485/0x10680522, total_disks: 4
ERROR: pdc: identifying /dev/sdb, magic_0: 0x52b33485/0x400522, magic_1: 0x52b33485/0x10680522, total_disks: 4
ERROR: pdc: identifying /dev/sdc, magic_0: 0x52b33485/0x420522, magic_1: 0x52b33485/0x10680522, total_disks: 4
ERROR: pdc: identifying /dev/sdd, magic_0: 0x52b33485/0x64d0522, magic_1: 0x52b33485/0x10680522, total_disks: 4
/dev/sdb: nvidia, "nvidia_eadbifff", stripe, ok, 488397166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_eadbifff", stripe, ok, 488397166 sectors, data@ 0

```
Maybe someone can tell me what this means (sda-d are the raid disks. I have an onboard raid controller by nVidia, but I'm NOT using it at the moment, so I'm wondering why there is a stripped raid discovered..)

---

### Post by spitenmalice on 2006-10-24
Hello Kevin,

Sorry for the confusion, I believe I know what is going on now and I have to clear some things up. When I said that the controller works as expected, I should have said that it works as "I" expected. This, and most promise cards, is using software raid also known as fakeraid. In my experience I haven't found many software raid controllers, to work as intended with Linux. When I said that it works with JBOD and Mirror, I ment that the controller was functional and I was able to install to the drives with Linux, however I setup the RAID (JBOD or Mirror) with Linux software RAID itself, and not with the card.

In my opinion I believe the reason for fakeraid not being supported is that Linux already supports it's own software raid, and probably runs a bit better then having to load 3rd party modules to get Linux to do something it already can do on it's own. This is however my opinion, people may disagree with me, but I don't really care. You see if you are able to get fakeraid running under Linux with the promise modules, your OS is still going to be doing all the processing for the raid controller. So it's technically no different then using Linux's software raid, accept you would be using promises middle man module which would cause slower throughput, because your OS has to communicate with the card through the drivers.

So if you still want to setup fakeraid as intended with the promise modules (drivers) check out this [link]("http://www.howtoforge.com/forums/showthread.php?t=1664")  It is a SuSE howto which was created by using a Gentoo howto and so on, should help to get it going as inteded, providing that the 64bit promise module (driver) works, unless you want to use the 32bit OS.

Or 

With the standard promise module installed with Edgy, just use that controller as the hard drive interface and nothing more (so no defining arrays on the card), then setup the raid configuration with Linux's software RAID, this is something that can be done right from the Ubuntu installer. Thus cutting out the middle man, and probably gaining some throughput. Let me know if you want help with Linux's Software raid. 

Again sorry for the confusion, I hope this helps.

---

### Post by kevin24 on 2006-10-25
Hi spitenmalice,


Again, thanks for all the help. I appreciate your suggestions, but I can't use software raid. Besides that the performance of fakeraid is higher (hardware XOR unit), I'm forced to use Windoze for some reasons (special programs and games; altough I will try to get these working under wine). The biggest disadvantage of software raid is its lack of platform independence. Another reason is that I don't have empty disks for temporary storage of 700 GB of data while setting up software raid..

So I will try the tutorial you suggested. If that doesn't work, then... I don't know. I don't wanna stick with windoze. So I will have to buy another raid controller.. ^^

However, I will post my experiences with the tutorial here.


kevin

---

### Post by xela321 on 2006-10-27
Hey thanks for everyone's input on the controller.  I actually am using kernel version 2.6.18 and the card works with dmraid flawlessly.  I might try it under 2.6.17, but... if it ain't broke, don't fix it right?  Especially if you fought the damn card for 2 weeks.

This machine now has ~1.8TB of storage, which I must say, is pretty  kewl.

Now that i've upgrade to edgy though.... hald is taking up 30% CPU time.  I posted about that here -> [http://www.ubuntuforums.org/showthread.php?t=278282&highlight=hald](http://www.ubuntuforums.org/showthread.php?t=278282&highlight=hald)

I doubt if it's a problem with the RAID card, but maybe someone reading this might be able to help.

---

### Post by kevin24 on 2006-10-27
I stumbled upon dmraid yesterday, but I was wondering if I should risk the lose of data (it's alpha software AFAIK). I installed dmraid on kubuntu rc using 2.6.17: it recognizes the card and the four disks, but it's not able to discover the used raid mode. I guess I'll have to apply the [dm-raid45]("http://people.redhat.com/~heinzm/sw/dm/dm-raid45/") patch by Heinz Mauelshagen. Since I am quite new to linux (I've never compiled a kernel or applied a patch until now), I just want to know if there's something I'll have to keep in mind to prevent destroying my system or my data - it would be nice to get some hints :-)

---

### Post by xela321 on 2006-10-27
Short of backing up your data (which you already said you can't do), I don't know of a sure-fire way of making sure your raid system is detected properly with out needing to be re-built.  If you have any spare drives, you may want to clear them, take out your array, then test the whole process on that.

I'll be honest, my friend pretty much did most of the work.  I know he installed 2.6.18, was able to modprobe raid5 and dmraid and all that jazz, once we got the prerequisites out of the way, it was a trivial exercise to initialize the array and start writing to it.  This kid also got his name in the kernel source code when he was a sophomore in high school (~4 years ago) by porting some encryption kernel module (so he knows what he's doing).

I mean to get together with him to produce a how-to.  When I do, I'll post a link to it in this thread.

-Alex

---

### Post by THG68 on 2006-10-30
Hi kevin24

I have the same problem you mention with the Promise FastTrak TX4310.
RAID5 is not possible, but the 4 disks are visible each (instead of 1 BIG disk only)
No data on the disks yet, so I do not have to worry about data loss.

I have just installed ubuntu desktop 6.10 over the weekend which uses kernel 2.6.17-10-generic (that's what I get with 'uname -r')

I have successfully compiled the tx4310 partial source as described in the (vendor's) readme and have insmod the ftsata2.ko and also copied it to .../kernel/drivers/scsi/

Since I bought the tx4310 for the purpose of RAID5, I really would appreciate if it worked as designed, e.g. without software raid control.

Since I'm not familiar with kernel upgrade/compilation:

**1) Could someone tell me how to upgrade to 2.6.18?**
**2) What else is needed (modules etc) beside the 'new' kernel?**

thanks a lot
THG68

---

### Post by THG68 on 2006-10-30
Hi 

some comments/ideas that came up:

1) I found that the disk sda - sdd are 'linked' to the driver 'sata_promise'. Since I have successfully added the promise driver 'ftsata2' (that I had compiled), maybe I just have to 'remove' the 'sata_promise' driver and assign 'ftsata2' to the disks?
**=> How would this be done?** (if possible at all)

2) found a message in the log files:
kernel: [17184058.088000] Promise 4310/579/779 Serieal Device Driver 2.6.1.0320 (Feb 07, 2006)
kernel: [17184058.092000] Driver 'fasttrak' needs updating - please use bus_type methods
**=> What am I to do regarding 'bus_type methods'?**

thanks
THG68

---

### Post by THG68 on 2006-10-30
My last comment for today:

Current version of the BIOS (on card): **2.5.1.3115**

Looking at the promise download page:
=> linux drivers (including partial code) **require BIOS 2.5.1.3116 **and WebPAM 2.2.0.23

I'll try and come back with results.

THG68

---

### Post by THG68 on 2006-10-31
I just updated the BIOS of my Promise FastTrak TX4310 from 2.5.1.3115 to 2.5.1.3119  successfully.

but this did not help much...
There are still the four disks seen instead of 1 big RAID5.

any advice is welcome

thanks
THG68

---

### Post by kevin24 on 2006-11-02
I tried to get raid 5 using the device mapper userspace, the program [dmraid]("http://people.redhat.com/~heinzm/sw/dmraid/") and the kernel patch [dm-raid45]("http://people.redhat.com/~heinzm/sw/dm/dm-raid45/"). Without this patch the device mapper only supports raid modes 0 and 1.

Kubuntu comes with kernel 2.6.17-10, but there is no patch for this special version available, so I compiled kernel 2.6.18-1. The bad news: I couldn't boot the patched kernel, I tried it a couple of times. I wondered if the kernel sources are damaged, so I installed gentoo with its patched kernel sources kernel-2.6.18-gentoo-r1. The kernel boots fine, but I'm not able to apply the dm-raid45 patch successfully. I haven't tried the vanilla sources yet.

@Alex: Please ask your friend what kind of kernel sources on which version he took and which patch he did apply; I really would appreciate that!

@THG: Altough I've read a couple of times that the Promise driver doesn't work with kernel versions >2.4 I also managed to compile it successfully (altough this "bus_type methods" error message you got points to some incompatibility). I like your idea of trying to get rid of the sata_promise driver; maybe 'ftsata2' not only recognizes the card but gives fakeraid functionality too. I don't have any (k)ubuntu version installed at the moment, so please tell me about your experiences. You can try 'modprobe -r sata_promise' or you could even recompile your kernel without promise support, so the card isn't recognized at all - then there can't be anything linked to it any more..

kevin

---

### Post by THG68 on 2006-11-13
Kevin,


I had compiled 2.6.18.1 kernel, but the system was unable to boot.

Back on 2.6.17-10, I have tried "modprobe -r sata_promise" (your hint) and later I also did "modprobe ftsata2" (the driver I compiled from the downloaded promise.com partial source code.)

in GPartEd, I now see only 2 scsi devices:
/dev/sda  (0.0)
/dev/sdb  (1019 Mib)  => this is my 4 x 300GB Disk RAID 5!

I don't understand why there are 2 scsi devices, but at least the 'big' one is seen correctly on sdb. Maybe this is because of "bus_type methods"? 

I have not tried to reboot yet, I'm afraid the sata_promise driver might get reloaded. 

Perhaps I'll try to recompile the kernel without sata_promise to get it out 'for ever'.

I'll keep posting my experience...

THG

---

### Post by THG68 on 2006-11-13
ok,

here is the bad news:

I have rebooted!

Result: sata_promise gets reloaded and I only see the 4 disks, each 300 GB!

The following set of commands brings back the situation described in my last post. (2 scsi, 1 size 0, 1 RAID5 size 1019 MiB)
1) modprobe -r sata_promise
2) modprobe -r ftsata2
3) modprobe ftsata2

My questions:
A) How to force sata_promise to not load at all?
B) How to get rid of /dev/sda (0.0) which is unusable?

Thanks
THG

---

### Post by kevin24 on 2006-11-18
THG68,


I've been busy this week, so excuse my delayed answer..

You said that you could enable the driver. Could you access the disk then?
I don't think that your ftsata2 module is working correctly. Okay, you see a single disk, but where are your partitions?

Regarding your questions:
A) I don't got access to a linux box at the moment, but I think you should be able to prevent sata_promise from loading by editing the file /etc/modprobe.d/blacklist.
B) As far as I know you can't get rid of any device links in /dev.

kevin

---

### Post by THG68 on 2006-11-18
Kevin,

I have tried the /etc/modprobe.d/blacklist hint.

at the bottom of the file, I added

```
# prevent sata_promise from loading
blacklist sata_promise
```

then I rebooted, but nothing had changed. I (again) see 4 drives...

I then additionally blacklisted the libata, since this is using sata_promise. 
```
# prevent sata_promise from loading
blacklist sata_promise
blacklist libata
```
After reboot > same result. (is the order importand when blacklisting?)

Regarding the partitions: I have not yet partitioned the 'big' disk, since I can't get the system to load the proper driver that shows 'only' this 'big disk'...

Questions:
A) is there a place where I can tell the system which driver to use for which device?
B) could it be possible to use alias? (instead of sata_promise use ftsata2?). If so, how and where to configure?

Thanks
THG

---

### Post by THG68 on 2006-11-18
Kevin, 

regarding the partitions of the 'big disk', you're right!
After manually modprobe -r sata_promise; modprobe -r ftsata2; modprobe ftsata2, I get the 'big disk' on /dev/sdb.

I tried to create a new partition, but this fails already when trying to create a new disklabel...

At this moment, I have no further idea on how to proceed and what else to try.

THG

---

### Post by kevin24 on 2006-11-18
THG68,


I'm sorry I can't answer your questions, since, as I mentioned earlier, I don't have a linux box to try at the moment.

I still think that the combination of the built-in driver sata_promise and the dm-raid45 kernel patch is the key to get this card working. It would be great if Alex came back to post her used kernel-sources and how she and her friend applied the patch.

It seems that there is no problem when using raid 0 or raid 1. I will buy 100 DVDs next week to backup most of my data, so I'm able to set up raid 0 instead of raid 5 (I want to use backups anyway from now on). It will take me days to burn the disks, but.. who cares? ;-)

Anyway, I will keep subscribed to this thread, so please post any new ideas :-)


kevin

---

### Post by dseagrav on 2007-08-08
For anyone still stuck on this -
To build the source driver you have to compile the kernel with register parameters, option REGPARAM.
This avoids the oops mentioned in the first post.
I don't do anything with Ubuntu, I found this out building an embedded solution based on a cut-down Debian, so I can't offer more specific guidance.

---

### Post by kaefert66014235 on 2008-02-17
some of you guys say you have managed to use the promise TX4310 as disk controller without raid functionality, with the "sata-promise" component. this one is part of my ubuntu 7.10's kernel out of the box, and i can see and format the hard disks from the alternate install disk.

```
kaefert@Blechserver:~$ lsmod | grep -i promise
sata_promise           13956  0 
libata                125168  3 ata_generic,sata_via,sata_promise
```


but after the installation, when i start gparted, or try the command "fdisk -l" it takes VEEEERY long (about 5 minutes) to finish and then the disks that are plugged into the TX4310 arn't shown

console output of gparted:
```
kaefert@Blechserver:~$ sudo gparted
[sudo] password for kaefert:
======================
libparted : 1.7.1
======================
/dev/sda kann nicht geöffnet werden - unerkanntes Disklabel.
/dev/sdb kann nicht geöffnet werden - unerkanntes Disklabel.
/dev/sdc kann nicht geöffnet werden - unerkanntes Disklabel.
/dev/sdd kann nicht geöffnet werden - unerkanntes Disklabel.
```

```
kaefert@Blechserver:~$ sudo fdisk -l
[sudo] password for kaefert:

Disk /dev/sde: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x237a2379

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9598    77095903+  83  Linux
/dev/sde3            9599       10011     3317422+   5  Extended
/dev/sde5            9599       10011     3317391   82  Linux swap / Solaris
```

But where i can see the 4 hard discs is with this command:
```
kaefert@Blechserver:~$ sudo cat /proc/scsi/scsi
[sudo] password for kaefert:
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500830AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500830AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500830AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500830AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ExcelStor Techno Rev: PF2O
  Type:   Direct-Access                    ANSI  SCSI revision: 05
```

has anybody some hint for me how to continue? im quite frustrated on this, im already working on that the last 3 days....

---

