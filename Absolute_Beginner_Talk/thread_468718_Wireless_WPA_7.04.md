---
title: "Wireless WPA 7.04"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by xRes on 2007-06-09
Hey Everyone, 
I have been trying to set up Wireless WPA on Ubuntu 7.04 and I have seen that it should already be installed on it and be ready to run. my network is WPA with passphrase and Ubuntu does see the network as it brings up its name, but it will only give me the option to try and connect using WEP which of course failes. I have tried  a few methods but to no avail. 
Any help much appreciated!
cheers
xRes

---

### Post by ugm6hr on 2007-06-09
> **xRes said:**
> Hey Everyone, 
I have been trying to set up Wireless WPA on Ubuntu 7.04 and I have seen that it should already be installed on it and be ready to run. my network is WPA with passphrase and Ubuntu does see the network as it brings up its name, but it will only give me the option to try and connect using WEP which of course failes. I have tried  a few methods but to no avail. 
Any help much appreciated!
cheers
xRes

In the page that asks for your WEP password - just click on the top box that says "enable roaming".

Then, right-click the icon with 2 computers or 4 grey bars at the top right corner - enable networking and enable wireless.  Then left click the same icon and select your SSID (make sure you broadcast SSID), and it should ask for WPA password.

If this doesn't work, I've guessed incorrectly as to what you've done.

---

### Post by necrolin on 2007-06-10
If you left click on the network connection icon and choose "Create new wireless network" then WPA is the choices. If you do "manual configuration" then you can only choose WEP for some reason. Don't know why. I'm using WPA, I only wish it didn't ask me for the password every time I re-boot.... erghhh.

---

### Post by buellman on 2007-06-10
> **necrolin said:**
> I'm using WPA, I only wish it didn't ask me for the password every time I re-boot.... erghhh.
This will help you:
[ Howto: Get Network Manager to stop asking you for your keyring password]("http://ubuntuforums.org/showthread.php?t=192281")

Greets. Buellman

---

### Post by necrolin on 2007-06-10
That works. Thanks.

---

### Post by daynah on 2007-06-14
So, I got my WPA working in the manner you described. Peachy Keen!

But then I got jiggery pokery, nm-applet was ticking me off and I was being stupid and not following any guides, just clickign randomly (I didn't do anything in terminal, no worries).

And I ended up not having any two computers in my bar. When I tried to right-click add, I only get the two-computers-with-signal-that-looks-like-arrow... and only gives me wep. Not the one that was different (that started as two computers and turned itno the cellphone signal thing) and gave me WPA. How do I get it back?

One day I'll listen to the forum... one day.

---

### Post by jfoobar on 2007-06-14
> **necrolin said:**
> If you left click on the network connection icon and choose "Create new wireless network" then WPA is the choices. If you do "manual configuration" then you can only choose WEP for some reason. Don't know why. I'm using WPA, I only wish it didn't ask me for the password every time I re-boot.... erghhh.

OK, I must be blind but I cannot find anywhere where I get a "Create new wireless network" option.   Network Manager Applet 0.6.4 is installed and has an icon in systray but left click only gives me a "manual configuration" option.

Any ideas?  I really need to get WPA working.

---

### Post by jfoobar on 2007-06-15
Anyone?  I am really having no luck finding someplace to create a new wireless network.

---

### Post by mikekie on 2007-06-26
Jfoobar - If you got to System..Administration menu choose Network option.  You should see your Wireless Connection.  If it does not say Roaming Mode Enabled then choose properties for the Wireless Connection and check the Enable Roaming Mode option.

After setting right click on the 2 Computer icon near the clock on the task bar and make sure Enable Wireless is checked.    Now left click on the 2 Computer icon and you should have option to Create New Wireless Network.

Hope this helps.

---

### Post by scholzilla on 2007-06-27
I'm having the same problem as xRes. WPA is not offered as an encryption option. I've followed all the instructions at [https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") to no avail. Roaming is enabled. I'm have a Realtek RTL8187 wireless card and am running ubuntu 7.04. I'm able to connect via wifi using WEP perfectly fine. Any other suggestions?

Thanks!

---

### Post by jimbob on 2007-06-27
Personally I would get rid of network manager and install Wicd *[COLOR="Blue"]http://wicd.sourceforge.net/[/COLOR]*

It is a much better wireless package IMHO and easy to follow to get your WPA1/2 configuration set up.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by macogw on 2007-06-27
It depends on your wireless card's chipset.  Some work with NetworkManager, some don't because their driver doesn't use Linux Wireless Extensions (WEXT).  Go to [http://linux-wless.passys.nl](http://linux-wless.passys.nl) and look up your wireless card (the name can be found by runnign "lspci" in the terminal).  If it's green, you're good.  Yellow, you've got a shot.  Then look at [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware) and see if that driver is listed as working (and how much working too...some might have wep only if they don't use WEXT).  If it NetworkManager's page doesn't say it has WPA support, you'll have to use wpa_supplicant and wifi-radar or wicd to get WPA.

As for the missing NM applet, hit alt+f2 and type "nm-applet"

---

### Post by scholzilla on 2007-06-28
Thanks for the replies. I removed network manager and installed wicd, but it doesn't see the wpa network, despite seeing numerous other wireless networks that are presumably not WPA encrypted. It should definitely see this network (ie it's not because the signal is not strong enough to reach my laptop). 

Also, I have a very dumb newbie question. I don't know which output from the lspci command refers to my wireless card. I know that my card is a [Realtek RTL8187]("http://www.realtek.com.tw/search/default.aspx?keyword=RTL8187"), but have no idea if it's the 8187B or 8187L--both are supposed to support wpa. Here's the output I get from lspci:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Thanks for your help.

---

### Post by jimbob on 2007-06-28
I do not see your wireless card either.  That's strange.

Can you connect to any networks at all that are listed?

Do you have wpasupplicant installed ?  *[COLOR="Blue"]apt-cache policy wpasupplicant[/COLOR]*

Perhaps the AP you are looking for is not broadcasting its ESSID.  In Wicd, click the 'hidden networks' tab and enter the SSID if you know it.  It will then show up and you can set it up.

Do you know your wireless device name (wlan0, eth1) etc?  Post the output of *[COLOR="Blue"]iwconfig wlan0[/COLOR]* ( or whatever the device is).

Also post the output of *[COLOR="Blue"]lsmod[/COLOR]*
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by scholzilla on 2007-06-28
Thanks for the quick reply. As it turns out, I just wasn't able to see that particular wifi network in my particular room of this building. I moved and now I can see it (sorry for not checking into that first). However, I still can't connect. I did [COLOR="DarkSlateBlue"]apt-cache policy wpasupplicant [/COLOR]and it showed it was installed. I'm able to enable the WPA1/2 encryption and there is a box called "Key" where I'm presumably supposed to enter something. Perhaps this is my problem, but I missed any info about what supposed to go in here (other than a reference to putting quotation marks around whatever is supposed to go in here). I do know that there is a username and password associated with the network. Is this my problem? I'm seeing the bar that says "connecting" but the connection fails. Sorry, I'm really new to this stuff.

Here is the output of iwconfig you requested:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"UAWiFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And here's the output of lsmod:

Module                  Size  Used by
battery                12040  0 
ac                      6920  0 
thermal                16912  0 
fan                     6536  0 
button                 10016  0 
rtl8187                35328  0 
eeprom_93cx6            4992  1 rtl8187
sky2                   47880  0 
isofs                  38628  1 
udf                    86664  0 
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16480  1 
cpufreq_stats           8416  0 
cpufreq_userspace       6176  0 
cpufreq_conservative     9736  0 
cpufreq_ondemand       10640  1 
freq_table              6336  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3072  0 
sony_acpi               7064  0 
tc1100_wmi              9224  0 
dev_acpi               17028  0 
pcc_acpi               15616  0 
container               6144  0 
asus_acpi              19756  0 
dock                   11992  0 
sbs                    17856  0 
i2c_ec                  6784  1 sbs
video                  19080  0 
backlight               8448  1 asus_acpi
ipv6                  307072  10 
af_packet              27020  2 
sbp2                   26628  0 
parport_pc             40104  0 
lp                     15048  0 
parport                43404  3 ppdev,parport_pc,lp
fuse                   51888  0 
joydev                 12928  0 
arc4                    3328  2 
ecb                     5120  2 
blkcipher               7552  1 ecb
rc80211_simple          7168  1 
snd_hda_intel          24224  1 
snd_hda_codec         262912  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              11520  0 
psmouse                43536  0 
mac80211              192388  2 rtl8187,rc80211_simple
cfg80211               26512  1 mac80211
pcmcia                 43800  0 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4736  0 
tifm_core              11520  1 tifm_7xx1
serio_raw               9092  0 
yenta_socket           29836  1 
rsrc_nonstatic         14208  1 yenta_socket
pcmcia_core            45860  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
i2c_piix4              11148  0 
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
k8temp                  7552  0 
i2c_core               26624  2 i2c_ec,i2c_piix4
tsdev                  10112  0 
evdev                  13056  5 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
ide_disk               18304  3 
ide_cd                 35104  1 
cdrom                  40744  1 ide_cd
ata_generic            10628  0 
libata                137000  1 ata_generic
scsi_mod              166968  2 sbp2,libata
generic                 6532  0 [permanent]
ehci_hcd               37004  0 
ohci_hcd               24196  0 
usbcore               154416  4 rtl8187,ehci_hcd,ohci_hcd
ohci1394               38088  0 
ieee1394              369784  2 sbp2,ohci1394
atiixp                  8208  0 [permanent]
processor              34952  2 thermal,powernow_k8
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability


Thanks again for all your patience.

---

### Post by jimbob on 2007-06-28
Yes, that is your problem.  You must put the exact same key as the AP you are trying to link up with in the key box in Wicd. Do NOT use any quotation marks and remember the name is case sensitive.
You must find out from someone what their key should be.

Then at the bottom click on connect and you should be good to go.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by scholzilla on 2007-06-29
Thanks, again. As it turns out, the problem isn't the Key (this particular AP doesn't have one), but a network administration issue. I can connect to other WPA1/2 networks fine. These guys don't appear to have anyone who can support linux, which makes me suspect that they don't know a whole lot about administration of networks. And this is a major university campus!

---

### Post by jimbob on 2007-06-29
As far as the network software at that level is concerned it really doesn't know the difference between operating systems.  The problem is that when you mention the word "Linux" to a lot of those guys their mental blocks activate and they get that glassy-eyed far away look in their eyes and deny all knowledge.

I tend to run into that problem occasionally with the cable company folks who come into the house  to check the modem and happen to see my setup.

I even had one guy who insisted he had to install his cd-rom software ( *.exe stuff) on my system to get things to work.   The only way to get rid of him was to let him put it on one of my old XP partitions (which I promptly deleted after he left).

So much for the age of enlightenment ...
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by xophere on 2007-07-31
Thanks I had been looking and found that my driver just supports wep.  So unclear to find.  Thanks for the post.  Gonna find a different card.

> **macogw said:**
> It depends on your wireless card's chipset.  Some work with NetworkManager, some don't because their driver doesn't use Linux Wireless Extensions (WEXT).  Go to [http://linux-wless.passys.nl](http://linux-wless.passys.nl) and look up your wireless card (the name can be found by runnign "lspci" in the terminal).  If it's green, you're good.  Yellow, you've got a shot.  Then look at [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware) and see if that driver is listed as working (and how much working too...some might have wep only if they don't use WEXT).  If it NetworkManager's page doesn't say it has WPA support, you'll have to use wpa_supplicant and wifi-radar or wicd to get WPA.

As for the missing NM applet, hit alt+f2 and type "nm-applet"

---

