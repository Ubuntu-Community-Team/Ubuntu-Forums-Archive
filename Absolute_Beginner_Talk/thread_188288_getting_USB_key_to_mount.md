---
title: "getting USB key to mount?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by bosconermal on 2006-06-03
Hi all:

My experience with Linux is now three days old, so I'm still a little confused.

I have a Maxell USB key that mounted when I booted off the Dapper installation disk, but now that I'm booting off the hard drive, it doesn't mount. In fact the system doesn't seem to see it at all, I think. If I go to System-->Adminstration-->disks, only hard drive, cdrom and floppy show up. If I use lsusb apparently nothing is there.

Any advice?

---

### Post by Sutekh on 2006-06-03
Can you open a Terminal (Applications -> Accessories Menu) and enter this command, which watches for system messages.
```
tail -f /var/log/messages
```
Then plug in your USB.  Can you post the output?

---

### Post by bosconermal on 2006-06-04
Hi and thank you!: A little awkward because I haven't yet got the Internet to work on the Ubuntu box. I did finally get it to recognize my Broadcom wireless card, so I'm moving forward. I'm walking this up on a floppy to my Windows computer to post.

Anyway, on the USB key. I booted up this morning and it mounted but it won't do it again, and I tried both cold and warm reboots.

Here is the output when I insert the key (it counts up to 127 addresses then starts again):

[SIZE="4"][SIZE="3"][SIZE="2"]richard@abulafia:~$ tail -f /var/log/messages
Jun  4 12:47:56 localhost kernel: [4294924.522000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.522000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.523000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.524000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.525000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.526000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.527000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 12:47:56 localhost kernel: [4294924.528000] ieee80211: eth0: IEEE80211_ASSOC_REQ received
Jun  4 13:04:25 localhost -- MARK --
Jun  4 13:24:26 localhost -- MARK --
Jun  4 13:32:48 localhost kernel: [4297616.844000] usb 1-1: new full speed USB device using uhci_hcd and address 47
Jun  4 13:32:49 localhost kernel: [4297617.344000] usb 1-1: new full speed USB device using uhci_hcd and address 48
Jun  4 13:32:49 localhost kernel: [4297617.844000] usb 1-1: new full speed USB device using uhci_hcd and address 49
Jun  4 13:32:50 localhost kernel: [4297618.344000] usb 1-1: new full speed USB device using uhci_hcd and address 50
Jun  4 13:32:50 localhost kernel: [4297618.844000] usb 1-1: new full speed USB device using uhci_hcd and address 51
Jun  4 13:32:51 localhost kernel: [4297619.344000] usb 1-1: new full speed USB device using uhci_hcd and address 52
Jun  4 13:32:51 localhost kernel: [4297619.844000] usb 1-1: new full speed USB device using uhci_hcd and address 53
Jun  4 13:32:52 localhost kernel: [4297620.344000] usb 1-1: new full speed USB device using uhci_hcd and address 54
Jun  4 13:32:52 localhost kernel: [4297620.844000] usb 1-1: new full speed USB device using uhci_hcd and address 55
Jun  4 13:32:53 localhost kernel: [4297621.344000] usb 1-1: new full speed USB device using uhci_hcd and address 56
Jun  4 13:32:53 localhost kernel: [4297621.844000] usb 1-1: new full speed USB device using uhci_hcd and address 57
Jun  4 13:32:54 localhost kernel: [4297622.344000] usb 1-1: new full speed USB device using uhci_hcd and address 58
Jun  4 13:32:54 localhost kernel: [4297622.844000] usb 1-1: new full speed USB device using uhci_hcd and address 59
Jun  4 13:32:55 localhost kernel: [4297623.344000] usb 1-1: new full speed USB device using uhci_hcd and address 60
Jun  4 13:32:55 localhost kernel: [4297623.844000] usb 1-1: new full speed USB device using uhci_hcd and address 61
Jun  4 13:32:56 localhost kernel: [4297624.344000] usb 1-1: new full speed USB device using uhci_hcd and address 62
Jun  4 13:32:56 localhost kernel: [4297624.844000] usb 1-1: new full speed USB device using uhci_hcd and address 63
Jun  4 13:32:57 localhost kernel: [4297625.344000] usb 1-1: new full speed USB device using uhci_hcd and address 64
Jun  4 13:32:57 localhost kernel: [4297625.844000] usb 1-1: new full speed USB device using uhci_hcd and address 65
Jun  4 13:32:58 localhost kernel: [4297626.344000] usb 1-1: new full speed USB device using uhci_hcd and address 66
Jun  4 13:32:58 localhost kernel: [4297626.844000] usb 1-1: new full speed USB device using uhci_hcd and address 67
Jun  4 13:32:59 localhost kernel: [4297627.344000] usb 1-1: new full speed USB device using uhci_hcd and address 68
Jun  4 13:32:59 localhost kernel: [4297627.844000] usb 1-1: new full speed USB device using uhci_hcd and address 69
Jun  4 13:33:00 localhost kernel: [4297628.344000] usb 1-1: new full speed USB device using uhci_hcd and address 70
Jun  4 13:33:00 localhost kernel: [4297628.844000] usb 1-1: new full speed USB device using uhci_hcd and address 71
Jun  4 13:33:01 localhost kernel: [4297629.344000] usb 1-1: new full speed USB device using uhci_hcd and address 72
Jun  4 13:33:01 localhost kernel: [4297629.844000] usb 1-1: new full speed USB device using uhci_hcd and address 73
Jun  4 13:33:02 localhost kernel: [4297630.344000] usb 1-1: new full speed USB device using uhci_hcd and address 74
Jun  4 13:33:02 localhost kernel: [4297630.844000] usb 1-1: new full speed USB device using uhci_hcd and address 75
Jun  4 13:33:03 localhost kernel: [4297631.344000] usb 1-1: new full speed USB device using uhci_hcd and address 76
Jun  4 13:33:03 localhost kernel: [4297631.844000] usb 1-1: new full speed USB device using uhci_hcd and address 77
Jun  4 13:33:04 localhost kernel: [4297632.344000] usb 1-1: new full speed USB device using uhci_hcd and address 78
Jun  4 13:33:04 localhost kernel: [4297632.844000] usb 1-1: new full speed USB device using uhci_hcd and address 79
Jun  4 13:33:05 localhost kernel: [4297633.344000] usb 1-1: new full speed USB device using uhci_hcd and address 80
Jun  4 13:33:05 localhost kernel: [4297633.844000] usb 1-1: new full speed USB device using uhci_hcd and address 81
Jun  4 13:33:06 localhost kernel: [4297634.344000] usb 1-1: new full speed USB device using uhci_hcd and address 82
Jun  4 13:33:06 localhost kernel: [4297634.844000] usb 1-1: new full speed USB device using uhci_hcd and address 83
Jun  4 13:33:07 localhost kernel: [4297635.344000] usb 1-1: new full speed USB device using uhci_hcd and address 84
Jun  4 13:33:07 localhost kernel: [4297635.844000] usb 1-1: new full speed USB device using uhci_hcd and address 85
Jun  4 13:33:08 localhost kernel: [4297636.344000] usb 1-1: new full speed USB device using uhci_hcd and address 86
Jun  4 13:33:08 localhost kernel: [4297636.844000] usb 1-1: new full speed USB device using uhci_hcd and address 87
Jun  4 13:33:09 localhost kernel: [4297637.344000] usb 1-1: new full speed USB device using uhci_hcd and address 88
Jun  4 13:33:09 localhost kernel: [4297637.844000] usb 1-1: new full speed USB device using uhci_hcd and address 89
Jun  4 13:33:10 localhost kernel: [4297638.344000] usb 1-1: new full speed USB device using uhci_hcd and address 90
Jun  4 13:33:10 localhost kernel: [4297638.844000] usb 1-1: new full speed USB device using uhci_hcd and address 91
Jun  4 13:33:11 localhost kernel: [4297639.344000] usb 1-1: new full speed USB device using uhci_hcd and address 92
Jun  4 13:33:11 localhost kernel: [4297639.844000] usb 1-1: new full speed USB device using uhci_hcd and address 93
Jun  4 13:33:12 localhost kernel: [4297640.344000] usb 1-1: new full speed USB device using uhci_hcd and address 94
Jun  4 13:33:12 localhost kernel: [4297640.844000] usb 1-1: new full speed USB device using uhci_hcd and address 95
Jun  4 13:33:13 localhost kernel: [4297641.344000] usb 1-1: new full speed USB device using uhci_hcd and address 96
Jun  4 13:33:13 localhost kernel: [4297641.844000] usb 1-1: new full speed USB device using uhci_hcd and address 97
Jun  4 13:33:14 localhost kernel: [4297642.344000] usb 1-1: new full speed USB device using uhci_hcd and address 98
Jun  4 13:33:14 localhost kernel: [4297642.844000] usb 1-1: new full speed USB device using uhci_hcd and address 99
Jun  4 13:33:15 localhost kernel: [4297643.344000] usb 1-1: new full speed USB device using uhci_hcd and address 100
Jun  4 13:33:15 localhost kernel: [4297643.844000] usb 1-1: new full speed USB device using uhci_hcd and address 101
Jun  4 13:33:16 localhost kernel: [4297644.344000] usb 1-1: new full speed USB device using uhci_hcd and address 102
Jun  4 13:33:16 localhost kernel: [4297644.844000] usb 1-1: new full speed USB device using uhci_hcd and address 103
Jun  4 13:33:17 localhost kernel: [4297645.344000] usb 1-1: new full speed USB device using uhci_hcd and address 104
Jun  4 13:33:17 localhost kernel: [4297645.844000] usb 1-1: new full speed USB device using uhci_hcd and address 105
Jun  4 13:33:18 localhost kernel: [4297646.344000] usb 1-1: new full speed USB device using uhci_hcd and address 106
Jun  4 13:33:18 localhost kernel: [4297646.844000] usb 1-1: new full speed USB device using uhci_hcd and address 107
Jun  4 13:33:19 localhost kernel: [4297647.344000] usb 1-1: new full speed USB device using uhci_hcd and address 108
Jun  4 13:33:19 localhost kernel: [4297647.844000] usb 1-1: new full speed USB device using uhci_hcd and address 109
Jun  4 13:33:20 localhost kernel: [4297648.344000] usb 1-1: new full speed USB device using uhci_hcd and address 110
Jun  4 13:33:20 localhost kernel: [4297648.844000] usb 1-1: new full speed USB device using uhci_hcd and address 111
Jun  4 13:33:21 localhost kernel: [4297649.344000] usb 1-1: new full speed USB device using uhci_hcd and address 112
Jun  4 13:33:21 localhost kernel: [4297649.844000] usb 1-1: new full speed USB device using uhci_hcd and address 113
Jun  4 13:33:22 localhost kernel: [4297650.344000] usb 1-1: new full speed USB device using uhci_hcd and address 114
Jun  4 13:33:22 localhost kernel: [4297650.844000] usb 1-1: new full speed USB device using uhci_hcd and address 115
Jun  4 13:33:23 localhost kernel: [4297651.344000] usb 1-1: new full speed USB device using uhci_hcd and address 116
Jun  4 13:33:23 localhost kernel: [4297651.844000] usb 1-1: new full speed USB device using uhci_hcd and address 117
Jun  4 13:33:24 localhost kernel: [4297652.344000] usb 1-1: new full speed USB device using uhci_hcd and address 118
Jun  4 13:33:24 localhost kernel: [4297652.844000] usb 1-1: new full speed USB device using uhci_hcd and address 119
Jun  4 13:33:25 localhost kernel: [4297653.344000] usb 1-1: new full speed USB device using uhci_hcd and address 120
Jun  4 13:33:25 localhost kernel: [4297653.844000] usb 1-1: new full speed USB device using uhci_hcd and address 121
Jun  4 13:33:26 localhost kernel: [4297654.344000] usb 1-1: new full speed USB device using uhci_hcd and address 122
Jun  4 13:33:26 localhost kernel: [4297654.844000] usb 1-1: new full speed USB device using uhci_hcd and address 123
Jun  4 13:33:27 localhost kernel: [4297655.344000] usb 1-1: new full speed USB device using uhci_hcd and address 124
Jun  4 13:33:27 localhost kernel: [4297655.844000] usb 1-1: new full speed USB device using uhci_hcd and address 125
Jun  4 13:33:28 localhost kernel: [4297656.344000] usb 1-1: new full speed USB device using uhci_hcd and address 126
Jun  4 13:33:28 localhost kernel: [4297656.844000] usb 1-1: new full speed USB device using uhci_hcd and address 127[/SIZE][/SIZE][/SIZE]

---

### Post by grsing on 2006-06-04
I'm not sure how to help on the USB drive, but which tutorials are you following for the Broadcom card?  This one: [http://www.ubuntuforums.org/showthread.php?t=185174&](http://www.ubuntuforums.org/showthread.php?t=185174&) is the only one I've found to work, after far too many hours of testing (unfortunately, if you've alreday been messing with the wireless, it's probably easier to reinstall and start from scratch, since many of the different suggested settings conflict).  Hope that helps, and at least makes it easier for you to post any more error messages on this problem.

---

### Post by bosconermal on 2006-06-04
I looked at that tutorial and spent an inordinate time trying to get it to work, but to no avail. I could never find fwcutter, etc. In the end I used an another driver that I found referenced in some tutorial and it worked. The card now finds  two wireless networks. I'm now trying to install network manager so I can choose one of them.

The driver I used is: bcm43xx-firmware_1.1-0ubuntu1_all.deb Worked like a charm with far less trouble.

---

### Post by joshrobinson on 2006-06-04
just remeber that the bcm43xx driver doesnt run at its full speed, im pretty sure it can only run at 11mbps.. so file transfers between computers will be slower then normal

---

### Post by grsing on 2006-06-04
Sure beats the speed of running up and down stairs with a floppy :)

---

### Post by grsing on 2006-06-04
As long as you found one that works, that's what matters.  Sometimes I think it's almost random which solution will work for which person.

---

### Post by Caligula on 2006-06-04
by saying "USB key" I assume you mean a usb drive? if not ignore the rest...

mounting it is pretty simple, though i only learnt it today... I was stuck on how to access my usb drive in the terminal until now... so here goes..

```
sudo mkdir /mnt/usbkey
```

that will create a directory where you can mount the drive into.

```
mount /dev/sda1 /mnt/usbkey
```

now just go there!
```
cd /mnt/usbkey
```

see if it's there
```
ls
```

worked for me...

instructions are from [here]("http://ldots.org/prodrive/")

please somebodt correct me if I'm wrong on something

---

### Post by bosconermal on 2006-06-04
I'm working on an old machine with Ubuntu, so the USB ports are in the back. I bought a USB hub so I don't have to crawl on my back under a desk to get to it. So far, with the USB hub attached, the USB drive mounts no problem. I'll see if it lasts.

I also now have the Internet running, and the speed is not too terrible. Ubuntu-wise, I am having a good day.

My next trick is to get printing to work. I may be back to you.

Thank you all for your help!

---

