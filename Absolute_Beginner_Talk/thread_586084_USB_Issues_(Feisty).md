---
title: "USB Issues (Feisty)"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by justinmiller87 on 2007-10-21
I am trying to figure out if something is wrong with my USB ports or if it's Ubuntu. Basically, if I plug anything into them - such as a flash drive - sometimes they mount, sometimes they don't. I did a *lsusb* on it and got the following:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Also, I did *sudo tail -f /var/log/messages* and received the following results:
(First Port)
```
Oct 22 06:37:04 justin-laptop kernel: [32820.348000] usb 4-3: new high speed USB device using ehci_hcd and address 2
Oct 22 06:37:04 justin-laptop kernel: [32820.860000] usb 4-3: new high speed USB device using ehci_hcd and address 3
Oct 22 06:37:05 justin-laptop kernel: [32821.868000] usb 4-3: new high speed USB device using ehci_hcd and address 5
Oct 22 06:37:06 justin-laptop kernel: [32822.396000] usb 4-3: new high speed USB device using ehci_hcd and address 6
Oct 22 06:37:06 justin-laptop kernel: [32822.868000] usb 4-3: new high speed USB device using ehci_hcd and address 7
Oct 22 06:37:08 justin-laptop kernel: [32824.388000] usb 4-3: new high speed USB device using ehci_hcd and address 9
Oct 22 06:37:08 justin-laptop kernel: [32825.172000] usb 4-3: new high speed USB device using ehci_hcd and address 11
Oct 22 06:37:10 justin-laptop kernel: [32826.428000] usb 4-3: new high speed USB device using ehci_hcd and address 12
Oct 22 06:37:11 justin-laptop kernel: [32827.428000] usb 4-3: new high speed USB device using ehci_hcd and address 14
Oct 22 06:37:11 justin-laptop kernel: [32828.212000] usb 4-3: new high speed USB device using ehci_hcd and address 15
Oct 22 06:37:12 justin-laptop kernel: [32828.708000] usb 4-3: new high speed USB device using ehci_hcd and address 16
Oct 22 06:37:13 justin-laptop kernel: [32829.716000] usb 4-3: new high speed USB device using ehci_hcd and address 17
Oct 22 06:37:14 justin-laptop kernel: [32830.468000] usb 4-3: new high speed USB device using ehci_hcd and address 18
Oct 22 06:37:14 justin-laptop kernel: [32831.252000] usb 4-3: new high speed USB device using ehci_hcd and address 19
Oct 22 06:37:15 justin-laptop kernel: [32831.748000] usb 4-3: new high speed USB device using ehci_hcd and address 20
Oct 22 06:37:15 justin-laptop kernel: [32832.260000] usb 4-3: new high speed USB device using ehci_hcd and address 21
Oct 22 06:37:16 justin-laptop kernel: [32833.020000] usb 4-3: new high speed USB device using ehci_hcd and address 23
Oct 22 06:37:17 justin-laptop kernel: [32834.028000] usb 4-3: new high speed USB device using ehci_hcd and address 24
Oct 22 06:37:18 justin-laptop kernel: [32835.028000] usb 4-3: new high speed USB device using ehci_hcd and address 27
Oct 22 06:37:19 justin-laptop kernel: [32835.828000] usb 4-3: new high speed USB device using ehci_hcd and address 29
Oct 22 06:37:20 justin-laptop kernel: [32836.820000] usb 4-3: new high speed USB device using ehci_hcd and address 31
Oct 22 06:37:22 justin-laptop kernel: [32838.340000] usb 4-3: new high speed USB device using ehci_hcd and address 33
Oct 22 06:37:22 justin-laptop kernel: [32838.852000] usb 4-3: new high speed USB device using ehci_hcd and address 34
Oct 22 06:37:23 justin-laptop kernel: [32839.860000] usb 4-3: new high speed USB device using ehci_hcd and address 37
Oct 22 06:37:25 justin-laptop kernel: [32841.628000] usb 4-3: new high speed USB device using ehci_hcd and address 39
Oct 22 06:37:26 justin-laptop kernel: [32842.388000] usb 4-3: new high speed USB device using ehci_hcd and address 40
Oct 22 06:37:27 justin-laptop kernel: [32843.412000] usb 4-3: new high speed USB device using ehci_hcd and address 42
Oct 22 06:37:28 justin-laptop kernel: [32844.420000] usb 4-3: new high speed USB device using ehci_hcd and address 43
Oct 22 06:37:29 justin-laptop kernel: [32846.096000] usb 4-3: new high speed USB device using ehci_hcd and address 44
Oct 22 06:37:30 justin-laptop kernel: [32846.948000] usb 4-3: new high speed USB device using ehci_hcd and address 45
Oct 22 06:37:31 justin-laptop kernel: [32848.220000] usb 4-3: new high speed USB device using ehci_hcd and address 46
Oct 22 06:37:33 justin-laptop kernel: [32849.492000] usb 4-3: new high speed USB device using ehci_hcd and address 49
Oct 22 06:37:34 justin-laptop kernel: [32850.500000] usb 4-3: new high speed USB device using ehci_hcd and address 51
Oct 22 06:37:34 justin-laptop kernel: [32851.260000] usb 4-3: new high speed USB device using ehci_hcd and address 52
Oct 22 06:37:35 justin-laptop kernel: [32851.748000] usb 4-3: new high speed USB device using ehci_hcd and address 53
Oct 22 06:37:36 justin-laptop kernel: [32852.780000] usb 4-3: new high speed USB device using ehci_hcd and address 54
Oct 22 06:37:37 justin-laptop kernel: [32853.788000] usb 4-3: new high speed USB device using ehci_hcd and address 56
Oct 22 06:37:38 justin-laptop kernel: [32854.788000] usb 4-3: new high speed USB device using ehci_hcd and address 57
Oct 22 06:37:39 justin-laptop kernel: [32855.836000] usb 4-3: new high speed USB device using ehci_hcd and address 59
Oct 22 06:37:40 justin-laptop kernel: [32856.828000] usb 4-3: new high speed USB device using ehci_hcd and address 60
Oct 22 06:37:41 justin-laptop kernel: [32857.588000] usb 4-3: new high speed USB device using ehci_hcd and address 61
Oct 22 06:37:42 justin-laptop kernel: [32858.860000] usb 4-3: new high speed USB device using ehci_hcd and address 63
Oct 22 06:37:44 justin-laptop kernel: [32860.132000] usb 4-3: new high speed USB device using ehci_hcd and address 65
Oct 22 06:37:44 justin-laptop kernel: [32860.868000] usb 4-3: new high speed USB device using ehci_hcd and address 67
Oct 22 06:37:45 justin-laptop kernel: [32861.652000] usb 4-3: new high speed USB device using ehci_hcd and address 69
Oct 22 06:37:46 justin-laptop kernel: [32862.388000] usb 4-3: new high speed USB device using ehci_hcd and address 71
Oct 22 06:37:47 justin-laptop kernel: [32863.380000] usb 4-3: new high speed USB device using ehci_hcd and address 72
Oct 22 06:37:48 justin-laptop kernel: [32864.692000] usb 4-3: new high speed USB device using ehci_hcd and address 75
Oct 22 06:37:49 justin-laptop kernel: [32865.428000] usb 4-3: new high speed USB device using ehci_hcd and address 77
Oct 22 06:37:49 justin-laptop kernel: [32866.212000] usb 4-3: new high speed USB device using ehci_hcd and address 78
Oct 22 06:37:51 justin-laptop kernel: [32867.468000] usb 4-3: new high speed USB device using ehci_hcd and address 81
Oct 22 06:37:51 justin-laptop kernel: [32867.980000] usb 4-3: new high speed USB device using ehci_hcd and address 82
Oct 22 06:37:52 justin-laptop kernel: [32868.740000] usb 4-3: new high speed USB device using ehci_hcd and address 83
Oct 22 06:37:52 justin-laptop kernel: [32869.268000] usb 4-3: new high speed USB device using ehci_hcd and address 84
Oct 22 06:37:53 justin-laptop kernel: [32869.748000] usb 4-3: new high speed USB device using ehci_hcd and address 85
Oct 22 06:37:53 justin-laptop kernel: [32870.260000] usb 4-3: new high speed USB device using ehci_hcd and address 86
Oct 22 06:37:54 justin-laptop kernel: [32871.020000] usb 4-3: new high speed USB device using ehci_hcd and address 88
Oct 22 06:37:55 justin-laptop kernel: [32872.028000] usb 4-3: new high speed USB device using ehci_hcd and address 91
Oct 22 06:37:56 justin-laptop kernel: [32872.796000] usb 4-3: new high speed USB device using ehci_hcd and address 93
Oct 22 06:37:56 justin-laptop kernel: [32873.300000] usb 4-3: new high speed USB device using ehci_hcd and address 94
Oct 22 06:37:57 justin-laptop kernel: [32874.060000] usb 4-3: new high speed USB device using ehci_hcd and address 96
Oct 22 06:37:58 justin-laptop kernel: [32874.548000] usb 4-3: new high speed USB device using ehci_hcd and address 97
Oct 22 06:37:58 justin-laptop kernel: [32875.068000] usb 4-3: new high speed USB device using ehci_hcd and address 98
Oct 22 06:38:00 justin-laptop kernel: [32876.588000] usb 4-3: new high speed USB device using ehci_hcd and address 101
Oct 22 06:38:01 justin-laptop kernel: [32877.588000] usb 4-3: new high speed USB device using ehci_hcd and address 103
Oct 22 06:38:01 justin-laptop kernel: [32878.108000] usb 4-3: new high speed USB device using ehci_hcd and address 104
Oct 22 06:38:03 justin-laptop kernel: [32879.628000] usb 4-3: new high speed USB device using ehci_hcd and address 106
Oct 22 06:38:04 justin-laptop kernel: [32880.756000] usb 4-3: new high speed USB device using ehci_hcd and address 107
Oct 22 06:38:05 justin-laptop kernel: [32881.908000] usb 4-3: new high speed USB device using ehci_hcd and address 109
```
(Second Port)
```
Oct 22 06:38:21 justin-laptop kernel: [32897.468000] usb 4-4: new high speed USB device using ehci_hcd and address 2
Oct 22 06:38:33 justin-laptop kernel: [32909.876000] usb 4-4: new high speed USB device using ehci_hcd and address 50
Oct 22 06:38:36 justin-laptop kernel: [32912.684000] usb 4-4: new high speed USB device using ehci_hcd and address 60
Oct 22 06:38:40 justin-laptop kernel: [32916.204000] usb 4-4: new high speed USB device using ehci_hcd and address 73
Oct 22 06:38:49 justin-laptop kernel: [32925.836000] usb 4-4: new high speed USB device using ehci_hcd and address 110
Oct 22 06:38:50 justin-laptop kernel: [32926.596000] usb 4-4: new high speed USB device using ehci_hcd and address 112
Oct 22 06:38:51 justin-laptop kernel: [32927.356000] usb 4-4: new high speed USB device using ehci_hcd and address 114
Oct 22 06:38:52 justin-laptop kernel: [32928.356000] usb 4-4: new high speed USB device using ehci_hcd and address 117
Oct 22 06:38:52 justin-laptop kernel: [32929.140000] usb 4-4: new high speed USB device using ehci_hcd and address 119
Oct 22 06:39:02 justin-laptop kernel: [32938.756000] usb 4-4: new high speed USB device using ehci_hcd and address 30
Oct 22 06:39:03 justin-laptop kernel: [32940.028000] usb 4-4: new high speed USB device using ehci_hcd and address 34
Oct 22 06:39:06 justin-laptop kernel: [32942.308000] usb 4-4: new high speed USB device using ehci_hcd and address 42
Oct 22 06:39:07 justin-laptop kernel: [32943.828000] usb 4-4: new high speed USB device using ehci_hcd and address 45
Oct 22 06:39:08 justin-laptop kernel: [32944.340000] usb 4-4: new high speed USB device using ehci_hcd and address 46
Oct 22 06:39:10 justin-laptop kernel: [32946.364000] usb 4-4: new high speed USB device using ehci_hcd and address 53
Oct 22 06:39:13 justin-laptop kernel: [32949.644000] usb 4-4: new high speed USB device using ehci_hcd and address 65
Oct 22 06:39:15 justin-laptop kernel: [32951.428000] usb 4-4: new high speed USB device using ehci_hcd and address 71
Oct 22 06:39:16 justin-laptop kernel: [32952.436000] usb 4-4: new high speed USB device using ehci_hcd and address 74
Oct 22 06:39:22 justin-laptop kernel: [32959.028000] usb 4-4: new high speed USB device using ehci_hcd and address 99
Oct 22 06:39:24 justin-laptop kernel: [32960.548000] usb 4-4: new high speed USB device using ehci_hcd and address 104
Oct 22 06:39:25 justin-laptop kernel: [32961.308000] usb 4-4: new high speed USB device using ehci_hcd and address 106
Oct 22 06:39:25 justin-laptop kernel: [32961.796000] usb 4-4: new high speed USB device using ehci_hcd and address 107
Oct 22 06:39:26 justin-laptop kernel: [32962.844000] usb 4-4: new high speed USB device using ehci_hcd and address 110
Oct 22 06:39:27 justin-laptop kernel: [32963.316000] usb 4-4: new high speed USB device using ehci_hcd and address 111
Oct 22 06:39:28 justin-laptop kernel: [32964.596000] usb 4-4: new high speed USB device using ehci_hcd and address 115
Oct 22 06:39:29 justin-laptop kernel: [32965.868000] usb 4-4: new high speed USB device using ehci_hcd and address 119
Oct 22 06:39:30 justin-laptop kernel: [32966.628000] usb 4-4: new high speed USB device using ehci_hcd and address 121
Oct 22 06:39:32 justin-laptop kernel: [32968.660000] usb 4-4: new high speed USB device using ehci_hcd and address 2
Oct 22 06:39:37 justin-laptop kernel: [32973.468000] usb 4-4: new high speed USB device using ehci_hcd and address 20
Oct 22 06:39:38 justin-laptop kernel: [32975.236000] usb 4-4: new high speed USB device using ehci_hcd and address 26
Oct 22 06:39:45 justin-laptop kernel: [32981.556000] usb 4-4: new high speed USB device using ehci_hcd and address 48
Oct 22 06:39:49 justin-laptop kernel: [32986.116000] usb 4-4: new high speed USB device using ehci_hcd and address 65
Oct 22 06:39:50 justin-laptop kernel: [32986.636000] usb 4-4: new high speed USB device using ehci_hcd and address 66
```

Now, these are built-in USB 2.0 ports, but if I log into Windows, they show up as USB 1.1, which is at least better than the results shown here.

If anyone has any suggestions to help remedy this, or if you think it's a hardware issue over a software one, I'd appreciate it.

Many thanks in advance.

---

### Post by cfaulkner on 2007-10-22
SO windows is recognizing them as v1.1 ports, but ubuntu is recognizing them as v2.0?  hrmm

What kind of mobo you have or is it like a dell or something?

---

### Post by justinmiller87 on 2007-10-22
> **cfaulkner said:**
> SO windows is recognizing them as v1.1 ports, but ubuntu is recognizing them as v2.0?  hrmm

What kind of mobo you have or is it like a dell or something?
'Tis an IBM Thinkpad R40. And it's only when they are recognized, however rarely, that they are found as 2.0 ports. There are times I have lost data because when it does recognize it, it usually pops up and tells me I have an unsafe device removal in the middle of a transfer, or for absolutely no reason at all. I'm trying to locate the chipset. If I find it, I'll post what it is.

---

### Post by cfaulkner on 2007-10-22
IIRC: those thinkpads had a lousy USB interface.  So i'm not really sure on this one.

doing a 

sudo tail -f /var/log/messages

and unplugging and plugging in USB device and watch that log as your doing it to see what's going on and if there are any differences.

Also, as it's plugged in, wiggle it around a little bit and see if anything changes in the tail.

---

### Post by 3rdalbum on 2007-10-22
It sounds to me like Windows is recognising a faulty USB and dropping back to USB 1.1 in order to compensate.

However, I once used Puppy Linux on another person's laptop and found that flash drives causing the same error messages you describe (about continually being assigned new addresses). All other distributions worked fine. So you might want to try a different distribution and see if the problem still occurs.

---

### Post by justinmiller87 on 2007-10-22
Well, I think I answered my own question then. It appears to be hardware.
```
Oct 22 08:30:12 justin-laptop kernel: [39607.624000] usb 4-3: new high speed USB device using ehci_hcd and address 12
Oct 22 08:30:13 justin-laptop kernel: [39608.888000] usb 4-3: new high speed USB device using ehci_hcd and address 13
Oct 22 08:30:13 justin-laptop kernel: [39609.376000] usb 4-3: new high speed USB device using ehci_hcd and address 14
Oct 22 08:30:14 justin-laptop kernel: [39610.160000] usb 4-3: new high speed USB device using ehci_hcd and address 15
Oct 22 08:30:16 justin-laptop kernel: [39611.680000] usb 4-3: new high speed USB device using ehci_hcd and address 17
Oct 22 08:30:16 justin-laptop kernel: [39612.416000] usb 4-3: new high speed USB device using ehci_hcd and address 18
Oct 22 08:30:17 justin-laptop kernel: [39612.936000] usb 4-3: new high speed USB device using ehci_hcd and address 19
Oct 22 08:30:18 justin-laptop kernel: [39613.920000] usb 4-3: new high speed USB device using ehci_hcd and address 20
Oct 22 08:30:18 justin-laptop kernel: [39614.456000] usb 4-3: new high speed USB device using ehci_hcd and address 21
Oct 22 08:30:19 justin-laptop kernel: [39615.456000] usb 4-3: new high speed USB device using ehci_hcd and address 24
Oct 22 08:30:58 justin-laptop kernel: [39654.440000] usb 4-3: new high speed USB device using ehci_hcd and address 26
Oct 22 08:30:59 justin-laptop kernel: [39654.944000] usb 4-3: new high speed USB device using ehci_hcd and address 27
Oct 22 08:31:00 justin-laptop kernel: [39655.952000] usb 4-3: new high speed USB device using ehci_hcd and address 28
Oct 22 08:31:01 justin-laptop kernel: [39657.224000] usb 4-3: new high speed USB device using ehci_hcd and address 31
Oct 22 08:31:02 justin-laptop kernel: [39658.232000] usb 4-3: new high speed USB device using ehci_hcd and address 32
Oct 22 08:31:03 justin-laptop kernel: [39658.992000] usb 4-3: new high speed USB device using ehci_hcd and address 33
Oct 22 08:31:03 justin-laptop kernel: [39659.124000] usb 4-3: configuration #1 chosen from 1 choice
Oct 22 08:31:03 justin-laptop kernel: [39659.188000] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 22 08:31:08 justin-laptop kernel: [39664.188000] scsi 5:0:0:0: Direct-Access     CBM      Flash Disk       4.00 PQ: 0 ANSI: 2
Oct 22 08:31:08 justin-laptop kernel: [39664.188000] SCSI device sdb: 996351 2048-byte hdwr sectors (2041 MB)
Oct 22 08:31:08 justin-laptop kernel: [39664.192000] sdb: Write Protect is off
Oct 22 08:31:08 justin-laptop kernel: [39664.192000] SCSI device sdb: 996351 2048-byte hdwr sectors (2041 MB)
Oct 22 08:31:08 justin-laptop kernel: [39664.192000] sdb: Write Protect is off
Oct 22 08:31:08 justin-laptop kernel: [39664.192000]  sdb: unknown partition table
Oct 22 08:31:08 justin-laptop kernel: [39664.196000] sd 5:0:0:0: Attached scsi removable disk sdb
Oct 22 08:31:08 justin-laptop kernel: [39664.196000] sd 5:0:0:0: Attached scsi generic sg2 type 0
Oct 22 08:31:17 justin-laptop kernel: [39673.680000] usb 4-3: USB disconnect, address 33
Oct 22 08:31:18 justin-laptop kernel: [39674.440000] usb 4-3: new high speed USB device using ehci_hcd and address 36
Oct 22 08:31:20 justin-laptop kernel: [39675.952000] usb 4-3: new high speed USB device using ehci_hcd and address 40
Oct 22 08:31:20 justin-laptop kernel: [39676.736000] usb 4-3: new high speed USB device using ehci_hcd and address 41
Oct 22 08:31:21 justin-laptop kernel: [39677.232000] usb 4-3: new high speed USB device using ehci_hcd and address 42
Oct 22 08:31:22 justin-laptop kernel: [39678.504000] usb 4-3: new high speed USB device using ehci_hcd and address 45
Oct 22 08:31:23 justin-laptop kernel: [39679.776000] usb 4-3: new high speed USB device using ehci_hcd and address 48
Oct 22 08:31:25 justin-laptop kernel: [39681.544000] usb 4-3: new high speed USB device using ehci_hcd and address 52
Oct 22 08:31:26 justin-laptop kernel: [39682.552000] usb 4-3: new high speed USB device using ehci_hcd and address 54
Oct 22 08:31:27 justin-laptop kernel: [39683.064000] usb 4-3: new high speed USB device using ehci_hcd and address 55
Oct 22 08:31:28 justin-laptop kernel: [39683.824000] usb 4-3: new high speed USB device using ehci_hcd and address 57
```

Ok. Blah. Anyone know if they make a PCMCIA wireless card with USB ports on it?

---

### Post by shad0w_walker on 2007-10-22
It does like faulty USB socket, i had the same issues with my desktops front usb sockets (Cable damage) and it was very dodgy with detecting and keeping devices running. Might be an idea to get it looked at if its under warranty.

---

### Post by cfaulkner on 2007-10-22
yes they do

on newegg, type pcmcia usb and there should be a few, here's a diretc link

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815124011](http://www.newegg.com/Product/Product.aspx?Item=N82E16815124011)

---

### Post by Kitsun on 2007-10-22
I am running a ThinkPad T30 with what sounds like the same problem, If I plug in my USB drive or a USB MicroSD card reader it fails to mount.

The USB plug is 1.1 (old laptop)

---

