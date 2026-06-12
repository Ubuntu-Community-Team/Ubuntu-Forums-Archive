---
title: "weird audio cd problem"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-02-12
i, currently, use openbox as my only window manager. when i still had gnome, or kde, when i would stick in an audio cd, a disc icon would appear on the desktop and i would click on it and play it. i know this isn't going to happen with openbox, but audio cds don't show up in thunar. the only way i can play an audio cd now, is to click 'play audio cd' in kaffeine and it plays. i've tried using xmms and selecting /media/cdrom and cdrom0, but nothing happens. there was a /dev/sdb, but that seems to be gone now. i want to be able to play cds in whichever player i wish, including cl players.

---

### Post by fuscia on 2007-02-12
this is in my /etc/fstab

*/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0*

i tried * mount /media/cdrom0* and got...

[i]mount: block device /dev/hdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/i]


i tried *dmesg | tail* and got...

[i][17188945.532000] end_request: I/O error, dev hdb, sector 24
[17188945.532000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17188945.532000] hdb: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17188945.532000] ide: failed opcode was: unknown
[17188945.532000] end_request: I/O error, dev hdb, sector 0
[17190505.940000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17190505.940000] hdb: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17190505.940000] ide: failed opcode was: unknown
[17190505.940000] end_request: I/O error, dev hdb, sector 64
[17190505.940000] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16[/i]

aha! (wtf is all that crap?) :( 

i tried *sudo mount /media/cdrom0* and got the same message as the first attempt. i was lost to begin with, but now that the birds have eaten the breadcrumbs, i'm screwed too.

---

### Post by RedSquirrel on 2007-02-12
> **fuscia said:**
> this is in my /etc/fstab

*/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0*

i tried * mount /media/cdrom0* and got...

[I]mount: block device /dev/hdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]


i tried *dmesg | tail* and got...

[I][17188945.532000] end_request: I/O error, dev hdb, sector 24
[17188945.532000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17188945.532000] hdb: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17188945.532000] ide: failed opcode was: unknown
[17188945.532000] end_request: I/O error, dev hdb, sector 0
[17190505.940000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17190505.940000] hdb: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17190505.940000] ide: failed opcode was: unknown
[17190505.940000] end_request: I/O error, dev hdb, sector 64
[17190505.940000] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16[/I]

aha! (wtf is all that crap?) :( 

i tried *sudo mount /media/cdrom0* and got the same message as the first attempt. i was lost to begin with, but now that the birds have eaten the breadcrumbs, i'm screwed too.

There is nothing weird about all of this. You cannot mount an audio cd. Audio programs access the media *directly*.

In XMMS, you have to specify /dev/hdc (or similar), not /media/cdrom0.

If that doesn't work, install the package "xmms-cdread". Then go into Options -> Preferences and disable "CD Audio Player" and enable "AudioCD Reader".

And it seems audio CDs just don't show up in Thunar. That's just the way it is, as far as I know. I guess Thunar just doesn't have that functionality (yet).

---

### Post by fuscia on 2007-02-13
thanks for the response. i was afraid i'd screwed something up. what i was looking for was a way to play cds in console mode. cplay didn't do to well, but orpheus works great.

---

### Post by RedSquirrel on 2007-02-13
> **fuscia said:**
> thanks for the response. i was afraid i'd screwed something up. what i was looking for was a way to play cds in console mode. cplay didn't do to well, but orpheus works great.

Interesting. I was looking at something like that a while ago. I'll have to give orpheus a try.

---

### Post by fuscia on 2007-02-13
> **RedSquirrel said:**
> Interesting. I was looking at something like that a while ago. I'll have to give orpheus a try.

something odd i've found out about orpheus - it keeps playing even after you've quit. you have to stop play before quitting. i have no clue why.

---

### Post by RedSquirrel on 2007-02-15
> **fuscia said:**
> something odd i've found out about orpheus - it keeps playing even after you've quit. you have to stop play before quitting. i have no clue why.

I wonder if they call that a bug or a *feature*. :)

I guess it's just that the layer of the app that is accessing the media is still running even though the UI is closed. Neat. I seem to recall reading somewhere winamp did that too, but I can't confirm because I've never used winamp. Oh well. At least the solution is simple: stop, then quit.

---

