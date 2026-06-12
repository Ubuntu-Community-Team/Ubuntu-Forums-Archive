---
title: "Ipod not showing up when i connect it?! help please"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-08
I've found a couple threads and read through them and tried some of the steps to see whether my system even recognizes when i plug my ipod in.  The good news is that it does.

When i do the following command: ```
sudo tail -f /var/log/messages
```  I get the following output:
```

Sep  8 00:16:49 localhost kernel: [17263524.124000] usb 5-5: new high speed USB device using ehci_hcd and address 5
Sep  8 00:16:49 localhost kernel: [17263524.256000] usb 5-5: configuration #1 chosen from 2 choices
Sep  8 00:16:49 localhost kernel: [17263524.256000] scsi3 : SCSI emulation for USB Mass Storage devices
Sep  8 00:16:54 localhost kernel: [17263529.256000]   Vendor: Apple     Model: iPod              Rev: 1.62
Sep  8 00:16:54 localhost kernel: [17263529.256000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep  8 00:16:54 localhost kernel: [17263529.256000] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
Sep  8 00:16:54 localhost kernel: [17263529.260000] sdb: Write Protect is off
Sep  8 00:16:54 localhost kernel: [17263529.260000] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
Sep  8 00:16:54 localhost kernel: [17263529.260000] sdb: Write Protect is off
Sep  8 00:16:54 localhost kernel: [17263529.260000]  sdb: sdb1 sdb2
Sep  8 00:16:54 localhost kernel: [17263529.268000] sd 3:0:0:0: Attached scsi removable disk sdb
Sep  8 00:16:54 localhost kernel: [17263529.268000] sd 3:0:0:0: Attached scsi generic sg1 type 0


```

So it see's it but hwere?  Is it sbd1 or sbd2?  I tried creating a directory in media called iPod and tried mounting sbd1 to that, but it didnt work.  Here's what I get:

```

vic@ubuntu:~$ sudo mount -t vfat /dev/sdb1 /media/iPod
mount: special device /dev/sdb1 does not exist

```

I'm lost here.. i dont know how to get it to show up so i can use gtkpod to transfer/remove songs..  I dont want to have to boot back into windows everytime i want to edit my playlist.  Any ideas?:confused: 

-Vic

---

### Post by jordanmthomas on 2006-09-08
Maybe try sdb2 instead?

---

### Post by Rizla on 2006-09-08
> **jordanmthomas said:**
> Maybe try sdb2 instead?

Tried that too.. no way i'd just try the 1st without the 2nd.  But thanks for  reading and helping.  

in other news, i have to say.  The forum is very responsive.  I've had a bunch of minor issues that with the help of peopel giving me some suggestions, not necessarily the correct ones.  It gave me the insight to fix the problem.  There is truely no way to learn without breaking things and bashing your head against a wall until you "get it".  Im still in the bashing my head stage...

---

### Post by jordanmthomas on 2006-09-08
Well, I don't know anything about Ipods (what filesystem, etc), I just noticed it seemed there were to partitions.  Hopefully someone else can help!

---

### Post by Rizla on 2006-09-08
> **jordanmthomas said:**
> Well, I don't know anything about Ipods (what filesystem, etc), I just noticed it seemed there were to partitions.  Hopefully someone else can help!

its fat32 because i formatted it in windows via itunes when i first set it up.

---

### Post by Rizla on 2006-09-08
Any help from some vets that might have experience troubleshooting a similar situation?:-?

---

### Post by harlan on 2006-09-08
I use an ipod nano and I recommend you to use gtkpod to manage your music. To read inside the ipod there are different tools. Now I have installed 
gtkpod
libgpod0
libgpod-common 
libmac-ipod-gnupod-perl
and it works. If you don't see the ipod on your desktop when you plug it, go to places/equipment (I don't know if that is the right term in English).
There are other audio players you can use: amarok, banshee, rhythmbox, yamipod...
There is an interesting project [www.ipodlinux.org]("www.ipodlinux.org")
to install linux in your ipod.

---

### Post by Rizla on 2006-09-08
I actually got it to work last night.  I swapped out the USB jumper on my motherboard that goes to my front panel usb on my pc case. I rebooted and then I was surprised to see a cool little ipod icon on my desktop.  I downloaded yamipod, which i could get to work because it said I had less than 5MB of space or something, then it would lock up and not do anything.  I then got gtkpod and it worked like a charm.

Yea! One more thing down.  I've almost got my system setup to the point that i'd consider myself fully transitioned from windows.  Still a couple quirks.  Right now i'm having a problem with bittorrent.  I cant download anything.  I can when im in windows, but its not working for linux..

Gotta go post a new help thread.  Thanks.

---

