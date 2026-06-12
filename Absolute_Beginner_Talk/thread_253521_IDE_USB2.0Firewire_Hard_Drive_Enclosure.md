---
title: "IDE USB2.0/Firewire Hard Drive Enclosure"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-09-08
I wanted to put a hard drive to use so I installed it to a firewire usb enclosure. The disk is in NTFS format one partition. I can read and write from windows xp  with either interface. When I used knoppix and turned it on with USB I can see a mass storage device in scsi controllers by prolific. I cannot find the drive to mount it read only. Firewire does not read at all in either Ubuntu 6.06 or Knoppix 5. 
Is there some code I must install in order to read from a hard disk mounted externally? This is surprising most of the time Ubuntu finds hardware no problem.
Kiheikev

---

### Post by gn2 on 2006-09-08
Is this an enclosure with both Firewire and USB connectors?

If it is perhaps try USB option?

I have a Raidsonic IcyBox and it works fine on USB, as does my Conico 2.5" drive enclosure, also USB.

---

### Post by keheikev on 2006-09-08
It is one with both interfaces. Firewire isnt recognized at all but the USB does show up in sys admin/device manager as the below. I cannot see the drive though just the usb 2.0 mass storage device interface from Prolific inc. Also the thing wont come to rest the read light is on so I have to shut down to turn it off. The enclosure is a KINGWIN. I called their tech support and they said that Linux would not be able to see an NTFS partition (well I know thats bull)
So you are having no problem with a fat32 or NTFS patitioned hard drive with usb 2.0?
 Its really funny as my compact flash drive reader is picked up no problem. The Kingwin under windows was quite balky for firewire. I had to access it with usb2.0 and I named the volume before it would start working with win xp he. Even then it didnt come up with a firewire icon.
Kiheikev
Iwill try the dmsg command and see what that comes up with.
Kevin:cool:

---

### Post by keheikev on 2006-09-08
Er that was dmeg here are the last 20 lines or so of the output....
7190089.700000] sd 0:0:0:0: SCSI error: return code = 0x50000
[17190089.700000] end_request: I/O error, dev sda, sector 39840961
[17190089.700000] Buffer I/O error on device sda1, logical block 39840898
[17190119.812000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190150.056000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190180.300000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190210.544000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190240.788000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190240.920000] sd 0:0:0:0: SCSI error: return code = 0x50000
[17190240.920000] end_request: I/O error, dev sda, sector 39840962
[17190240.920000] Buffer I/O error on device sda1, logical block 39840899
[17190271.032000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190301.276000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190331.520000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190361.764000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190392.008000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190392.140000] sd 0:0:0:0: SCSI error: return code = 0x50000
[17190392.140000] end_request: I/O error, dev sda, sector 39840963
[17190392.140000] Buffer I/O error on device sda1, logical block 39840900
[17190422.252000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190452.496000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190482.740000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190512.984000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190543.228000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190543.360000] sd 0:0:0:0: SCSI error: return code = 0x50000
[17190543.360000] end_request: I/O error, dev sda, sector 39840964
[17190543.360000] Buffer I/O error on device sda1, logical block 39840901
[17190543.364000] sda: Current: sense key: No Sense
[17190543.364000]     Additional sense: No additional sense information
[17190573.476000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190603.720000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190633.964000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190664.208000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190694.452000] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[17190694.584000] sd 0:0:0:0: SCSI error: return code = 0x50000
[17190694.584000] end_request: I/O error, dev sda, sector 39851520
[17190694.584000] Buffer I/O error on device sda, logical block 4981440
One thing that is funny is there are a icons still in device manager for the unplugged compact flash drive and others I have a jump drive too.
Kevin

---

### Post by gn2 on 2006-09-08
To answer your question, I have tried a few IDE hard drives in both my laptop and desktop sized USB enclosures, but I don't have any Fat32 partitions, only NTFS and ext2. All work OK.
Not sure, but think there could be difficulties with Sata drive names clashing with USB. I'm a new Linux user and still struggling a bit....

---

### Post by keheikev on 2006-09-09
Well all of us are struggling a bit but it does have its rewards. Anyway I am thinking the thing is just broke or not compatible at the least. It should be detected faster (windows explorer drags forever to detect the new drive) and have a firewire birdie in the systray. I wanted both interfaces as I knew one was faster. I decided to let tigerdirect send an exchange in order to see if its the kingwin or my system. From what you say the things which are really simple should just plain work if the computer has either or both USB 2.0 or firewire in regardless of the Operating system (xp,2000,linux, OS 9,10).
:D 
Kiheikev
Aloha!

---

### Post by YeahBuntu on 2006-09-09
Just to be sure.. is this an IDE drive or an SATA drive with an IDE changeover?

If it is an SATA drive and you have a free SATA connector on your motherboard you may want to try this enclosure.  I have [this one]("http://www.directron.com/kh350sebk.html") runing over at my parents for backup.  Because I really hate going over there and fixing every little thing they break.  I just have run a backup whenever I'm there and things are still ' working ok ' 

Anyway I have not tried yet to see if Ubuntu can see it.  I can pop over there tomorrow and report my findings with the Live CD. 

Cheers.

---

### Post by keheikev on 2006-09-09
Well its just a plain old IDE seagate drive. It works really well on the ide interface. Say I thought I should invite you over to my linux newsgroup at [www.annexcafe.com](www.annexcafe.com) general.linux2linux. 
Let me know if your sata drive is seen in ubuntu in the enclosure.
Kevin

---

