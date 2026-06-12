---
title: "Using External Harddrive"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by DasMatts on 2007-05-28
Hello Everyone,

I am new to Ubuntu and have forgotten my Bible ( I am currently doing research in the US). I have purchased a external hard drive and I cannot figure out how to save to it. I am using Feisty Fawn on my IBM T40. 

Thanks for your help everyone. 

Matt

I also must say, I am very new to Ubuntu but love it. All the extra work and steps that have to be taken is well worth having complete control over my computer and getting Bill Gates that much more out of my life!

---

### Post by taurus on 2007-05-28
What filesystem is that external harddrive?  Post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by DasMatts on 2007-05-28
I put that into my system, but i don't know how to access the external hard drive. It is recently formatted and there is nothing on it. Here are the results of the command:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4294    34491523+  83  Linux
/dev/sda2            4295        4484     1526175    5  Extended
/dev/sda5            4295        4484     1526143+  82  Linux swap / Solaris

I hope this helps.

Cheers, 

Matt

---

### Post by taurus on 2007-05-28
Are you sure the drive is plugged in and turned on because it doesn't show up on the list of devices at all?

What's the output of this command from a terminal then?

```
dmesg | tail
```

---

### Post by DasMatts on 2007-05-28
Hey, 

I re-did the first command and got this:

Disk /dev/sda: 40.0 GB, 40007761920 bytes

255 heads, 63 sectors/track, 4864 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        4294    34491523+  83  Linux

/dev/sda2            4295        4484     1526175    5  Extended

/dev/sda5            4295        4484     1526143+  82  Linux swap / Solaris


I then entered the second command and this poped up.

[ 3525.952000] usb 4-4: new high speed USB device using ehci_hcd and address 77

[ 3526.456000] usb 4-4: new high speed USB device using ehci_hcd and address 78

[ 3526.716000] ehci_hcd 0000:00:1d.7: port 4 reset error -110

[ 3526.716000] hub 4-0:1.0: hub_port_status failed (err = -32)

[ 3527.968000] usb 4-4: new high speed USB device using ehci_hcd and address 81

[ 3528.472000] usb 4-4: new high speed USB device using ehci_hcd and address 82

[ 3529.228000] usb 4-4: new high speed USB device using ehci_hcd and address 84

[ 3534.016000] usb 4-4: new high speed USB device using ehci_hcd and address 102

[ 3534.276000] ehci_hcd 0000:00:1d.7: port 4 reset error -110

[ 3534.276000] hub 4-0:1.0: hub_port_status failed (err = -32)


My external is now showing up on my desktop, it took about 3 minutes for it to show. This may have been the problem.

Cheers, 

Matt

---

### Post by DasMatts on 2007-06-04
Hello again, 

I am again having trouble mounting my external hard drive. I went though the same steps as last time and yet i am getting no results. Any ideas?

Matt

---

