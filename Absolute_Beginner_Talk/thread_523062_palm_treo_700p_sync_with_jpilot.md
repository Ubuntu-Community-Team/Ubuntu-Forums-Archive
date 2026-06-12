---
title: "palm treo 700p sync with jpilot"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2007-08-11
Hi ,

Palm treo 700p connected via usb. ubuntu 7.04.

when trying to sync with jpilot, i get the following:

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

What do I do?

---

### Post by Pragmatist on 2007-08-11
Have you read this yet?
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

---

### Post by Harry789 on 2007-08-14
Wow, this great help, thanx.

However I am not allowed to save changes to the file - how come?

---

### Post by Pragmatist on 2007-08-14
> **Harry789 said:**
> ....I am not allowed to save changes to [SIZE=2]**the file**[/SIZE] - how come?
Which file?  Did you use sudo or gksudo?

---

### Post by Harry789 on 2007-08-14
Ok completed instructions and everything went well, but it is still not syncing.

I no longer get an error message but it just does not connect.

Here is the output from jpilot when pressing the sync button:

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
I press the hotsync on the palm and after 2 minutes of waiting the palm goes back to say that no connection was established.

where should i look for errors?

---

### Post by Pragmatist on 2007-08-15
Here are some things I would try:

1.) Press hotsync on the Treo first (Not the cradle, but the hotsync application within the Treo), then wait 2 or 3 seconds, and then press hotsync on Jpilot.
 This order, and the pause, are often important workarounds.

2.) Try this in a terminal:
(a) Disconnect your Treo
(b) Type this:
```
tail -f /var/log/messages
```
(c) Plug the Treo in and watch for messages in the terminal.  Your looking for things like: ttyUSB1 or ttyUSB3 or ttyUSB5 and so on.  If you don't get that, then post what you do get and we will take it from there.

---

### Post by cinematography on 2007-08-23
Thank you for the tips! It fixed my syncing problem.

---

### Post by angelogladding on 2007-11-15
Hi I too am attempting to sync my Treo 700p with J-Pilot on Ubuntu (Gutsy). I've tried multiple orders of initiating the HotSync. I followed the advice of initiating from the Treo's HotSync software, waiting a couple of seconds, and then clicking J-Pilot's HotSync. After a couple of seconds J-Pilot hangs. The entire process looks like this:

```
Nov 15 17:52:07 ki kernel: [ 2767.268000] usb 1-2: new full speed USB device using uhci_hcd and address 20
Nov 15 17:52:08 ki kernel: [ 2767.828000] usb 1-2: new full speed USB device using uhci_hcd and address 21
Nov 15 17:52:09 ki kernel: [ 2768.348000] usb 1-2: new full speed USB device using uhci_hcd and address 22
Nov 15 17:52:45 ki kernel: [ 2804.496000] usb 1-2: new full speed USB device using uhci_hcd and address 23
Nov 15 17:52:45 ki kernel: [ 2804.668000] usb 1-2: configuration #1 chosen from 1 choice
Nov 15 17:52:45 ki kernel: [ 2804.672000] visor 1-2:1.0: Handspring Visor / Palm OS converter detected
Nov 15 17:52:45 ki kernel: [ 2804.672000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Nov 15 17:52:45 ki kernel: [ 2804.672000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Nov 15 17:53:15 ki kernel: [ 2835.116000] ipw2200: Firmware error detected.  Restarting.
```

Thanks for any help,
Angelo

---

### Post by Fisher Warn on 2008-01-02
i am having the same problem, please help me,
Thanks

---

### Post by Pragmatist on 2008-01-02
What device is jpilot looking for? ttyUSB0 ttyUSB1
 
Try putting this for the device    **usb:**
 
You include the colon at the end. What this does is it tells jpilot to look for a usb device. Many people, including myself, have found that this works.
 
Let us know what happens.

---

### Post by MeanderingCode on 2008-01-10
> **Pragmatist said:**
> What device is jpilot looking for? ttyUSB0 ttyUSB1
 
Try putting this for the device    **usb:**
 
...
 
Let us know what happens.

Wow.  I'll have to add myself to the list, using Xubuntu 7.10 and a Palm Treo 700p.
So, so, so much time wasted and sleep missed and it was that simple.  Damn.

---

### Post by jnewm on 2008-02-03
> **Pragmatist said:**
> What device is jpilot looking for? ttyUSB0 ttyUSB1
 
Try putting this for the device    **usb:**
 
You include the colon at the end. What this does is it tells jpilot to look for a usb device. Many people, including myself, have found that this works.
 
Let us know what happens.

Thanks so much!  Same worked for me with a Treo 650.

---

### Post by Samatva on 2008-02-03
On any Palm problems, suspect the factory sync cable. I've had two OEM cables, both have problems. Neither of my third-party cables need anything more than a little wiggle...

Just my 2-cent's worth

---

