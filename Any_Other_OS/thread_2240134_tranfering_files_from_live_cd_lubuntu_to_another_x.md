---
title: "tranfering files from live cd lubuntu to another xp laptop"
date: 2014-08-18
forum: Any Other OS
---

### Post by aris_miletis on 2014-08-18
Hello guys, I have a failing hard drive which can't boot but I can access it's files. I'm currently operating it with a lubuntu live cd and I need to rescue the data by transferring them to another,windows xp, laptop. It seems that my only option is a wifi or ethernet lan solution but I can't figure out how with other online guides.

Any help would be much appreciated.

---

### Post by coldraven on 2014-08-18
The simplest way would be to boot with your Lubuntu live CD and then plug in a USB drive or stick. Then just copy the files and physically move them to the XP laptop.
I have a couple of old 160GB HDDs that are in cheap enclosures. You can pick them* up on Ebay for about £5. 
I also have a 1TB external USB drive which is very handy for your sort of problem. I think it cost about £80.
The usual FAT32 on memory sticks has a 4GB file size limit so if you want to copy files bigger than that use Gparted to format the drive or stick to NTFS so that XP can read it. 
**Make sure that you select the correct drive before formatting!**

*This sort of thing 
[http://www.ebay.co.uk/itm/USB-2-0-External-2-5-SATA-HDD-Hard-Disk-Drive-Enclosure-Aluminum-Case-Caddy-UK-/291035236894?pt=UK_Collectables_HardDriveEnclosures_RL&hash=item43c30d4a1e](http://www.ebay.co.uk/itm/USB-2-0-External-2-5-SATA-HDD-Hard-Disk-Drive-Enclosure-Aluminum-Case-Caddy-UK-/291035236894?pt=UK_Collectables_HardDriveEnclosures_RL&hash=item43c30d4a1e)

---

### Post by steeldriver on 2014-08-18
If you can't use the 'sneakernet' approach, I think for a one-off like this (rather than wrestling with network shares) the simplest option might be python's SimpleHTTPServer

[http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python)

If you're in a live session there should be no firewalling to worry about (just make sure you're behind a NAT'ed router though)

---

### Post by aris_miletis on 2014-08-18
> **coldraven said:**
> The simplest way would be to boot with your Lubuntu live CD and then plug in a USB drive or stick. Then just copy the files and physically move them to the XP laptop.
 thing is that those files are 40gb total in size and i can't use my 4gb usb stick

okay i've set up the http server and i can access the files from a browser in linux but i can't access it from the xp computer, what should I do next?
edit: I found them by typing the linux laptop's ip adress
Thank you so much for the help guys!

---

### Post by steeldriver on 2014-08-18
what happens when you try to access it from the xp computer?

can you ping the linux computer from xp (open cmd.exe and type ping 192.168.1.16 - replacing 192.168.1.16 by the LAN IP of the Linux machine)

EDIT: apologies, it needs to be run as root to access the (default) port 8000

```

**sudo** python -m SimpleHTTPServer

```

---

