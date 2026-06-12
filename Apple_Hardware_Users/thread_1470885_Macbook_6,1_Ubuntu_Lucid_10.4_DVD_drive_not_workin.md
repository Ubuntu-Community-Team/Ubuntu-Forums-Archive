---
title: "Macbook 6,1 Ubuntu Lucid 10.4 DVD drive not working after install"
date: 2010-05-03
forum: Apple Hardware Users
---

### Post by NeddyDownUnder on 2010-05-03
I'm hoping that someone can help me, I'd really appreciate it.

I've just installed a fresh copy of Lucid on my Macbook 6,1 (laptop..., triple boot with Win7) and I have managed to get most things to work. In general I'm really happy with Ubuntu, it's great! But I can't get my DVD drive to work correctly. Here's my situation: 

Installed Lucid from live CD. 

Tweaked a few things, Lucid works a treat.

Try to insert a DVD or CD, sometimes nothing happens. Other times it just ejects it. Either way it does not spin up at all. Furthermore, after a DVD / CD is ejected I can't insert anything else into the drive. It physically blocks up. I have to restart to get it to unblock. I can hear the mechanism free up when I reboot. If I insert a DVD / CD before I boot Lucid I can use the DVD / CD but mostly I can't eject it and if I can i can't insert any other DVD /CD's into the drive as it blocks up.

I really don't have much of a clue how to solve this. It does appear that Lucid thinks I have a SCSI connection to the DVD drive when i know it's SATA (does that make a diference?) 

I'm not sure what info people may need to help me so I'll try to just include a few things I think may be useful. Please ask me if you need more info.

**Command** sudo dmidecode -s system-product-name 
```
MacBook6,1
```**Command **uname -a
```
Linux Linux-Mac 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
```**Command** lspci
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP7
```**Command **sudo lshw (extract)
  ```
*-cdrom
                description: DVD writer
                product: DVD-R   UJ-898
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HA07
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open

```Any help will be appreciated. 

Thanks.

---

### Post by xguilx on 2010-05-22
Hi, 

I just had the same problem with my Macbook.

To solve it, i created a mount point for Dvd rom
For example 
sudo mkdir /media/cdrom

and so i edited the fstab file
sodu gedit /etc/fstab

by just adding the command line to manage Cdrom (wich in /dev/sr0 on my computer)
# DVDrom 
/dev/sr0        /media/cdrom   udf,iso9660 user,noauto     0       0

If your Dvdrom is stuck, you can force ejection :
sudo eject /dev/sr0

Hope it will help!

---

### Post by NeddyDownUnder on 2010-05-24
Thanks for trying to help. Unfortunately the fstab entry did not help me. There is actually no response from the drive at all when I enter a disc. I mean I can push it all the way in and still feel the disc where as when OS X or windows is running Once I push the disc in the drive actually grabs the disc and loads it physically and then spins it up...

For now I've put this in the too hard basket as I don't have time to fiddle with it anymore...

Cheers for the reply.

---

