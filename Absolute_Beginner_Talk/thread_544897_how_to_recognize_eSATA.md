---
title: "how to recognize eSATA"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-06
someone else had this problem two weeks ago and didn't get any response; I hope that I do better (if so I promise to share what I learn with the other guy!)

I am just getting started with Linux.  I installed a PCI eSATA card, popped it into the back of the case and plugged it into the motherboard SATA port.

however, when I try to start the computer at that point, it just freezes at the first screen - won't do anything!

when I power down the eSATA drive, it starts as normal.  But then, when I power the eSATA drive back on, it doesn't find it at all. Nothing happens.  I can't figure out how to tell the system that the drive is there!

What to do?  I'm used to Mac OS X, where the system can generally find the drive, even if it can't read or write to it or mount it.

Help - any suggestions??

willfriedwald

---

### Post by bobpur on 2007-09-06
I installed a PCI eSATA card, popped it into the back of the case and plugged it into the motherboard SATA port.

I had a problem with this line in your message. I take it to mean that you installed the card in the PCI slot that it is suppose to mount in AND plugged it into the motherboard SATA port????  If your SATA card has internal ports they are to plug SATA Drives into NOT to connect to the motherboard. You already done that through the PCI slot.  I don't know what effect that would have on your computer; but, it can't be good.
I went to www. newegg.com and read some of the reviews on different SATA Cards and your problem (Assuming it is connected correctly) is not unheard of. I don't know about Linux.
Is it formatted to FAT 32 so linux and Windows can, both, read it?

---

### Post by willfriedwald on 2007-09-07
thank you!


My bad! the set up is more like Mac than I realized.

The PCI - SATA card that I was using has an internal cable on the other end, so I assumed that it was supposed to be plugged in to one of the empty SATA ports on the motherboard.


so I will unplug it from the SATA port, as you say, the PCI card is already connected to the board.

I formatted the drive itself in UNIX on the Mac, using OS X disk utility.


will see what happens when I unplug it from the board and restart...

thanks!

W

---

### Post by willfriedwald on 2007-09-07
Okay - I unplugged it from the motherboard SATA port, then restarted.

I turned on the drive first, and the thing did re-start withe eSATA drive powered on, so I guess that's an improvement.

However, the OS still apparently does NOT find the eSATA drive - I don't know quite how to look for it - it doesn't seem to be anywhere in the device manager.

Is there an equivalent of Disk Utility in Ubuntu?  How do I look for it and mount it?

As I said, I pre-formatted the drive (using Mac Disk Utility) in UNIX, although what Mac formats as "unix" may not actually be readable in Linux.  But hopefully the system will at least find the drive and offer to format it or initialize it...

thanks for any further help!

willfriedwald



thanks!

W

---

### Post by flangemonkey on 2007-09-24
please post the output of 
```

fdisk -l

```
and 
```

lspci

```
also 
```

dmesg | tail -15

```
would probably be useful, if you run that shortly after plugging in the HD

---

### Post by HereInOz on 2007-09-24
Is the drive actually being mounted at all?  In *nix systems, you generally need to tell the system to mount a drive, so that it can be read.

Read up on the "mount" command, and also read up on the use of the fstab file to mount fixed disks on boot up.

---

### Post by HereInOz on 2007-09-24
System > Preferences > Hardware Information should show you the drive and give you the UUID which you can use in fstab to mount it, or the necessary info to do a temporary mount.

---

