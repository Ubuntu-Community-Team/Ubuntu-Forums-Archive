---
title: "Powerbook g3 pismo wifi says connected but no connection"
date: 2010-02-02
forum: Apple Hardware Users
---

### Post by Magliter on 2010-02-02
I have ubuntu then installed xubuntu-desktop on my powerbook g3 pismo

the wireless bar uptop says im connected to my wireless router, mind you the internet worked on OS X, however when I open up terminal I can't ping nor can I browse on firefox

I tried the lspci only to show no broadcom device or any that would hint at a wireless card

also i installed bw43-fwcutter to no avail..please help

---

### Post by linuxopjemac on 2010-02-03
what kind of card ? old fashioned airport ?

---

### Post by Magliter on 2010-02-03
Internal so I'm guessing so

---

### Post by linuxopjemac on 2010-02-04
can you give me the output of
```
sudo lspci
```

and 

```
sudo lsmod
```

and

```
sudo ifconfig
```

and 

```
sudo iwconfig
```

airport support is nowadays in the kernel...maybe you did not have the right module loaded

---

### Post by natgab on 2010-02-09
> **linuxopjemac said:**
> can you give me the output of
```
sudo lspci, lsmod, ifconfig, iwconfig
```
airport support is nowadays in the kernel...maybe you did not have the right module loaded

--linuxopjemac,

I also have a Pismo G3 and I am having trouble getting online. My Pismo is a G3 400 MHz / 256MB / 40GB HD / 8MB Rage ATI Mobility / DVD. I loaded Ubuntu 9.04 and have the video working (that will be a different post).

I have used WIFI & Ethernet with OS 9, OS X without problems. I tried both, with information required (i have a home network) and no luck.  The ethernet would not connect and Wifi would not show up like I did not have a airport card.  I have an original Apple airport, not 3rd party brand.

Internet works on my other Ubuntu computer in my signature. And two other PPC Macs have worked with Ubuntu.

Here is the info you asked in the post above, [B]but for my Pismo:
[/B]
```
@ubuntu:~$ sudo lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 CardBus bridge: Texas Instruments PCI1211
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth FireWire (rev 01)
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)
_________________________________________________

@ubuntu:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             9544  1 
ppdev                   8932  0 
lp                      9932  0 
parport                37936  2 ppdev,lp
bridge                 53540  0 
stp                     2692  1 bridge
rfcomm                 40436  0 
bnep                   14048  2 
sco                    10920  2 
l2cap                  22180  6 rfcomm,bnep
bluetooth              59824  6 rfcomm,bnep,sco,l2cap
uinput                  8544  2 
ipv6                  274064  10 
snd_powermac           46144  3 
snd_pcm_oss            42656  0 
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                75684  2 snd_powermac,snd_pcm_oss
snd_seq_dummy           2852  0 
snd_seq_oss            35444  0 
snd_seq_midi            7104  0 
snd_rawmidi            24288  1 snd_seq_midi
snd_seq_midi_event      7136  2 snd_seq_oss,snd_seq_midi
snd_seq                56896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23396  2 snd_pcm,snd_seq
snd_seq_device          7596  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62420  15 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6916  1 snd
snd_page_alloc          9448  1 snd_pcm
sbp2                   21740  0 
scsi_mod              162808  1 sbp2
loop                   16876  0 
apm_emu                 1984  0 
apm_emulation           8000  2 apm_emu
pcmcia                 37136  0 
evdev                  11076  15 
airport                 5056  0 
yenta_socket           27020  1 
orinoco                53556  1 airport
rsrc_nonstatic         10688  1 yenta_socket
pcmcia_core            38744  3 pcmcia,yenta_socket,rsrc_nonstatic
hermes_dld              7776  1 orinoco
hermes                  7584  3 airport,orinoco,hermes_dld
pmac_zilog             17828  0 
serial_core            24044  1 pmac_zilog
uninorth_agp            9100  1 
agpgart                38460  1 uninorth_agp
ext3                  143304  1 
jbd                    48340  1 ext3
mbcache                 8096  1 ext3
ohci1394               34768  0 
sungem                 32356  0 
sungem_phy             11680  1 sungem
ieee1394               92060  2 sbp2,ohci1394
ide_gd_mod             24484  3 
ide_cd_mod             39272  0 
cdrom                  39672  1 ide_cd_mod
windfarm_core          11248  0 
_____________________________________________

@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:65:6a:35:f4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x800 

eth1      Link encap:Ethernet  HWaddr 00:30:65:11:7a:5d  
          inet addr:10.10.40.2  Bcast:10.10.40.15  Mask:255.255.255.120
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1470 (1.4 KB)  TX bytes:1470 (1.4 KB)
__________________________________________________

@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"10.10.40.2"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
_______________________________________________
```

I hope that you have some ideas what to do.  thanks

---

### Post by linuxopjemac on 2010-02-09
You seem to have the right modules loaded:
> hermes_dld              7776  1 orinoco
hermes                  7584  3 airport,orinoco,hermes_dld

You even have a wireless connection to "HERMES I" on eth1. I don't see a problem. How did you get this connection ? Networkmanager? Or did you put info into /etc/network/interfaces ?

> 
eth1      Link encap:Ethernet  HWaddr 00:30:65:11:7a:5d  
          inet addr:10.10.40.2  Bcast:10.10.40.15  Mask:255.255.255.120
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:57 

eth1      IEEE 802.11b  ESSID:"10.10.40.2"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What is the problem? can you ping your router ? 

NB the encryption key is not set...maybe you have a protected network ?

---

### Post by linuxopjemac on 2010-02-09
If you do have WPA, then this might help (post #90)

[http://ubuntuforums.org/showthread.php?t=1114297&page=9](http://ubuntuforums.org/showthread.php?t=1114297&page=9)

---

### Post by natgab on 2010-02-09
> **linuxopjemac said:**
> You seem to have the right modules loaded:

You even have a wireless connection to "HERMES I" on eth1. I don't see a problem. How did you get this connection ? Networkmanager? Or did you put info into /etc/network/interfaces ?

[COLOR="Blue"]---I used network manager. Even tried making a second ethernet connection, since on my main computer it only works in the second of two ethernet connection for some reason.[/COLOR]

> What is the problem? can you ping your router ? 

NB the encryption key is not set...maybe you have a protected network ?

[COLOR="Blue"]---We have a Lynksis Router and a Lynksis cable modem plugged into my brother Windows PC. He is using WEP 40 on it.  We have a name for network and enter a password.

When I tried the ethernet, I would get the two green circles and the arrows showing that it was connecting.  But then it would not.  I even tried my brothers cable, since my has a loose connector and got same result.[/COLOR]

---

### Post by linuxopjemac on 2010-02-10
you have to set the WEP key in the network mananger

---

### Post by natgab on 2010-02-11
> **linuxopjemac said:**
> you have to set the WEP key in the network mananger

---I will probably wait for the weekend and mess around with it again.  I might reload the whole system and make it dual-boot, just to still have OS X. This way I can still use the laptop while I perfect Ubuntu on it.

I had optimistically loaded only Ubuntu hoping it would be a snap to set-up on a 10 year old laptop. ;)


thanks

---

### Post by natgab on 2010-02-12
> **linuxopjemac said:**
> you have to set the WEP key in the network mananger

I repartitioned and made a second install of 9.04, alternate install.  I was carefull to plug in Ethernet and enter my LAN info when installing. (I did not in my other install)  I was able to boot and it even let me update all recommended updates for Jaunty 9.04.  [COLOR="Blue"]**But after reboot, I again lost wired internet.**[/COLOR]  No luck with wireless either.  

But in this version I now get a pulldown menu where wireless icon is and it asks me if I want to join hidden network.  I push button for yes and get dialog box to enter name and type of wireless security (wep 40) and enter the password. (I did push radio button after screenshot)

My problem is that our system does not use DHCP, but the system defaults to it.  I then go to network manager and set my information in the IPV4 panel. I tick the box that says allow all to use and authenticate w/ my password to allow always. I then can see the two little green lights and the arrows trying to connect.  But it always stays at about 50%.

Note: If I try again, I have to re-enter my info in the IPV4 panel for my LAN. I included a screen shot, hope this helps. **[COLOR="Blue"]SEE BOTH PICTURES BELOW[/COLOR]**

---

### Post by linuxopjemac on 2010-02-13
If your system does not use DHCP, you have to enter your ip address, broadcast address and gateway address yourself. Read a bit about this on the internet.

I can also recall that it was problematic in Ubuntu with hidden networks....
[http://ubuntuforums.org/showthread.php?t=1286143&highlight=hidden+network](http://ubuntuforums.org/showthread.php?t=1286143&highlight=hidden+network)

---

### Post by natgab on 2010-02-13
> **linuxopjemac said:**
> If your system does not use DHCP, you have to enter your ip address, broadcast address and gateway address yourself. Read a bit about this on the internet.

I can also recall that it was problematic in Ubuntu with hidden networks....
[http://ubuntuforums.org/showthread.php?t=1286143&highlight=hidden+network](http://ubuntuforums.org/showthread.php?t=1286143&highlight=hidden+network)

Yes, I have always had to enter the ip, broadcast & gateway info even on OS X.  I have been filling in the information both for the ethernet and the wirelss.  With wireless adding the extra network SSID & password.

I will read the article, I guess I might be stuck only attempting to use it in ethernet, since that does not require the password, just the ip info, etc.  My current main machine is wired ethernet and my iMac I previously used for Debian & Ubuntu was also wired.

I will post back any progress I have.

---

### Post by natgab on 2010-02-15
linuxopjemac,

Still no success with hidden network on Ubuntu. I decided to try my Debian Lenny disc that I had burned for my G3 iMac. It worked better video-wise than Ubuntu. Ubuntu gave me wavy messed up video before the log-in and after shutdown.  Debian gives me the normal start up text & clean shutdown. But it did also need the modified Xorg. to fix split screen.

I have not yet searched the Debian forum, I will do that this week.  I saw that you have your Pismo listed as using Debian on the iLinux website in your signature. Are you using Karmic 9.10 or Debian on the Pismo?

I really only expect to use my Pismo around the house or at a friend's house.  So I sort of need the hidden WIFI/WEP to work, as i don't expect to be using open network in a coffeehouse or a library.

thanks for your help so far :KS

---

### Post by linuxopjemac on 2010-02-15
I use Debian Lenny on my Pismo. At home I have a WPA2 secured network. That works like a charm. I have no experience with hidden networks though...

---

