---
title: "USB not visible?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ains on 2007-09-08
Greets :)
I have a hifi that connects via USB but when hooked up the USB device doesn't seem to appear at all. 
I did the command: sudo tail -f /var/log/messages
and got:
```

Sep  9 01:53:57 aindow kernel: [ 1962.658181] usb 1-1: new full speed USB device using uhci_hcd and address 7
Sep  9 01:53:57 aindow kernel: [ 1962.863022] usb 1-1: configuration #1 chosen from 1 choice
Sep  9 01:53:57 aindow kernel: [ 1962.958817] input: Philips Philips Audio Set as /class/input/input11
Sep  9 01:53:57 aindow kernel: [ 1962.958850] input: USB HID v1.00 Device [Philips Philips Audio Set] on usb-0000:00:10.0-1
Sep  9 01:53:58 aindow kernel: [ 1963.437858] end_request: I/O error, dev fd0, sector 0
Sep  9 01:54:10 aindow kernel: [ 1975.583120] end_request: I/O error, dev fd0, sector 0

```

don't know the relevance of those last 2 but they keep coming up.
so it's seeing that it's connected right? but i can't find anyway to get to it. 
I'm trying to get it to work on VMware windows xp also but it doesn't come up with new device etc.
I'm completely crap with computers so help is really appreciated..

edit: seems it's not picking up any of my usb devices in vmware or ubuntu since i tried some others...

thanks
ains

---

