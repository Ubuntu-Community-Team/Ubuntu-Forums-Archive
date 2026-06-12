---
title: "How do I know if the blacklist worked?"
date: 2012-08-13
forum: Any Other OS
---

### Post by UltimateCat on 2012-08-13
I realized that I had to blacklist the rt2800 because since installing Debian the internet is not working.  2 drivers are attempting  the same device.

So I tried
```
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf

```

When I first executed the command I had permission denied.
So I tried again. Only this time I executed su and put in my password. The terminal didn't indicate a result.

```
ztcoracat@mock:~$ echo "blacklist rt2800usb" >> /etc/modeprobe.d/.blacklist.conf
bash:/etc/modprobe.d/.blacklist.conf: Permission denied

```
So I tried su and my passoword
```
ztcoracat@mock:~$su
password
root@mock:/home/ztcoracat# echo"blacklist rt2800usb" >> /etc.modprobe.d?blacklist.conf
root@mock:/home/ztcoracat#

```
The internet connection is not working.  The Authentication Required by Wireless Network opens but when I click connect the network icon just spins and doesn't connect.
Did I execute something wrong?

---

### Post by UltimateCat on 2012-08-13
According to the Debian wiki page rt2870sta is the correct driver for Debian 6.0.5 Sqeeze.

I have even went to another help forum and they made it clear to me that I need to blacklist this driver.

[http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)

I've been trying to get the connection to work and have not been able to.
Any help would be a blessing.

---

### Post by 2F4U on 2012-08-14
To see whether the module in question is loaded or not, execute **lsmod**.

---

### Post by UltimateCat on 2012-08-15
Got it 
```
lsmod

```

Think the blacklist worked. The Network Mgr icon now turns to 4 bars and connection is established. (that's new progress) 

When my system ( Debian Squeeze) booted up today the network icon connected.  The funny thing is that Iceweasel and Epiphany Web browser's are not working. I'm getting Errors.

Ice Weasel says:
```
Server Not Found
Problem Loading Page

```

And the Epiphany Web Browser says:
```
Loading www.debian.org
Unable to load page
The URL http://www.debian.org
Cannot resolve hostname

```

I checked on the etc/network/interface file and all the info. is ok. The ip address, netmask and etc. And, last week with help I installed the firmware; wireless tolls and the libiw30_30~pre9-5_amd64.deb like I was advised.

Not sure what to do here but I've been trying to get my OS to go online now for about 2 weeks.  What could be the problem?
How do I fix this?

---

### Post by UltimateCat on 2012-08-15
Here's the output:

```
 ztcoracat@mock:~$ lsmod  
 Module                  Size  Used by  
 nls_utf8                1208  1  
 nls_cp437               5817  1  
 vfat                    7884  1  
 fat                    40038  1 vfat  
 parport_pc             18855  0  
 ppdev                   5030  0  
 lp                      7462  0  
 parport                27954  3 parport_pc,ppdev,lp  
 sco                     7225  2  
 bridge                 39646  0  
 stp                     1440  1 bridge  
 bnep                    9427  2  
 rfcomm                 29629  0  
 l2cap                  24752  6 bnep,rfcomm  
 crc16                   1319  1 l2cap  
 bluetooth              41827  6 sco,bnep,rfcomm,l2cap  
 powernow_k8            10978  0  
 cpufreq_userspace       1992  0  
 cpufreq_powersave        902  0  
 cpufreq_stats           2740  0  
 cpufreq_conservative     5162  0  
 binfmt_misc             6431  1  
 fuse                   50924  1  
 loop                   11799  0  
 snd_hda_codec_realtek   235714  1  
 rt2870sta             360987  0  
 arc4                    1274  2  
 snd_hda_intel          20035  1  
 snd_hda_codec          54292  2 snd_hda_codec_realtek,snd_hda_intel  
 ecb                     1841  2  
 radeon                574908  2  
 ttm                    40162  1 radeon  
 snd_hwdep               5380  1 snd_hda_codec  
 rt2800usb              28691  0  
 snd_pcm                60487  2 snd_hda_intel,snd_hda_codec  
 rt2x00usb               6765  1 rt2800usb  
 drm_kms_helper         20369  1 radeon  
 snd_seq                42881  0  
 drm                   142352  4 radeon,ttm,drm_kms_helper  
 i2c_algo_bit            4209  1 radeon  
 snd_timer              15598  2 snd_pcm,snd_seq  
 shpchp                 26248  0  
 edac_core              29261  0  
 rt2x00lib              21810  2 rt2800usb,rt2x00usb  
 snd_seq_device          4493  1 snd_seq  
 edac_mce_amd            6433  0  
 mac80211              137372  2 rt2x00usb,rt2x00lib  
 xpad                    8592  0  
 pci_hotplug            21587  1 shpchp  
 k10temp                 2715  0  
 snd                    46526  10 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device 
 cfg80211              101496  2 rt2x00lib,mac80211  
 rfkill                 13044  4 bluetooth,cfg80211  
 crc_ccitt               1323  2 rt2870sta,rt2800usb  
 soundcore               4598  1 snd  
 button                  4650  0  
 led_class               2433  2 rt2x00lib,xpad  
 snd_page_alloc          6249  2 snd_hda_intel,snd_pcm  
 i2c_piix4               8328  0  
 ff_memless              3692  1 xpad  
 i2c_core               15819  5 radeon,drm_kms_helper,drm,i2c_algo_bit,i2c_piix4  
 pcspkr                  1699  0  
 joydev                  8459  0  
 evdev                   7352  10  
 processor              29935  1 powernow_k8  
 usb_storage            40217  1  
 ext3                  106710  1  
 jbd                    37317  1 ext3  
 mbcache                 5050  1 ext3  
 usbhid                 33292  0  
 hid                    63257  1 usbhid  
 sg                     24069  0  
 sr_mod                 12602  0  
 cdrom                  29351  1 sr_mod  
 sd_mod                 29937  5  
 crc_t10dif              1276  1 sd_mod  
 ata_generic             3239  0  
 pata_atiixp             3489  0  
 r8169                  36840  0  
 ahci                   32870  2  
 thermal                11674  0  
 libata                133776  3 ata_generic,pata_atiixp,ahci  
 mii                     3210  1 r8169  
 ohci_hcd               19343  0  
 ehci_hcd               32097  0  
 scsi_mod              126725  5 usb_storage,sg,sr_mod,sd_mod,libata  
 thermal_sys            11942  2 processor,thermal  
 usbcore               123122  9 rt2870sta,rt2800usb,rt2x00usb,xpad,usb_storage,usbhid,ohci_hcd,ehci_hcd 
 nls_base                6377  5 nls_utf8,nls_cp437,vfat,fat,usbcore  
 

```

---

### Post by UltimateCat on 2012-08-15
I entered my root password before following the path to the file etc/network/interfaces. I opened the interfaces file and tried to edit it because I still can not get my system onto the internet. Debian would not let me save the changes I made.
Instead I was given a warning in red " "Could not save the file etc/network/interfaces; you do not have permissions necessary to save the file."

I disabled the Ipv6 because my connection is not wired. 
I found this Debian thread and am pretty sure this is the case for me.

[http://forums.debian.net/viewtopic.php?f=5&t=55989](http://forums.debian.net/viewtopic.php?f=5&t=55989)

Please advise; I'm confused:confused:

---

### Post by UltimateCat on 2012-08-19
Had I know that opening a terminal and start typing nano and the name of the file would edit the file I would of been online a lot sooner.

I'm online now and Iceweasel with Vimperator works well.

---

