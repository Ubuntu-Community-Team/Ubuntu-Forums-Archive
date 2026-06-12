---
title: "usb mp3 player seen as hardware but not as drive"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by DWE on 2007-07-22
I just bought a Samsung YP-U3 MP3 Player (1gb flash)

Plugged it in, and Ubuntu 7.04 sees it in Hardware Information, but does not recognise it as a drive.

Here's waht lsmod has to say about it

*-usb UNCLAIMED 
                   description: Generic USB device 
                   product: Samsung YP-U3 
                   vendor: Samsung Electronics 
                   physical id: 1 
                   bus info: usb@1:1 
                   version: 2.20 
                   serial: CBBBF762AFF00000 
                   capabilities: usb-2.00 
                   configuration: maxpower=500mA speed=12.0MB/s 

and here's what tail -f /var/log/messages has to say before and after plugging in
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.590740] end_request: I/O error, dev hdd, sector 4 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.594274] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.596433] end_request: I/O error, dev hdd, sector 0 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.598669] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.600819] end_request: I/O error, dev hdd, sector 4 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.603362] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.605513] end_request: I/O error, dev hdd, sector 0 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.607754] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.609907] end_request: I/O error, dev hdd, sector 4 
Jul 22 04:33:26 maggie-desktop kernel: [ 4021.517992] usb 1-1: USB disconnect, address 2 
Jul 22 04:34:25 maggie-desktop kernel: [ 4079.713179] usb 2-1: new full speed USB device using ohci_hcd and address 2 
Jul 22 04:34:25 maggie-desktop kernel: [ 4079.929230] usb 2-1: configuration #1 chosen from 1 choice 

I am assuming that the Samsung needs formatting before Ubuntu will recognise it as a drive. I don't use Windows, only Ubuntu. So.... how do I format it? (if thats the problem?)

Thanx in advance

---

### Post by Daveth on 2007-07-22
not a solution but it might take you further..

[https://answers.launchpad.net/ubuntu/+question/9427](https://answers.launchpad.net/ubuntu/+question/9427)

---

### Post by ugm6hr on 2007-07-25
I believe I have read somewhere that Samsung U3 players will only allow file transfers with their own software, which requires Windows :(

You might be out of luck with that...

---

### Post by Damanther on 2007-07-25
Go the the samsung.com/uk site and download the european version of the firmware. 

I did that for my YP-U2J and it works like a charm. Shows up as a mounded usb disk, plays ogg files and everything.

If the uk site doesn't have a model close enough to yours, try the /au site.

PS, you have to have a windows machine to run the frirmware installer though :(
It might work under wine but I haven't tried that.

Damanther

---

