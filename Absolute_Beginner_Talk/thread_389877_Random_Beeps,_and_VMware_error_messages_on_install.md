---
title: "Random Beeps, and VMware error messages on install"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-21
Hi guys,

I reformatted my Ubuntu last week, and I've had 2 problems.

1) Random beeps. I don't know why, but I've kept hearing random beeps every now and then. They have a few variations, but they more or less sound a bit techno...about half a second in lenght. Is there any way to find out which/what is causing it? Cause its realli irritating :(

One thing to note is that I haven't finished updating my ubuntu yet. Could it be the update notifier making all the beeps?
[COLOR="Red"]
I got problem #1 fixed already ! Sorry about that. I was GAIM (doh!). The sounds I was hearing were the sounds of people logging in and out or somthing. I guess I wasn't used to the sounds that it was making, and I didn't see anything "pop up" when the sounds came out, so I didn't associate it. Heh.[/COLOR]

Here's a list of my "top":

```

Tasks: 130 total,   6 running, 123 sleeping,   0 stopped,   1 zombie
Cpu(s): 66.7% us,  0.0% sy,  0.0% ni,  0.0% id, 33.3% wa,  0.0% hi,  0.0% si
Mem:   1036096k total,  1023412k used,    12684k free,     4808k buffers
Swap:  1044216k total,     9952k used,  1034264k free,   582112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
29002 kinson    16   0  3432 1248  284 S 64.5  0.1   1:29.24 rsync
 6260 root      16   0 84752  70m  13m R 32.3  7.0   7:53.10 Xorg
29956 kinson    15   0  146m  29m  15m S 32.3  2.9   0:28.18 rhythmbox
31073 kinson    15   0  2196 1132  856 R 32.3  0.1   0:00.11 top
    1 root      16   0  1564  524  460 S  0.0  0.1   0:01.14 init
    2 root      34  19     0    0    0 R  0.0  0.0   0:35.72 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.92 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.12 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  167 root      15   0     0    0    0 S  0.0  0.0   0:02.71 pdflush
  168 root      15   0     0    0    0 S  0.0  0.0   0:01.06 pdflush
  170 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  169 root      15   0     0    0    0 S  0.0  0.0   0:15.65 kswapd0
  757 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod

```

2. I used automatix to install vmware and some other stuff, a few of them failed(automatix said), but I'm not sure whether vmware succeeded. I can run vmware player(its in my programs list), but everytime I try and install something like kalarm or amarok though apt-get/aptitude, after installing kalarm, it follows up by trying to do something with vmware:

(This starts directly after it finished installing kalarm):
```

Setting up kalarm (3.5.2-0ubuntu6) ...

Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.96.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]
The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.45.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
kinson@kinbuntu:~$ kalarm

```

Any ideas guys? :(

Cheers,
Kinson

---

