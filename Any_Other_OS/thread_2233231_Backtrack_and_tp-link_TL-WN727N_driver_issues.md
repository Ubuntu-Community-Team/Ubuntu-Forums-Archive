---
title: "Backtrack and tp-link TL-WN727N driver issues"
date: 2014-07-07
forum: Any Other OS
---

### Post by spr3 on 2014-07-07
i'm not install driver tp-link   model:TL-WN727N     IN Back track 53r
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bt 3.2.6 i686,  Ubuntu 10.04.3 LTS, lucid

CPU    : Intel(R) Pentium(R) 4 CPU 3.40GHz
Memory : 1001 MB
Uptime : 13:56:57 up 17 min,  2 users,  load average: 0.02, 0.10, 0.20


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
    Kernel driver in use: pcnet32
    Kernel modules: pcnet32
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 02)
    Kernel driver in use: snd_ens1371


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




module parameters ~~~~~~~~~~~~~~~~~~


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ooooooo
 Interface & ID | Type | Driver | State        | Default | Speed     | Support      | HW Addr   
ooooooo
                |      |        |              |         |           |              |           
+++++++


NetworkManager.state ~~~~~~~~~~~~~~~


NetworkManager.conf ~~~~~~~~~~~~~~~~



NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.235.2
domain localdomain
search localdomain


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.235.2   0.0.0.0         UG    100    0        0 eth0
192.168.235.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

--- 192.168.235.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.207/1.263/1.320/0.066 ms

--- 192.168.235.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.295/0.295/0.296/0.017 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bt.conf]
blacklist rt2870sta
blacklist rt2860sta

[/etc/modprobe.d/blacklist.conf]
blacklist ar9170usb
blacklist r8187
blacklist ath_pci
blacklist<module>


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modules]
loop

[/etc/pm/sleep.d/action_wpa] [executable]
#!/bin/sh

# Action script to enable/disable wpa-roam interfaces in reaction to
# pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2008-2009, Kel Modderman <kel@otaku42.de>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

if [ ! -x /sbin/wpa_action ]; then
    exit 0
fi

SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, disconnect any wpa-roam managed interfaces,
# reconnect it on resume.

case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac

if [ -z "$COMMAND" ]; then
    # ifplugd(8) - <iface> <action>
    #
    # If an ifplugd managed interface is brought up, disconnect any
    # wpa-roam managed interfaces so that only one "roaming" interface
    # remains active on the system.

    IFPLUGD_IFACE="${1}"

    case "${2}" in
        up)
            COMMAND=disconnect
            ;;
        down)
            COMMAND=reconnect
            ;;
        *)
            echo "${SELF}: unknown $0 arguments: ${@}" >&2
            exit 1
            ;;
        esac
fi

if [ -z "$COMMAND" ]; then
    echo "${SELF}: unknown arguments: ${@}" >&2
    exit 1
fi

for CTRL in /var/run/wpa_supplicant/*; do
    [ -S "${CTRL}" ] || continue

    IFACE="${CTRL#/var/run/wpa_supplicant/}"

    wpa_action "${IFACE}" check || continue

    if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
        # if ifplugd is managing this interface (not likely but..)
        # do nothing
        continue
    fi

    wpa_cli -i "${IFACE}" "${COMMAND}"
done


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.2.6 root=UUID=d0618407-707e-41f7-8393-6591caa69cf3 ro text splash vga=791


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.031296] Initializing cgroup subsys net_cls
[    5.444102] audit: initializing netlink socket (disabled)
[    6.673303] arcnet loaded.
[   24.564983] pcnet32: pcnet32.c:v1.35 21.Apr.2008 tsbogend@alpha.franken.de
[   25.212213] pcnet32 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   25.316732] pcnet32: PCnet/PCI II 79C970A at 0x2000, <MAC eth0> assigned IRQ 19
[   25.393622] pcnet32: eth0: registered as PCnet/PCI II 79C970A
[   25.448702] pcnet32: 1 cards_found
[   48.221362] pcnet32 0000:02:01.0: eth0: link up

    ======== Done ========



```

---

### Post by varunendra on 2014-07-07
Welcome to the forums spr3!

Is this a virtual machine you are trying to use the USB adapter in? The adapter is using a very new chip which no open source driver supports yet.
```
Bus 001 Device 002: ID **[COLOR="#0000CD"]148f:7601[/COLOR]** Ralink Technology, Corp.
```
The only Linux driver for it is the proprietary driver that Ralink (Mediatek) provides : [http://www.mediatek.com/en/downloads/mt7601u-usb/](http://www.mediatek.com/en/downloads/mt7601u-usb/)

You will have to download and compile the driver manually. Instructions should be in the package you'll download.

By the way, neither your system is an Asus, nor the OS in question is Ubuntu, and the version the OS (BackTrack?) is based on is mostly outdated. So your question is in no way suitable for this thread. I'll request the mods to move your posts to its own thread in a relevant section, but I suggest you consider using an OS version that is currently supported (for example, maybe Kali Linux based on a [currently supported]("https://wiki.ubuntu.com/Releases") Ubuntu version, or Ubuntu itself to get proper support here).

**EDIT:**
I forgot that I had already written instructions for installing the proprietary driver here : [http://ubuntuforums.org/showthread.php?t=2206873&p=12936176#post12936176](http://ubuntuforums.org/showthread.php?t=2206873&p=12936176#post12936176)

---

### Post by Bucky Ball on 2014-07-07
*Thread moved to **Other OS/Distro Support**.*

... and posts moved to own thread.

Welcome. While you are quite at liberty to seek help on the Ubuntu forums, Backtrack is not officially supported in the main support areas here. Good luck.

---

### Post by coffeecat on 2014-07-07
And just to complement what has already been said, Backtrack itself is now unmaintained. You would do better to use a supported and up-to-date operating system.

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

---

