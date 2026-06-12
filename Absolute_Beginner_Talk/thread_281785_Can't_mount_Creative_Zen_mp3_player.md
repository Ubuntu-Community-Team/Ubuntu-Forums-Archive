---
title: "Can't mount Creative Zen mp3 player"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by c0rd3l1a on 2006-10-21
I just bought a Creative Zen Vision: M mp3 player and I can't mount it. I'm using Dapper. 
The device manager recognizes it, but doesn't tell me its pathname. It says "linux.sysfs_path_device  /sys/devices/pci0000:00/0000:00:1d.1/usb2/2-1". And when I tried $ tail -f /var/log/messages, all I got was "usb 2-1: new full speed USB device using uhci_hcd and address 4". Also, gnomad2 isn't recognizing it at all.
Please help.

---

### Post by c0rd3l1a on 2006-10-21
After spending some quality time with various search features on this site and google, I found out that my mp3 player is an MTP device (it works with a database instead of a filesystem?), and this is why it won't mount properly. However, device manager recognizes that it is there and after following all of the instructions found here [http://ubuntuforums.org/showthread.php?t=199250&highlight=mp3+player+creative](http://ubuntuforums.org/showthread.php?t=199250&highlight=mp3+player+creative)  I was able to get gnomad2 to access my mp3 player!! However, now I've discovered that my laptop won't recognize *both* the mp3 player *and* my external hard drive (where all of my music is) at the same time, so I have a new problem. I hope that this second post helps some others out, though.

---

