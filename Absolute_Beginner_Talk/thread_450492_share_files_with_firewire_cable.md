---
title: "share files with firewire cable"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by r76 on 2007-05-21
I want to transfer files between two computers, in windows i just attach a firewire cable between the two and they can see each others shared folders (I think it is through network connections).  How do I do this in Ubuntu please?  Do I need network software?

---

### Post by lyceum on 2007-05-22
It is the same thing, but if you are trying to move from Ubuntu to NTFS you will need to add some things. I know you can set it up with Automatix.

---

### Post by compiledkernel on 2007-05-22
sudo apt-get install ntfs-3g ntfs-config

Assuming its an NTFS Partition look at this link. 

Should help you mount NTFS paritions 

[http://feistyguide.blogspot.com/2007_05_01_archive.html](http://feistyguide.blogspot.com/2007_05_01_archive.html)

Automatix isnt really nessecary when you can use the NTFS Configuration Tool to configure mounted ntfs drives.

---

### Post by r76 on 2007-05-22
Thanks, but neither of the computers is NTFS they are both ext3, i found that eth1394 is blacklisted in /etc/modprobe.d/blacklist so I commented it out and restarted but still no luck

---

### Post by r76 on 2007-05-23
OK so I found this:
[http://howto.x-tend.be/FireWireClustering/x57.html](http://howto.x-tend.be/FireWireClustering/x57.html)
it sounds from that like after removing the blacklist I need to "modprobe eth1394", check dmesg output then set "ifconfig" IP addresses?

Suppose that works do I need samba or NFS or both (or neither) to share files?  I want to be able to transfer about 20GB of files from one machine to the other.

---

