---
title: "Can't get online, new to Linux"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by metsfan47 on 2007-08-11
Hello everyone!  I just built my first PC and I love open-source software so I thought I'd give Ubuntu a try.  The only problem I seem to be having is that I can't get online.  It says I have an active wired connection.  When I go to Connection Information:

Interface: Wired Ethernet
Speed: 100Mb/s
Driver: forcedeth
IP, Broadcast Address, Subnet Mask, Default Route, Primary DNS, Secondary DNS, all 0.0.0.0

The network card is intergrated into the motherboard, which is an Asus A8M-VM, if that helps.  I apoligize in advance if I'm being really stupid, but I'm out of idea's.  Thank you all in advance!

-Aaron

---

### Post by bwtranch on 2007-08-11
No, you are not stupid. You are just having a problem right now. Let's see if we can fix it. Would you please open a terminal and type in lsmod and also ifconfig and post the output? That will give us the information that we will need to track the problem. I may need other people to help because I am not a wizards:) like they are. I just mostly write programs.

---

### Post by ugm6hr on 2007-08-11
And tell us how you connect to the internet:
Modem, Router, Network etc.

---

### Post by bwtranch on 2007-08-11
Thanks UGM6hr. You gonna help me try to help this guy?

---

### Post by metsfan47 on 2007-08-11
Wow, thank you both for your quick reply's. Here is the info.  

aaron@aaron-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
powernow_k8            16064  1 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
video                  16388  0 
asus_acpi              17308  0 
dock                   10268  0 
button                  8720  0 
ac                      6020  0 
battery                10756  0 
backlight               7040  1 asus_acpi
container               5248  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
lp                     12452  0 
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
serio_raw               7940  0 
pcspkr                  4224  0 
psmouse                38920  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
k8temp                  6656  0 
agpgart                35400  0 
i2c_nforce2             6784  0 
i2c_core               22784  2 i2c_ec,i2c_nforce2
af_packet              23816  4 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ata_generic             9092  0 
sata_nv                20868  2 
libata                125720  2 ata_generic,sata_nv
scsi_mod              142348  3 sg,sd_mod,libata
usbhid                 26592  0 
hid                    27392  1 usbhid
floppy                 59524  0 
forcedeth              46728  0 
ehci_hcd               34188  0 
generic                 5124  0 [permanent]
amd74xx                15260  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  4 usbhid,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
aaron@aaron-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:4B:84:A8  
          inet6 addr: fe80::217:31ff:fe4b:84a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142816 (139.4 KiB)  TX bytes:7696 (7.5 KiB)
          Interrupt:19 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:17:31:4B:84:A8  
          inet addr:169.254.6.179  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2388 (2.3 KiB)  TX bytes:2388 (2.3 KiB)

aaron@aaron-desktop:~$

---

### Post by metsfan47 on 2007-08-11
Oh sorry, I forgot.  I connect via a Motorola cable modem with Comcast High Speed internet.  Thanks again!

-Aaron

---

### Post by ugm6hr on 2007-08-11
> **metsfan47 said:**
> 
aaron@aaron-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:4B:84:A8  
          inet6 addr: fe80::217:31ff:fe4b:84a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142816 (139.4 KiB)  TX bytes:7696 (7.5 KiB)
          Interrupt:19 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:17:31:4B:84:A8  
          inet addr:169.254.6.179  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x8000 


This looks like you've already got a connection to your modem.  Presumably the ethernet cable runs direct from your computer to the cable modem?

I personally use a router, so am not 100% sure about getting a cable modem to work with Ubuntu.  How do you get the modem to work in Windows?

One thing to try:
```
ping *IP*
```

EDIT: You need to put in your modem's IP for this to work.  I can't remember if there is any easy way to get this info without knowing it already...  The 169.254.255.255 is not it...
If this returns a ping - it confirms a connection with the cable modem, so it is not an ethernet issue, but a cable modem issue.  While I know that you can ping a router, I am not 100% certain you can ping a modem....

@bwtranch: going to try!!!

One further thing to try - after booting up:
```
sudo /etc/init.d/networking restart
```

---

### Post by metsfan47 on 2007-08-11
Yes, I have an ethernet cable directly from PC to cable modem.  
When I ping 192.254.255.255 I get: 

from 169.254.6.179 icmp_seq=[n] Destination Host Unreachable
where n = a sequential number for a few hundred lines of that.  

-Aaron

---

### Post by MenZa on 2007-08-11
As I always assume when a network is playing up, I think your problem is with Avahi. Avahi has given me problems on every single system I've ever installed, and I hate it to bits. Now, I believe you can find your solution by deactivating the Avahi daemon from running when you start up, but I forgot where the script is run. Could someone enlighten us?

---

### Post by metsfan47 on 2007-08-11
I'm tried everything ugm, but with no luck.  Does anyone know how to deactivate this Avahi daemon?  Thanks!

-Aaron

---

### Post by MenZa on 2007-08-11
> **metsfan47 said:**
> I'm tried everything ugm, but with no luck.  Does anyone know how to deactivate this Avahi daemon?  Thanks!

-Aaron

Well, deactivating it is pretty simple *sudo /etc/init.d/avahi-daemon -k*, it's stopping it from launching at startup that's the problem.

---

### Post by metsfan47 on 2007-08-11
if I deactivate it and still can't get online, would it be safe to assume that Avahi isn't the problem, or am I mistaken?  Thanks

-Aaron

---

### Post by MenZa on 2007-08-11
> **metsfan47 said:**
> if I deactivate it and still can't get online, would it be safe to assume that Avahi isn't the problem, or am I mistaken?

Hmm, no, I've personally had to reboot once or twice for it to work, which is why we need to have it deactivated from the moment you start up your PC.

---

### Post by metsfan47 on 2007-08-11
ah, I see.  

I'm afraid I have to get going now, but I really would like to thank everyone for your help thus far.  If anyone things of anything, please let me know.  If not, I'll be back tomorrow for some more help.  Again, thank you all very much!  Have a great day!

-Aaron

---

### Post by metsfan47 on 2007-08-11
I thought maybe if I contacted Comcast tech support they might me able to help (how naive of me). They didn't even want to talk to me when they found out I didn't have Windows.  Does anyone have any other idea's regarding this problem?  Thank you!

-Aaron

---

### Post by afzalnaj on 2007-08-11
try these

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587)
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587/comments/6](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/65587/comments/6)

 im a complete newbie to linux, i dont even know what avahi is and what they are talking about but i guessed from the talk that this might work.wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: Tahoma, Arial, Arial; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

### Post by afzalnaj on 2007-08-11
is something wrong with my browser...when i try to edit any post and save it the whole wysiwyg {background-attachment:....thing comes up

---

