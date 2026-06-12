---
title: "PPPOE - cannot connect to the internet"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by AdHaR on 2007-12-15
Hi everyone,

I have a pppoe connection from my ISP. I am recently not being able to connect to the internet. Initially to setup my connection I used
```
sudo pppoeconf
```
I used all the defaults that it suggested. To turn on the connection each time i use
```
sudo pon dsl-provider
```
and to turn off
```
sudo poff
```

Now what is happening is that I start the connection using pon, but i cant access any sites using my browser (firefox, epiphany). I tried
```
ps -e
```
to make sure that pppd is running (which it is), and then tried pinging
```
ping ubuntuforums.org
```
but it says
```
ping: unknown host ubuntufourms.org
```

I even tried restarting the networking by doing
```
sudo /etc/init.d/networking restart
```
still no luck :(

Please help me...I am getting insane to point that I am thinking of reinstalling gutsy...or worse yet...go back to windows... :(

Oh btw this is the output from ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:BB:5C:D7  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:febb:5cd7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12696 (12.3 KB)  TX bytes:5724 (5.5 KB)
          Interrupt:22 Base address:0xc400 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:2D:1F:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:14483235 (13.8 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110468 (107.8 KB)  TX bytes:110468 (107.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:67.70.123.131  P-t-P:64.230.197.230  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3139 (3.0 KB)  TX bytes:54 (54.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.126.1  Bcast:172.16.126.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
and plog does not output anything

---

### Post by dcstar on 2007-12-15
> **AdHaR said:**
> Hi everyone,

I have a pppoe connection from my ISP. I am recently not being able to connect to the internet. Initially to setup my connection I used
.......
Post the output of:
```
netstat -rn
cat /etc/hosts
```

---

### Post by AdHaR on 2007-12-15
netstat ->
```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
udp        0      0 127.0.0.1:1025          127.0.0.1:1025          ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  18     [ ]         DGRAM                    15903    /dev/log
unix  2      [ ]         DGRAM                    8367     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    8788     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    16078    @/org/freedesktop/hal/udev_event
unix  2      [ ]         DGRAM                    154856   
unix  2      [ ]         DGRAM                    153687   
unix  2      [ ]         DGRAM                    153307   
unix  3      [ ]         STREAM     CONNECTED     151106   @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     151105   
unix  3      [ ]         STREAM     CONNECTED     151104   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     151103   
unix  3      [ ]         STREAM     CONNECTED     110587   /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     110586   
unix  3      [ ]         STREAM     CONNECTED     110583   /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     110582   
unix  3      [ ]         STREAM     CONNECTED     108880   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     108879   
unix  3      [ ]         STREAM     CONNECTED     108731   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     108730   
unix  3      [ ]         STREAM     CONNECTED     108701   @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     108700   
unix  3      [ ]         STREAM     CONNECTED     108684   /tmp/orbit-k8c/linc-22c6-0-36ad8a77344f3
unix  3      [ ]         STREAM     CONNECTED     108683   
unix  3      [ ]         STREAM     CONNECTED     108680   /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     108679   
unix  3      [ ]         STREAM     CONNECTED     108673   /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     108672   
unix  3      [ ]         STREAM     CONNECTED     108668   /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     108667   
unix  3      [ ]         STREAM     CONNECTED     108493   socket
unix  3      [ ]         STREAM     CONNECTED     108477   
unix  3      [ ]         STREAM     CONNECTED     108396   /tmp/orbit-k8c/linc-22bb-0-6033d8fa8ef25
unix  3      [ ]         STREAM     CONNECTED     108395   
unix  3      [ ]         STREAM     CONNECTED     108392   /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     108391   
unix  3      [ ]         STREAM     CONNECTED     108267   /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     108266   
unix  3      [ ]         STREAM     CONNECTED     62621    @/tmp/fam-k8c-
unix  3      [ ]         STREAM     CONNECTED     62620    
unix  2      [ ]         DGRAM                    62547    
unix  3      [ ]         STREAM     CONNECTED     26978    
unix  3      [ ]         STREAM     CONNECTED     26977    
unix  3      [ ]         STREAM     CONNECTED     26938    /tmp/orbit-k8c/linc-191a-0-30b0096798e27
unix  3      [ ]         STREAM     CONNECTED     26936    
unix  3      [ ]         STREAM     CONNECTED     26935    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     26934    
unix  3      [ ]         STREAM     CONNECTED     26933    /tmp/orbit-k8c/linc-191a-0-30b0096798e27
unix  3      [ ]         STREAM     CONNECTED     26932    
unix  3      [ ]         STREAM     CONNECTED     26929    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     26928    
unix  3      [ ]         STREAM     CONNECTED     26924    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     26923    
unix  3      [ ]         STREAM     CONNECTED     26919    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     26918    
unix  3      [ ]         STREAM     CONNECTED     23866    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     23865    
unix  2      [ ]         DGRAM                    23348    
unix  3      [ ]         STREAM     CONNECTED     22275    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22274    
unix  3      [ ]         STREAM     CONNECTED     22272    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22271    
unix  3      [ ]         STREAM     CONNECTED     22269    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22268    
unix  3      [ ]         STREAM     CONNECTED     22267    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22266    
unix  3      [ ]         STREAM     CONNECTED     22264    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22263    
unix  3      [ ]         STREAM     CONNECTED     22262    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22261    
unix  3      [ ]         STREAM     CONNECTED     22259    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22258    
unix  3      [ ]         STREAM     CONNECTED     22256    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22255    
unix  3      [ ]         STREAM     CONNECTED     22254    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22253    
unix  3      [ ]         STREAM     CONNECTED     22251    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22250    
unix  3      [ ]         STREAM     CONNECTED     22248    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22247    
unix  3      [ ]         STREAM     CONNECTED     22245    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22244    
unix  3      [ ]         STREAM     CONNECTED     22243    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22242    
unix  3      [ ]         STREAM     CONNECTED     22240    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22239    
unix  3      [ ]         STREAM     CONNECTED     22238    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22237    
unix  3      [ ]         STREAM     CONNECTED     22235    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22234    
unix  3      [ ]         STREAM     CONNECTED     22233    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22232    
unix  3      [ ]         STREAM     CONNECTED     22230    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     22229    
unix  3      [ ]         STREAM     CONNECTED     22228    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22227    
unix  3      [ ]         STREAM     CONNECTED     22226    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22225    
unix  3      [ ]         STREAM     CONNECTED     22224    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22223    
unix  3      [ ]         STREAM     CONNECTED     22222    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22221    
unix  3      [ ]         STREAM     CONNECTED     22220    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22219    
unix  3      [ ]         STREAM     CONNECTED     22218    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22217    
unix  3      [ ]         STREAM     CONNECTED     22191    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     22190    
unix  3      [ ]         STREAM     CONNECTED     22189    /tmp/orbit-k8c/linc-18a9-0-31c20e80c8c26
unix  3      [ ]         STREAM     CONNECTED     22188    
unix  3      [ ]         STREAM     CONNECTED     22181    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     22180    
unix  3      [ ]         STREAM     CONNECTED     22178    /tmp/orbit-k8c/linc-18a9-0-31c20e80c8c26
unix  3      [ ]         STREAM     CONNECTED     22177    
unix  3      [ ]         STREAM     CONNECTED     22176    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     22175    
unix  3      [ ]         STREAM     CONNECTED     22174    /tmp/orbit-k8c/linc-18a9-0-31c20e80c8c26
unix  3      [ ]         STREAM     CONNECTED     22173    
unix  3      [ ]         STREAM     CONNECTED     22170    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     22169    
unix  3      [ ]         STREAM     CONNECTED     22165    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22164    
unix  3      [ ]         STREAM     CONNECTED     22139    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     22138    
unix  3      [ ]         STREAM     CONNECTED     22137    /tmp/orbit-k8c/linc-189d-0-f3c664d1df7f
unix  3      [ ]         STREAM     CONNECTED     22136    
unix  3      [ ]         STREAM     CONNECTED     22078    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     22077    
unix  3      [ ]         STREAM     CONNECTED     22076    /tmp/orbit-k8c/linc-189f-0-f3c664dca312
unix  3      [ ]         STREAM     CONNECTED     22075    
unix  3      [ ]         STREAM     CONNECTED     22067    /tmp/orbit-k8c/linc-189f-0-f3c664dca312
unix  3      [ ]         STREAM     CONNECTED     22066    
unix  3      [ ]         STREAM     CONNECTED     22065    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     22064    
unix  3      [ ]         STREAM     CONNECTED     22063    /tmp/orbit-k8c/linc-189f-0-f3c664dca312
unix  3      [ ]         STREAM     CONNECTED     22062    
unix  3      [ ]         STREAM     CONNECTED     22059    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     22058    
unix  3      [ ]         STREAM     CONNECTED     22054    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22053    
unix  3      [ ]         STREAM     CONNECTED     22049    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     22048    
unix  3      [ ]         STREAM     CONNECTED     22047    /tmp/orbit-k8c/linc-18a1-0-f3c664da1086
unix  3      [ ]         STREAM     CONNECTED     22046    
unix  3      [ ]         STREAM     CONNECTED     22037    /tmp/orbit-k8c/linc-18a1-0-f3c664da1086
unix  3      [ ]         STREAM     CONNECTED     22036    
unix  3      [ ]         STREAM     CONNECTED     22035    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     22034    
unix  3      [ ]         STREAM     CONNECTED     22033    /tmp/orbit-k8c/linc-18a1-0-f3c664da1086
unix  3      [ ]         STREAM     CONNECTED     22032    
unix  3      [ ]         STREAM     CONNECTED     22029    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     22028    
unix  3      [ ]         STREAM     CONNECTED     22024    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     22023    
unix  3      [ ]         STREAM     CONNECTED     22017    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     22016    
unix  3      [ ]         STREAM     CONNECTED     22015    /tmp/orbit-k8c/linc-18a3-0-f3c664d5f86f
unix  3      [ ]         STREAM     CONNECTED     22014    
unix  3      [ ]         STREAM     CONNECTED     22007    /tmp/orbit-k8c/linc-18a3-0-f3c664d5f86f
unix  3      [ ]         STREAM     CONNECTED     22006    
unix  3      [ ]         STREAM     CONNECTED     22005    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     22004    
unix  3      [ ]         STREAM     CONNECTED     22003    /tmp/orbit-k8c/linc-18a3-0-f3c664d5f86f
unix  3      [ ]         STREAM     CONNECTED     22002    
unix  3      [ ]         STREAM     CONNECTED     21999    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     21998    
unix  3      [ ]         STREAM     CONNECTED     21994    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     21993    
unix  3      [ ]         STREAM     CONNECTED     21988    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     21987    
unix  3      [ ]         STREAM     CONNECTED     21986    /tmp/orbit-k8c/linc-189d-0-f3c664d1df7f
unix  3      [ ]         STREAM     CONNECTED     21985    
unix  3      [ ]         STREAM     CONNECTED     21984    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     21983    
unix  3      [ ]         STREAM     CONNECTED     21982    /tmp/orbit-k8c/linc-189d-0-f3c664d1df7f
unix  3      [ ]         STREAM     CONNECTED     21981    
unix  3      [ ]         STREAM     CONNECTED     21978    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     21977    
unix  3      [ ]         STREAM     CONNECTED     21973    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     21972    
unix  3      [ ]         STREAM     CONNECTED     21787    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     21786    
unix  3      [ ]         STREAM     CONNECTED     21785    /tmp/orbit-k8c/linc-1889-0-6a43ae3e593d8
unix  3      [ ]         STREAM     CONNECTED     21784    
unix  3      [ ]         STREAM     CONNECTED     21777    /tmp/orbit-k8c/linc-1889-0-6a43ae3e593d8
unix  3      [ ]         STREAM     CONNECTED     21776    
unix  3      [ ]         STREAM     CONNECTED     21775    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     21774    
unix  3      [ ]         STREAM     CONNECTED     21773    /tmp/orbit-k8c/linc-1889-0-6a43ae3e593d8
unix  3      [ ]         STREAM     CONNECTED     21772    
unix  3      [ ]         STREAM     CONNECTED     21769    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     21768    
unix  3      [ ]         STREAM     CONNECTED     21764    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     21763    
unix  3      [ ]         STREAM     CONNECTED     21757    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     21756    
unix  3      [ ]         STREAM     CONNECTED     21755    /tmp/orbit-k8c/linc-188b-0-398ce1325403e
unix  3      [ ]         STREAM     CONNECTED     21754    
unix  3      [ ]         STREAM     CONNECTED     21747    /tmp/orbit-k8c/linc-188b-0-398ce1325403e
unix  3      [ ]         STREAM     CONNECTED     21746    
unix  3      [ ]         STREAM     CONNECTED     21745    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     21744    
unix  3      [ ]         STREAM     CONNECTED     21743    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21742    
unix  3      [ ]         STREAM     CONNECTED     21741    /tmp/orbit-k8c/linc-188b-0-398ce1325403e
unix  3      [ ]         STREAM     CONNECTED     21740    
unix  3      [ ]         STREAM     CONNECTED     21737    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     21736    
unix  3      [ ]         STREAM     CONNECTED     21732    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     21731    
unix  3      [ ]         STREAM     CONNECTED     21716    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     21715    
unix  3      [ ]         STREAM     CONNECTED     21713    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     21712    
unix  3      [ ]         STREAM     CONNECTED     21711    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     21710    
unix  3      [ ]         STREAM     CONNECTED     21709    /tmp/orbit-k8c/linc-1883-0-2435ac29e4c41
unix  3      [ ]         STREAM     CONNECTED     21708    
unix  3      [ ]         STREAM     CONNECTED     21701    /tmp/orbit-k8c/linc-1883-0-2435ac29e4c41
unix  3      [ ]         STREAM     CONNECTED     21700    
unix  3      [ ]         STREAM     CONNECTED     21699    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     21698    
unix  3      [ ]         STREAM     CONNECTED     21697    /tmp/orbit-k8c/linc-1883-0-2435ac29e4c41
unix  3      [ ]         STREAM     CONNECTED     21696    
unix  3      [ ]         STREAM     CONNECTED     21693    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     21692    
unix  3      [ ]         STREAM     CONNECTED     21688    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     21687    
unix  3      [ ]         STREAM     CONNECTED     21673    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     21672    
unix  3      [ ]         STREAM     CONNECTED     21671    /tmp/orbit-k8c/linc-1828-0-772de9e2b4718
unix  3      [ ]         STREAM     CONNECTED     21670    
unix  3      [ ]         STREAM     CONNECTED     21663    /tmp/orbit-k8c/linc-1828-0-772de9e2b4718
unix  3      [ ]         STREAM     CONNECTED     21662    
unix  3      [ ]         STREAM     CONNECTED     21661    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     21660    
unix  3      [ ]         STREAM     CONNECTED     21654    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     21653    
unix  3      [ ]         STREAM     CONNECTED     21625    /tmp/orbit-k8c/linc-1828-0-772de9e2b4718
unix  3      [ ]         STREAM     CONNECTED     21624    
unix  3      [ ]         STREAM     CONNECTED     21621    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20763    
unix  3      [ ]         STREAM     CONNECTED     20678    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20677    
unix  3      [ ]         STREAM     CONNECTED     20675    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20674    
unix  3      [ ]         STREAM     CONNECTED     20403    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20402    
unix  3      [ ]         STREAM     CONNECTED     20373    /tmp/mapping-k8c
unix  3      [ ]         STREAM     CONNECTED     20365    
unix  3      [ ]         STREAM     CONNECTED     20358    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20357    
unix  3      [ ]         STREAM     CONNECTED     20356    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20355    
unix  3      [ ]         STREAM     CONNECTED     20348    /tmp/orbit-k8c/linc-1810-0-79df36f3344d1
unix  3      [ ]         STREAM     CONNECTED     20347    
unix  3      [ ]         STREAM     CONNECTED     20340    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20339    
unix  3      [ ]         STREAM     CONNECTED     20335    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20334    
unix  3      [ ]         STREAM     CONNECTED     20324    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20323    
unix  3      [ ]         STREAM     CONNECTED     20322    /tmp/orbit-k8c/linc-17fa-0-3f3d181a95f3d
unix  3      [ ]         STREAM     CONNECTED     20321    
unix  3      [ ]         STREAM     CONNECTED     20318    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20317    
unix  3      [ ]         STREAM     CONNECTED     20309    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20308    
unix  3      [ ]         STREAM     CONNECTED     20307    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20306    
unix  3      [ ]         STREAM     CONNECTED     20304    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     20303    
unix  3      [ ]         STREAM     CONNECTED     20302    /tmp/orbit-k8c/linc-17c9-0-277a164943039
unix  3      [ ]         STREAM     CONNECTED     20301    
unix  3      [ ]         STREAM     CONNECTED     20300    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     20298    
unix  3      [ ]         STREAM     CONNECTED     20299    /tmp/orbit-k8c/linc-17d1-0-2f9a6cd91b531
unix  3      [ ]         STREAM     CONNECTED     20297    
unix  3      [ ]         STREAM     CONNECTED     20289    /tmp/orbit-k8c/linc-17f9-0-56facb251d06
unix  3      [ ]         STREAM     CONNECTED     20288    
unix  3      [ ]         STREAM     CONNECTED     20285    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20284    
unix  3      [ ]         STREAM     CONNECTED     20280    /tmp/orbit-k8c/linc-17fe-0-7c9acd3bd92b0
unix  3      [ ]         STREAM     CONNECTED     20279    
unix  3      [ ]         STREAM     CONNECTED     20276    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20275    
unix  3      [ ]         STREAM     CONNECTED     20271    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20270    
unix  3      [ ]         STREAM     CONNECTED     20264    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20263    
unix  3      [ ]         STREAM     CONNECTED     20262    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     20261    
unix  3      [ ]         STREAM     CONNECTED     20221    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20220    
unix  3      [ ]         STREAM     CONNECTED     20217    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20216    
unix  2      [ ]         DGRAM                    20215    
unix  3      [ ]         STREAM     CONNECTED     20202    /tmp/orbit-k8c/linc-17d5-0-277a164b184
unix  3      [ ]         STREAM     CONNECTED     20201    
unix  3      [ ]         STREAM     CONNECTED     20198    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20197    
unix  3      [ ]         STREAM     CONNECTED     20196    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20195    
unix  3      [ ]         STREAM     CONNECTED     20194    /tmp/orbit-k8c/linc-17d4-0-277a164aefbc9
unix  3      [ ]         STREAM     CONNECTED     20193    
unix  3      [ ]         STREAM     CONNECTED     20190    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20189    
unix  3      [ ]         STREAM     CONNECTED     20099    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20098    
unix  3      [ ]         STREAM     CONNECTED     20097    /tmp/orbit-k8c/linc-17e9-0-7dadb7909b61
unix  3      [ ]         STREAM     CONNECTED     20096    
unix  3      [ ]         STREAM     CONNECTED     20093    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20092    
unix  3      [ ]         STREAM     CONNECTED     20089    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20088    
unix  3      [ ]         STREAM     CONNECTED     20078    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     20077    
unix  3      [ ]         STREAM     CONNECTED     20188    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     20076    
unix  3      [ ]         STREAM     CONNECTED     20072    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20071    
unix  3      [ ]         STREAM     CONNECTED     20187    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     20049    
unix  3      [ ]         STREAM     CONNECTED     20044    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20043    
unix  3      [ ]         STREAM     CONNECTED     20037    /tmp/orbit-k8c/linc-17c9-0-277a164943039
unix  3      [ ]         STREAM     CONNECTED     20036    
unix  3      [ ]         STREAM     CONNECTED     20033    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20032    
unix  3      [ ]         STREAM     CONNECTED     20030    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     20029    
unix  3      [ ]         STREAM     CONNECTED     20025    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     20024    
unix  3      [ ]         STREAM     CONNECTED     20007    /tmp/orbit-k8c/linc-17ca-0-7513c6b9da351
unix  3      [ ]         STREAM     CONNECTED     20006    
unix  3      [ ]         STREAM     CONNECTED     20003    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     20002    
unix  3      [ ]         STREAM     CONNECTED     20001    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     20000    
unix  3      [ ]         STREAM     CONNECTED     19996    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     19995    
unix  3      [ ]         STREAM     CONNECTED     19988    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     19987    
unix  4      [ ]         STREAM     CONNECTED     19985    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     19984    
unix  3      [ ]         STREAM     CONNECTED     19977    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19976    
unix  3      [ ]         STREAM     CONNECTED     19975    /tmp/orbit-k8c/linc-17c8-0-7513c6b95b5bc
unix  3      [ ]         STREAM     CONNECTED     19974    
unix  3      [ ]         STREAM     CONNECTED     19971    /tmp/orbit-k8c/linc-17c6-0-44f411c558882
unix  3      [ ]         STREAM     CONNECTED     19970    
unix  3      [ ]         STREAM     CONNECTED     19967    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     19965    
unix  3      [ ]         STREAM     CONNECTED     19966    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     19964    
unix  3      [ ]         STREAM     CONNECTED     19963    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     19960    
unix  3      [ ]         STREAM     CONNECTED     19956    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     19955    
unix  3      [ ]         STREAM     CONNECTED     19962    /tmp/.ICE-unix/6010
unix  3      [ ]         STREAM     CONNECTED     19949    
unix  3      [ ]         STREAM     CONNECTED     19943    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     19942    
unix  3      [ ]         STREAM     CONNECTED     19924    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     19923    
unix  3      [ ]         STREAM     CONNECTED     19922    /tmp/orbit-k8c/linc-17c0-0-44f411da6ad5c
unix  3      [ ]         STREAM     CONNECTED     19921    
unix  3      [ ]         STREAM     CONNECTED     19918    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     19917    
unix  3      [ ]         STREAM     CONNECTED     19913    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     19912    
unix  3      [ ]         STREAM     CONNECTED     19903    @/tmp/dbus-mixwG0XhjT
unix  3      [ ]         STREAM     CONNECTED     19902    
unix  3      [ ]         STREAM     CONNECTED     19901    
unix  3      [ ]         STREAM     CONNECTED     19900    
unix  3      [ ]         STREAM     CONNECTED     19869    /tmp/orbit-k8c/linc-177a-0-c6d025188415
unix  3      [ ]         STREAM     CONNECTED     19868    
unix  3      [ ]         STREAM     CONNECTED     19867    /tmp/orbit-k8c/linc-17ba-0-dadc88a58425
unix  3      [ ]         STREAM     CONNECTED     19634    
unix  3      [ ]         STREAM     CONNECTED     19615    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     19614    
unix  3      [ ]         STREAM     CONNECTED     19592    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19591    
unix  3      [ ]         STREAM     CONNECTED     19503    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19502    
unix  3      [ ]         STREAM     CONNECTED     19489    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19488    
unix  2      [ ]         DGRAM                    18303    
unix  2      [ ]         DGRAM                    18302    
unix  2      [ ]         DGRAM                    18054    
unix  3      [ ]         STREAM     CONNECTED     17957    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     17956    
unix  4      [ ]         STREAM     CONNECTED     18458    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17955    
unix  2      [ ]         DGRAM                    17891    
unix  3      [ ]         STREAM     CONNECTED     17828    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17827    
unix  2      [ ]         DGRAM                    17826    
unix  3      [ ]         STREAM     CONNECTED     17819    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17818    
unix  3      [ ]         STREAM     CONNECTED     17813    
unix  3      [ ]         STREAM     CONNECTED     17812    
unix  2      [ ]         DGRAM                    17810    
unix  3      [ ]         STREAM     CONNECTED     17778    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17777    
unix  2      [ ]         DGRAM                    17771    
unix  2      [ ]         DGRAM                    17463    
unix  3      [ ]         STREAM     CONNECTED     17412    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     17404    
unix  3      [ ]         STREAM     CONNECTED     17403    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17402    
unix  3      [ ]         STREAM     CONNECTED     16943    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     16942    
unix  3      [ ]         STREAM     CONNECTED     16937    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     16936    
unix  3      [ ]         STREAM     CONNECTED     16931    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16930    
unix  3      [ ]         STREAM     CONNECTED     16923    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     16541    
unix  3      [ ]         STREAM     CONNECTED     16922    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     16534    
unix  3      [ ]         STREAM     CONNECTED     16532    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     16530    
unix  3      [ ]         STREAM     CONNECTED     16507    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     16498    
unix  3      [ ]         STREAM     CONNECTED     16506    @/var/run/hald/dbus-2FIHplrpVn
unix  3      [ ]         STREAM     CONNECTED     16476    
unix  3      [ ]         STREAM     CONNECTED     16073    @/var/run/hald/dbus-YSKejSq1b2
unix  3      [ ]         STREAM     CONNECTED     16072    
unix  3      [ ]         STREAM     CONNECTED     16069    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16068    
unix  3      [ ]         STREAM     CONNECTED     16047    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16046    
unix  3      [ ]         STREAM     CONNECTED     16045    @/tmp/dbus-qAvVpBBtic
unix  3      [ ]         STREAM     CONNECTED     16044    
unix  3      [ ]         STREAM     CONNECTED     16043    
unix  3      [ ]         STREAM     CONNECTED     16042    
unix  3      [ ]         STREAM     CONNECTED     16024    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16023    
unix  3      [ ]         STREAM     CONNECTED     16013    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16012    
unix  2      [ ]         DGRAM                    16008    
unix  3      [ ]         STREAM     CONNECTED     15993    
unix  3      [ ]         STREAM     CONNECTED     15992    
unix  2      [ ]         DGRAM                    15983    

```

hosts file ->
```


# The following lines are desirable for IPv6 capable hosts

```

---

### Post by dcstar on 2007-12-15
```
netstat -rn
```

Is that too difficult to type in?

---

### Post by AdHaR on 2007-12-15
Oops...sorry. I am going back and forth from my desktop to my notebook, and i didnt notice the arguments.

netstat -rn ->
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
64.230.197.230  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
172.16.126.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0

```

---

### Post by dcstar on 2007-12-15
> **AdHaR said:**
> Oops...sorry. I am going back and forth from my desktop to my notebook, and i didnt notice the arguments.

netstat -rn ->
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
64.230.197.230  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
172.16.126.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0

```

That seems to show that there is no Gateway entry, which is why you have no connectivity to the Internet.

As an example, mine is:

```
dc@dc-desktop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0        ** UG**        0 0          0 eth0
```
and my hosts file is:
```
dc@dc-desktop:~$ cat /etc/hosts
127.0.0.1 localhost dc-desktop
127.0.1.1 dc-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

You seem to be missing vital network configuration information generally, if you have another Ubuntu system that works then you can copy the working config over, otherwise it looks like the install has been corrupted.

---

### Post by mithras86 on 2007-12-22
I had somehow the same problems with Gutsy. In Feisty everthing worked fine, but in Gutsy I had a lot problems with my DNS server. I commented the line usepeerdns in /etc/ppp/peers/dsl-provider.

I capetured the nameservers in Feisty from /etc/ppp/resolv.conf and added them in the NetworkManager (click -> Manual configuration -> DNS -> Add both DNS servers there). I restarted the network (sudo /etc/init.d/networking restart) and now I've internet :D

I hope my dns problems won't get back by a reboot, but we'll see ;)

---

