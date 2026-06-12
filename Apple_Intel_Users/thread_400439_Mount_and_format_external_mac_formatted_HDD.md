---
title: "Mount and format external mac formatted HDD"
date: 2007-04-03
forum: Apple Intel Users
---

### Post by BravoGolf on 2007-04-03
My sincerest apologies if this has been asked a billion times, I've searched Google and forums but couldn't find an answer :(

Basically, I've just instalelled Ubuntu via Parallels on Mac OS X 10.4.9 and have an external HDD that's currently formatted to the mac file system that I would now like to format in the Ubuntu to the ext3 file system.

And there, I'm lost. It finds the HDD on Mac but how do I find the HDD in Ubuntu?

And then, once found, how do I format the HDD :confused:

---

### Post by Sammi on 2007-04-03
Open Synaptic. Search for gparted and install it. Then launch gparted by clicking System -> Administration -> Gnome partition manager in the top panel. Your device should show up and you should be given the option to format it by right clicking on it.

---

### Post by BravoGolf on 2007-04-03
> **Sammi said:**
> Open Synaptic. Search for gparted and install it. Then launch gparted by clicking System -> Administration -> Gnome partition manager in the top panel. Your device should show up and you should be given the option to format it by right clicking on it.

Thank you, Sammi, I appreciate your help. I've got Gnome there now but for some reason it doesn't detect the external HDD. Mac, on ther hand, does.

Is there something I need to do to tell Ubuntu that the external HDD is there?

---

### Post by Sammi on 2007-04-03
Honestly if the device doesn't show up right there in Gparted all by itself, then this problem is beyond me :(

---

### Post by cyberdork33 on 2007-04-03
you may have to virtually "plug-in" the device in the VM settings.

---

### Post by BravoGolf on 2007-04-04
> **cyberdork33 said:**
> you may have to virtually "plug-in" the device in the VM settings.

Thanks Sammi.

Cyberdork, cheers for the reply. You mean in the Parallels application I have to let it know there's an external present? If so, I checked the HDD settings and saw no option to add an external Hard Drive :(

---

### Post by cyberdork33 on 2007-04-04
in that configuration, you will only be able to mount hard drive images (which is another option, make a hard drive image on the disk, then add it). USB devices on the Mac are not "connected" to the VM. To Ubuntu, it is like the external hard drive is not attached at all. Look in the USB config to see if you can have certain devices "plugged" at boot time.

---

### Post by BravoGolf on 2007-04-04
> **cyberdork33 said:**
> in that configuration, you will only be able to mount hard drive images (which is another option, make a hard drive image on the disk, then add it). USB devices on the Mac are not "connected" to the VM. To Ubuntu, it is like the external hard drive is not attached at all. Look in the USB config to see if you can have certain devices "plugged" at boot time.

Thank you. I've now set Parallels to use the USB device.

But now I get the following error in the Terminal when it tries to add the device automatically:

[13759.328953] irq 9: nobody cared (try booting with the "irqpoll" option)
[13759.328986]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[13759.329059]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
[13759.329070]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[13759.329081]  <c014007b> disk_store+0x10b/0x12e  <c012782f> __do_softirq+0x5f/0xe0
[13759.329112]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
[13759.329119]  <c010408a> common_interrupt+0x1a/0x20  <c0102080> default_idle+0x0/0x60
[13759.329129]  <c01020aa> default_idle+0x2a/0x60  <c0102122> cpu_idle+0x42/0xb0
[13759.329138]  <c03f07a1> start_kernel+0x321/0x3a0  <c03f0210> unknown_bootoption+0x0/0x270
[13759.329181] handlers:
[13759.329184] [<d0897830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[13759.329207] [<d0953cb0>] (snd_intel8x0_interrupt+0x0/0x210 [snd_intel8x0])
[13759.329217] Disabling IRQ #9
[13759.675634] usb 2-1: new high speed USB device using ehci_hcd and address 2
[13776.824741] usb 2-1: device not accepting address 2, error -110
[13776.992424] usb 2-1: new high speed USB device using ehci_hcd and address 3
[13794.095835] usb 2-1: device not accepting address 3, error -110
[13794.263910] usb 2-1: new high speed USB device using ehci_hcd and address 4
[13809.778393] usb 2-1: device not accepting address 4, error -110
[13809.959802] usb 2-1: new high speed USB device using ehci_hcd and address 5
[13825.514396] usb 2-1: device not accepting address 5, error -110
[14215.977404] usb 2-1: new high speed USB device using ehci_hcd and address 6
[14233.429040] usb 2-1: device not accepting address 6, error -110
[14233.591405] usb 2-1: new high speed USB device using ehci_hcd and address 7
[14250.699368] usb 2-1: device not accepting address 7, error -110
[14250.868041] usb 2-1: new high speed USB device using ehci_hcd and address 8
[14265.838931] usb 2-1: device not accepting address 8, error -110
[14274.624743] usb 2-1: new high speed USB device using ehci_hcd and address 10
[14291.773026] usb 2-1: device not accepting address 10, error -110
[14291.941013] usb 2-1: new high speed USB device using ehci_hcd and address 11
[14309.164806] usb 2-1: device not accepting address 11, error -110
[14309.333571] usb 2-1: new high speed USB device using ehci_hcd and address 12
[14324.565945] usb 2-1: device not accepting address 12, error -110
[14324.727369] usb 2-1: new high speed USB device using ehci_hcd and address 13

---

### Post by BravoGolf on 2007-04-04
Hey all, the device is now registered and showing up as a device in the Gparted partition manager app. However, when I right click it there is no option available to format. Or, rather, it's there but the format, or any option is greyed out

---

### Post by cyberdork33 on 2007-04-04
I am not really sure why you are trying to dedicate the drive to Parallels... However, you may need to repartition the drive... delete the current partition and create a new linux partition.

---

### Post by Sammi on 2007-04-04
You need to unmount the drive before you can format it or edit the partition table.

---

### Post by phil90 on 2007-04-04
Good just what I need to format my new hard drive


I got an external hard drive I don't understand there is a difference of more than 20 gb between what the Hard drive is suppose to have as capacity and what there is on the hard drive itself. I know there might be a slight difference but the difference is 22 gb Did they sell me the wrong thing??

---

### Post by BravoGolf on 2007-04-05
> **phil90 said:**
> Good just what I need to format my new hard drive


I got an external hard drive I don't understand there is a difference of more than 20 mo  between what the Hard drive is suppose to have as capacity and what there is on the hard drive itself. I know there might be a slight difference but the difference is 22 mb Did they sell me the wrong thing??

Not sure what you mean but it's normal for a HDD to not have the full amount of space available, some is usually reserved or simply not available. My 500g HDD, for example, has a few gigs missing.

Sammi et al, thank you. I used Ubuntu on another machine and formatted the drive perfectly, though I had to format the drive on Windows to NTFS first (previously it was a Unix file system formatted by the mac) and then download a package to Ubuntu to allow me to read NTFS drives, but otherwise all is well :)

---

### Post by Sammi on 2007-04-05
> **phil90 said:**
> Good just what I need to format my new hard drive


I got an external hard drive I don't understand there is a difference of more than 20 mo  between what the Hard drive is suppose to have as capacity and what there is on the hard drive itself. I know there might be a slight difference but the difference is 22 mb Did they sell me the wrong thing??
This is a common phenomenon and there is nothing wrong with your harddrive. See the "consumer confusion" section of this article: [http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

In short it's because there are two ways of defining a "gigabyte". HD manufacturer market the harddrives with one definition and operating systems report the size with a different definition, which gives a lower value than the marketed one. There are class action lawsuits over this misleading marketing practice.

EDIT: This article goes into more detail: [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

---

### Post by phil90 on 2007-04-05
Thanks for the answer I tought they give me the wrong produce 

a difference of 22 Gb is a lot and now that I formatted it to Ext3 there is another 5 gb taken. But anyway its not like i dont have lot of capacity I don't even think i would ever fill it who knows. Now I know that I have the right product 



Bye

---

### Post by Sammi on 2007-04-06
> **phil90 said:**
> Thanks for the answer I tought they give me the wrong produce 

a difference of 22 Gb is a lot and now that I formatted it to Ext3 there is another 5 gb taken. But anyway its not like i dont have lot of capacity I don't even think i would ever fill it who knows. Now I know that I have the right product 



Bye
Those 22 (or 27) gigabytes are still there. You just need to use "the other definition of gigabyte" to get that number.

---

