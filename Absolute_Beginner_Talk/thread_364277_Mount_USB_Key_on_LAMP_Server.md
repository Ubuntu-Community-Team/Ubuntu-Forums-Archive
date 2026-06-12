---
title: "Mount USB Key on LAMP Server"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by lenwood on 2007-02-18
Hi All, I just installed 6.06 as a LAMP server on my home network. I couldn't figure out how to download files using that computer, so I loaded them onto a USB key. Now I can't figure out how to mount the USB key. I can see it in the list of drives with fdisk, but I cannot access the files on it for some reason. Can someone help?

Thanks,
Chris

---

### Post by smdeep on 2007-02-18
Hi
Generally the usbdrive is sda1. I generally do a sudo tail -f /var/log/syslog and plug the usb drive in. Just look for lines like these:
Feb 18 12:58:32 shuchi kernel: [17192272.616000] sda: assuming drive cache: write through
Feb 18 12:58:32 shuchi kernel: [17192272.616000]  sda: sda1

I have a directory in /media named usbdrive. I just mount it like this:

sudo mount /dev/sda1 /media/usbdrive

HTH

---

### Post by Betard on 2007-02-19
> **smdeep said:**
> Hi
Generally the usbdrive is sda1. I generally do a sudo tail -f /var/log/syslog and plug the usb drive in. Just look for lines like these:
Feb 18 12:58:32 shuchi kernel: [17192272.616000] sda: assuming drive cache: write through
Feb 18 12:58:32 shuchi kernel: [17192272.616000]  sda: sda1

This worked perfect for me... I am completely new to linux and just did the same install as lenwood, glad to find a solution so quick.

the only issue I have is that after I do the "sudo tail -f...." command how do I get out?  I have a screen full of dates and info but I cant get back to the command line...

Did I mess something up?

---

### Post by po0f on 2007-02-19
Betard,

No you didn't mess up, you just didn't kill the program.  Press Ctrl-C to kill it.

---

### Post by Betard on 2007-02-19
Thanks po0f, as soon as I read that I thought "of course!"

I thought of 2 other questions:

1 - do I have to do this everytime I plug it in?

2 - do I have to un-mount it when I take it out?

the reason I ask is because I unplugged it and then plugged it back in and got

```


[series of numbers here] FAT: Directory bread (block 513) failed
[series of numbers here]  3:0:0:0 rejecting I/O to dead device



```

---

### Post by Betard on 2007-02-20
I am still having issues with this, so if anyone could help I would appreciate it.  I know its probably simple to some, but its something I just cant seem to figure out.

---

### Post by po0f on 2007-02-20
Betard,

You might have killed it by unplugging it without unmounting it.  I think you'll have to reformat it and start fresh.  :(

---

### Post by Betard on 2007-02-20
Thankfully the data on the usb key is ok, I didnt know that I would have to mount and umount everytime I wanted to use it/take it out.

The one thing I like about linux so far is "small victories", I am quite happy with myself (and the help I get here) when a challenge is overcome, albeit probably way less of a challenge for users with a little more experience under their belt. 

Thanks again po0f :)

---

### Post by MachaB on 2007-08-04
Dears,

Thanks for the very useful explanations. For me it seemed to work fine until I tried to actually access my usb device.

First, instead of having sda: sda1 in the second step I had sdb: sdb1. So I keyed in 'sudo mount /dev/sdb1 /' ('sudo mount /dev/sdb1/ media/usbdrive' or .../usbwhatever wouldn't work). And now what do I do? I still don't know how to access my usb key and can't 'sudo unmount...' because it says device is busy (with what???). 

In case it helps, I work with a dual booted (Ubuntu server / Win XP) Dell with AMD 64. 

Thanks for your help.

---

### Post by MachaB on 2007-08-06
Oops, I finally understood you actually have to mount your device on a mounting point that is a valid directory... now it works... and next time I'll try to plug in my brain before posting... :oops:

---

