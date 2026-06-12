---
title: "Two almost 1GB log files - odd?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by dimbulb1024 on 2007-03-11
I have found two log files in the var/log folder that are almost 1 GB each.
kern.log.0 is 962.7 MB
messages.0 is 961.3 MB
Both where created on the 5th of March within minutes of each other. 

This seems very strange to me. Any ideas?

---

### Post by astrolabio on 2007-03-11
What there is inside?

do a
tail -n 100 logfile.log
to see the last 100 rows of that file

---

### Post by dimbulb1024 on 2007-03-11
Here is the info requested. Let me know if it means anything to you. Thanks

last 100 of kern.log.0

Mar  5 07:18:47 pconejo-laptop kernel: [17534740.720000] end_request: I/O error, dev sr0, sector 14293584
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.740000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.740000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.740000] end_request: I/O error, dev sr0, sector 14293592
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.760000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.760000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.760000] end_request: I/O error, dev sr0, sector 14293592
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.780000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.780000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.780000] end_request: I/O error, dev sr0, sector 14293600
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.800000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.800000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.800000] end_request: I/O error, dev sr0, sector 14293600
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.820000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.820000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.820000] end_request: I/O error, dev sr0, sector 14293608
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.840000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.840000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.840000] end_request: I/O error, dev sr0, sector 14293608
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.860000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.860000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.860000] end_request: I/O error, dev sr0, sector 14293616
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.880000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.880000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.880000] end_request: I/O error, dev sr0, sector 14293616
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.900000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.900000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.900000] end_request: I/O error, dev sr0, sector 14293624
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.920000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.920000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.920000] end_request: I/O error, dev sr0, sector 14293624
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.940000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.940000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.940000] end_request: I/O error, dev sr0, sector 14293632
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.960000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.960000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.960000] end_request: I/O error, dev sr0, sector 14293632
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.980000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.980000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.980000] end_request: I/O error, dev sr0, sector 14293640
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.000000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.000000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.000000] end_request: I/O error, dev sr0, sector 14293640
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.020000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.020000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.020000] end_request: I/O error, dev sr0, sector 14293648
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.040000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.040000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.040000] end_request: I/O error, dev sr0, sector 14293648
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.060000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.060000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.060000] end_request: I/O error, dev sr0, sector 14293656
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.080000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.080000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.080000] end_request: I/O error, dev sr0, sector 14293656
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.100000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.100000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.100000] end_request: I/O error, dev sr0, sector 14293664
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.120000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.120000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.120000] end_request: I/O error, dev sr0, sector 14293664
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.140000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.140000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.140000] end_request: I/O error, dev sr0, sector 14293672
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.160000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.160000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.160000] end_request: I/O error, dev sr0, sector 14293672
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.192000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.192000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.192000] end_request: I/O error, dev sr0, sector 14293680
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.224000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.224000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.224000] end_request: I/O error, dev sr0, sector 14293680
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.256000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.256000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.256000] end_request: I/O error, dev sr0, sector 14293688
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.288000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.288000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.288000] end_request: I/O error, dev sr0, sector 14293688
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.320000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.320000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.320000] end_request: I/O error, dev sr0, sector 14293696
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.356000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.356000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.356000] end_request: I/O error, dev sr0, sector 14293808
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.388000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.388000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.388000] end_request: I/O error, dev sr0, sector 14294008
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.408000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.408000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.408000] end_request: I/O error, dev sr0, sector 14293700
Mar  5 07:19:28 pconejo-laptop kernel: [17534781.796000] kjournald starting.  Commit interval 5 seconds
Mar  5 07:19:28 pconejo-laptop kernel: [17534781.808000] EXT3 FS on sdb1, internal journal
Mar  5 07:19:28 pconejo-laptop kernel: [17534781.808000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 07:31:49 pconejo-laptop kernel: [17535523.268000] kjournald starting.  Commit interval 5 seconds
Mar  5 07:31:50 pconejo-laptop kernel: [17535523.280000] EXT3 FS on sdb1, internal journal
Mar  5 07:31:50 pconejo-laptop kernel: [17535523.280000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 07:32:19 pconejo-laptop kernel: [17535552.604000] kjournald starting.  Commit interval 5 seconds
Mar  5 07:32:19 pconejo-laptop kernel: [17535552.616000] EXT3 FS on sdb1, internal journal
Mar  5 07:32:19 pconejo-laptop kernel: [17535552.616000] EXT3-fs: mounted filesystem with ordered data mode.


last 100 of message.0

Mar  5 07:18:47 pconejo-laptop kernel: [17534740.860000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.860000] end_request: I/O error, dev sr0, sector 14293616
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.880000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.880000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.880000] end_request: I/O error, dev sr0, sector 14293616
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.900000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.900000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.900000] end_request: I/O error, dev sr0, sector 14293624
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.920000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.920000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.920000] end_request: I/O error, dev sr0, sector 14293624
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.940000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.940000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.940000] end_request: I/O error, dev sr0, sector 14293632
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.960000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.960000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.960000] end_request: I/O error, dev sr0, sector 14293632
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.980000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.980000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534740.980000] end_request: I/O error, dev sr0, sector 14293640
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.000000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.000000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.000000] end_request: I/O error, dev sr0, sector 14293640
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.020000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.020000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.020000] end_request: I/O error, dev sr0, sector 14293648
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.040000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.040000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.040000] end_request: I/O error, dev sr0, sector 14293648
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.060000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.060000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.060000] end_request: I/O error, dev sr0, sector 14293656
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.080000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.080000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.080000] end_request: I/O error, dev sr0, sector 14293656
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.100000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.100000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.100000] end_request: I/O error, dev sr0, sector 14293664
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.120000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.120000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.120000] end_request: I/O error, dev sr0, sector 14293664
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.140000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.140000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.140000] end_request: I/O error, dev sr0, sector 14293672
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.160000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.160000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.160000] end_request: I/O error, dev sr0, sector 14293672
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.192000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.192000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.192000] end_request: I/O error, dev sr0, sector 14293680
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.224000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.224000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.224000] end_request: I/O error, dev sr0, sector 14293680
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.256000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.256000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.256000] end_request: I/O error, dev sr0, sector 14293688
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.288000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.288000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.288000] end_request: I/O error, dev sr0, sector 14293688
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.320000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.320000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.320000] end_request: I/O error, dev sr0, sector 14293696
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.356000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.356000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.356000] end_request: I/O error, dev sr0, sector 14293808
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.388000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.388000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.388000] end_request: I/O error, dev sr0, sector 14294008
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.408000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.408000]     Additional sense: Medium not present
Mar  5 07:18:47 pconejo-laptop kernel: [17534741.408000] end_request: I/O error, dev sr0, sector 14293700
Mar  5 07:19:02 pconejo-laptop gconfd (root-11792): starting (version 2.16.0), pid 11792 user 'root'
Mar  5 07:19:02 pconejo-laptop gconfd (root-11792): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  5 07:19:02 pconejo-laptop gconfd (root-11792): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar  5 07:19:02 pconejo-laptop gconfd (root-11792): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  5 07:19:02 pconejo-laptop gconfd (root-11792): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  5 07:19:02 pconejo-laptop gconfd (root-11792): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar  5 07:19:08 pconejo-laptop gconfd (root-11792): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 0
Mar  5 07:19:13 pconejo-laptop gconfd (dimbulb-11726): GConf server is not in use, shutting down.
Mar  5 07:19:13 pconejo-laptop gconfd (dimbulb-11726): Exiting
Mar  5 07:19:28 pconejo-laptop kernel: [17534781.796000] kjournald starting.  Commit interval 5 seconds
Mar  5 07:19:28 pconejo-laptop kernel: [17534781.808000] EXT3 FS on sdb1, internal journal
Mar  5 07:19:28 pconejo-laptop kernel: [17534781.808000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 07:31:49 pconejo-laptop kernel: [17535523.268000] kjournald starting.  Commit interval 5 seconds
Mar  5 07:31:50 pconejo-laptop kernel: [17535523.280000] EXT3 FS on sdb1, internal journal
Mar  5 07:31:50 pconejo-laptop kernel: [17535523.280000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 07:32:01 pconejo-laptop gnome-power-manager: (root) GNOME interactive logout because the power button has been pressed
Mar  5 07:32:03 pconejo-laptop gconfd (root-11792): Exiting
Mar  5 07:32:13 pconejo-laptop gconfd (dimbulb-12533): starting (version 2.16.0), pid 12533 user 'dimbulb'
Mar  5 07:32:13 pconejo-laptop gconfd (dimbulb-12533): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  5 07:32:13 pconejo-laptop gconfd (dimbulb-12533): Resolved address "xml:readwrite:/home/dimbulb/.gconf" to a writable configuration source at position 1
Mar  5 07:32:13 pconejo-laptop gconfd (dimbulb-12533): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  5 07:32:13 pconejo-laptop gconfd (dimbulb-12533): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  5 07:32:13 pconejo-laptop gconfd (dimbulb-12533): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar  5 07:32:19 pconejo-laptop kernel: [17535552.604000] kjournald starting.  Commit interval 5 seconds
Mar  5 07:32:19 pconejo-laptop kernel: [17535552.616000] EXT3 FS on sdb1, internal journal
Mar  5 07:32:19 pconejo-laptop kernel: [17535552.616000] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 07:32:20 pconejo-laptop gconfd (dimbulb-12533): Resolved address "xml:readwrite:/home/dimbulb/.gconf" to a writable configuration source at position 0
Mar  5 07:32:25 pconejo-laptop bonobo-activation-server (dimbulb-12570): Passing command-line arguments in .server files is deprecated: "/usr/bin/tomboy --panel-applet"
Mar  5 07:35:58 pconejo-laptop exiting on signal 15

---

### Post by dimbulb1024 on 2007-03-12
~ Update ~
The files have been gzip'ed by the system and now are very small and no worries anymore.

Still wonder why they where so big to begin with.

---

### Post by astrolabio on 2007-03-12
Looking at your post seems that you encountered some problem with your ext3 partition lately. To be sure of what exacly is the problem you should examine what those files contains as a whole. 

If they contains mostly stuff like that it might be that there's something wrong with your disk.

The last time I had something like that happening to me i had my disk die on me in two months,so you better do some buckup.

BUT I'M NOT EXPERT ENOUGH to help you with this. 

You should talk to some guy from the Hardware subforum or something about this. it might be a complete different problem, so don't panic and ask to more qualified people than me.

Hope you solve your problem. I'm really sorry i can't be of better help.:(

---

