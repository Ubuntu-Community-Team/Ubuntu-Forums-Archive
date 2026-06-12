---
title: "My Internet is not redirecting properly"
date: 2011-02-22
forum: Apple Hardware Users
---

### Post by Zero_Viscosity on 2011-02-22
Hello Forum, I have an Intel iMac 8,1

I Triple boot it with OS X, Windows 7 and Ubuntu 10.10

I use REFIT and everything was working find until yesterday :/

I was playing around with Ubuntu and I installed VirtualBox by Oracle just for the heck of it, after that my internet stopped working. Skype works fine, i can make calls and people appear as online or offline, every other web protocol does not work though. I have searched and other people have the problem, I changed my DNS servers, I flushed DNS etc. etc. I disabled IPv6 and changed my DNS to another one. I am stumped now.. The internet worked fine day before last, the only thing that I can think of that may have messed it up is Virtual Box, but I already deleted it. I really dont want to re-install because I have had bad experiences with uninstalling Ubuntu. Any help would be **Greatly** Appreciated. 

Also my sound does not work, currently I use an Altec Lansing system that is plugged into my Audio Jack behind my computer.

---

### Post by Hatsune Miku on 2011-02-23
> **Zero_Viscosity said:**
> Hello Forum, I have an Intel iMac 8,1

I Triple boot it with OS X, Windows 7 and Ubuntu 10.10

I use REFIT and everything was working find until yesterday :/

I was playing around with Ubuntu and I installed VirtualBox by Oracle just for the heck of it, after that my internet stopped working. Skype works fine, i can make calls and people appear as online or offline, every other web protocol does not work though. I have searched and other people have the problem, I changed my DNS servers, I flushed DNS etc. etc. I disabled IPv6 and changed my DNS to another one. I am stumped now.. The internet worked fine day before last, the only thing that I can think of that may have messed it up is Virtual Box, but I already deleted it. I really dont want to re-install because I have had bad experiences with uninstalling Ubuntu. Any help would be **Greatly** Appreciated. 

Also my sound does not work, currently I use an Altec Lansing system that is plugged into my Audio Jack behind my computer.

Run this command and paste the output here.

```
netstat
```

---

### Post by Zero_Viscosity on 2011-02-28
Ok, Sorry for the delay in Response; I thought this forum emailed you when you get new posts on a thread..

Anyways, UBuntu gave me this when I entered "netstat" into terminal

```

nix  3      [ ]         STREAM     CONNECTED     14425    /tmp/orbit-user/linc-a09-0-7b744b8868a14
unix  3      [ ]         STREAM     CONNECTED     14424    
unix  3      [ ]         STREAM     CONNECTED     14421    /tmp/orbit-user/linc-a7a-0-45e345de78fa5
unix  3      [ ]         STREAM     CONNECTED     14420    
unix  3      [ ]         STREAM     CONNECTED     14419    /tmp/orbit-user/linc-a79-0-3c0a834279e09
unix  3      [ ]         STREAM     CONNECTED     14418    
unix  3      [ ]         STREAM     CONNECTED     14422    /tmp/orbit-user/linc-a84-0-6b053c7379892
unix  3      [ ]         STREAM     CONNECTED     14415    
unix  3      [ ]         STREAM     CONNECTED     14416    /tmp/orbit-user/linc-a83-0-6467ddf379219
unix  3      [ ]         STREAM     CONNECTED     14414    
unix  3      [ ]         STREAM     CONNECTED     14413    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14412    
unix  3      [ ]         STREAM     CONNECTED     14408    /tmp/orbit-user/linc-a84-0-6b053c7379892
unix  3      [ ]         STREAM     CONNECTED     14407    
unix  3      [ ]         STREAM     CONNECTED     14409    /tmp/orbit-user/linc-a83-0-6467ddf379219
unix  3      [ ]         STREAM     CONNECTED     14406    
unix  3      [ ]         STREAM     CONNECTED     14410    /tmp/orbit-user/linc-a79-0-3c0a834279e09
unix  3      [ ]         STREAM     CONNECTED     14405    
unix  3      [ ]         STREAM     CONNECTED     14411    /tmp/orbit-user/linc-a7a-0-45e345de78fa5
unix  3      [ ]         STREAM     CONNECTED     14404    
unix  3      [ ]         STREAM     CONNECTED     14403    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     14402    
unix  3      [ ]         STREAM     CONNECTED     14401    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14397    
unix  3      [ ]         STREAM     CONNECTED     14400    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14395    
unix  3      [ ]         STREAM     CONNECTED     14399    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14394    
unix  3      [ ]         STREAM     CONNECTED     14398    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14392    
unix  3      [ ]         STREAM     CONNECTED     14390    /tmp/orbit-user/linc-a81-0-66662ca479b5c
unix  3      [ ]         STREAM     CONNECTED     14389    
unix  3      [ ]         STREAM     CONNECTED     14388    /tmp/orbit-user/linc-a7f-0-79b3b8337960a
unix  3      [ ]         STREAM     CONNECTED     14387    
unix  3      [ ]         STREAM     CONNECTED     14386    /tmp/orbit-user/linc-a81-0-66662ca479b5c
unix  3      [ ]         STREAM     CONNECTED     14385    
unix  3      [ ]         STREAM     CONNECTED     14384    /tmp/orbit-user/linc-a7f-0-79b3b8337960a
unix  3      [ ]         STREAM     CONNECTED     14383    
unix  3      [ ]         STREAM     CONNECTED     14382    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14381    
unix  3      [ ]         STREAM     CONNECTED     14380    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14379    
unix  3      [ ]         STREAM     CONNECTED     14333    /tmp/orbit-user/linc-a79-0-3c0a834279e09
unix  3      [ ]         STREAM     CONNECTED     14332    
unix  3      [ ]         STREAM     CONNECTED     14331    /tmp/orbit-user/linc-a81-0-66662ca479b5c
unix  3      [ ]         STREAM     CONNECTED     14330    
unix  3      [ ]         STREAM     CONNECTED     14329    /tmp/orbit-user/linc-a84-0-6b053c7379892
unix  3      [ ]         STREAM     CONNECTED     14328    
unix  3      [ ]         STREAM     CONNECTED     14327    /tmp/orbit-user/linc-a7f-0-79b3b8337960a
unix  3      [ ]         STREAM     CONNECTED     14326    
unix  3      [ ]         STREAM     CONNECTED     14324    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     14318    
unix  3      [ ]         STREAM     CONNECTED     14317    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     14312    
unix  3      [ ]         STREAM     CONNECTED     14316    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     14308    
unix  3      [ ]         STREAM     CONNECTED     14307    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     14304    
unix  3      [ ]         STREAM     CONNECTED     14303    /tmp/orbit-user/linc-a83-0-6467ddf379219
unix  3      [ ]         STREAM     CONNECTED     14302    
unix  3      [ ]         STREAM     CONNECTED     14301    /tmp/orbit-user/linc-a7a-0-45e345de78fa5
unix  3      [ ]         STREAM     CONNECTED     14300    
unix  3      [ ]         STREAM     CONNECTED     14299    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     14296    
unix  3      [ ]         STREAM     CONNECTED     14295    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     14292    
unix  3      [ ]         STREAM     CONNECTED     14290    /tmp/orbit-user/linc-a6f-0-7d6f2655ea69
unix  3      [ ]         STREAM     CONNECTED     14289    
unix  3      [ ]         STREAM     CONNECTED     14277    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14276    
unix  3      [ ]         STREAM     CONNECTED     14264    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14263    
unix  3      [ ]         STREAM     CONNECTED     14260    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14259    
unix  3      [ ]         STREAM     CONNECTED     14253    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14252    
unix  3      [ ]         STREAM     CONNECTED     14242    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14241    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14240    
unix  3      [ ]         STREAM     CONNECTED     14239    
unix  3      [ ]         STREAM     CONNECTED     14231    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14230    
unix  3      [ ]         STREAM     CONNECTED     14225    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     14224    
unix  3      [ ]         STREAM     CONNECTED     14211    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14210    
unix  3      [ ]         STREAM     CONNECTED     14206    /var/run/usbmuxd
unix  3      [ ]         STREAM     CONNECTED     14204    
unix  3      [ ]         STREAM     CONNECTED     14201    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     14200    
unix  3      [ ]         STREAM     CONNECTED     13753    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13752    
unix  3      [ ]         STREAM     CONNECTED     13744    @/dbus-vfs-daemon/socket-wzqAlvr8
unix  3      [ ]         STREAM     CONNECTED     13743    
unix  3      [ ]         STREAM     CONNECTED     13742    @/dbus-vfs-daemon/socket-4No46c5a
unix  3      [ ]         STREAM     CONNECTED     13741    
unix  3      [ ]         STREAM     CONNECTED     13734    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13733    
unix  3      [ ]         STREAM     CONNECTED     13732    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13731    
unix  3      [ ]         STREAM     CONNECTED     13729    /tmp/orbit-user/linc-a09-0-7b744b8868a14
unix  3      [ ]         STREAM     CONNECTED     13728    
unix  3      [ ]         STREAM     CONNECTED     13718    /tmp/orbit-user/linc-a09-0-7b744b8868a14
unix  3      [ ]         STREAM     CONNECTED     13717    
unix  3      [ ]         STREAM     CONNECTED     13715    @/dbus-vfs-daemon/socket-lNubawpg
unix  3      [ ]         STREAM     CONNECTED     13714    
unix  3      [ ]         STREAM     CONNECTED     13716    @/dbus-vfs-daemon/socket-RuBXeIBq
unix  3      [ ]         STREAM     CONNECTED     13713    
unix  3      [ ]         STREAM     CONNECTED     13712    /tmp/orbit-user/linc-a5d-0-3ea65ae87803e
unix  3      [ ]         STREAM     CONNECTED     13710    
unix  3      [ ]         STREAM     CONNECTED     13708    /tmp/orbit-user/linc-a5b-0-5cc3b80778ec3
unix  3      [ ]         STREAM     CONNECTED     13707    
unix  3      [ ]         STREAM     CONNECTED     13705    @/dbus-vfs-daemon/socket-G1fYEMpu
unix  3      [ ]         STREAM     CONNECTED     13704    
unix  3      [ ]         STREAM     CONNECTED     13702    @/dbus-vfs-daemon/socket-M6gRisMq
unix  3      [ ]         STREAM     CONNECTED     13701    
unix  3      [ ]         STREAM     CONNECTED     13696    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13695    
unix  3      [ ]         STREAM     CONNECTED     13694    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13693    
unix  3      [ ]         STREAM     CONNECTED     13688    /tmp/orbit-user/linc-a5d-0-3ea65ae87803e
unix  3      [ ]         STREAM     CONNECTED     13687    
unix  3      [ ]         STREAM     CONNECTED     13683    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13682    
unix  3      [ ]         STREAM     CONNECTED     13680    /tmp/orbit-user/linc-a5b-0-5cc3b80778ec3
unix  3      [ ]         STREAM     CONNECTED     13679    
unix  3      [ ]         STREAM     CONNECTED     13681    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13678    
unix  3      [ ]         STREAM     CONNECTED     13675    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13674    
unix  3      [ ]         STREAM     CONNECTED     13660    /tmp/orbit-user/linc-a5b-0-5cc3b80778ec3
unix  3      [ ]         STREAM     CONNECTED     13659    
unix  3      [ ]         STREAM     CONNECTED     13656    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     13655    
unix  3      [ ]         STREAM     CONNECTED     13651    /tmp/orbit-user/linc-a5d-0-3ea65ae87803e
unix  3      [ ]         STREAM     CONNECTED     13650    
unix  3      [ ]         STREAM     CONNECTED     13647    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     13646    
unix  3      [ ]         STREAM     CONNECTED     13637    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13636    
unix  3      [ ]         STREAM     CONNECTED     13635    /var/run/usbmuxd
unix  3      [ ]         STREAM     CONNECTED     13634    
unix  3      [ ]         STREAM     CONNECTED     13630    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13629    
unix  3      [ ]         STREAM     CONNECTED     13626    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13624    
unix  3      [ ]         STREAM     CONNECTED     13625    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13623    
unix  3      [ ]         STREAM     CONNECTED     13612    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13611    
unix  3      [ ]         STREAM     CONNECTED     13534    /tmp/orbit-user/linc-a09-0-7b744b8868a14
unix  3      [ ]         STREAM     CONNECTED     13533    
unix  3      [ ]         STREAM     CONNECTED     13527    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13526    
unix  3      [ ]         STREAM     CONNECTED     13525    /tmp/orbit-user/linc-a45-0-432c31e2490ea
unix  3      [ ]         STREAM     CONNECTED     13524    
unix  3      [ ]         STREAM     CONNECTED     13511    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13510    
unix  3      [ ]         STREAM     CONNECTED     13507    /home/user/.pulse/10577f20c99960173ca6cb0e00000004-runtime/native
unix  3      [ ]         STREAM     CONNECTED     13506    
unix  3      [ ]         STREAM     CONNECTED     13498    /tmp/orbit-user/linc-a49-0-5354fa22ad742
unix  3      [ ]         STREAM     CONNECTED     13497    
unix  3      [ ]         STREAM     CONNECTED     13494    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13493    
unix  3      [ ]         STREAM     CONNECTED     13477    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13476    
unix  3      [ ]         STREAM     CONNECTED     13472    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13471    
unix  3      [ ]         STREAM     CONNECTED     13468    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13467    
unix  3      [ ]         STREAM     CONNECTED     13459    @/dbus-vfs-daemon/socket-xVU6Gbm3
unix  3      [ ]         STREAM     CONNECTED     13457    
unix  3      [ ]         STREAM     CONNECTED     13458    @/dbus-vfs-daemon/socket-UrmSPmcH
unix  3      [ ]         STREAM     CONNECTED     13456    
unix  3      [ ]         STREAM     CONNECTED     13446    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13444    
unix  3      [ ]         STREAM     CONNECTED     13438    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13437    
unix  3      [ ]         STREAM     CONNECTED     13436    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13435    
unix  3      [ ]         STREAM     CONNECTED     13423    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13422    
unix  3      [ ]         STREAM     CONNECTED     13420    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13419    
unix  2      [ ]         DGRAM                    13417    
unix  3      [ ]         STREAM     CONNECTED     13400    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13399    
unix  3      [ ]         STREAM     CONNECTED     13365    @/tmp/.ICE-unix/2491
unix  3      [ ]         STREAM     CONNECTED     13364    
unix  3      [ ]         STREAM     CONNECTED     13359    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13358    
unix  3      [ ]         STREAM     CONNECTED     13355    /tmp/orbit-user/linc-a04-0-5cdc4067569f6
unix  3      [ ]         STREAM     CONNECTED     13354    
unix  3      [ ]         STREAM     CONNECTED     13351    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13350    
unix  3      [ ]         STREAM     CONNECTED     13330    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13329    
unix  3      [ ]         STREAM     CONNECTED     13328    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13327    
unix  3      [ ]         STREAM     CONNECTED     13298    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13297    
unix  3      [ ]         STREAM     CONNECTED     13295    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13294    
unix  3      [ ]         STREAM     CONNECTED     13285    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13284    
unix  3      [ ]         STREAM     CONNECTED     13271    /home/user/.pulse/10577f20c99960173ca6cb0e00000004-runtime/native
unix  3      [ ]         STREAM     CONNECTED     13270    
unix  3      [ ]         STREAM     CONNECTED     13266    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13265    
unix  3      [ ]         STREAM     CONNECTED     13264    @/tmp/.ICE-unix/2491
unix  3      [ ]         STREAM     CONNECTED     13263    
unix  3      [ ]         STREAM     CONNECTED     13261    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13260    
unix  3      [ ]         STREAM     CONNECTED     13254    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13253    
unix  3      [ ]         STREAM     CONNECTED     13252    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13251    
unix  3      [ ]         STREAM     CONNECTED     13245    /tmp/orbit-user/linc-a07-0-6e0d050368dc5
unix  3      [ ]         STREAM     CONNECTED     13243    
unix  3      [ ]         STREAM     CONNECTED     13246    /tmp/orbit-user/linc-a11-0-2b195fb968e4a
unix  3      [ ]         STREAM     CONNECTED     13242    
unix  3      [ ]         STREAM     CONNECTED     13244    /tmp/orbit-user/linc-a19-0-7ea86eff68ec2
unix  3      [ ]         STREAM     CONNECTED     13241    
unix  3      [ ]         STREAM     CONNECTED     13232    /tmp/orbit-user/linc-a09-0-7b744b8868a14
unix  3      [ ]         STREAM     CONNECTED     13231    
unix  3      [ ]         STREAM     CONNECTED     13228    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13227    
unix  3      [ ]         STREAM     CONNECTED     13226    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13223    
unix  3      [ ]         STREAM     CONNECTED     13225    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13220    
unix  3      [ ]         STREAM     CONNECTED     13224    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     13217    
unix  2      [ ]         DGRAM                    13187    
unix  3      [ ]         STREAM     CONNECTED     13179    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13178    
unix  3      [ ]         STREAM     CONNECTED     13168    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13167    
unix  3      [ ]         STREAM     CONNECTED     13165    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13164    
unix  3      [ ]         STREAM     CONNECTED     13161    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13160    
unix  3      [ ]         STREAM     CONNECTED     13142    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13141    
unix  3      [ ]         STREAM     CONNECTED     13094    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13093    
unix  2      [ ]         DGRAM                    13092    
unix  3      [ ]         STREAM     CONNECTED     13072    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     13071    
unix  3      [ ]         STREAM     CONNECTED     13069    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13068    
unix  3      [ ]         STREAM     CONNECTED     13065    @/tmp/.ICE-unix/2491
unix  3      [ ]         STREAM     CONNECTED     13064    
unix  3      [ ]         STREAM     CONNECTED     13062    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13061    
unix  3      [ ]         STREAM     CONNECTED     13054    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13053    
unix  3      [ ]         STREAM     CONNECTED     13050    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13049    
unix  3      [ ]         STREAM     CONNECTED     13038    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13037    
unix  3      [ ]         STREAM     CONNECTED     13007    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13006    
unix  2      [ ]         DGRAM                    13002    
unix  3      [ ]         STREAM     CONNECTED     12922    /tmp/orbit-user/linc-a01-0-6b809f2b6054d
unix  3      [ ]         STREAM     CONNECTED     12921    
unix  3      [ ]         STREAM     CONNECTED     12918    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     12917    
unix  3      [ ]         STREAM     CONNECTED     12905    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12904    
unix  3      [ ]         STREAM     CONNECTED     12902    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12901    
unix  3      [ ]         STREAM     CONNECTED     12898    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12897    
unix  3      [ ]         STREAM     CONNECTED     12896    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12895    
unix  3      [ ]         STREAM     CONNECTED     12894    /tmp/orbit-user/linc-a00-0-3a74254658a0c
unix  3      [ ]         STREAM     CONNECTED     12893    
unix  3      [ ]         STREAM     CONNECTED     12890    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     12889    
unix  3      [ ]         STREAM     CONNECTED     12745    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12744    
unix  3      [ ]         STREAM     CONNECTED     12741    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12740    
unix  2      [ ]         DGRAM                    12608    
unix  3      [ ]         STREAM     CONNECTED     12580    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12579    
unix  3      [ ]         STREAM     CONNECTED     12503    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12502    
unix  3      [ ]         STREAM     CONNECTED     12498    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12497    
unix  3      [ ]         STREAM     CONNECTED     12460    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12459    
unix  3      [ ]         STREAM     CONNECTED     12454    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12453    
unix  3      [ ]         STREAM     CONNECTED     12426    /tmp/orbit-user/linc-9e7-0-620d9204b9574
unix  3      [ ]         STREAM     CONNECTED     12425    
unix  3      [ ]         STREAM     CONNECTED     12422    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     12421    
unix  3      [ ]         STREAM     CONNECTED     12398    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12397    
unix  3      [ ]         STREAM     CONNECTED     12396    /tmp/orbit-user/linc-9e9-0-df0e98eaff80
unix  3      [ ]         STREAM     CONNECTED     12395    
unix  3      [ ]         STREAM     CONNECTED     12392    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     12391    
unix  3      [ ]         STREAM     CONNECTED     12382    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12381    
unix  3      [ ]         STREAM     CONNECTED     12376    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12375    
unix  3      [ ]         STREAM     CONNECTED     12372    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     12371    
unix  3      [ ]         STREAM     CONNECTED     12312    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12311    
unix  3      [ ]         STREAM     CONNECTED     12279    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12278    
unix  3      [ ]         STREAM     CONNECTED     12186    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12185    
unix  3      [ ]         STREAM     CONNECTED     12183    /tmp/orbit-user/linc-9bb-0-4471008842cf3
unix  3      [ ]         STREAM     CONNECTED     12182    
unix  3      [ ]         STREAM     CONNECTED     12179    /tmp/orbit-user/linc-9e4-0-3a207f763cc27
unix  3      [ ]         STREAM     CONNECTED     12178    
unix  3      [ ]         STREAM     CONNECTED     12174    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12173    
unix  3      [ ]         STREAM     CONNECTED     11945    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     11944    
unix  3      [ ]         STREAM     CONNECTED     11885    @/tmp/dbus-pjxIs9Ek4i
unix  3      [ ]         STREAM     CONNECTED     11884    
unix  3      [ ]         STREAM     CONNECTED     11882    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11881    
unix  3      [ ]         STREAM     CONNECTED     11878    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11877    
unix  3      [ ]         STREAM     CONNECTED     11876    
unix  3      [ ]         STREAM     CONNECTED     11875    
unix  3      [ ]         STREAM     CONNECTED     11864    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11863    
unix  3      [ ]         STREAM     CONNECTED     11713    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11712    
unix  3      [ ]         STREAM     CONNECTED     11600    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11599    
unix  3      [ ]         STREAM     CONNECTED     11256    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11255    
unix  3      [ ]         STREAM     CONNECTED     11250    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11249    
unix  3      [ ]         STREAM     CONNECTED     11242    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11241    
unix  3      [ ]         STREAM     CONNECTED     11202    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11201    
unix  2      [ ]         DGRAM                    11200    
unix  3      [ ]         STREAM     CONNECTED     11139    @/tmp/gdm-session-NmDoIPmw
unix  3      [ ]         STREAM     CONNECTED     11138    
unix  3      [ ]         STREAM     CONNECTED     11135    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11134    
unix  2      [ ]         DGRAM                    11133    
unix  3      [ ]         STREAM     CONNECTED     10551    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10550    
unix  3      [ ]         STREAM     CONNECTED     10537    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10536    
unix  3      [ ]         STREAM     CONNECTED     10383    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10382    
unix  3      [ ]         STREAM     CONNECTED     9842     
unix  3      [ ]         STREAM     CONNECTED     9841     
unix  2      [ ]         DGRAM                    9789     
unix  3      [ ]         STREAM     CONNECTED     9786     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9785     
unix  2      [ ]         DGRAM                    9383     
unix  2      [ ]         DGRAM                    8853     
unix  3      [ ]         STREAM     CONNECTED     8697     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8696     
unix  2      [ ]         DGRAM                    8695     
unix  2      [ ]         DGRAM                    8677     
unix  3      [ ]         STREAM     CONNECTED     8667     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8664     
unix  3      [ ]         STREAM     CONNECTED     8534     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8533     
unix  3      [ ]         STREAM     CONNECTED     8476     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8475     
unix  3      [ ]         STREAM     CONNECTED     8442     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8441     
unix  3      [ ]         STREAM     CONNECTED     8440     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8439     
unix  3      [ ]         STREAM     CONNECTED     8434     
unix  3      [ ]         STREAM     CONNECTED     8433     
unix  2      [ ]         DGRAM                    8431     
unix  2      [ ]         DGRAM                    8430     
unix  3      [ ]         STREAM     CONNECTED     8409     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8408     
unix  2      [ ]         DGRAM                    8402     
unix  3      [ ]         STREAM     CONNECTED     8399     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8398     
unix  3      [ ]         STREAM     CONNECTED     8390     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8389     
unix  2      [ ]         DGRAM                    8385     
unix  3      [ ]         STREAM     CONNECTED     8326     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8325     
unix  3      [ ]         STREAM     CONNECTED     8310     
unix  3      [ ]         STREAM     CONNECTED     8309     
unix  3      [ ]         DGRAM                    6308     
unix  3      [ ]         DGRAM                    6307     
unix  3      [ ]         STREAM     CONNECTED     6268     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     6267     



```

---

### Post by Zero_Viscosity on 2011-03-05
Bump....

Can someone please help me?

This support forum isnt very supportful....  :confused:

Helfen ich bitte

153 Views, no completely helpful response :(

---

### Post by Zero_Viscosity on 2011-03-09
Hello??

Some help Please?

---

### Post by Zero_Viscosity on 2011-03-15
Please help me. I do not know what to do.

---

### Post by Hatsune Miku on 2011-05-01
> **Zero_Viscosity said:**
> Please help me. I do not know what to do.

Do you have any firewall program installed?

---

