---
title: "Using Sansa Sandisk Mp3 player"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by dilaudid on 2007-01-02
Hi all,

I've been trying to get my mp3 player - a Sansa Sandisk m250 - to work on Kubuntu edgy 6.1. I understand that it should automatically mount using something called HAL. I tried "tail -f /var/log/messages" (which shows what ubuntu kernel is doing right now) to see what happened as I connected the player:
```
Jan  2 10:38:38 charlemagne kernel: [17185707.696000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jan  2 10:38:38 charlemagne kernel: [17185707.856000] usb 2-1: configuration #128 chosen from 1 choice
```

Anyway I just found out the reason it is not installing is that there is a setting on the MP3 player itself - USB mode must be set to MSC not MTP. Once I changed this Kubuntu recognised the player and it opened it in a new window. This was tried on a Thinkpad T23 running KUbuntu edgy 6.10 and a Thinkpad 22 running Xubuntu edgy 6.10

Thanks for the great OS!

---

### Post by iceworm on 2007-02-28
Hey

I am new to this forum but I'll cut to the chase. I have a Sansa c240. Been using it for a while and been running like a charm. I recently switched over to Ubuntu.
The problem I have is that I can not see any of my files. It shows up as being mounted and all the folders are visible but none of my files are shown. I tried searching around google and here and found nothing. I called up Sandisk and they informed me that they do not support Linux and using the c240 in Linux could somehow lead to Linux repartitioning my c240, which made no sense. 

So is there anything I could try?

Appreciate it.

---

### Post by jubxie on 2007-03-11
I believe that the sansa cannot see files transfered via mtp(windows protocol)
when connected in msc(mass storage) mode.

---

### Post by pNoyr3D on 2007-03-18
Well yeah, I just started on UBUNTU and I just hooked up my Sansa e260 and it worked like a charm, I always have mine in MSC mode.

---

