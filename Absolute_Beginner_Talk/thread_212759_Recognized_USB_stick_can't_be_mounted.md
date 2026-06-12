---
title: "Recognized USB stick can't be mounted"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by yikes on 2006-07-10
Hi there, 
I bought a secondhand notebook and it has Ubuntu Breezy Badger installed on it. 

I plugged in my Pendrive USB stick and used a program called 'Kfind' to see if I could see the files on it. 
In Kfind's 'Select Folder' window I see my USB stick listed, but clicking on its name results in the following message:

[I]Could not mount device.
The reported error was:
mount can't find /dev/sta1 in 
/etc/fstab or /etc/mtab[/I]

I checked for a /sta1 in /dev/ and for a /mtab in /etc/ but both do not exist.
Should I create these two and is that a common Linux user's routine or am I to expect more troubles if I do?

BTW, the Ubuntu is a clean install and I haven't changed anything on it.

Thanks in advance

---

### Post by taurus on 2006-07-10
Open a terminal and see which device the system thinks your USB stick is...
```

dmesg

```
It's probably something like /dev/sda1, /dev/sda2, /dev/sda3, or /dev/sda4...

---

### Post by yikes on 2006-07-10
Thanks, I did that but nowhere in the Terminal's results is any mention of dev/sda[...]. 
Whan searching for sda1, sda2, sda3 or sda4, I find that they don't exist and looking in my dev folder there is no 'sda' combined with any number.

---

### Post by taurus on 2006-07-10
Let me get this right.  You insert the USB stick into a USB slot and "dmesg" doesn't say anything about your USB stick at the end!!!

---

### Post by yikes on 2006-07-10
I didn't say it didn't say anything about my USB stick, it just didn't say anything that indicated which device the system thinks my USB stick is. Of course I first used your clue in the form of /dev/sda1, /dev/sda2, /dev/sda3, or /dev/sda4. After that, I looked for any other indications in the Terminal's results, with no results.

Additional info on my hardware: it's a notebook that has its own USB port which does not work. I bought a new and unused dock for it which has its own USB port, and naturally used the dock's port for my USB stick.

The Terminal's info says:
 
[I]hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
hub 1-0:1.0: over-current change on port 2
usb 1-2: new full speed USB device using uhci_hcd and adress 2[/i]

Then goes on (somewhere later) about the USB mass storage driver and says:
usb_device found at 2

Hope this is of any use to you,

Cheers

---

### Post by yikes on 2006-07-12
Never mind, I kicked Ubuntu off my notebook and replaced it with BeOS :cool:

---

