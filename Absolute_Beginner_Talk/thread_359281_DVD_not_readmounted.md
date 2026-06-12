---
title: "DVD not read/mounted"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Shaddarr on 2007-02-11
Hi there,

I got great help with my last question and have another (no kidding? :-P )

This seems like it should have some 'crazy-easy' solution, but I am not finding any specific information on it from some basic searches on Google and here in the great Ubuntu Forii...

I am running Dapper with am LG DVD writer. I have some training videos I put on there in UDF format in XP a while back, but when I insert the disc, it doesn't show up on the desktop.

When I Nautilus to the drive it gives the error:[INDENT][I]
**Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.**
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so[/I][/INDENT]


Is it a problem with UDF? Should I use another format, is that the only problem? 
I bet it's something 'real easy' that I'm just not thinking about since I'm tired.. heh  :redface: 

Thanks for any ideas

---

### Post by mr.v. on 2007-02-12
for starters, immediately after trying to mount it and getting the error, go to a console (applications --> accessories --> terminal) and type what it says:
```

dmesg | tail
```
and post the results. it may present a more detailed error report that can help.

---

### Post by sir_cheats_a_lot on 2007-02-13
I'm having the same issue, but mine is with one specific DVD, my other ones all work :confused:      mounts fine in windows though.. not sure why its having issues..
I'm using Kubuntu "edgy" v. 6.10.

mine reported:

$ sudo mount /dev/hdc /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


$ dmesg | tail
[17183486.692000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183486.692000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17183486.692000] ide: failed opcode was: unknown
[17183486.692000] end_request: I/O error, dev hdc, sector 4294180792
[17183486.692000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17183486.692000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[17183486.692000] ide: failed opcode was: unknown
[17183486.692000] end_request: I/O error, dev hdc, sector 4294180792
[17183489.148000] grow_buffers: requested out-of-range block 18446744073709355024 for device hdc
[17183489.148000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=-196592, block=-196592


...bet this one has the developers scratching their heads..

---

