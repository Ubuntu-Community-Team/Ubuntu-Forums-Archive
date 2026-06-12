---
title: "How to refresh drives?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by highrelyguy on 2007-08-14
Hi!

I have two sata drives in hotswap trays.  How do I get the devices recognized after the machine has booted?  I need to "refresh" the devices.  Presently, I can only mount a drive after it has changed by rebooting.  That seems awfully Microsoft to me - I'm sure LINUX has a better way.  Please help!

---

### Post by guguma on 2007-08-14
did you try unmounting the drive and mounting it back again.

---

### Post by highrelyguy on 2007-08-14
Yup.  But of course the message I got when I tried to unmount was: not mounted.

---

### Post by Blutack on 2007-08-14
And what happened when you tried to mount it?

---

### Post by highrelyguy on 2007-08-14
"Special device does not exist."

---

### Post by Blutack on 2007-08-14
What does 
dmesg 
say just after you swap the drives?

---

### Post by highrelyguy on 2007-08-14
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 20
[43030695.280000] Buffer I/O error on device hdb, logical block 5
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 24
[43030695.280000] Buffer I/O error on device hdb, logical block 6
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 28
[43030695.280000] Buffer I/O error on device hdb, logical block 7
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 0
[43030695.280000] Buffer I/O error on device hdb, logical block 0
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 4
[43030695.280000] Buffer I/O error on device hdb, logical block 1
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 0
[43030695.290000] hdb: tray open
[43030695.290000] end_request: I/O error, dev hdb, sector 4
[43030695.290000] hdb: tray open
[43030695.290000] end_request: I/O error, dev hdb, sector 0
[43030695.290000] hdb: tray open
[43030695.290000] end_request: I/O error, dev hdb, sector 4
root@teamplayer1:/var/www#

---

### Post by Blutack on 2007-08-14
That's not good!  Was the drive mounted when you pulled it?

---

### Post by highrelyguy on 2007-08-14
Yes, it could have been.

---

### Post by Blutack on 2007-08-14
Oops...
Are you using dapper by any chance?
And are your drives in /etc/fstab?

---

### Post by highrelyguy on 2007-08-14
I'm using 6.10 - that's fiesty right??  



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0
   1
/dev/sda1       /boot           ext3    defaults        0       2
# /dev/sda5
UUID=9286a7bc-08ff-4b8c-93e4-0a7dc4cf1e39 none            swap    sw
  0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
(END)

---

### Post by highrelyguy on 2007-08-14
I'm using 6.10 - that's Fiesty fawn right???

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0
   1
/dev/sda1       /boot           ext3    defaults        0       2
# /dev/sda5
UUID=9286a7bc-08ff-4b8c-93e4-0a7dc4cf1e39 none            swap    sw
  0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
(END)

---

### Post by Blutack on 2007-08-14
Oh, sorry, the error was coming from the cdrom drive, nothing to do with the sata ones.  Feisty is actually 7.04 - the year 2007 and the month it was released in.  
Can you run
tail -f /var/log/dmesg
then plug the tray in?
Hopefully the display should change...if it does, once its all settled down, press Ctrl-C to quit tail and post it.

---

### Post by highrelyguy on 2007-08-14
I unplugged the drive, ran the tail then plugged it back in - it never changed and this is what it said:


root@teamplayer1:/etc# tail -f /var/log/dmesg
[42949389.970000] EXT3 FS on dm-0, internal journal
[42949390.140000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949390.140000] md: bitmap version 4.39
[42949390.700000] e1000: eth1: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[42949390.750000] kjournald starting.  Commit interval 5 seconds
[42949390.750000] EXT3 FS on sda1, internal journal
[42949390.750000] EXT3-fs: mounted filesystem with ordered data mode.
[42949392.040000] NET: Registered protocol family 10
[42949392.040000] lo: Disabled Privacy Extensions
[42949392.040000] IPv6 over IPv4 tunneling driver

---

### Post by highrelyguy on 2007-08-14
Hmm, that's strange.  I just ran dmesg | less and jumped to the bottom and this is what I saw:

[43030695.280000] Buffer I/O error on device hdb, logical block 5
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 24
[43030695.280000] Buffer I/O error on device hdb, logical block 6
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 28
[43030695.280000] Buffer I/O error on device hdb, logical block 7
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 0
[43030695.280000] Buffer I/O error on device hdb, logical block 0
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 4
[43030695.280000] Buffer I/O error on device hdb, logical block 1
[43030695.280000] hdb: tray open
[43030695.280000] end_request: I/O error, dev hdb, sector 0
[43030695.290000] hdb: tray open
[43030695.290000] end_request: I/O error, dev hdb, sector 4
[43030695.290000] hdb: tray open
[43030695.290000] end_request: I/O error, dev hdb, sector 0
[43030695.290000] hdb: tray open
[43030695.290000] end_request: I/O error, dev hdb, sector 4
[43040086.870000] nv_sata: Primary device removed
[43040118.010000] nv_sata: Primary device added
(END)

WHy didn't the tail work?

---

### Post by highrelyguy on 2007-08-14
Hmm, I don't see where the tail stuff even came from.  Strange.

---

### Post by Blutack on 2007-08-14
Because I made the stupid error of thinking the output of dmesg and /var/log/dmesg are the same thing...they ain't.  Sorry!  Well, we have some data now.  Looks like it's recognising the drives are moving anyway, which is nice.  Was there any more after the
[43040118.010000] nv_sata: Primary device added
Specifically anything about a /dev/something?

---

### Post by highrelyguy on 2007-08-14
Nope, that's all.

---

### Post by Blutack on 2007-08-14
Sorry!
[http://kerneltrap.org/node/5632](http://kerneltrap.org/node/5632)
We don't have hotswapping sata drives...yet...
I should really have checked before leading you on that merry dance.

---

### Post by highrelyguy on 2007-08-14
WOW!  Well, I really appreciate your help - thank you!  So, to be sure of what I'm trying accomplish here, you don't see a way for me to tell the kernel to rescan for devices - I have to reboot?

---

### Post by Blutack on 2007-08-14
Looks like it I'm afraid.  I had my head stuck around stuff like firewire and usb removable devices - SATA and stuff is a bit more complicated.  You'll have to wait til probably the version after Gutsy, or compile your own kernel once the Libata patches are in (not as hard as it sounds).
Again sorry, I'll blame it on tiredness.

---

### Post by highrelyguy on 2007-08-14
Well, it's guys like you that have made this OS what it is today.  Thank you for your support.  Get some sleep.

---

