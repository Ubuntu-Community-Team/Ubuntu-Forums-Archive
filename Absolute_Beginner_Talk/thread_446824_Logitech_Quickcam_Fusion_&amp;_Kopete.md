---
title: "Logitech Quickcam Fusion &amp; Kopete"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Hjaltlander on 2007-05-17
Hi,

I just reinstalled Ubuntu 7.04, and I am trying to get my webcam to work, using Kopete.

I have managed to view another persons webcam, no problem, but if i launch my one all i get is a green screen. So I figure I need to set it up, some people have had problems with there Logitech Quickcam Fusion, but I am hopefull someone will be able to point me in the correct direction, to solve this problem?

Regards, Hjaltlander

---

### Post by Tripletaco on 2007-05-18
I've been wanting to get my Logitech Fusion to work too.  The directions on this forum are just too complicated or not quite step-by-step enough for me.  Good luck.  Maybe this will bump this thread a bit.  I could use some help too.  I am not sure how to compile when that is called for.  Maybe on feisty that is automatic...I don't know.  I'm learning.  Just takes time for me.

---

### Post by Vantskruv on 2007-05-20
I have the same problems. I'm using Wengo and I also get a green screen when testing the camera in the application. I'm using Kubuntu Feisty and I've downloaded, compiled and installed UVC from [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)

When typing dmesg in Konsole I get this:

[PHP][18100.482537] usb 4-5: new high speed USB device using ehci_hcd and address 4
[18100.796120] usb 4-5: configuration #1 chosen from 1 choice
[18101.039227] Linux video capture interface: v2.00
[18101.097235] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[18101.110825] usbcore: registered new interface driver uvcvideo
[18101.111112] USB Video Class driver (v0.1.0)
[18102.185217] 4:3:3: cannot set freq 16000 to ep 0x86
[18104.185912] usbcore: registered new interface driver snd-usb-audio
[18255.403831] uvcvideo: Failed to query (129) UVC control 9 (unit 2) : -32 (exp. 2).
[18255.427815] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
[18265.595079] uvcvideo: Failed to query (131) UVC control 7 (unit 2) : -32 (exp. 2).
[19058.388923] hda: tray open
[19058.389388] end_request: I/O error, dev hda, sector 0
[19058.389392] Buffer I/O error on device hda, logical block 0
[19058.389396] Buffer I/O error on device hda, logical block 1
[19058.389399] Buffer I/O error on device hda, logical block 2
[19058.389401] Buffer I/O error on device hda, logical block 3
[19058.389404] Buffer I/O error on device hda, logical block 4
[19058.389406] Buffer I/O error on device hda, logical block 5
[19058.389408] Buffer I/O error on device hda, logical block 6
[19058.389410] Buffer I/O error on device hda, logical block 7
[19058.390933] hda: tray open
[19058.391421] end_request: I/O error, dev hda, sector 0
[19058.391424] Buffer I/O error on device hda, logical block 0
[19058.391761] hda: tray open
[19058.392384] end_request: I/O error, dev hda, sector 4
[19058.392387] Buffer I/O error on device hda, logical block 1
[19058.413081] floppy0: disk absent or changed during operation
[19058.413087] end_request: I/O error, dev fd0, sector 0
[19058.413494] floppy0: disk absent or changed during operation
[19058.413497] end_request: I/O error, dev fd0, sector 0
[19098.045996] hda: tray open
[19098.046479] end_request: I/O error, dev hda, sector 0
[19098.046483] printk: 2 messages suppressed.
[19098.046486] Buffer I/O error on device hda, logical block 0
[19098.046836] hda: tray open
[19098.047432] end_request: I/O error, dev hda, sector 4
[19098.047435] Buffer I/O error on device hda, logical block 1
[19098.047438] Buffer I/O error on device hda, logical block 2
[19098.047441] Buffer I/O error on device hda, logical block 3
[19098.047443] Buffer I/O error on device hda, logical block 4
[19098.047446] Buffer I/O error on device hda, logical block 5
[19098.047448] Buffer I/O error on device hda, logical block 6
[19098.048730] hda: tray open
[19098.049210] end_request: I/O error, dev hda, sector 0
[19098.049549] hda: tray open
[19098.050174] end_request: I/O error, dev hda, sector 4
[19098.070762] floppy0: disk absent or changed during operation
[19098.070767] end_request: I/O error, dev fd0, sector 0
[19098.071044] floppy0: disk absent or changed during operation
[19098.071046] end_request: I/O error, dev fd0, sector 0
[19173.937098] usb 4-5: USB disconnect, address 4
[19176.398941] usb 4-6: new high speed USB device using ehci_hcd and address 5
[19176.708651] usb 4-6: configuration #1 chosen from 1 choice
[19176.708846] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[19177.721918] 5:3:3: cannot set freq 16000 to ep 0x86
[19197.628680] uvcvideo: Failed to query (135) UVC control 3 (unit 2) : -32 (exp. 2).
[19197.957663] uvcvideo: Failed to query (135) UVC control 9 (unit 2) : -32 (exp. 2).
[19197.967780] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
[19197.971526] uvcvideo: Failed to query (135) UVC control 2 (unit 2) : -32 (exp. 2).
[19197.974023] uvcvideo: Failed to query (135) UVC control 3 (unit 2) : -32 (exp. 2).
[19198.276158] uvcvideo: Failed to query (135) UVC control 7 (unit 2) : -110 (exp. 2).
[19202.370797] uvcvideo: Failed to query (131) UVC control 3 (unit 2) : -32 (exp. 2).
[19202.598613] uvcvideo: Failed to query (131) UVC control 9 (unit 2) : -32 (exp. 2).
[20957.839976] uvcvideo: Failed to query (131) UVC control 1 (unit 0) : -32 (exp. 26).
[21103.734449] usb 4-6: USB disconnect, address 5
[21138.448277] usb 4-6: new high speed USB device using ehci_hcd and address 6
[21138.761639] usb 4-6: configuration #1 chosen from 1 choice
[21138.761836] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[21139.775288] 6:3:3: cannot set freq 16000 to ep 0x86
[21231.120154] usb 4-6: USB disconnect, address 6
[21247.210159] usb 4-6: new high speed USB device using ehci_hcd and address 7
[21247.523780] usb 4-6: configuration #1 chosen from 1 choice
[21247.523984] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[21248.537180] 7:3:3: cannot set freq 16000 to ep 0x86
[21272.145653] uvcvideo: Failed to query (130) UVC control 2 (unit 2) : -32 (exp. 2).[/PHP]

---

### Post by strungoutfan78 on 2007-06-22
The problem with these webcams is that they are run by the uvcvideo driver, which in turn utilizes the **v4l2** module instead of **v4l**.  Kopete I know for sure does not support v4l2 yet.  I believe it is proposed as part of KDE4.  As far as Wengo goes, I think it's the same story, as I stumbled on this post while trying to figure out why I couldn't get my Logitech webcam to work with it.  I'm pretty sure this info is accurate, but I'm sure similar info has been posted all around these forums, as I've beaten my head against the wall on this issue as well, so maybe search around a little more to make sure I'm not completely wrong about this.

---

