---
title: "Network not working at all (wireless AND wired)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by johnfoozmich on 2007-02-25
Hello everyone,

I'm sure everybody is tired of hearing about network problems, but I thought I would throw mine onto the pile as well (I have looked around the forums and the net for most of the day trying methods that just didn't work).

I'm not all that experience with linux but I have used it several times before, and when I got a new desktop I thought I would turn my laptop into a linux box.  Looking around I saw good things about Ubuntu so I downloaded it and installed it and all that.

Anyway... after installing it, my wireless didn't work.  I didn't think much of that since I figured I'd have to do a little digging, but then when I plugged in an ethernet cable THAT connection didn't work either.  I have it auto-assigning settings with DHCP, as we have done on the rest of our computers in the house with no problems.  The connection will sometimes come on for maybe a minute or two rarely (after not changing anything) and then it loses itself.  It makes it very hard to download updates when I have such a small window to do it in.  Does anybody have any idea what's going on?  Everybody seems to have no problem with a wired connection but I can't even get that.

I am using a Dell (hate them) and my wireless card is a BCM4306 802.11b/g Wireless LAN controller from Broadcom, and similarly my wired connection is a BCM4401 100Base-T.

Please give me any help you can think of, as I am getting quite frustrated with this and am very close to surrendering to Windows once again.

Thanks!

---

### Post by apjone on 2007-02-25
please post your /etc/network/interfaces please

---

### Post by jkeyes0 on 2007-02-25
May sound odd, but do you have another cable you can try? In most cases, when a connection (wired) is unstable, it is somewhere in the hardware, and the cable is the most likely cause of failure. I'd say try it on another system if possible or try another cable to see if that helps out.

---

### Post by tgalati4 on 2007-02-25
Welcome to the community.  We feel your pain.  You have broadcom chipsets in both your wireless and wired network cards.  This can be a challenge.  Broadcom has repeatedly refused cooperation with the Linux community to release either open source or even binary closed drivers.  There is some good work going on in reverse engineering open source drivers and ndiswrapper works mostly using the appropriate windows driver.

There is a nifty, graphical ndiswrapper installer.  Search ndiswrapper in synaptic.  Have you tried ndiswrapper?

Good luck

---

### Post by johnfoozmich on 2007-02-25
Thanks for the replies.

To apjone:

My etc/network/interfaces is:

"auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface dsl-provider inet ppp
provider dsl-provider

auto eth0"

eth0 is my wired card, eth1 is my wireless.  Not sure where the other ones came from..



To jkeyes0:

I tried another cable, no luck.



To tgalati4:

I've heard of ndiswrapper, and tried to download it on my desktop then transfer it over to my ubuntu box to install, but it just ended up needing way too many dependencies to manually retrieve and transfer.  It's a pain without any sort of connection at all.

---

### Post by tgalati4 on 2007-02-25
Yea, I forgot.  It's difficult to install without a network connection.  Boot a live CD and run synaptic it will find drivers off of the CD.  I think it was installed as part of the base Dapper 6.06.1 Live CD.  I could be wrong, but try ndiswrapper in a console and see if it already exists.

You will need to find your windows broadcom.inf files for both the wired and wireless cards.

If you mount your windows drive, then you can use the drivers in place or you can copy them to a USB stick and copy them to your home directory for safe keeping.

You will run it twice once for the wired and once for the wireless.  The ndiswrapper works well with Broadcom chipsets, but it does go against Ubuntu's open source policy.  It's really a hack until open source, reverse-engineered drivers become widely available.

The other option is to grab a cheapie pcmcia wired network card (borrow one from a friend) that may be compatible out of the box and get you going.

Good luck.  At least you know what to try next.

---

### Post by johnfoozmich on 2007-02-25
Okay, I think I have everything I need.  I found some drivers for the cards and I got ndiswrapper installed during another brief period of service.  Can you recall what steps I need to take to install these drivers now or know of a link offhand for it?  Thanks a lot!

---

### Post by tgalati4 on 2007-02-25
There are three pieces to this puzzle:
1) current windows drivers:  broadcom.inf
2) sink the ndiswrapper hooks into the windows drivers
3) load the ndiswrapper module into the kernel

You have the drivers.

in a shell:

sudo ndiswrapper -i mycheesybroadcomcard.inf
sudo ndiswrapper -i mycheesybroadcomwireless.inf

Now load the kernel module:

sudo modprobe ndiswrapper

Check for network:

ifconfig

iwconfig

Go to the network panel and set up your settings.

Get the graphical ndiswrapper installer from synaptic (search ndiswrapper)--of course now you don't need it anymore.

Rock and roll!

---

### Post by johnfoozmich on 2007-02-26
Okay, I copied over the drivers and installed them using the method you gave.  Still no change. Doing ndiswrapper -l brings up what I just installed, but it just says that each one is an invalid driver.

Here is the result of the config calls:

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:1F:6B:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



I have the correct ESSID settings in my network settings.  I really don't think I could have the wrong drivers either....

---

### Post by tgalati4 on 2007-02-26
What version of Ubuntu did you install?

If it is Edgy, then I recall that there is a module that needs blacklisting because it prevents ndiswrapper from working.  That may be  your problem.

Share with us:

lsmod

Add any broadcom 43XX modules to the blacklist: (there should be two, one for wireless and one for wired--or perhaps the same driver for both!)

/etc/modprobe.d/blacklist

---

### Post by johnfoozmich on 2007-02-26
I dunno, I just downloaded whatever version was on the front page at [www.ubuntu.com](www.ubuntu.com),  Ubuntu 6.10.  Should I try switching to another?

---

### Post by johnfoozmich on 2007-02-26
Sorry, did see the last part of your message.

~$ lsmod
Module                  Size  Used by
ndiswrapper           208656  0 
arc4                    3200  2 
ieee80211_crypt_wep     6528  1 
nls_utf8                3200  0 
nls_cp437               6912  0 
vfat                   14720  0 
fat                    56348  1 vfat
ipv6                  272288  10 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
speedstep_ich           6544  0 
speedstep_lib           5764  1 speedstep_ich
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
af_packet              24584  4 
pcmcia                 40380  0 
joydev                 11200  0 
sg                     37404  0 
sd_mod                 22656  0 
snd_intel8x0           34844  1 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
tsdev                   9152  0 
b44                    26764  0 
snd_ac97_codec         97696  1 snd_intel8x0
bcm43xx               127252  0 
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_ac97_bus            3456  1 snd_ac97_codec
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
mii                     6912  1 b44
i2c_core               23424  1 i2c_ec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
serio_raw               8452  0 
psmouse                41352  0 
evdev                  11392  2 
intel_agp              26012  1 
agpgart                34888  1 intel_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcspkr                  4352  0 
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
usbhid                 45152  0 
usb_storage            75072  0 
scsi_mod              144648  4 sbp2,sg,sd_mod,usb_storage
libusual               17040  1 usb_storage
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0 
usbcore               134912  7 ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_disk               18560  3 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


And here is my blacklist, with my additions to the bottom


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist ieee80211softmac   
blacklist ieee80211

---

### Post by johnfoozmich on 2007-02-27
Well, if anyone is still following this, I've blacklisted the bcm43xx drivers and inserted the drivers I needed with ndiswrapper.  It says that the driver is installed and the hardware is present.  I put ndiswrapper into my /etc/modules file.  It still does not work.  Any more ideas perhaps?

---

### Post by jingo811 on 2007-02-27
I dunno about your Wireless, I too had a 3 months wrestle with mine without solving anything.  But that was the Ubuntu Breezy time (version 5.04 if I'm correct), gonna give it a try this month on my Dapper 6.06 LTS (Long Term Support).

Anyhow you had a Wired "Network Interface Card" (NIC) in your laptop right?
My painful experience with Linux is solve your Wired Internet before trying on Wireless unless it's detected at installation.

Try the below commands in terminal, if your NIC is eth1 try that instead:

----  Magic Networking  ----
```
sudo dhclient eth0
sudo route add default gw 192.168.0.1
```

---

### Post by johnfoozmich on 2007-02-27
My wired connection is very spotty, sometimes it will come on but more often than not it's not working.  

sudo dhclient eth0 just produced mostly junk, with many "DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval (some number)" finally ending with 

"No DHCPOFFERS received.
No working leases in persistent database - sleeping"

And the second command you listed didn't work at all, it just said "SIOCADDRT: Network is unreachable"

So yeah..

---

### Post by jingo811 on 2007-02-27
Did you try this?
```
sudo dhclient eth1
```
If none of this work I suggest you make a new post asking ppl how to specifically contain and disable your Wireless configuration files.  Making your Wired NIC the only Internet connecting component on your laptop.  Then it might be easier to troubleshoot and make Wired Internet work for you.  
When that's accomplished you could try solve your Wireless without the stress and time pressure (give it some months), it's not likely to be solved in an instant.

If you're only focused on fixing your Wired Internet I suggest you comment out anything that has to do with your Wireless to keep the problem factors down to a minimum.  You posted this earlier:

> 
My etc/network/interfaces is:

"auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface dsl-provider inet ppp
provider dsl-provider

auto eth0"

eth0 is my wired card, eth1 is my wireless. Not sure where the other ones came from..

I would do this:
1.
```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup
```
2.
```
sudo gedit /etc/network/interfaces
```
3. And change it like this, but you should double check with other ppl before doing any extending troubleshooting with your Wired NIC!
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

[COLOR="Red"]#iface dsl-provider inet ppp
#provider dsl-provider[/COLOR]

#auto eth0

```

That part is new to me though 
[COLOR="Red"]#iface dsl-provider inet ppp
#provider dsl-provider[/COLOR]
so I don't know what really happens when you comment it out, you might have to uncomment it to make things work, or you might not need to.

---

