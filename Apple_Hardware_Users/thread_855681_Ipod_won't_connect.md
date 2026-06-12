---
title: "Ipod won't connect"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by LordDelta on 2008-07-10
Ok, I'm having a problem with getting my ipod connected to my Hardy desktop. There is perhaps a possiblity there is something wrong with my ipod, but it does connect, just rather sporadically. 

So, right now my iPod (5th generation 60 GB model) is plugged in and connected to my ubuntu macbook, and the ipod knows its plugged in, but as far as my macbook/hardy is concerned, the ipod doesn't exist. I'm not sure where it would be under /dev either, so I don't know how I'd mount it manually. Though, it should automount, no? 

When it did work, the iPod had died, and was charging, then it started up, and mounted itself to the desktop, and RythmBox started itself up as well. I could successfully eject it as well. Now, I plug back into the computer (I've rebooted since then as well), and it doesn't come up. Clueless how to make it appear. I don't want to pull it either, because for some reason that crashes my ipod ( I can't turn it off or restart it ). Any help would be most welcome :(

---

### Post by forger on 2008-07-10
Try plug it in, wait for a minute or so and unplug it

type in terminal:
dmesg

The last lines should show you some info about the plugged in device

---

### Post by LordDelta on 2008-07-10
ok, I typed in that command, and found this output:

```

[  667.539550] usb 5-3: new high speed USB device using ehci_hcd and address 8
[  667.672951] usb 5-3: configuration #1 chosen from 2 choices
[  667.837479] usbcore: registered new interface driver libusual
[  667.885889] Initializing USB Mass Storage driver...
[  667.886020] scsi4 : SCSI emulation for USB Mass Storage devices
[  667.886116] usbcore: registered new interface driver usb-storage
[  667.886122] USB Mass Storage support registered.
[  667.886275] usb-storage: device found at 8
[  667.886279] usb-storage: waiting for device to settle before scanning
[  670.062286] usb-storage: device scan complete
[  670.063125] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  817.018484] sd 4:0:0:0: [sdb] Spinning up disk.....not responding...
[ 1160.805743] sd 4:0:0:0: [sdb] READ CAPACITY failed
[ 1160.805753] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1160.805759] sd 4:0:0:0: [sdb] Sense Key : Not Ready [current] 
[ 1160.805765] sd 4:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[ 1160.807089] sd 4:0:0:0: [sdb] Write Protect is off
[ 1160.807097] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1160.807101] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1160.807203] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1160.807272] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1356.761940] sd 4:0:0:0: [sdb] Spinning up disk.....not responding...
[ 1701.087290] sd 4:0:0:0: [sdb] READ CAPACITY failed
[ 1701.087299] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1701.087306] sd 4:0:0:0: [sdb] Sense Key : Not Ready [current] 
[ 1701.087313] sd 4:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[ 1701.088522] sd 4:0:0:0: [sdb] Write Protect is off
[ 1701.088529] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1701.088533] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1848.044051] sd 4:0:0:0: [sdb] Spinning up disk.....not responding...
[ 2192.317755] sd 4:0:0:0: [sdb] READ CAPACITY failed
[ 2192.317765] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2192.317773] sd 4:0:0:0: [sdb] Sense Key : Not Ready [current] 
[ 2192.317781] sd 4:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[ 2192.319185] sd 4:0:0:0: [sdb] Write Protect is off
[ 2192.319192] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 2192.319198] sd 4:0:0:0: [sdb] Assuming drive cache: write through

```

---

### Post by cyberdork33 on 2008-07-11
It doesn't look good:
> ```

[  817.018484] sd 4:0:0:0: [sdb] Spinning up disk.....not responding..
```

Looks like the hard drive might be failing. Have you tried doing a restore? Does it work OK in OS X / Windows?

Your iPod is /dev/sdb though for reference.

---

### Post by LordDelta on 2008-07-11
How could the hard drive be failing, though? It works just fine as far as I can tell when its unplugged, it works like a dream when it powers up and connects, just not when its already powered up?

Its not like I haven't dropped it now and again (its a couple years old), but I would think if the Hard Drive was failing I might hear skipping when I'm listening to songs or something. Unless there really is that much buffer built into playing songs that it can read several times.

The only reason I say its possibly a problem with the iPod, is that I did install some custom firmware (I think the equivalent of jail-breaking my iPod), but I didn't think it should make so much of a difference, especially not as its been like this only rather recently, and it had the modded firmware on it for about a year.

But, I will test it with OSX and Windows. I seem to remember XP always had issues with ejecting it, but then that XP box has 5 virtual drives and has troubles ejecting cds, OSX I don't remember quite as well, since my main music library is on the Windows box

---

### Post by cyberdork33 on 2008-07-11
Ok, I used to have weird issues with custom firmware a long time ago. Try restoring to the default fimrware and see if you have the same probblems. If your normal use is OK, I wouldn't guess it is a hard drive failure, but rather a software (firmware) issue, or a problem with the linux driver.

---

