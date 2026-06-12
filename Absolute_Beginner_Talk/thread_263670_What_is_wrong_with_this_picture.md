---
title: "What is wrong with this picture?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by mchlor on 2006-09-23
Why does my ubuntu 6.06 i386 installs and runs everything from /tmp directory?  thanks.

```

arrowhead@dvd:/tmp$ netstat /?
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 192.168.1.2:51177       www1.itotf.net:www      ESTABLISHED
tcp        0      0 192.168.1.2:53133       216.239.63.104:www      ESTABLISHED
tcp        0      0 localhost:42457         localhost:50558         ESTABLISHED
tcp        0      0 localhost:50558         localhost:42457         ESTABLISHED
tcp        0      0 192.168.1.2:34445       rev177.asus.com:www     ESTABLISHED
udp        0      0 192.168.1.2:32851       192.168.1.1:domain      ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    13409    /dev/log
unix  2      [ ]         DGRAM                    5069     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    11234    @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     16961    /tmp/orbit-arrowhead/linc-224e-0-5663ca5a32f6d
unix  3      [ ]         STREAM     CONNECTED     16960
unix  3      [ ]         STREAM     CONNECTED     16957    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     16956
unix  3      [ ]         STREAM     CONNECTED     16951    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16950
unix  3      [ ]         STREAM     CONNECTED     16706    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     16705
unix  3      [ ]         STREAM     CONNECTED     16701    /tmp/orbit-arrowhead/linc-2129-0-14358f4b44127
unix  3      [ ]         STREAM     CONNECTED     16700
unix  3      [ ]         STREAM     CONNECTED     16697    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     16696
unix  3      [ ]         STREAM     CONNECTED     16693    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     16692
unix  3      [ ]         STREAM     CONNECTED     16688    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16687
unix  3      [ ]         STREAM     CONNECTED     16608
unix  3      [ ]         STREAM     CONNECTED     16607
unix  3      [ ]         STREAM     CONNECTED     16605    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     16604
unix  3      [ ]         STREAM     CONNECTED     16602    /tmp/orbit-arrowhead/linc-20f1-0-36410bc36571e
unix  3      [ ]         STREAM     CONNECTED     16601
unix  3      [ ]         STREAM     CONNECTED     16600    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     16599
unix  3      [ ]         STREAM     CONNECTED     16598    /tmp/orbit-arrowhead/linc-20f1-0-36410bc36571e
unix  3      [ ]         STREAM     CONNECTED     16597
unix  3      [ ]         STREAM     CONNECTED     16594    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     16593
unix  3      [ ]         STREAM     CONNECTED     16590    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     16589
unix  3      [ ]         STREAM     CONNECTED     16585    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16584
unix  3      [ ]         STREAM     CONNECTED     14497    /tmp/.X11-unix/X0
unix  4      [ ]         STREAM     CONNECTED     14496
unix  3      [ ]         STREAM     CONNECTED     14456    /tmp/orbit-arrowhead/linc-1aee-0-988dad2319e7
unix  3      [ ]         STREAM     CONNECTED     14455
unix  3      [ ]         STREAM     CONNECTED     14452    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     14451
unix  3      [ ]         STREAM     CONNECTED     14440    /tmp/.X11-unix/X0
unix  4      [ ]         STREAM     CONNECTED     14439
unix  3      [ ]         STREAM     CONNECTED     13769    /tmp/orbit-arrowhead/linc-1310-0-57100200c4a83
unix  3      [ ]         STREAM     CONNECTED     13768
unix  3      [ ]         STREAM     CONNECTED     13767    /tmp/orbit-arrowhead/linc-1593-0-5fae2d073f2b5
unix  3      [ ]         STREAM     CONNECTED     13766
unix  3      [ ]         STREAM     CONNECTED     13765    /tmp/orbit-arrowhead/linc-14f8-0-3cc57f5770de3
unix  3      [ ]         STREAM     CONNECTED     13764
unix  3      [ ]         STREAM     CONNECTED     13763    /tmp/orbit-arrowhead/linc-1593-0-5fae2d073f2b5
unix  3      [ ]         STREAM     CONNECTED     13762
unix  3      [ ]         STREAM     CONNECTED     13761    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     13760
unix  3      [ ]         STREAM     CONNECTED     13757    /tmp/orbit-arrowhead/linc-1593-0-5fae2d073f2b5
unix  3      [ ]         STREAM     CONNECTED     13756
unix  3      [ ]         STREAM     CONNECTED     13753    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     13752
unix  3      [ ]         STREAM     CONNECTED     13617    /tmp/orbit-arrowhead/linc-14f8-0-3cc57f5770de3
unix  3      [ ]         STREAM     CONNECTED     13616
unix  3      [ ]         STREAM     CONNECTED     13615    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     13614
unix  3      [ ]         STREAM     CONNECTED     13612    /tmp/orbit-arrowhead/linc-14f8-0-3cc57f5770de3
unix  3      [ ]         STREAM     CONNECTED     13611
unix  3      [ ]         STREAM     CONNECTED     13608    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     13607
unix  3      [ ]         STREAM     CONNECTED     13604    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     13603
unix  3      [ ]         STREAM     CONNECTED     13599    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13598
unix  3      [ ]         STREAM     CONNECTED     13438    @/tmp/dbus-eus7H6Y02j
unix  3      [ ]         STREAM     CONNECTED     13437
unix  3      [ ]         STREAM     CONNECTED     13436    /tmp/orbit-arrowhead/linc-1470-0-7770b77fd8e6d
unix  3      [ ]         STREAM     CONNECTED     13435
unix  3      [ ]         STREAM     CONNECTED     13432    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     13431
unix  3      [ ]         STREAM     CONNECTED     13427    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13426
unix  3      [ ]         STREAM     CONNECTED     13417    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     13416
unix  3      [ ]         STREAM     CONNECTED     13249    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     13248
unix  3      [ ]         STREAM     CONNECTED     12859    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12858
unix  3      [ ]         STREAM     CONNECTED     12857    @/tmp/dbus-eus7H6Y02j
unix  3      [ ]         STREAM     CONNECTED     12856
unix  3      [ ]         STREAM     CONNECTED     12855    /tmp/orbit-arrowhead/linc-1326-0-1850ef9f59b4b
unix  3      [ ]         STREAM     CONNECTED     12854
unix  3      [ ]         STREAM     CONNECTED     12851    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12850
unix  3      [ ]         STREAM     CONNECTED     12846    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12845
unix  3      [ ]         STREAM     CONNECTED     12773    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12772
unix  3      [ ]         STREAM     CONNECTED     12771    /tmp/orbit-arrowhead/linc-12e1-0-1e0876d72e1a0
unix  3      [ ]         STREAM     CONNECTED     12770
unix  3      [ ]         STREAM     CONNECTED     12769    /tmp/orbit-arrowhead/linc-130e-0-571002006ff4a
unix  3      [ ]         STREAM     CONNECTED     12768
unix  3      [ ]         STREAM     CONNECTED     12764    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12763
unix  3      [ ]         STREAM     CONNECTED     12762    /tmp/orbit-arrowhead/linc-12e1-0-1e0876d72e1a0
unix  3      [ ]         STREAM     CONNECTED     12761
unix  3      [ ]         STREAM     CONNECTED     12760    /tmp/orbit-arrowhead/linc-1310-0-57100200c4a83
unix  3      [ ]         STREAM     CONNECTED     12758
unix  3      [ ]         STREAM     CONNECTED     12750    /tmp/orbit-arrowhead/linc-1310-0-57100200c4a83
unix  3      [ ]         STREAM     CONNECTED     12749
unix  3      [ ]         STREAM     CONNECTED     12748    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12747
unix  3      [ ]         STREAM     CONNECTED     12746    /tmp/orbit-arrowhead/linc-1310-0-57100200c4a83
unix  3      [ ]         STREAM     CONNECTED     12745
unix  3      [ ]         STREAM     CONNECTED     12742    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12741
unix  3      [ ]         STREAM     CONNECTED     12737    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12736
unix  3      [ ]         STREAM     CONNECTED     12733    /tmp/orbit-arrowhead/linc-130e-0-571002006ff4a
unix  3      [ ]         STREAM     CONNECTED     12732
unix  3      [ ]         STREAM     CONNECTED     12731    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12730
unix  3      [ ]         STREAM     CONNECTED     12729    /tmp/orbit-arrowhead/linc-130e-0-571002006ff4a
unix  3      [ ]         STREAM     CONNECTED     12728
unix  3      [ ]         STREAM     CONNECTED     12725    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12724
unix  3      [ ]         STREAM     CONNECTED     12720    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12719
unix  3      [ ]         STREAM     CONNECTED     12706    /tmp/mapping-arrowhead
unix  3      [ ]         STREAM     CONNECTED     12698
unix  3      [ ]         STREAM     CONNECTED     12696    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12693
unix  3      [ ]         STREAM     CONNECTED     12689    /tmp/orbit-arrowhead/linc-12e1-0-1e0876d72e1a0
unix  3      [ ]         STREAM     CONNECTED     12688
unix  3      [ ]         STREAM     CONNECTED     12687    /tmp/orbit-arrowhead/linc-12f1-0-31be2cdae8890
unix  3      [ ]         STREAM     CONNECTED     12686
unix  3      [ ]         STREAM     CONNECTED     12680    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12679
unix  3      [ ]         STREAM     CONNECTED     12678    /tmp/orbit-arrowhead/linc-12e1-0-1e0876d72e1a0
unix  3      [ ]         STREAM     CONNECTED     12677
unix  3      [ ]         STREAM     CONNECTED     12676    /tmp/orbit-arrowhead/linc-1303-0-3300398e552aa
unix  3      [ ]         STREAM     CONNECTED     12675
unix  3      [ ]         STREAM     CONNECTED     12668    /tmp/orbit-arrowhead/linc-1303-0-3300398e552aa
unix  3      [ ]         STREAM     CONNECTED     12667
unix  3      [ ]         STREAM     CONNECTED     12666    /tmp/orbit-arrowhead/linc-12f1-0-31be2cdae8890
unix  3      [ ]         STREAM     CONNECTED     12665
unix  3      [ ]         STREAM     CONNECTED     12662    /tmp/orbit-arrowhead/linc-1303-0-3300398e552aa
unix  3      [ ]         STREAM     CONNECTED     12661
unix  3      [ ]         STREAM     CONNECTED     12660    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12659
unix  3      [ ]         STREAM     CONNECTED     12658    /tmp/orbit-arrowhead/linc-1303-0-3300398e552aa
unix  3      [ ]         STREAM     CONNECTED     12657
unix  3      [ ]         STREAM     CONNECTED     12654    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12653
unix  3      [ ]         STREAM     CONNECTED     12648    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12647
unix  3      [ ]         STREAM     CONNECTED     12630    /tmp/orbit-arrowhead/linc-12f5-0-da39aa7654e1
unix  3      [ ]         STREAM     CONNECTED     12629
unix  3      [ ]         STREAM     CONNECTED     12628    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12627
unix  3      [ ]         STREAM     CONNECTED     12626    /tmp/orbit-arrowhead/linc-12f5-0-da39aa7654e1
unix  3      [ ]         STREAM     CONNECTED     12625
unix  3      [ ]         STREAM     CONNECTED     12622    @/tmp/dbus-eus7H6Y02j
unix  3      [ ]         STREAM     CONNECTED     12621
unix  3      [ ]         STREAM     CONNECTED     12620    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12619
unix  2      [ ]         DGRAM                    12618
unix  3      [ ]         STREAM     CONNECTED     12617    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12616
unix  3      [ ]         STREAM     CONNECTED     12613    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12612
unix  3      [ ]         STREAM     CONNECTED     12608    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12607
unix  3      [ ]         STREAM     CONNECTED     12604    /tmp/orbit-arrowhead/linc-12f3-0-da39aa74903b
unix  3      [ ]         STREAM     CONNECTED     12603
unix  3      [ ]         STREAM     CONNECTED     12600    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12598
unix  3      [ ]         STREAM     CONNECTED     12595    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12594
unix  3      [ ]         STREAM     CONNECTED     12590    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12589
unix  3      [ ]         STREAM     CONNECTED     12586    /tmp/orbit-arrowhead/linc-12e3-0-1e0876d75a596
unix  3      [ ]         STREAM     CONNECTED     12585
unix  3      [ ]         STREAM     CONNECTED     12584    /tmp/orbit-arrowhead/linc-12f1-0-31be2cdae8890
unix  3      [ ]         STREAM     CONNECTED     12583
unix  3      [ ]         STREAM     CONNECTED     12580    /tmp/orbit-arrowhead/linc-12f1-0-31be2cdae8890
unix  3      [ ]         STREAM     CONNECTED     12579
unix  3      [ ]         STREAM     CONNECTED     12578    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12577
unix  3      [ ]         STREAM     CONNECTED     12571    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12570
unix  3      [ ]         STREAM     CONNECTED     12572    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12569
unix  3      [ ]         STREAM     CONNECTED     12568    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12567
unix  3      [ ]         STREAM     CONNECTED     12566    /tmp/orbit-arrowhead/linc-12f1-0-31be2cdae8890
unix  3      [ ]         STREAM     CONNECTED     12565
unix  3      [ ]         STREAM     CONNECTED     12562    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12561
unix  3      [ ]         STREAM     CONNECTED     12552    @/tmp/dbus-eus7H6Y02j
unix  3      [ ]         STREAM     CONNECTED     12551
unix  3      [ ]         STREAM     CONNECTED     12550    /tmp/orbit-arrowhead/linc-12ee-0-1e0876d7dabf5
unix  3      [ ]         STREAM     CONNECTED     12549
unix  3      [ ]         STREAM     CONNECTED     12546    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12545
unix  3      [ ]         STREAM     CONNECTED     12540    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12539
unix  3      [ ]         STREAM     CONNECTED     12535    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12534
unix  3      [ ]         STREAM     CONNECTED     12531    /tmp/orbit-arrowhead/linc-12d2-0-7be0bcae87a58
unix  3      [ ]         STREAM     CONNECTED     12530
unix  3      [ ]         STREAM     CONNECTED     12524    /tmp/orbit-arrowhead/linc-12e3-0-1e0876d75a596
unix  3      [ ]         STREAM     CONNECTED     12523
unix  3      [ ]         STREAM     CONNECTED     12522    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12521
unix  3      [ ]         STREAM     CONNECTED     12481    /tmp/orbit-arrowhead/linc-12e3-0-1e0876d75a596
unix  3      [ ]         STREAM     CONNECTED     12479
unix  3      [ ]         STREAM     CONNECTED     12475    /tmp/orbit-arrowhead/linc-12d2-0-7be0bcae87a58
unix  3      [ ]         STREAM     CONNECTED     12474
unix  3      [ ]         STREAM     CONNECTED     12473    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12472
unix  3      [ ]         STREAM     CONNECTED     12476    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12471
unix  3      [ ]         STREAM     CONNECTED     12468    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12467
unix  3      [ ]         STREAM     CONNECTED     12463    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12462
unix  3      [ ]         STREAM     CONNECTED     12457    /tmp/orbit-arrowhead/linc-12e1-0-1e0876d72e1a0
unix  3      [ ]         STREAM     CONNECTED     12456
unix  3      [ ]         STREAM     CONNECTED     12455    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12454
unix  3      [ ]         STREAM     CONNECTED     12449    @/tmp/dbus-eus7H6Y02j
unix  3      [ ]         STREAM     CONNECTED     12448
unix  3      [ ]         STREAM     CONNECTED     12446    /tmp/orbit-arrowhead/linc-12e1-0-1e0876d72e1a0
unix  3      [ ]         STREAM     CONNECTED     12445
unix  3      [ ]         STREAM     CONNECTED     12442    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12441
unix  3      [ ]         STREAM     CONNECTED     12438    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12437
unix  3      [ ]         STREAM     CONNECTED     12433    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12432
unix  3      [ ]         STREAM     CONNECTED     12429    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12428
unix  3      [ ]         STREAM     CONNECTED     12427    /tmp/orbit-arrowhead/linc-12e5-0-1e0876d71bdc1
unix  3      [ ]         STREAM     CONNECTED     12426
unix  3      [ ]         STREAM     CONNECTED     12423    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12422
unix  3      [ ]         STREAM     CONNECTED     12419    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12418
unix  3      [ ]         STREAM     CONNECTED     12414    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12413
unix  3      [ ]         STREAM     CONNECTED     12402    /tmp/.ICE-unix/4763
unix  3      [ ]         STREAM     CONNECTED     12401
unix  3      [ ]         STREAM     CONNECTED     12399    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12398
unix  3      [ ]         STREAM     CONNECTED     12397    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12396
unix  3      [ ]         STREAM     CONNECTED     12395    /tmp/orbit-arrowhead/linc-12db-0-101d6e236890a
unix  3      [ ]         STREAM     CONNECTED     12394
unix  3      [ ]         STREAM     CONNECTED     12391    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12390
unix  3      [ ]         STREAM     CONNECTED     12371    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12370
unix  2      [ ]         STREAM                   12361
unix  3      [ ]         STREAM     CONNECTED     12357    /tmp/orbit-arrowhead/linc-12d2-0-7be0bcae87a58
unix  3      [ ]         STREAM     CONNECTED     12356
unix  3      [ ]         STREAM     CONNECTED     12353    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12352
unix  3      [ ]         STREAM     CONNECTED     12348    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12347
unix  3      [ ]         STREAM     CONNECTED     12336    /tmp/orbit-arrowhead/linc-129b-0-45d9ab106cb52
unix  3      [ ]         STREAM     CONNECTED     12335
unix  3      [ ]         STREAM     CONNECTED     12334    /tmp/orbit-arrowhead/linc-12d0-0-451b21f41663
unix  3      [ ]         STREAM     CONNECTED     12333
unix  3      [ ]         STREAM     CONNECTED     12295    /tmp/orbit-arrowhead/linc-129b-0-45d9ab106cb52
unix  3      [ ]         STREAM     CONNECTED     12294
unix  3      [ ]         STREAM     CONNECTED     12293    /tmp/orbit-arrowhead/linc-12cb-0-1f3ff0eb5af28
unix  3      [ ]         STREAM     CONNECTED     12148
unix  2      [ ]         DGRAM                    12134
unix  3      [ ]         STREAM     CONNECTED     12128    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12127
unix  3      [ ]         STREAM     CONNECTED     12124    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12123
unix  3      [ ]         STREAM     CONNECTED     12122
unix  3      [ ]         STREAM     CONNECTED     12121
unix  3      [ ]         STREAM     CONNECTED     11770    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11769
unix  2      [ ]         DGRAM                    11750
unix  2      [ ]         DGRAM                    11741
unix  3      [ ]         STREAM     CONNECTED     11630    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11629
unix  3      [ ]         STREAM     CONNECTED     11608    @/tmp/hald-local/dbus-dqEIkAnTRC
unix  3      [ ]         STREAM     CONNECTED     11606
unix  3      [ ]         STREAM     CONNECTED     11607    @/tmp/hald-local/dbus-dqEIkAnTRC
unix  3      [ ]         STREAM     CONNECTED     11600
unix  3      [ ]         STREAM     CONNECTED     11582    @/tmp/hald-local/dbus-dqEIkAnTRC
unix  3      [ ]         STREAM     CONNECTED     11580
unix  3      [ ]         STREAM     CONNECTED     11581    @/tmp/hald-local/dbus-dqEIkAnTRC
unix  3      [ ]         STREAM     CONNECTED     11574
unix  3      [ ]         STREAM     CONNECTED     11548    @/tmp/hald-local/dbus-dqEIkAnTRC
unix  3      [ ]         STREAM     CONNECTED     11543
unix  3      [ ]         STREAM     CONNECTED     11407    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     11406
unix  3      [ ]         STREAM     CONNECTED     11410    @/tmp/hald-local/dbus-dqEIkAnTRC
unix  3      [ ]         STREAM     CONNECTED     11401
unix  3      [ ]         STREAM     CONNECTED     11229    @/tmp/hald-runner/dbus-lLRdojE8j8
unix  3      [ ]         STREAM     CONNECTED     11228
unix  3      [ ]         STREAM     CONNECTED     11205
unix  3      [ ]         STREAM     CONNECTED     11204
unix  2      [ ]         DGRAM                    11062
unix  4      [ ]         STREAM     CONNECTED     11419    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11035
unix  2      [ ]         DGRAM                    10138
arrowhead@dvd:/tmp$

```

Also please How can I install Ethereal?  apt-get don't work and it's not in synaptic.  thanks.

---

### Post by bulldog on 2006-09-23
Have no clough,but if it comforts you,mine does the same.

Think its the same as in Windows temp folder.

It's in synaptic to install.

Have you the Universe and Multiverse repo's enabled?
And all the others for that matter.

My sources.list:

## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main #restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo2
##deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./


##Xgl/Compiz
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

##Moblock
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main

##Test
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

##Asher repo's
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

## Canonical commercial repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by whizbaby on 2006-09-23
/tmp is used by applications to store session-related and similar data (e.g. X0-lock), nothing runs *in* /tmp.

---

### Post by DigitalAxis on 2006-09-23
Ethereal is in the Universe repository, which you'll have to activate yourself

A quick guide: In Synaptic, go to "Settings", then go to "Repositories", then scroll down until you see "Ubuntu 6.06 LTS (Binary)" with "Community-maintained (Universe)" and "Non-free (Multiverse)" in smaller letters.  Click that box to enable it; then close the window and have Synaptic re-load information.

If that didn't help, there are many guides on these forums, and in the [Wiki]("https://help.ubuntu.com/community"), that can help you. 

What you're listing is the network connections, most of which are linked to temporary files in your temporary directory.  Ubuntu installs the software itself and everything else in other folders- type **ls /usr/bin** and **ls /etc** to see the programs and the configuration files folders.

---

### Post by mchlor on 2006-09-23
Thank you thank you thank you!!!

---

