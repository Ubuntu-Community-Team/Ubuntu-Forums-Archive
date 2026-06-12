---
title: "Problems in getting PPC syncing via Multisync"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by dafreak on 2007-06-23
Ok folks I'm at wits end trying to get my Dell Axim X30 to sync via multisync. I have followed all of the directions on the SynCE website and I still can not get the PDA to sync. I'll post all of the information that I can think of, let me know if any additional information is needed and I'll post it. 

So here's a rundown of all the info:

dmesg output:

[194654.032461] ipaq 3-2:1.0: device disconnected
[194659.303458] usb 3-2: new full speed USB device using uhci_hcd and address 61
[194659.453407] usb 3-2: configuration #1 chosen from 1 choice
[194659.456382] ipaq 3-2:1.0: PocketPC PDA converter detected
[194659.458689] usb 3-2: PocketPC PDA converter now attached to ttyUSB0

I have done a sudo synce-serial-config /dev/ttyUSB0 and get:

You can now run synce-serial-start to start a serial connection.

So I then do a sudo synce-serial-start and get:

synce-serial-start is now waiting for your device to connect.

All is going well it seems so I decide to use one of the tools to test out the connection a bit and thats where I get the indication that something is not right. I do a synce-pstatus and get:

synce-pstatus: Could not find configuration at path '(Default)'

I have searched all over the forums for folks with the same error message but have not seen a solution posted yet although it is possible I missed it. I've tried doing a google search with the same results. Does anybody have any ideas what I'm doing wrong? If you need any additional info I will provide it.

---

### Post by ffoletti on 2007-06-25
well, I have a Dell Axim X30, I sync appointments and contacts through synce, multisync and evolution, but I've never been able to get synce-pstatus do anything...
so I can confirm that pstatus gives me something wrong, but for me it's not a big problem, I can do all I need... did you managed in syncing?

---

