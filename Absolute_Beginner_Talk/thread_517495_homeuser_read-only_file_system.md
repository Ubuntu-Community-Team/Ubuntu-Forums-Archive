---
title: "/home/user read-only file system?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by genfinch on 2007-08-04
ktorrent tells me that some of the files it needs to change are on a read-only file system. but in fact they are in my home folder, or more precisely, in /home/user/.kde/share/apps/ktorrent. i ended up desperately chmodding all of /home/user/.kde/share/apps/ktorrent recursively to 777, but no dice. what to do? that particular torrent keeps stopping due to that problem, though its colleagues (with their data also in /home/user/.kde/share/apps/ktorrent) continue fine. i'm at my wits' end, plz help.

---

### Post by taurus on 2007-08-04
Try changing the ownership of that directory to your login name.

```
sudo chown -R **user**:**user** /home/**user**/.kde/share/apps/ktorrent
```
Replace **user** with your actual login name.

---

### Post by talby on 2007-08-04
Recently I had a failing hard drive having "/" keep on being remounted as read-only, maybe check your dmesg output and / or /var/log/messages for hdd errors or remount messages.

I was able to clone the drive successfully before it went completely bad, no more read-only remounts :)

---

### Post by genfinch on 2007-08-04
@ taurus
i am the owner of that folder and theoretically i have rw rights on it and everything in it. tried your suggestion nonetheless, but it didn't change a thing, apparently. thanks all the same.

@talby
dmesg gives me 

```
isa0060/serio0).
[17352498.500000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17352533.044000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17352533.044000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17352708.084000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17352708.084000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17352910.108000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17352910.108000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17352915.248000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17352915.248000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353018.400000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353018.400000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353018.404000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353018.404000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353122.336000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353122.336000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353200.076000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353200.076000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353209.940000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353209.940000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353224.632000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17353224.756000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353224.756000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353295.272000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353295.272000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353395.216000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353395.216000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353397.508000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353397.508000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353798.540000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353798.540000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353811.252000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353811.252000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353823.272000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353823.272000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17353989.400000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17353989.400000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17353993.808000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17353993.808000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354084.840000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354084.840000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354090.724000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354090.724000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354259.068000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354259.068000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354260.464000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354260.464000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354519.632000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354519.632000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354545.656000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354545.656000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354579.868000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354579.868000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354609.240000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354609.240000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354611.004000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17354611.004000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17354611.004000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17354622.856000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354622.856000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354634.704000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354634.704000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354640.904000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354640.904000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354644.408000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354644.408000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354652.640000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354652.640000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354659.828000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354659.828000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354777.892000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354777.892000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354784.632000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354784.632000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354830.968000] FAT: Filesystem panic (dev sda1)
[17354830.968000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354830.968000]     File system has been set read-only
[17354830.968000] FAT: Filesystem panic (dev sda1)
[17354830.968000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354830.972000] FAT: Filesystem panic (dev sda1)
[17354830.972000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354830.972000] FAT: Filesystem panic (dev sda1)
[17354830.972000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354846.132000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17354846.132000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17354846.512000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354846.512000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17354860.944000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17354860.944000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17355582.904000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17355582.904000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17355951.164000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17355951.164000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17357644.148000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17357644.148000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17357719.976000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17357719.976000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17358462.744000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17358462.744000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17358603.192000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17358603.192000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17358685.392000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17358685.392000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17358685.528000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17358685.528000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17358749.304000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17358749.304000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17359275.300000] cdrom: This disc doesn't have any tracks I recognize!
[17359341.900000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17359341.900000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17359350.316000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17359350.316000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17359407.708000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17359407.708000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17359559.448000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17359559.448000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17359559.808000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17359559.808000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17359580.804000] FAT: Filesystem panic (dev sda1)
[17359580.804000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17359580.804000]     File system has been set read-only
[17359580.804000] FAT: Filesystem panic (dev sda1)
[17359580.804000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17359580.804000] FAT: Filesystem panic (dev sda1)
[17359580.804000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17359580.804000] FAT: Filesystem panic (dev sda1)
[17359580.804000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17359891.936000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17359891.936000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17359896.336000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17359896.336000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17359909.572000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17359909.572000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17359972.036000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17359972.036000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17359977.348000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17359977.348000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17360606.156000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17360606.156000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17360623.976000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17360623.976000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17360643.312000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17360643.312000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17360754.960000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17360754.960000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17360801.632000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17360801.632000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17360820.012000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17360820.012000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17360840.140000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17360840.140000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17360882.540000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17360882.540000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17360895.484000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17360895.484000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17360895.484000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17360901.564000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17360901.564000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17360908.088000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17360908.088000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17361033.252000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17361033.252000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17361039.292000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17361039.292000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17361050.480000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17361050.480000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17361248.004000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17361248.004000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17361318.956000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17361318.956000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17361529.552000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17361529.552000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17361533.172000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17361533.172000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17361638.072000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17361638.072000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17361639.636000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17361639.636000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17364705.500000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17364705.500000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17365816.580000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17365816.580000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17365818.324000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17365818.324000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17365950.416000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17365950.416000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366038.404000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366038.404000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366043.912000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366043.912000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366064.228000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366064.228000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366092.096000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366092.096000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366099.540000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366099.540000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366115.128000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366115.128000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366130.796000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366130.796000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366149.104000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366149.104000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366208.216000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366208.216000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366216.780000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366216.780000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366299.224000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366299.224000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366300.220000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366300.220000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366313.092000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366313.092000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366432.748000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366432.748000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366636.456000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366636.456000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366650.628000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366650.628000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366658.256000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366658.256000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366674.248000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366674.248000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366690.588000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366690.588000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366714.988000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366714.988000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366788.636000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366788.636000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366788.836000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366788.836000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366801.732000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366801.732000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366917.176000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366917.176000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366926.436000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366926.436000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366939.884000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366939.884000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366962.280000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366962.280000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366973.468000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366973.468000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17366976.924000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17366976.924000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17366986.104000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17366986.104000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367007.020000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367007.020000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367018.212000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367018.212000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367033.332000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367033.332000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367036.608000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367036.608000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367054.856000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367054.856000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367065.044000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367065.044000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367091.012000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367091.012000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367096.548000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367096.548000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367100.268000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367100.268000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367117.808000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367117.808000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367140.288000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367140.288000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367160.588000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367160.588000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367169.976000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367169.976000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367200.288000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367200.288000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367223.576000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367223.576000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367225.032000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367225.032000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367253.952000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367253.952000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367270.448000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367270.448000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367302.800000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367302.800000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367310.212000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367310.212000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367330.376000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367330.376000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367371.084000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367371.084000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367383.244000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367383.244000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367426.012000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367426.012000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367431.076000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367431.076000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367441.548000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367441.548000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367457.136000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367457.136000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367480.004000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367480.004000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367491.884000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367491.884000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367495.256000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367495.256000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367510.704000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367510.704000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367524.936000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367524.936000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367542.744000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367542.744000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367553.336000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367553.336000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367557.844000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367557.844000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367574.384000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367574.384000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367611.152000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367611.152000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367614.396000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367614.396000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367628.160000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367628.160000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17367708.396000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17367708.396000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17367709.448000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17367709.448000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17368222.528000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17368222.528000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17368232.312000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17368232.312000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17369458.180000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17369458.180000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17369471.024000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17369471.024000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17369547.008000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17369547.008000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17369547.016000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17369547.016000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
```

and i've no idea what that means. :confused:
as for /var/log/messages, more of the same. 
anyway, according to fstab and mtab, my whole /dev/hda6 aka /home is mounted rw with me as the owner.

i just don't know what's going on, i can't find anything wrong with my whole general setup sort of thing, and no-one on the ktorrent forum or anywhere in the google universe seems to be having the same problem. :break into tears:
maybe someone knows some link to a forum or something, you can even call me a n00b for not finding it myself, i don't mind. 

please...

---

### Post by AlexenderReez on 2007-08-04
i don't really sure what is going here...but i suggest to run ktorrent in sudo mode if that case --->

> gksudo ktorrent

---

### Post by genfinch on 2007-08-04
right. i seem to have to start all my torrents manually again, so i'll try that tomorrow. it's time for bed here. thanks for your help everyone and i'll get back to you guys tomorrow with news of triumphant success or abject failure. night.

---

### Post by belikralj on 2007-08-04
I agree with talby. It's probably to do with linux finding errors on your hard disk and mounting it as read only. Now somebody more terminal savy should tell you how to remount the root file system because I'm don't think that 'sudo mount -a' will do it. You could check out what the mount command does by typing 'man mount' into the terminal. And I don't recommend this but you could try to temporarily change the entry in the file /etc/fstab that says errors=remount-ro to remount-rw. However I would wait for somebody else to post a better solution, sorry I couldn't help more...

---

### Post by genfinch on 2007-08-05
OK, here's the latest. i tried running ktorrent as root and the torrent worked fine BUT when i started other ones, their combined temporary files soon were too much for the root partition. i've only just recovered from the ensuing damage. well, i'm not changing my whole partition table, i only just got the whole thing set up the way i wanted it. so now i'm running ktorrent as myself agin and lo and behold, everything goes smoothly. i don't get it, but i'm certainly not gonna complain.
but i'm sure you guys are right and i should check that everything's in order with my drives. any suggestions what forum i could pester to find out how to? :biggrin:

---

### Post by fimbulvetr on 2007-08-05
> **genfinch said:**
> OK, here's the latest. i tried running ktorrent as root and the torrent worked fine BUT when i started other ones, their combined temporary files soon were too much for the root partition. i've only just recovered from the ensuing damage. well, i'm not changing my whole partition table, i only just got the whole thing set up the way i wanted it. so now i'm running ktorrent as myself agin and lo and behold, everything goes smoothly. i don't get it, but i'm certainly not gonna complain.
but i'm sure you guys are right and i should check that everything's in order with my drives. any suggestions what forum i could pester to find out how to? :biggrin:


```
[17354830.968000] FAT: Filesystem panic (dev sda1)
[17354830.968000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354830.968000]     File system has been set read-only
[17354830.968000] FAT: Filesystem panic (dev sda1)
[17354830.968000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354830.972000] FAT: Filesystem panic (dev sda1)
[17354830.972000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
[17354830.972000] FAT: Filesystem panic (dev sda1)
[17354830.972000]     fat_get_cluster: invalid cluster chain (i_pos 3180207840)
```

This was in the dmesg you pasted above. This means something is either disastrously wrong with your hard drive and you should be prepared for an imminent failure, OR that somethings wrong with the FAT kernel driver. Chances are that your hard drive is bad.

I can't stress this enough.

Install the package ```
 smartmontools
```

and run:

```

sudo smartctl -a /dev/hda

```

and paste the output in a reply.

---

