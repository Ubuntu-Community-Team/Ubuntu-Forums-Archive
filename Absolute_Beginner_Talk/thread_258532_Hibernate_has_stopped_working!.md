---
title: "Hibernate has stopped working!"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-16
I often use the hibernate function instead of shutting down, as I am in the middle of things often. 2 or 3 days ago perhaps, it seems to have stopped working. I shut down by choosing the hibernate function and all seems well, until I turn it on again and it asks for both my username and password and everything is gone, just as if I had done a full shutdown. This in incredibly frustrating as I loose all the stuff I was doing!! Can anyone help me to fix this?
Thank you
Justin

---

### Post by trubblemaker on 2006-09-22
I'm so with you 

I'm running a Gateway, 512 ram
 CPU: Intel(R) Celeron(R) M processor         1.40GHz stepping 08

the /etc/default/acpi-support I'm using is [from this post]("http://ubuntuforums.org/showpost.php?p=1178889&postcount=12")

<just before hibernate>
I think it flashes that something fails but then the screen is turned off. Don't know where to look for a log.
<after hibernate>
hibernate is still the same as turning off my computer.  (by turning off I mean that it is equivalent to turning it off.)  If I don't have my splash screen up I can see it clearing signature 2.  When I turn the computer back on, (after a hibenate) it really is like a normal turning-back-on and not the awesome back to where I was, like hibernate is supposed to. How can I make it hibernate for real?

I was able to hibernate before upgrading to dapper so it is possible. And I just need to find the right settings.  Any help is welcome.

---

### Post by woodlandjustin on 2006-09-26
Latest update on my situation:

Since I posted, hibernate actually sarted working! And now, it doesn't work again. Seems I just have to be lucky on whether it will work or not, and I only know if it has worked when I come to turn my computer on again. I noticed one thing the last time it failed to hibernate:

I asked it to hibernate, and it did it's stuff, and the screen went maybe black? but then there appeared the usual box which asks me for my password (I think, or perhaps my username?) and so, since it asked, I started to write it, but after only 3 characters it turned off. It has done this before when I try to hibernate, probably one of those times (or every time?) it failed.

I'm running Dapper, on a Toshiba laptop, with Gnome

---

### Post by dc. on 2006-10-10
Same here! I've used hibernate more or less regularly and then after maybe ten times I was confronted with the normal login screen!
It happened again this morning, I was able to find something in /var/log/messages

```
Oct 10 11:34:51 localhost kernel: [17179576.252000] Attempting manual resume
Oct 10 11:34:51 localhost kernel: [17179576.252000] Freezing cpus ...
Oct 10 11:34:51 localhost kernel: [17179576.252000] Stopping tasks: ==========<6>usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 10 11:34:51 localhost kernel: [17179577.264000] usb 3-2: new full speed USB device using uhci_hcd and address 2
Oct 10 11:34:51 localhost kernel: [17179577.436000] =|
Oct 10 11:34:51 localhost kernel: [17179577.436000] Shrinking memory...  ^H-^Hdone (0 pages freed)
Oct 10 11:34:51 localhost kernel: [17179577.476000] Loading image metadata ... done (64 pages loaded)
Oct 10 11:34:51 localhost kernel: [17179578.228000] busybox: page allocation failure. order:0, mode:0x8020
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [__alloc_pages+535/800] __alloc_pages+0x217/0x320
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [get_zeroed_page+39/80] get_zeroed_page+0x27/0x50
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [alloc_data_pages+57/256] alloc_data_pages+0x39/0x100
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [swsusp_read+499/560] swsusp_read+0x1f3/0x230
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [software_resume+126/240] software_resume+0x7e/0xf0
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [resume_store+148/160] resume_store+0x94/0xa0
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [flush_write_buffer+55/64] flush_write_buffer+0x37/0x40
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [sysfs_write_file+92/144] sysfs_write_file+0x5c/0x90
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [vfs_write+214/432] vfs_write+0xd6/0x1b0
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [sys_write+75/128] sys_write+0x4b/0x80
Oct 10 11:34:51 localhost kernel: [17179578.228000]  [syscall_call+7/11] syscall_call+0x7/0xb
Oct 10 11:34:51 localhost kernel: [17179578.228000] Mem-info:
Oct 10 11:34:51 localhost kernel: [17179578.228000] DMA per-cpu:
Oct 10 11:34:51 localhost kernel: [17179578.228000] cpu 0 hot: low 0, high 0, batch 1 used:0
Oct 10 11:34:51 localhost kernel: [17179578.228000] cpu 0 cold: low 0, high 0, batch 1 used:0
Oct 10 11:34:51 localhost kernel: [17179578.228000] DMA32 per-cpu: empty
Oct 10 11:34:51 localhost kernel: [17179578.228000] Normal per-cpu:
Oct 10 11:34:51 localhost kernel: [17179578.228000] cpu 0 hot: low 0, high 186, batch 31 used:30
Oct 10 11:34:51 localhost kernel: [17179578.228000] cpu 0 cold: low 0, high 62, batch 15 used:4
Oct 10 11:34:51 localhost kernel: [17179578.228000] HighMem per-cpu: empty
Oct 10 11:34:51 localhost kernel: [17179578.228000] Free pages:        3020kB (0kB HighMem)
Oct 10 11:34:51 localhost kernel: [17179578.228000] Active:2031 inactive:2326 dirty:0 writeback:0 unstable:0 free:755 slab:1689 mapped:331 pagetables:13
Oct 10 11:34:51 localhost kernel: [17179578.228000] DMA free:2016kB min:88kB low:44kB high:88kB active:0kB inactive:0kB present:16384kB pages_scanned:0 all_
Oct 10 11:34:51 localhost kernel: [17179578.228000] lowmem_reserve[]: 0 0 495 495
Oct 10 11:34:51 localhost kernel: [17179578.228000] DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclai
Oct 10 11:34:51 localhost kernel: [17179578.228000] lowmem_reserve[]: 0 0 495 495
Oct 10 11:34:51 localhost kernel: [17179578.228000] Normal free:1004kB min:2800kB low:1400kB high:2800kB active:8124kB inactive:9304kB present:507712kB page
Oct 10 11:34:51 localhost kernel: [17179578.228000] lowmem_reserve[]: 0 0 0 0
Oct 10 11:34:51 localhost kernel: [17179578.228000] HighMem free:0kB min:128kB low:32kB high:64kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_un
Oct 10 11:34:51 localhost kernel: [17179578.228000] lowmem_reserve[]: 0 0 0 0
Oct 10 11:34:51 localhost kernel: [17179578.228000] DMA: 0*4kB 0*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 2016kB
Oct 10 11:34:51 localhost kernel: [17179578.228000] DMA32: empty
Oct 10 11:34:51 localhost kernel: [17179578.228000] Normal: 1*4kB 1*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1004kB
Oct 10 11:34:51 localhost kernel: [17179578.228000] HighMem: empty
Oct 10 11:34:51 localhost kernel: [17179578.228000] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct 10 11:34:51 localhost kernel: [17179578.228000] Free swap  = 0kB
Oct 10 11:34:51 localhost kernel: [17179578.228000] Total swap = 0kB
Oct 10 11:34:51 localhost kernel: [17179578.228000] Free swap:            0kB
Oct 10 11:34:51 localhost kernel: [17179578.236000] 131024 pages of RAM
Oct 10 11:34:51 localhost kernel: [17179578.236000] 0 pages of HIGHMEM
Oct 10 11:34:51 localhost kernel: [17179578.236000] 2304 reserved pages
Oct 10 11:34:51 localhost kernel: [17179578.236000] 370 pages shared
Oct 10 11:34:51 localhost kernel: [17179578.236000] 0 pages swap cached
Oct 10 11:34:51 localhost kernel: [17179578.236000] 0 pages dirty
Oct 10 11:34:51 localhost kernel: [17179578.236000] 0 pages writeback
Oct 10 11:34:51 localhost kernel: [17179578.236000] 331 pages mapped
Oct 10 11:34:51 localhost kernel: [17179578.236000] 1689 pages slab
Oct 10 11:34:51 localhost kernel: [17179578.236000] 13 pages pagetables
Oct 10 11:34:51 localhost kernel: [17179578.264000] Restarting tasks...<6>usbcore: registered new driver hiddev
Oct 10 11:34:51 localhost kernel: [17179578.304000]  done
Oct 10 11:34:51 localhost kernel: [17179578.304000] Thawing cpus ...
Oct 10 11:34:51 localhost kernel: [17179578.316000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 10 11:34:51 localhost kernel: [17179578.316000] EXT3-fs: write access will be enabled during recovery.
Oct 10 11:34:51 localhost kernel: [17179578.324000] input: Logitech Trackball as /class/input/input1
Oct 10 11:34:51 localhost kernel: [17179578.324000] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.0-2
Oct 10 11:34:51 localhost kernel: [17179578.324000] usbcore: registered new driver usbhid
Oct 10 11:34:51 localhost kernel: [17179578.324000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Oct 10 11:34:51 localhost kernel: [17179587.248000] EXT3-fs: recovery complete.

```

So this is *un*successful resume. You can see that it also talks about recovery for the ext3-partition which would not be needed if had resumed properly.

The annoying thing for me here is that this bug is *random*! I was used to the linux way: Either you do it wrong and it doesn't work or you do it right and it works all the time.
But this is like windows, bah.

I hope someone has a suggestion!

I filed a bug report and already found another bug-report which states the same which is much older but still unchecked.... :rolleyes: 

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/65032](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/65032)
and
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49615](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/49615)

---

### Post by Rhaurison Bergamin on 2006-10-10
Have you upgraded to 6.06.1 ?????

---

### Post by dc. on 2006-10-10
I've installed dapper and have all updates.

---

### Post by ajaustin on 2006-10-11
I thought I might have it cracked when I realised that I didn't have enough swap for 2 times RAM size, fixed that and it now looks like it is saving everything away for the hiberbate resume and then powers off.  (It didn't do this before.)

However, when I power up it seems to make no attempt to resume and goes to a normal login screen.

Also, I have software RAID running and this is broken on resume and has to completely resync, which isn't what one wants.  The relevant log entry seems to be:-

> Oct 11 16:30:49 localhost kernel: [17179574.012000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Oct 11 16:30:49 localhost kernel: [17179574.016000] md: bitmap version 4.39
Oct 11 16:30:49 localhost kernel: [17179574.020000] md: raid1 personality registered as nr 3
Oct 11 16:30:49 localhost kernel: [17179574.264000] md: md0 stopped.
Oct 11 16:30:49 localhost kernel: [17179574.308000] md: bind<hdb1>
Oct 11 16:30:49 localhost kernel: [17179574.308000] md: bind<hda1>
Oct 11 16:30:49 localhost kernel: [17179574.312000] raid1: raid set md0 active with 2 out of 2 mirrors
Oct 11 16:30:49 localhost kernel: [17179574.328000] md: md1 stopped.
Oct 11 16:30:49 localhost kernel: [17179574.380000] md: bind<hdb3>
Oct 11 16:30:49 localhost kernel: [17179574.380000] md: bind<hda3>
Oct 11 16:30:49 localhost kernel: [17179574.384000] md: md1: raid array is not clean -- starting background reconstruction
Oct 11 16:30:49 localhost kernel: [17179574.388000] raid1: raid set md1 active with 2 out of 2 mirrors
Oct 11 16:30:49 localhost kernel: [17179574.392000] md: syncing RAID array md1
Oct 11 16:30:49 localhost kernel: [17179574.396000] md: minimum _guaranteed_ reconstruction speed: 1000 KB/sec/disc.
Oct 11 16:30:49 localhost kernel: [17179574.396000] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for reconstruction.
Oct 11 16:30:49 localhost kernel: [17179574.404000] md: using 128k window, over a total of 76878976 blocks.
Oct 11 16:30:49 localhost kernel: [17179574.532000] Attempting manual resume
Oct 11 16:30:49 localhost kernel: [17179574.536000] Stopping tasks: ============
Oct 11 16:30:49 localhost kernel: [17179580.540000]  stopping tasks failed (1 tasks remaining)
Oct 11 16:30:49 localhost kernel: [17179580.544000] Restarting tasks...<6> Strange, md1_resync not stopped
Oct 11 16:30:49 localhost kernel: [17179580.548000]  done
Oct 11 16:30:49 localhost kernel: [17179580.924000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 11 16:30:49 localhost kernel: [17179580.928000] EXT3-fs: write access will be enabled during recovery.
Oct 11 16:30:49 localhost kernel: [17179584.268000] EXT3-fs: recovery complete.
Oct 11 16:30:49 localhost kernel: [17179584.268000] kjournald starting.  Commit interval 5 seconds
Oct 11 16:30:49 localhost kernel: [17179584.276000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 11 16:30:49 localhost kernel: [17179593.324000] Linux agpgart interface v0.101 (c) Dave Jones

Maybe hibernate doesn't work with software RAID?  Or could it be something else?

Tony

---

### Post by dc. on 2006-10-11
I don't use software RAID, so I can't answer that.
However the thing is, that it works *mostofthetime* and then you stare at the 'normal' boot process which is not a good feeling because you know that some of the files you had left open could have been damaged.

---

### Post by trubblemaker on 2006-10-11
Yeah it's a real pain as it used to work in breezy

---

### Post by trubblemaker on 2007-01-18
Fix for hibernation issue thought I'd update this for others that had issues:

[https://launchpad.net/ubuntu/+bug/69208](https://launchpad.net/ubuntu/+bug/69208)

turns out upgrades to dapper didn't get an entry they needed. and your swap space may be "kinda"  messed up/missing

check out the link for the fix.

---

