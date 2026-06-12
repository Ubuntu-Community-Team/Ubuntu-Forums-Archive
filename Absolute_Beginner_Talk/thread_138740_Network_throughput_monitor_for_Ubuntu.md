---
title: "Network throughput monitor for Ubuntu"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by MatsB on 2006-03-02
Does anyone know of any good application that can give network utilization figures in Mbit/sec?

---

### Post by Vorian on 2006-03-02
there are a couple of gdesklets you could use....

---

### Post by MatsB on 2006-03-02
Hm, I tried to run apt-get install gdesklets gdesklets-data but it doesn't work:

# apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets

---

### Post by Vorian on 2006-03-02
strange... 

were you using root? (noticed the #)

This is the how-to


This requires some files and application.
1. Open the terminal and write:
Code:

sudo apt-get install gdesklets gdesklets-data


2. Now we want gdesklets to start automatically every time we boot up. Click System tab in the upper panel. Then Preferences ---> Sessions.
3. Click the Startup Programs tab and click the Add button.
4. In the startup Command write: gdesklets and click OK.
5. To choose and run the gdesklets stuff. Click the Applications tab in the upper panel. Then Accessories ---> gDesklets.
6. Have a look around and pick a gdesklet you like, to add it select the gdesklet. Then go to the file tab and select Run selected desklet.
7. Now the choosen gdesklet appears and will follow your mouse until you make a left click. To move it again click with middle mouse button or left+right mouse button.
8. To configure the choosen gdesklet, simply right click on it and menu will pop up.
9. For more gdesklets: [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

NOTE: Some gdesklets might need that you have some extra libs. installed. A good way is to find the gdesklets at [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) and check up on what you need to get the gdesklet you have choosen to work.

---

### Post by Thraxes on 2006-03-02
Netstat for the terminal is also pretty usefull.

---

### Post by MatsB on 2006-03-03
Still no luck :(

root@net:/home/net# netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.localdo:32769 localhost.localdo:39489 ESTABLISHED
tcp        0      0 192.168.0.121:45107     wailuku.xlogicgroup:www TIME_WAIT
tcp        0      0 localhost.localdo:39489 localhost.localdo:32769 ESTABLISHED
tcp        0      1 192.168.0.121:40834     localhost.localdoma:ipp SYN_SENT
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  4      [ ]         DGRAM                    27465    /dev/log
unix  2      [ ]         DGRAM                    4029     @udevd
unix  2      [ ]         DGRAM                    8214     @/var/run/hal/hotplug_socket2
unix  2      [ ]         DGRAM                    27600
unix  2      [ ]         DGRAM                    27524
unix  3      [ ]         STREAM     CONNECTED     24890    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     24889
unix  3      [ ]         STREAM     CONNECTED     24774    /tmp/orbit-net/linc-263a-0-2c7b4892586cf
unix  3      [ ]         STREAM     CONNECTED     24773
unix  3      [ ]         STREAM     CONNECTED     24770    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     24769
unix  3      [ ]         STREAM     CONNECTED     24759    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     24758
unix  3      [ ]         STREAM     CONNECTED     23176
unix  3      [ ]         STREAM     CONNECTED     23175
unix  3      [ ]         STREAM     CONNECTED     22836
unix  3      [ ]         STREAM     CONNECTED     22835
unix  3      [ ]         STREAM     CONNECTED     22687
unix  3      [ ]         STREAM     CONNECTED     22686
unix  3      [ ]         STREAM     CONNECTED     22683
unix  3      [ ]         STREAM     CONNECTED     22682
unix  3      [ ]         STREAM     CONNECTED     22679
unix  3      [ ]         STREAM     CONNECTED     22678
unix  3      [ ]         STREAM     CONNECTED     22675
unix  3      [ ]         STREAM     CONNECTED     22674
unix  3      [ ]         STREAM     CONNECTED     22671
unix  3      [ ]         STREAM     CONNECTED     22670
unix  3      [ ]         STREAM     CONNECTED     22667
unix  3      [ ]         STREAM     CONNECTED     22666
unix  3      [ ]         STREAM     CONNECTED     22663
unix  3      [ ]         STREAM     CONNECTED     22662
unix  3      [ ]         STREAM     CONNECTED     22659
unix  3      [ ]         STREAM     CONNECTED     22658
unix  3      [ ]         STREAM     CONNECTED     22655
unix  3      [ ]         STREAM     CONNECTED     22654
unix  3      [ ]         STREAM     CONNECTED     22651
unix  3      [ ]         STREAM     CONNECTED     22650
unix  3      [ ]         STREAM     CONNECTED     22647
unix  3      [ ]         STREAM     CONNECTED     22646
unix  3      [ ]         STREAM     CONNECTED     22643
unix  3      [ ]         STREAM     CONNECTED     22642
unix  3      [ ]         STREAM     CONNECTED     22639
unix  3      [ ]         STREAM     CONNECTED     22638
unix  3      [ ]         STREAM     CONNECTED     22635
unix  3      [ ]         STREAM     CONNECTED     22634
unix  3      [ ]         STREAM     CONNECTED     22631
unix  3      [ ]         STREAM     CONNECTED     22630
unix  3      [ ]         STREAM     CONNECTED     22627
unix  3      [ ]         STREAM     CONNECTED     22626
unix  3      [ ]         STREAM     CONNECTED     22623
unix  3      [ ]         STREAM     CONNECTED     22622
unix  3      [ ]         STREAM     CONNECTED     22619
unix  3      [ ]         STREAM     CONNECTED     22618
unix  3      [ ]         STREAM     CONNECTED     22615
unix  3      [ ]         STREAM     CONNECTED     22614
unix  3      [ ]         STREAM     CONNECTED     22611
unix  3      [ ]         STREAM     CONNECTED     22610
unix  3      [ ]         STREAM     CONNECTED     22607
unix  3      [ ]         STREAM     CONNECTED     22606
unix  3      [ ]         STREAM     CONNECTED     22603
unix  3      [ ]         STREAM     CONNECTED     22602
unix  3      [ ]         STREAM     CONNECTED     22599
unix  3      [ ]         STREAM     CONNECTED     22598
unix  3      [ ]         STREAM     CONNECTED     22595
unix  3      [ ]         STREAM     CONNECTED     22594
unix  3      [ ]         STREAM     CONNECTED     22591
unix  3      [ ]         STREAM     CONNECTED     22590
unix  3      [ ]         STREAM     CONNECTED     22588
unix  3      [ ]         STREAM     CONNECTED     22587
unix  3      [ ]         STREAM     CONNECTED     22584
unix  3      [ ]         STREAM     CONNECTED     22583
unix  3      [ ]         STREAM     CONNECTED     22581
unix  3      [ ]         STREAM     CONNECTED     22580
unix  2      [ ]         DGRAM                    22571
unix  3      [ ]         STREAM     CONNECTED     22040
unix  3      [ ]         STREAM     CONNECTED     22039
unix  3      [ ]         STREAM     CONNECTED     22036
unix  3      [ ]         STREAM     CONNECTED     22035
unix  2      [ ]         DGRAM                    14420
unix  3      [ ]         STREAM     CONNECTED     13892
unix  3      [ ]         STREAM     CONNECTED     13891
unix  3      [ ]         STREAM     CONNECTED     13889    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     13888
unix  3      [ ]         STREAM     CONNECTED     13867    /tmp/orbit-net/linc-1f23-0-4e83869a159c5
unix  3      [ ]         STREAM     CONNECTED     13866
unix  3      [ ]         STREAM     CONNECTED     13865    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     13864
unix  3      [ ]         STREAM     CONNECTED     13863    /tmp/orbit-net/linc-1f23-0-4e83869a159c5
unix  3      [ ]         STREAM     CONNECTED     13862
unix  3      [ ]         STREAM     CONNECTED     13859    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     13858
unix  3      [ ]         STREAM     CONNECTED     13857    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     13856
unix  3      [ ]         STREAM     CONNECTED     13852    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13851
unix  3      [ ]         STREAM     CONNECTED     11736    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11735
unix  3      [ ]         STREAM     CONNECTED     11729    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11728
unix  3      [ ]         STREAM     CONNECTED     11727    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11726
unix  3      [ ]         STREAM     CONNECTED     11725    /tmp/orbit-net/linc-1eb7-0-65f59ae1b556f
unix  3      [ ]         STREAM     CONNECTED     11724
unix  3      [ ]         STREAM     CONNECTED     11723    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11722
unix  3      [ ]         STREAM     CONNECTED     11716    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11715
unix  3      [ ]         STREAM     CONNECTED     11714    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11713
unix  3      [ ]         STREAM     CONNECTED     11711    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11710
unix  3      [ ]         STREAM     CONNECTED     11709    /tmp/orbit-net/linc-1eb9-0-65f59ae1c05f1
unix  3      [ ]         STREAM     CONNECTED     11707
unix  3      [ ]         STREAM     CONNECTED     11699    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11698
unix  3      [ ]         STREAM     CONNECTED     11697    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11696
unix  3      [ ]         STREAM     CONNECTED     11694    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11693
unix  3      [ ]         STREAM     CONNECTED     11692    /tmp/orbit-net/linc-1ebb-0-65f59ae1c67ca
unix  3      [ ]         STREAM     CONNECTED     11690
unix  3      [ ]         STREAM     CONNECTED     11686    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11685
unix  3      [ ]         STREAM     CONNECTED     11681    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11680
unix  3      [ ]         STREAM     CONNECTED     11679    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11678
unix  3      [ ]         STREAM     CONNECTED     11677    /tmp/orbit-net/linc-1ebd-0-b5f25cb9a1ab
unix  3      [ ]         STREAM     CONNECTED     11675
unix  3      [ ]         STREAM     CONNECTED     11666    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11665
unix  3      [ ]         STREAM     CONNECTED     11664    /tmp/orbit-net/linc-1ebd-0-b5f25cb9a1ab
unix  3      [ ]         STREAM     CONNECTED     11663
unix  3      [ ]         STREAM     CONNECTED     11662    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11661
unix  3      [ ]         STREAM     CONNECTED     11660    /tmp/orbit-net/linc-1ebd-0-b5f25cb9a1ab
unix  3      [ ]         STREAM     CONNECTED     11659
unix  3      [ ]         STREAM     CONNECTED     11656    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11655
unix  3      [ ]         STREAM     CONNECTED     11651    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11650
unix  3      [ ]         STREAM     CONNECTED     11647    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11646
unix  3      [ ]         STREAM     CONNECTED     11645    /tmp/orbit-net/linc-1ebf-0-b5f25cb13b18
unix  3      [ ]         STREAM     CONNECTED     11644
unix  3      [ ]         STREAM     CONNECTED     11637    /tmp/orbit-net/linc-1ebf-0-b5f25cb13b18
unix  3      [ ]         STREAM     CONNECTED     11636
unix  3      [ ]         STREAM     CONNECTED     11635    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11634
unix  3      [ ]         STREAM     CONNECTED     11633    /tmp/orbit-net/linc-1ebf-0-b5f25cb13b18
unix  3      [ ]         STREAM     CONNECTED     11632
unix  3      [ ]         STREAM     CONNECTED     11629    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11628
unix  3      [ ]         STREAM     CONNECTED     11624    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11623
unix  3      [ ]         STREAM     CONNECTED     11620    /tmp/orbit-net/linc-1ebb-0-65f59ae1c67ca
unix  3      [ ]         STREAM     CONNECTED     11617
unix  3      [ ]         STREAM     CONNECTED     11619    /tmp/orbit-net/linc-1eb9-0-65f59ae1c05f1
unix  3      [ ]         STREAM     CONNECTED     11616
unix  3      [ ]         STREAM     CONNECTED     11618    /tmp/orbit-net/linc-1eb7-0-65f59ae1b556f
unix  3      [ ]         STREAM     CONNECTED     11614
unix  3      [ ]         STREAM     CONNECTED     11615    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11611
unix  3      [ ]         STREAM     CONNECTED     11610    /tmp/orbit-net/linc-1ebb-0-65f59ae1c67ca
unix  3      [ ]         STREAM     CONNECTED     11609
unix  3      [ ]         STREAM     CONNECTED     11606    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11605
unix  3      [ ]         STREAM     CONNECTED     11601    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11600
unix  3      [ ]         STREAM     CONNECTED     11613    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11599
unix  3      [ ]         STREAM     CONNECTED     11598    /tmp/orbit-net/linc-1eb9-0-65f59ae1c05f1
unix  3      [ ]         STREAM     CONNECTED     11597
unix  3      [ ]         STREAM     CONNECTED     11594    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11593
unix  3      [ ]         STREAM     CONNECTED     11589    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11588
unix  3      [ ]         STREAM     CONNECTED     11612    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11585
unix  3      [ ]         STREAM     CONNECTED     11584    /tmp/orbit-net/linc-1eb7-0-65f59ae1b556f
unix  3      [ ]         STREAM     CONNECTED     11583
unix  3      [ ]         STREAM     CONNECTED     11580    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11579
unix  3      [ ]         STREAM     CONNECTED     11575    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11574
unix  3      [ ]         STREAM     CONNECTED     11557    /tmp/orbit-net/linc-1eb5-0-77843ecb84a74
unix  3      [ ]         STREAM     CONNECTED     11553
unix  3      [ ]         STREAM     CONNECTED     11546    /tmp/orbit-net/linc-1eb5-0-77843ecb84a74
unix  3      [ ]         STREAM     CONNECTED     11545
unix  3      [ ]         STREAM     CONNECTED     11544    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11543
unix  3      [ ]         STREAM     CONNECTED     11542    /tmp/orbit-net/linc-1eb5-0-77843ecb84a74
unix  3      [ ]         STREAM     CONNECTED     11541
unix  3      [ ]         STREAM     CONNECTED     11538    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11537
unix  3      [ ]         STREAM     CONNECTED     11533    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11532
unix  3      [ ]         STREAM     CONNECTED     11525    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11524
unix  3      [ ]         STREAM     CONNECTED     11511    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11510
unix  3      [ ]         STREAM     CONNECTED     11507    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11506
unix  3      [ ]         STREAM     CONNECTED     11505    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11504
unix  3      [ ]         STREAM     CONNECTED     11503    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11502
unix  3      [ ]         STREAM     CONNECTED     11501    /tmp/orbit-net/linc-1ea3-0-6c41b7c24288d
unix  3      [ ]         STREAM     CONNECTED     11500
unix  3      [ ]         STREAM     CONNECTED     11497    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11494
unix  3      [ ]         STREAM     CONNECTED     11492    /tmp/mapping-net
unix  3      [ ]         STREAM     CONNECTED     11484
unix  3      [ ]         STREAM     CONNECTED     11481    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11480
unix  3      [ ]         STREAM     CONNECTED     11479    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11478
unix  3      [ ]         STREAM     CONNECTED     11477    /tmp/orbit-net/linc-1e9c-0-3f97d6ec23d43
unix  3      [ ]         STREAM     CONNECTED     11476
unix  3      [ ]         STREAM     CONNECTED     11467    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11466
unix  3      [ ]         STREAM     CONNECTED     11463    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11462
unix  3      [ ]         STREAM     CONNECTED     11461    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11460
unix  3      [ ]         STREAM     CONNECTED     11459    /tmp/orbit-net/linc-1e9c-0-3f97d6ec23d43
unix  3      [ ]         STREAM     CONNECTED     11458
unix  3      [ ]         STREAM     CONNECTED     11457    /tmp/orbit-net/linc-1e90-0-4a60bac28badb
unix  3      [ ]         STREAM     CONNECTED     11456
unix  3      [ ]         STREAM     CONNECTED     11455    /tmp/orbit-net/linc-1ea3-0-6c41b7c24288d
unix  3      [ ]         STREAM     CONNECTED     11453
unix  3      [ ]         STREAM     CONNECTED     11452    /tmp/orbit-net/linc-1e9a-0-3f97d6ec346b8
unix  3      [ ]         STREAM     CONNECTED     11451
unix  3      [ ]         STREAM     CONNECTED     11454    /tmp/orbit-net/linc-1ea3-0-6c41b7c24288d
unix  3      [ ]         STREAM     CONNECTED     11442
unix  3      [ ]         STREAM     CONNECTED     11439    /tmp/orbit-net/linc-1ea3-0-6c41b7c24288d
unix  3      [ ]         STREAM     CONNECTED     11438
unix  3      [ ]         STREAM     CONNECTED     11437    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11436
unix  3      [ ]         STREAM     CONNECTED     11426    /tmp/orbit-net/linc-1e9e-0-3f97d6ec7d80b
unix  3      [ ]         STREAM     CONNECTED     11425
unix  3      [ ]         STREAM     CONNECTED     11424    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11423
unix  3      [ ]         STREAM     CONNECTED     11422    /tmp/orbit-net/linc-1e9e-0-3f97d6ec7d80b
unix  3      [ ]         STREAM     CONNECTED     11421
unix  3      [ ]         STREAM     CONNECTED     11416    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11415
unix  3      [ ]         STREAM     CONNECTED     11414    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11413
unix  3      [ ]         STREAM     CONNECTED     11412    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11411
unix  181    [ ]         STREAM     CONNECTED     11407    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11406
unix  3      [ ]         STREAM     CONNECTED     11401    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11400
unix  3      [ ]         STREAM     CONNECTED     11397    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11396
unix  3      [ ]         STREAM     CONNECTED     11395    /tmp/orbit-net/linc-1ea3-0-6c41b7c24288d
unix  3      [ ]         STREAM     CONNECTED     11394
unix  3      [ ]         STREAM     CONNECTED     11391    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11390
unix  3      [ ]         STREAM     CONNECTED     11383    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11382
unix  3      [ ]         STREAM     CONNECTED     11381    @/tmp/dbus-SYru5fNh6g
unix  3      [ ]         STREAM     CONNECTED     11380
unix  3      [ ]         STREAM     CONNECTED     11379    /tmp/orbit-net/linc-1e9a-0-3f97d6ec346b8
unix  3      [ ]         STREAM     CONNECTED     11377
unix  3      [ ]         STREAM     CONNECTED     11378    /tmp/orbit-net/linc-1e9c-0-3f97d6ec23d43
unix  3      [ ]         STREAM     CONNECTED     11376
unix  3      [ ]         STREAM     CONNECTED     11375    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11373
unix  3      [ ]         STREAM     CONNECTED     11372    /tmp/orbit-net/linc-1e9a-0-3f97d6ec346b8
unix  3      [ ]         STREAM     CONNECTED     11371
unix  3      [ ]         STREAM     CONNECTED     11368    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11367
unix  3      [ ]         STREAM     CONNECTED     11363    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11362
unix  3      [ ]         STREAM     CONNECTED     11374    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11359
unix  3      [ ]         STREAM     CONNECTED     11358    /tmp/orbit-net/linc-1e9c-0-3f97d6ec23d43
unix  3      [ ]         STREAM     CONNECTED     11357
unix  3      [ ]         STREAM     CONNECTED     11354    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11353
unix  3      [ ]         STREAM     CONNECTED     11349    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11348
unix  3      [ ]         STREAM     CONNECTED     11342    /tmp/orbit-net/linc-1e90-0-4a60bac28badb
unix  3      [ ]         STREAM     CONNECTED     11341
unix  3      [ ]         STREAM     CONNECTED     11340    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11339
unix  3      [ ]         STREAM     CONNECTED     11334    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11333
unix  3      [ ]         STREAM     CONNECTED     11324    @/tmp/dbus-SYru5fNh6g
unix  3      [ ]         STREAM     CONNECTED     11323
unix  3      [ ]         STREAM     CONNECTED     11322    /tmp/orbit-net/linc-1e98-0-4a60bac2ec5a3
unix  3      [ ]         STREAM     CONNECTED     11321
unix  3      [ ]         STREAM     CONNECTED     11318    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11317
unix  3      [ ]         STREAM     CONNECTED     11314    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11313
unix  3      [ ]         STREAM     CONNECTED     11309    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11308
unix  3      [ ]         STREAM     CONNECTED     11295    /tmp/orbit-net/linc-1e90-0-4a60bac28badb
unix  3      [ ]         STREAM     CONNECTED     11294
unix  3      [ ]         STREAM     CONNECTED     11291    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11290
unix  3      [ ]         STREAM     CONNECTED     11287    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11286
unix  3      [ ]         STREAM     CONNECTED     11282    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11281
unix  3      [ ]         STREAM     CONNECTED     11277    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11276
unix  3      [ ]         STREAM     CONNECTED     11273    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11272
unix  3      [ ]         STREAM     CONNECTED     11270    /tmp/orbit-net/linc-1e92-0-6454feb353811
unix  3      [ ]         STREAM     CONNECTED     11269
unix  3      [ ]         STREAM     CONNECTED     11266    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11265
unix  3      [ ]         STREAM     CONNECTED     11264    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11263
unix  3      [ ]         STREAM     CONNECTED     11259    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11258
unix  3      [ ]         STREAM     CONNECTED     11255    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11254
unix  3      [ ]         STREAM     CONNECTED     11253    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11252
unix  3      [ ]         STREAM     CONNECTED     11251    /tmp/orbit-net/linc-1e8e-0-6454feb31bb09
unix  3      [ ]         STREAM     CONNECTED     11250
unix  3      [ ]         STREAM     CONNECTED     11247    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11246
unix  3      [ ]         STREAM     CONNECTED     11245    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11240
unix  3      [ ]         STREAM     CONNECTED     11236    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11235
unix  3      [ ]         STREAM     CONNECTED     11228    /tmp/.ICE-unix/7723
unix  3      [ ]         STREAM     CONNECTED     11227
unix  3      [ ]         STREAM     CONNECTED     11226    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11225
unix  3      [ ]         STREAM     CONNECTED     11224    /tmp/orbit-net/linc-1e89-0-2cbdde2964cf8
unix  3      [ ]         STREAM     CONNECTED     11223
unix  3      [ ]         STREAM     CONNECTED     11220    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11219
unix  3      [ ]         STREAM     CONNECTED     11210    /tmp/orbit-net/linc-1e62-0-7b917a1d9746
unix  3      [ ]         STREAM     CONNECTED     11202
unix  3      [ ]         STREAM     CONNECTED     11173    /tmp/orbit-net/linc-1e62-0-7b917a1d9746
unix  3      [ ]         STREAM     CONNECTED     11172
unix  3      [ ]         STREAM     CONNECTED     11171    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11170
unix  3      [ ]         STREAM     CONNECTED     11163    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11162
unix  3      [ ]         STREAM     CONNECTED     11154    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11153
unix  3      [ ]         STREAM     CONNECTED     11128    @/tmp/fam-net-
unix  3      [ ]         STREAM     CONNECTED     11127
unix  3      [ ]         STREAM     CONNECTED     11120    /tmp/orbit-net/linc-1e62-0-7b917a1d9746
unix  3      [ ]         STREAM     CONNECTED     11119
unix  3      [ ]         STREAM     CONNECTED     11116    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     11115
unix  3      [ ]         STREAM     CONNECTED     11111    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11110
unix  3      [ ]         STREAM     CONNECTED     11102    /tmp/orbit-net/linc-1e2b-0-21895b67af1d
unix  3      [ ]         STREAM     CONNECTED     11101
unix  3      [ ]         STREAM     CONNECTED     11100    /tmp/orbit-net/linc-1e60-0-44230aa091f5d
unix  3      [ ]         STREAM     CONNECTED     11099
unix  3      [ ]         STREAM     CONNECTED     11084    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11079
unix  2      [ ]         STREAM                   11076
unix  3      [ ]         STREAM     CONNECTED     11037    /tmp/orbit-net/linc-1e2b-0-21895b67af1d
unix  3      [ ]         STREAM     CONNECTED     11036
unix  3      [ ]         STREAM     CONNECTED     11035    /tmp/orbit-net/linc-1e57-0-6befab30608db
unix  3      [ ]         STREAM     CONNECTED     10842
unix  2      [ ]         DGRAM                    10828
unix  3      [ ]         STREAM     CONNECTED     10822    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10821
unix  3      [ ]         STREAM     CONNECTED     10818    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10817
unix  3      [ ]         STREAM     CONNECTED     10816
unix  3      [ ]         STREAM     CONNECTED     10815
unix  3      [ ]         STREAM     CONNECTED     10481    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10480
unix  2      [ ]         DGRAM                    10473
unix  2      [ ]         DGRAM                    10459
unix  2      [ ]         DGRAM                    10281
unix  2      [ ]         DGRAM                    10045
unix  8      [ ]         STREAM     CONNECTED     10346    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10002
unix  3      [ ]         STREAM     CONNECTED     8658     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8657
unix  3      [ ]         STREAM     CONNECTED     8664     @/tmp/hald-local/dbus-eVecqWEsay
unix  3      [ ]         STREAM     CONNECTED     8656
unix  3      [ ]         STREAM     CONNECTED     8651     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     8608
unix  3      [ ]         STREAM     CONNECTED     8620     @/tmp/hald-local/dbus-eVecqWEsay
unix  3      [ ]         STREAM     CONNECTED     8607
unix  3      [ ]         STREAM     CONNECTED     8200
unix  3      [ ]         STREAM     CONNECTED     8199
unix  2      [ ]         DGRAM                    8187
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net#
root@net:/home/net# sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets
root@net:/home/net#

---

### Post by darf681 on 2006-03-03
Might try adding in the other repositories in Synaptic Package Manager, then try to install it.

---

### Post by MatsB on 2006-03-03
Other repositories works just fine.

---

### Post by Vorian on 2006-03-03
try it in sudo, not as a root.

---

### Post by DigitalXpert on 2006-07-11
The best I've used is iptraf.  Run it as root from a terminal.  Gives you alot of info and is better on your cpu than a desktop widget thats running all the time.  You can just fire it up when you need it.

---

