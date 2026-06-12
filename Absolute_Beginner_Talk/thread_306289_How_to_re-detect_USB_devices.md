---
title: "How to re-detect USB devices?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by wrybread on 2006-11-24
I have a USB audio card on my laptop, and I remove it when walking around, but re-insert it when I want audio. Ubuntu 6.10 does a great job of detecting it if I reboot, and sometimes it detects it when I re-insert it, but it generally doesn't.

Is there some command I can invoke to get Ubuntu to redetect hardware devices?

Thanks for the help.

---

### Post by taurus on 2006-11-24
After you reinsert it, look in dmesg to see what it is and mount it from a terminal, Applications -> Accessories -> Terminal.

```
dmesg | tail
sudo mkdir /media/usb
sudo mount -t vfat /dev/sda1 /media/usb
(assuming it's /dev/sda1...)
```

---

### Post by wrybread on 2006-11-24
Thanks for the quick reply. It's not working, but I think I just don't know what it's called. Here's what just happened:

wrybread@boofus:~$ dmesg | tail
[17190486.740000] hdc: tray open
[17190486.740000] end_request: I/O error, dev hdc, sector 834220
[17190486.740000] Buffer I/O error on device hdc, logical block 208555
[17190486.816000] hdc: tray open
[17190486.816000] end_request: I/O error, dev hdc, sector 834224
[17190486.816000] Buffer I/O error on device hdc, logical block 208556
[17190487.780000] VFS: busy inodes on changed media.
[17191116.752000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[17191769.516000] ipw2100: Fatal interrupt. Scheduling firmware restart.
[17192028.908000] usb 1-1: USB disconnect, address 2
wrybread@boofus:~$ sudo mkdir /media/usbaudio
wrybread@boofus:~$ sudo mount -t vfat /dev/sda1 /media/usbaudio
mount: special device /dev/sda1 does not exist
wrybread@boofus:~$ sudo mount -t vfat /dev/ipw2100 /media/usbaudio
mount: special device /dev/ipw2100 does not exist

Can you tell what the USB audio device is called from the output of dmesg | tail?

---

### Post by wrybread on 2006-11-24
Whoops, looks like ipw2100 refers to my wifi card.

---

### Post by taurus on 2006-11-24
Did you insert that USB audio device into a USB port?

---

### Post by po0f on 2006-11-24
wrybread,

Unplug your audio card.  From a terminal, type the following command and replug it in:
```
$ tail -f /var/log/messages
```
Post the output, and what kind of card it is as well.

---

### Post by wrybread on 2006-11-24
Interesting, nothing shows up when I connect it. 

The card is some cheepy USB audio card I got on ebay for $5. Am I stuck with a reboot, or is there some command I can invoke to force it to poll the USB?

---

### Post by po0f on 2006-11-24
wrybread,

If nothing shows up in /var/log/messages when you reconnect it, the kernel doesn't know about it.  (/var/log/messages is pretty much a kernel log.)  I guess the only way of making sure you have audio is to keep it plugged in when you want to hear something.

When you do go to reboot, look through the output of `lsmod` and try to figure out what module is the driver for your sound card.  After doing `tail -f /var/log/messages`, unplug it to see if the module is removed.  If it is, try replugging it and modprobe'ing the module.

[EDIT]

I guess an alternative would be to restart udev, might not work though:
```
$ sudo /etc/init.d/udev restart
```

---

### Post by wrybread on 2006-11-24
Well this didn't do anything:

```
sudo /etc/init.d/udev restart

```

Rebooting worked though. And furthermore rebooting made it so I can now disconnect and reconnect the device at will. Here's what I now get in dmesg when I disconnect/reconnect it (with my comments added):

```

# DISCONNECTED
Nov 24 20:52:59 boofus kernel: [17180319.432000] usb 1-1: USB disconnect, address 5
# RECONNECTED
Nov 24 20:53:04 boofus kernel: [17180323.956000] usb 1-1: new full speed USB device using uhci_hcd and address 6
Nov 24 20:53:04 boofus kernel: [17180324.116000] usb 1-1: configuration #1 chosen from 1 choice
Nov 24 20:53:04 boofus kernel: [17180324.200000] input: C-Media USB Headphone Set   as /class/input/input5
Nov 24 20:53:04 boofus kernel: [17180324.200000] input: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.0-1

```

So am I understanding this correctly: it's being mounted as /class/input/input5? So in theory this could mount it if the problem returns:

```

sudo mkdir /media/usbaudio
sudo mount -t vfat /class/input/input5 /media/usbaudio

```

Here's the output of dmesg | grep usb right after a reboot if anyone's curious. And thanks for the help on this, I'm mostly using the experience to learn about working with hardware in Linux.

```
wrybread@boofus:~$ dmesg | grep USB
[17179575.912000] USB Universal Host Controller Interface driver v3.0
[17179575.912000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.912000] hub 1-0:1.0: USB hub found
[17179576.016000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.016000] hub 2-0:1.0: USB hub found
[17179576.120000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.120000] hub 3-0:1.0: USB hub found
[17179576.244000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179576.248000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.248000] hub 4-0:1.0: USB hub found
[17179576.256000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179577.012000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179588.644000] input: C-Media USB Headphone Set   as /class/input/input2
[17179588.644000] input: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.0-1
[17179588.644000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
wrybread@boofus:~$ 


```

---

