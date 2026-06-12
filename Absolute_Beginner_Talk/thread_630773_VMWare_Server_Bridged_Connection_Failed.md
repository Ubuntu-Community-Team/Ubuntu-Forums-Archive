---
title: "VMWare Server Bridged Connection Failed"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2007-12-03
I installed vmware server and am trying to bridge it to my wireless card, which is called "ath0".

I ran vmware-config-network.pl, ran the editor for network connections, and changed vmnet0 from eth0 to ath0. Here's the respose:

```

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: ath0, vmnet1,
vmnet8, eth0. Which one do you want to bridge to vmnet0? [eth0] ath0

The following virtual networks have been defined:

. vmnet0 is bridged to ath0
. vmnet1 is a host-only network on private subnet 192.168.253.0.
. vmnet8 is a NAT network on private subnet 192.168.147.0.

Do you wish to make additional changes to the current virtual networks 
settings? (yes/no) [yes] no

Generating SSL Server Certificate

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

```

Basically, it failed, I did the same with vmnet2, when vmnet0 was connected to eth0, and that also failed. Must be a problem with my wireless, but I don't know what to do with it.

Further, here is dmesg's output to this problem:

```

[32692.147895] /dev/vmnet: port on hub 0 successfully opened
[32692.148088] bridge-ath0: enabling the bridge
[32692.148091] bridge-ath0: can't bridge with ath0, bad header length 88
[32692.148094] bridge-ath0: interface ath0 is not a valid Ethernet interface
[32692.148689] bridge-ath0: can't bridge with ath0, bad header length 88

```

Any ideas?

Thanks.

---

### Post by pteri498 on 2007-12-04
*bump*

---

### Post by dishkuvek on 2007-12-19
I am experiencing the exact same problem, with the exact same wireless networking card.  Have you had any success?

---

### Post by dishkuvek on 2007-12-19
Hey, I actually found a solution to the problem in another thread:

[http://ubuntuforums.org/showthread.php?t=285846](http://ubuntuforums.org/showthread.php?t=285846)

There is a link to the madwifi bug tracker in there, it will take you to a patch to get the bridged networking working!  Mine is running great now!

[http://madwifi.org/ticket/407](http://madwifi.org/ticket/407)

---

