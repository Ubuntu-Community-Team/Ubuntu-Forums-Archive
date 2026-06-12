---
title: "Wireless Issues for Newbie!  Please help!"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by hfthomp on 2006-08-03
Hey guys, newbie here.  I installed ubuntu on my machine last night, my first crack at Linux.  My desktop is connected to my home network via a wireless PCI card, Zonet ZEW1601.  I have found on this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

that has the Ralink 2500 chipset.  I followed the instructions on that page, by activating my ra0 wireless connection.  I typed in my ESSID, and WEP key.  I enable the connection, hit Okay, and after a  minute or so of trying to come back the system hung up on me.  After rebooting, and logging in the system hangs up on me and just sits there, never fully loading!  Could someone please give me a spot of advice?  Thanks.

P.S.  I have tried booting up in Recovery mode, and it is hanging up in that as well.  the last line it's displayed is:

[4294695.289000] sd 3:0:0:0: Attached scsi generic sg2 type 0

At this point, should I just reinstall Ubuntu?  Is there anything else I can do to get my wireless working?

---

### Post by kb3hkg on 2006-08-04
can u run lspci and iwconfig in a terminal and post the results, for lspci only entry for card is necessary. And are you sure what chipset this card uses?

---

### Post by stormblue on 2006-08-04
A quick google search seams to indicate it uses the RT61 drivers.  It may be something to investigate.

---

### Post by hfthomp on 2006-08-04
Why does this page:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29)

say it uses the rt2500 chipset/driver, and then what exactly does "Supported in installed system" mean?  Thanks for the help so far.

---

### Post by stormblue on 2006-08-04
You may want to read [this]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=9604&sid=4a16419f0d0b5cdb01d5ebc1e5388149")

---

### Post by hfthomp on 2006-08-04
I just ran lspci and iwconfig...here are the results

lspci:

0000:02:02.0 Netword controller: Ralink: Unknown Device 0301

iwconfig:

ra0     RT61 Wireless  ESSID:""
        Mode: Auto   Channel:0
        RTS thr=0 B     Fragment thr=0 B
        Link Quality:0    Signal level:0    Noise Level:113
        Rx invalid nwid:0  Rx invalid crypt:0   Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anyone have any ideas?

---

### Post by stormblue on 2006-08-04
It appears to me with the device unknown line your drivers might be messed up.


Run 

```
sudo iwlist ra0 scan
``` 

and paste the output in here.

---

### Post by dragonlor20 on 2006-08-26
> **stormblue said:**
> It appears to me with the device unknown line your drivers might be messed up.


Run 

```
sudo iwlist ra0 scan
``` 

and paste the output in here.

I am having similar wireless problems with the RT61 RaLink driver... my output for > sudo iwlist ra0 scan was as follows:

> ra0       Scan completed :

          Cell 01 - Address: 00:02:6F:31:13:D5
                    Mode:Managed
                    ESSID:"rlwa6668"
                    Encryption key:off
                    Channel:1

          Cell 02 - Address: 00:16:B6:CB:A3:EC
                    Mode:Managed
                    ESSID:"linksys"
                    Encryption key:on
                    Channel:6

          Cell 03 - Address: 00:02:6F:31:50:A8
                    Mode:Managed
                    ESSID:"rlwa6656"
                    Encryption key:off
                    Channel:6

          



Hopefully someone can help, i have been having this problem for a week now... It detects the networks but not internet. It seems like whatever is wrong must be fairly simple to fix, but I just don't know enough to find it...

---

