---
title: "Flash card reader failure"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by cypah on 2007-07-23
I am running 7.04 and have a USB reader attached and was working but after an upgrade of lots of stuff next time I plugged in the card from the camera it fails to pop up the dialog asking if I want to DL the photos. They are .jpg fat32 format. 

I never paid any attention to the name of the icon that used to show on the desk-t so don't know the critters name. this is a mount failure it looks to me but what is the critters name and where does it live?

I ran ....  dmesge

Mon 23 Jul 2007 01:53:27 AM CDT ... 
[   68.652000] Bluetooth: L2CAP socket layer initialized
[   68.728000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[   68.848000] eth0: no IPv6 routers present
[   68.852000] usb 1-1: device descriptor read/64, error -71
[   69.076000] usb 1-1: device descriptor read/64, error -71
[   69.292000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[   69.412000] usb 1-1: device descriptor read/64, error -71
[   69.636000] usb 1-1: device descriptor read/64, error -71
[   69.852000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[   70.260000] usb 1-1: device not accepting address 8, error -71
[   70.372000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[   70.780000] usb 1-1: device not accepting address 9, error -71
[   70.828000] Bluetooth: RFCOMM socket layer initialized
[   70.828000] Bluetooth: RFCOMM TTY layer initialized

I don't have a clue what this means but looks strange for it to appear in the middle of loading Bluetooth but .... maybe ok

back on the 19th I ran this:


 more -f /var/log/messages
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.360000] uhci_hcd 0000:00:07.2: UHCI Host Controller
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.360000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.360000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001440
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.364000] usb usb1: configuration #1 chosen from 1 choice
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.364000] hub 1-0:1.0: USB hub found
..........
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.708000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Jul 19 07:51:05 Aelf-FarieForge kernel: [   11.912000] Attempting manual resume
Jul 19 07:51:05 Aelf-FarieForge kernel: [   12.028000] kjournald starting.  Commit interval 5 seconds
Jul 19 07:51:05 Aelf-FarieForge kernel: [   12.028000] EXT3-fs: mounted filesystem with ordered data mode.
Jul 19 07:51:05 Aelf-FarieForge kernel: [   12.272000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Jul 19 07:51:05 Aelf-FarieForge kernel: [   12.832000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Jul 19 07:51:05 Aelf-FarieForge kernel: [   13.352000] usb 1-2: new full speed USB device using uhci_hcd and address 5

Also I found out that this motherboard is Intel with VIA and that means it uses uhci but I don't know what that means and I see that the last line
[   13.352000] usb 1-2: new full speed USB device using uhci_hcd and address 5
has  uhci_hcd I think this may be the critters name but address 5 is a mystery could critter name  maybe be simply hcd5?

I have all this information but I cannot figure out what to do to restore this card reader so that it will once again work. Hope I have given enough so that if someone can see what happened and how to correct it so i can understand and learn it will be greatly appreciated sit there and wait till I insert a card and pop up the dialog to transfer the photos, I use it a lot 

I think at this point remounting this thing is what is needed but I can't figure out how to do itJ
Thanks cypah

---

### Post by cypah on 2007-07-24
Hmmmmm it's been almost 24hrs can't someone please sort me out? I am really nervous using the xterminal.
Thanks cypah

---

