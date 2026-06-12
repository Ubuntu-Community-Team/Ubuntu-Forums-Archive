---
title: "Wireless problem--appears to be quick fix"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-18
I am completely new to Ubuntu and linux.  I just installed ubuntu under a dual booting system.  I am having problems with my wireless.  Although I don't know how to use the terminal, I think I know the problem.  One of the reasons I picked ubuntu was because my wireless card WORKED out of the box when I used the live CD.  After I installed it, it did not.  I looked at Network Manager under the live CD again and know that there is a difference in the settings.  Under the live CD, ubuntu 7.10 (64) loads the prism54pci driver.  This driver works perfectly.  When I installed ubuntu, ubuntu loaded the prism54 driver.  I think I need to somehow tell the terminal to replace the prism54 driver with the prism54pci driver.  I have googled and searched the forums extensively, so please do not give me a link to another thread.  I should say that a wired connection is not convient on that computer and I would like to do that as a last resort, so I would like to do it without installing anything that requires the internet because the wireless connection is my internet connection on that computer.  This problem is the only thing holding me back from never booting my windows partition again.

---

### Post by Law506 on 2008-03-18
have you gone into the synaptic manager and searched for that pci driver??

also you might want to refresh your list and you might want to add some more repositories as well in case that driver isn't found at first.

But it sounds like a basic driver, so it should be in there.

---

### Post by forrestcupp on 2008-03-18
Try going to System->Administration->Restricted Drivers Manager to see if it is there.  If so, you can easily enable it there.

---

### Post by hikujk123 on 2008-03-18
Thanks for responding.  If I enable it, do I have to disable the other one first?  If so, how?

---

### Post by hikujk123 on 2008-03-18
I did what forrestcup said, but ubuntu said that my hardware does not require any restricted drivers.  I can't do what Law said without an internet connection, can I?  Is there anyway I can tell ubuntu to take the wireless settings from the liveCD?  PLEASE HELP! I don't want to use windows anymore.

---

### Post by hikujk123 on 2008-03-18
bump

---

### Post by forrestcupp on 2008-03-18
Be careful about bumping that quickly.  The mods don't like it.

Can you connect straight to the router with a network cable to try what law said?

---

### Post by hikujk123 on 2008-03-18
I can if there is no other way.  Once I get the new one, how do I disable the old one?

---

### Post by hikujk123 on 2008-03-18
I can't find it on synaptic.  I don't really know if I am using synaptic properly but am pretty sure it isn't there.  Since it is on the liveCD, doesn't that mean it is built into ubuntu?  I found something called prismstumbler though.  Will that work?

---

### Post by hikujk123 on 2008-03-18
Will intalling wifi radar do anything? :( I am upset because everything worked in the live CD, but now I can't even surf the web.

---

### Post by hikujk123 on 2008-03-18
bump.  Problem still not solved.:(  I love everything Ubuntu has to offer and dislike windows, but if I can't get my internet connection to work, I don't know what to do.  Would reinstalling Ubuntu do anything because everything worked on the live CD?  If so, how would I reinstall it without messing up my partitions?  I would just want the new install to replace ubuntu on my linux partition, as I have a dual boot system.  It would not be advisable for me to upgrade to Hardy Heron because I am a beginner, right?

---

### Post by hikujk123 on 2008-03-18
Does anyone know?:confused:

---

### Post by forrestcupp on 2008-03-18
Do you have a wireless icon in your notification area?  If so, right click it and see if wireless is enabled.  The left click it and see what connections come up.

---

### Post by cmnorton on 2008-03-18
Check your /etc/network/interfaces file. If necessary edit it as root (using sudo in front of your favorite editor and using your password when prompted), so it has the following only in it (other than comments).

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

Using a file like this, I was able to use wireless and wired without tweaking a thing in between.

---

### Post by hikujk123 on 2008-03-18
Forrestcup, I know how to do that.  As I said before, I had wireless working perfectly while using the live CD.  The problem is the driver.  I just don't know how to change it.  I want to switch my prism54 driver with my prism54pci driver.  For some unknown reason, the live CD loads prism54pci (which works), and installed ubuntu loads prism54 (which does not work).  C.M. Norton, I do not have experience with the terminal...what should I type into it?  Oh yeah, and wi-fi radar did not work.

---

### Post by cmnorton on 2008-03-18
> **hikujk123 said:**
> Forrestcup, I know how to do that.  As I said before, I had wireless working perfectly while using the live CD.  The problem is the driver.  I just don't know how to change it.  I want to switch my prism54 driver with my prism54pci driver.  For some unknown reason, the live CD loads prism54pci (which works), and installed ubuntu loads prism54 (which does not work).  C.M. Norton, I do not have experience with the terminal...what should I type into it?  Oh yeah, and wi-fi radar did not work.

sudo cp /etc/network/interfaces /etc/network/interfaces.sav (or instead of .sav, use today's date like 031808)

gksudo gedit /etc/network/interfaces

(you'll be prompted for the administrator's password. That's your password if you are the one who installed the system or are in the admin group.)

Check to see what's there.  If there are more lines than what is listed below, remove all lines, other than comments, except for what is below. If the lines below are not there, add them, and make sure there are no other lines in interfaces.

auto lo
iface lo inet loopback

Edit:
---------------------------

If suggest you reboot after editing this file.

---

### Post by hikujk123 on 2008-03-18
It said exactly what you said it would.  I am going to reboot to see what happens.

---

### Post by hikujk123 on 2008-03-18
I did what you said.  It didn't make a difference. ** Is there any way to replace the prism54 driver with the prism54pci driver?**

---

### Post by hikujk123 on 2008-03-18
bump

---

### Post by hikujk123 on 2008-03-18
BUMP.  The problem has still not been resolved.  Please help!:(:confused:](*,):cry:

---

### Post by theRightNee on 2008-03-18
have you tried reading the WifiDocs on your issues?

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by hikujk123 on 2008-03-19
Yes, I have.  It is not as simple as I thought it would be.  Can someone please give me a direct answer to this question: **Is there a way I can replace my prism54 driver with a prism54pci driver?**  I know how to use network manager.  As I have said over and over again, wireless worked perfectly in the live CD.  I should add that I successfully used WEP.  My problem remains the bolded question above that no one has answered.  I am not familiar with the command line, so if someone could tell me what to type that would  be helpful.  I have googled and searched the forums, so giving me links and telling me how to use the network manager won't help.

---

### Post by hikujk123 on 2008-03-19
Bump

---

### Post by handydan918 on 2008-03-19
I would try ```
sudo rmmod prism54
``` 
and ```
sudo modprobe prism54pci 
```
(assuming those are the correct driver names...)

Seems like 3 pages should have brought that suggestion to the fore already...

---

### Post by hikujk123 on 2008-03-19
I did that.  I think that the driver is called prism54 pci (with a space).  Thanks for being the first one that really answered my question.  However, this did not work.  How do I reinstall ubuntu without messing up my windows partition?

---

### Post by NR1224 on 2008-03-19
assuming that you are using 7.10, try the 8.04 alpha or beta if its out yet. I had the same problem but 8.04 had support for my wifi out of box.

---

### Post by handydan918 on 2008-03-19
> **hikujk123 said:**
> I did that.  I think that the driver is called prism54 pci (with a space).  Thanks for being the first one that really answered my question.  However, this did not work.  How do I reinstall ubuntu without messing up my windows partition?
OK, I'm not buying it. If the live CD worked, there is no reason in blue blazes the installed system shouldn't. Upgrading to Retching Rabbit or Pooping Penguin or what ever cannot be the only solution.
How about if you post the output of ```
lspci | grep -i net
```

as well as ```
lsmod
```

Let's see what's *really* in there...

---

### Post by handydan918 on 2008-03-19
> **NR1224 said:**
> assuming that you are using 7.10, try the 8.04 alpha or beta if its out yet. I had the same problem but 8.04 had support for my wifi out of box.

Unless I grossly misread the OP, he has already stated the live cd worked. That seems like "out-of-the-box-support" to me...

The issue is this: "If the live cd worked, what needs to be changed so that the installed system will work too?"

---

### Post by hikujk123 on 2008-03-19
Thanks for not giving up on me.  I tried loading the sis900 driver (because the live CD now said it used that one).  That did not work, then I read your post, so here:

The first one gave me this:
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:08.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


The second one gave me this:
Module                  Size  Used by
ipv6                  317192  8 
af_packet              28172  2 
binfmt_misc            14860  1 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  0 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9608  0 
container               6400  0 
video                  21140  0 
sbs                    21520  0 
ac                      7304  0 
dock                   12264  0 
button                 10400  0 
battery                12424  0 
sbp2                   27144  0 
lp                     15048  0 
snd_intel8x0           40104  1 
snd_ac97_codec        122200  1 snd_intel8x0
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
p54pci                 15232  0 
p54common              14848  1 p54pci
snd_rawmidi            29824  1 snd_seq_midi
mac80211              196104  2 p54pci,p54common
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
cfg80211                8720  1 mac80211
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
pcspkr                  4608  0 
serio_raw               9092  0 
prism54                64264  0 
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                45596  0 
k8temp                  7680  0 
snd                    69288  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_intel8x0,snd_pcm
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
sis_agp                11652  0 
evdev                  13056  4 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sd_mod                 32512  3 
sg                     41384  0 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
sata_sis               11524  2 
ata_generic             9988  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ehci_hcd               40076  0 
sis900                 27648  0 
mii                     7424  1 sis900
ohci_hcd               25092  0 
usbcore               161584  3 ehci_hcd,ohci_hcd
pata_sis               18564  1 sata_sis
libata                138928  3 sata_sis,ata_generic,pata_sis
scsi_mod              172856  5 sbp2,sd_mod,sg,sr_mod,libata
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor


Thanks for being so patient,

---

### Post by handydan918 on 2008-03-19
I'm having a little trouble nailing down the actual name of the driver for this card. 
Try this:
Boot the live cd. 
Verify wireless is working.
In a terminal, do
```
lspci |grep -i net
```

and ```
lsmod
```

again. 
This will tell us what driver is being used on the live cd, and if it is reporting the hardware the same way.

---

### Post by handydan918 on 2008-03-19
Go back and follow post #24 again. Use copy and paste to get it into the terminal. From what I have found, that is the correct name of the driver, and there is no space. (You should always be suspicious of any filename that has a space in Linux...either it's wrong, or it needs to be handled carefully!)

When you do those commands from #24, post the output of each back here for diagnostics. 
Well, unless they just work....

:)

---

### Post by hikujk123 on 2008-03-19
I am using the live CD right now.  I know wireless is working because I unplugged my wired connection and was still able to post this message.  Here are the outputs:

1) 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:08.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


2)Module                  Size  Used by
ipv6                  317192  8 
af_packet              28172  4 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
lp                     15048  0 
powernow_k8            16608  0 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9608  0 
video                  21140  0 
sbs                    21520  0 
container               6400  0 
button                 10400  0 
dock                   12264  0 
ac                      7304  0 
prism54                64264  0 
arc4                    3328  2 
ecb                     5248  2 
blkcipher               8452  1 ecb
rc80211_simple          8064  1 
snd_intel8x0           40104  1 
snd_ac97_codec        122200  1 snd_intel8x0
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
k8temp                  7680  0 
p54pci                 15232  0 
p54common              14848  1 p54pci
mac80211              196104  3 rc80211_simple,p54pci,p54common
cfg80211                8720  1 mac80211
parport_pc             41896  1 
psmouse                45596  0 
pcspkr                  4608  0 
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                44172  3 ppdev,lp,parport_pc
serio_raw               9092  0 
snd                    69288  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38300  0 
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_intel8x0,snd_pcm
pci_hotplug            36612  1 shpchp
sis_agp                11652  0 
evdev                  13056  4 
battery                12424  0 
squashfs               45192  1 
loop                   21764  2 
unionfs                87216  1 
sd_mod                 32512  2 
nls_cp437               8192  1 
isofs                  39268  1 
sg                     41384  0 
sr_mod                 19876  1 
cdrom                  41768  1 sr_mod
sata_sis               11524  1 
ohci1394               38984  0 
ieee1394              109528  1 ohci1394
sis900                 27648  0 
mii                     7424  1 sis900
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  3 ehci_hcd,ohci_hcd
pata_sis               18564  2 sata_sis
ata_generic             9988  0 
libata                138928  3 sata_sis,pata_sis,ata_generic
scsi_mod              172856  4 sd_mod,sg,sr_mod,libata
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor


Thanks again handydan.  We are getting closer.

---

### Post by handydan918 on 2008-03-19
One more time, with feeling!!
(From the installed system)
Just to be sure...
```
depmod -a
```
now...
```
rmmod prism54
```

and then


modprobe ```
p54pci
```

and again, post the output, unless it just hooks up.

---

### Post by hikujk123 on 2008-03-19
Outputs:

1)
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
2)ERROR: Removing 'prism54': Operation not permitted
3) last one had no output

Edit:  I already tried the number 24 command both ways.

---

### Post by handydan918 on 2008-03-19
> **hikujk123 said:**
> Outputs:

1)
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
2)ERROR: Removing 'prism54': Operation not permitted
3) last one had no output

OK, well the last one was the important one anyway. (At least, if it worked!)
So, did it?
If not let's see ```
lsmod | grep 54
```

---

### Post by hikujk123 on 2008-03-19
No, it does work yet :(.  Here is the output:
p54pci                 15232  0 
p54common              14848  1 p54pci
mac80211              196104  2 p54pci,p54common
prism54                64264  0

---

### Post by handydan918 on 2008-03-19
Try 
```
sudo rmmod prism54
```
 again. 
If that doesn't work, try 
```
sudo echo prism54 >> /etc/modprobe.d/blacklist
```

and then reboot and see if anyone salutes!

---

### Post by hikujk123 on 2008-03-19
I tried the first one.  There was no output and it didn't work.  The second one said:            bash: /etc/modprobe.d/blacklist: Permission denied

---

### Post by theRightNee on 2008-03-19
sudo -s
type your password
and you are now with root capabilities for the entire terminal session (use the power carefully)

---

### Post by hikujk123 on 2008-03-19
did what theRightNee said.  Then, I followed the three code handydan said to do and got the following.
WARNING: /etc/modprobe.d/blacklist line 27: ignoring bad line starting with 'prism54'

I also black listed prism54.

I am going to reboot.  I hope this works...

---

### Post by hikujk123 on 2008-03-19
Did not work. :( This is probably the longest thread during which no progress has been made. :( Thanks for the support so far.  I will post the diagnostics.

 lsmod | grep 54

p54pci                 15232  0 
p54common              14848  1 p54pci
mac80211              196104  2 p54pci,p54common
prism54                64264  0 

Although I am new, it seems that we still haven't killed that original prism54 driver.

Edit:

lsmod

Module                  Size  Used by
ipv6                  317192  8 
af_packet              28172  2 
binfmt_misc            14860  1 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  0 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9608  0 
container               6400  0 
video                  21140  0 
sbs                    21520  0 
ac                      7304  0 
dock                   12264  0 
button                 10400  0 
battery                12424  0 
sbp2                   27144  0 
lp                     15048  0 
snd_intel8x0           40104  1 
snd_ac97_codec        122200  1 snd_intel8x0
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
p54pci                 15232  0 
p54common              14848  1 p54pci
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
mac80211              196104  2 p54pci,p54common
cfg80211                8720  1 mac80211
pcspkr                  4608  0 
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
serio_raw               9092  0 
prism54                64264  0 
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                45596  0 
k8temp                  7680  0 
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_intel8x0,snd_pcm
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
sis_agp                11652  0 
evdev                  13056  4 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sd_mod                 32512  3 
sg                     41384  0 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
sata_sis               11524  2 
ata_generic             9988  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
sis900                 27648  0 
mii                     7424  1 sis900
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  3 ehci_hcd,ohci_hcd
pata_sis               18564  1 sata_sis
libata                138928  3 sata_sis,ata_generic,pata_sis
scsi_mod              172856  5 sbp2,sd_mod,sg,sr_mod,libata
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

---

### Post by hikujk123 on 2008-03-19
Great.  Now my ubuntu partition is completely messed up.  When I boot it up, it simply gives me the command line.  :mad:

---

### Post by Iandefor on 2008-03-19
Can you post the output of ```
dmesg
``` please?

Also, 
```
sudo echo prism54 >> /etc/modprobe.d/blacklist
``` is not the correct way to blacklist prism54.

the correct way would be```
echo blacklist prism54 | sudo tee -a /etc/modprobe.d/blacklist
```The correct syntax for the blacklist file is the same as the rest of modprobe. You still need to specify "blacklist [module]" in order for it to be blacklisted.

---

### Post by Suparious on 2008-03-19
you could always reinstall. You will have to partition manually (basically just assign mount points for each partition and choose "do not format') and choose 'No' when the installer asks you to install GRUB to the "MBR".

or even do a rescue, but it may still need you to partition manually if you care about your Ubuntu install.

if you can sudo on the commandline, you most likely wouldn't need to reinstall.

---

### Post by hikujk123 on 2008-03-19
I don't mind erasing the all of the data on my ubuntu partition, as long as my windows partition is safe.  So do I choose manual install?

Edit:  Not that I like windows better, I just installed ubuntu, so I don't have that many files on it. :)

---

### Post by hikujk123 on 2008-03-19
> **Iandefor said:**
> Can you post the output of ```
dmesg
``` please?

Also, 
```
sudo echo prism54 >> /etc/modprobe.d/blacklist
``` is not the correct way to blacklist prism54.

the correct way would be```
echo blacklist prism54 | sudo tee -a /etc/modprobe.d/blacklist
```The correct syntax for the blacklist file is the same as the rest of modprobe. You still need to specify "blacklist [module]" in order for it to be blacklisted.

Do you mean after reinstalling or before?

---

### Post by handydan918 on 2008-03-19
Try it before reinstalling. There is never any hurry to reinstall. You can always do that as a last resort.

And sorry about the echo sudo thing...I always stub my toes on sudoisms...guess I jsut got used to being root for doing root stuff over the years.

edit: I knew this was going to be a toughie as soon as I read the title!

---

### Post by Iandefor on 2008-03-20
> **hikujk123 said:**
> Do you mean after reinstalling or before?Before. Reinstall is generally a last resort; if you can fix the problem it's generally better than reinstalling.

By the way, you should also open up /etc/modprobe.d/blacklist and remove the line that just says prism54. You can do this safely with nano:

```
sudo nano /etc/modprobe.d/blacklist
``` Find the line, delete it, and hit Control-x. It'll ask you if you wish to save; enter y, then enter.

---

### Post by handydan918 on 2008-03-20
> **Iandefor said:**
> Before. Reinstall is generally a last resort; if you can fix the problem it's generally better than reinstalling.

By the way, you should also open up /etc/modprobe.d/blacklist and remove the line that just says prism54. You can do this safely with nano:

```
sudo nano /etc/modprobe.d/blacklist
``` Find the line, delete it, and hit Control-x. It'll ask you if you wish to save; enter y, then enter.

Why?

---

### Post by hikujk123 on 2008-03-20
I tried handy dan's command (sudo apt-get reconfigure xserver-xorg), but it wanted me to reconfigure everything manually.  For someone new to linux and taking into account ubuntu easy-to-use guided install, it was much easier to reinstall.  Let's get back to the wireless issue if it doesn't for some unknown reason work out of the box this time (ubuntu is installing right now).

I am thankful so many people want to help.  But now after the fresh installation, which command should I type first?  I really don't want to mess up my ubuntu partition again.

Edit:  Is important to say that I am using the 64 bit version?

---

### Post by Iandefor on 2008-03-20
> **handydan918 said:**
> Why?Why what?

---

### Post by hikujk123 on 2008-03-20
after the new install, dmesg gives me this:

[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] Command line: root=UUID=17aeb410-b829-4ea1-a0b4-7c5de5fffa13 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ff0000 - 0000000017ff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017ff3000 - 0000000018000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 98288) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7EC0 checksum 0
[    0.000000] ACPI: RSDP 000F7EC0, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 17FF3000, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 17FF3040, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 17FF30C0, 4169 (r1 AWARD  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 17FF0000, 0040
[    0.000000] ACPI: APIC 17FF7240, 005A (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000017ff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 98288) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000017ff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->    98288
[    0.000000] On node 0 totalpages: 98191
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1126 pages reserved
[    0.000000]   DMA zone: 2817 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1287 pages used for memmap
[    0.000000]   DMA32 zone: 92905 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e6c00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 95722
[    0.000000] Kernel command line: root=UUID=17aeb410-b829-4ea1-a0b4-7c5de5fffa13 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[   10.708911] time.c: Detected 2210.271 MHz processor.
[   10.709611] Console: colour VGA+ 80x25
[   10.709628] Checking aperture...
[   10.709631] CPU 0: aperture @ e8000000 size 64 MB
[   10.714927] Memory: 375572k/393152k available (2274k kernel code, 17192k reserved, 1185k data, 296k init)
[   10.714982] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.794861] Calibrating delay using timer specific routine.. 4422.61 BogoMIPS (lpj=8845226)
[   10.794900] Security Framework v1.0.0 initialized
[   10.794912] SELinux:  Disabled at boot.
[   10.794968] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   10.795466] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   10.795708] Mount-cache hash table entries: 256
[   10.795862] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.795865] CPU: L2 Cache: 512K (64 bytes/line)
[   10.795867] CPU 0/0 -> Node 0
[   10.795887] SMP alternatives: switching to UP code
[   10.796093] Freeing SMP alternatives: 24k freed
[   10.796546] Early unpacking initramfs... done
[   11.069132] ACPI: Core revision 20070126
[   11.069181] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.111333] Using local APIC timer interrupts.
[   11.156551] result 12558358
[   11.156552] Detected 12.558 MHz APIC timer.
[   11.158685] Brought up 1 CPUs
[   11.158864] NET: Registered protocol family 16
[   11.158940] ACPI: bus type pci registered
[   11.158947] PCI: Using configuration type 1
[   11.160124] ACPI: EC: Look up EC in DSDT
[   11.162752] ACPI: Interpreter enabled
[   11.162755] ACPI: (supports S0 S1 S3 S4 S5)
[   11.162769] ACPI: Using IOAPIC for interrupt routing
[   11.166434] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.166444] PCI: Probing PCI hardware (bus 00)
[   11.166971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.183201] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   11.183313] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   11.183411] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   11.183500] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   11.183589] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   11.183679] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   11.183766] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   11.183853] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   11.183921] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.183930] pnp: PnP ACPI init
[   11.183938] ACPI: bus type pnp registered
[   11.185592] pnp: PnP ACPI: found 11 devices
[   11.185594] ACPI: ACPI bus type pnp unregistered
[   11.185646] PCI: Using ACPI for IRQ routing
[   11.185648] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.185657] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   11.185748] NET: Registered protocol family 8
[   11.185750] NET: Registered protocol family 20
[   11.185803] agpgart: Detected AGP bridge 0
[   11.188105] agpgart: AGP aperture is 64M @ 0xe8000000
[   11.188188] pnp: 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[   11.188191] pnp: 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[   11.188194] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   11.188197] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   11.188432] PCI: Bridge: 0000:00:01.0
[   11.188435]   IO window: 9000-9fff
[   11.188438]   MEM window: ed000000-ed0fffff
[   11.188441]   PREFETCH window: e0000000-e7ffffff
[   11.188496] NET: Registered protocol family 2
[   11.190629] Time: tsc clocksource has been installed.
[   11.222652] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   11.222720] TCP established hash table entries: 16384 (order: 6, 393216 bytes)
[   11.222971] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[   11.223201] TCP: Hash tables configured (established 16384 bind 16384)
[   11.223204] TCP reno registered
[   11.234737] checking if image is initramfs... it is
[   11.762866] Freeing initrd memory: 7205k freed
[   11.769785] audit: initializing netlink socket (disabled)
[   11.769800] audit(1206011962.020:1): initialized
[   11.771417] VFS: Disk quotas dquot_6.5.1
[   11.771462] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   11.771554] io scheduler noop registered
[   11.771556] io scheduler anticipatory registered
[   11.771558] io scheduler deadline registered
[   11.771632] io scheduler cfq registered (default)
[   11.772330] Boot video device is 0000:01:00.0
[   11.792084] Real Time Clock Driver v1.12ac
[   11.792162] Linux agpgart interface v0.102 (c) Dave Jones
[   11.792165] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.792265] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.792754] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.793332] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.793525] input: Macintosh mouse button emulation as /class/input/input0
[   11.793585] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.796879] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.796884] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.797052] mice: PS/2 mouse device common for all mice
[   11.797177] TCP cubic registered
[   11.797234] NET: Registered protocol family 1
[   11.797427] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   11.797435] Freeing unused kernel memory: 296k freed
[   11.866323] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.951179] AppArmor: AppArmor initialized<5>audit(1206011963.204:2):  type=1505 info="AppArmor initialized" pid=1199
[   12.956249] fuse init (API version 7.8)
[   12.960903] Failure registering capabilities with primary security module.
[   12.972855] ACPI: Fan [FAN] (on)
[   12.979412] ACPI: Thermal Zone [THRM] (40 C)
[   13.473504] SCSI subsystem initialized
[   13.477900] libata version 2.21 loaded.
[   13.479076] pata_sis 0000:00:02.5: version 0.5.1
[   13.479240] scsi0 : pata_sis
[   13.479281] scsi1 : pata_sis
[   13.479377] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x0000000000014000 irq 14
[   13.479381] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x0000000000014008 irq 15
[   13.504404] usbcore: registered new interface driver usbfs
[   13.504430] usbcore: registered new interface driver hub
[   13.504451] usbcore: registered new device driver usb
[   13.514053] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.548056] sis900.c: v1.08.10 Apr. 2 2006
[   14.117243] ata2.00: ATAPI: HP  DVD Writer 630, AH02, max UDMA/33
[   14.293117] ata2.00: configured for UDMA/33
[   14.295183] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 630c  AH02 PQ: 0 ANSI: 5
[   14.296095] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   14.296231] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   14.296238] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   14.296620] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   14.296639] ohci_hcd 0000:00:03.0: irq 20, io mem 0xed105000
[   14.355015] usb usb1: configuration #1 chosen from 1 choice
[   14.355143] hub 1-0:1.0: USB hub found
[   14.355152] hub 1-0:1.0: 3 ports detected
[   14.460924] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   14.461076] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   14.461084] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   14.461389] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   14.461408] ohci_hcd 0000:00:03.1: irq 21, io mem 0xed106000
[   14.522817] usb usb2: configuration #1 chosen from 1 choice
[   14.522952] hub 2-0:1.0: USB hub found
[   14.522959] hub 2-0:1.0: 3 ports detected
[   14.628844] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[   14.628992] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   14.629000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   14.629321] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   14.629341] ohci_hcd 0000:00:03.2: irq 22, io mem 0xed102000
[   14.690796] usb usb3: configuration #1 chosen from 1 choice
[   14.690936] hub 3-0:1.0: USB hub found
[   14.690945] hub 3-0:1.0: 2 ports detected
[   14.796840] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[   14.796994] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   14.797336] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   14.797368] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   14.797378] ehci_hcd 0000:00:03.3: irq 23, io mem 0xed103000
[   14.797386] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.797767] usb usb4: configuration #1 chosen from 1 choice
[   14.797943] hub 4-0:1.0: USB hub found
[   14.797949] hub 4-0:1.0: 8 ports detected
[   14.904520] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   14.905369] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   14.914009] 0000:00:04.0: Using transceiver found at address 1 as default
[   14.914633] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 19, 00:11:2f:be:aa:69.
[   14.914720] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.968211] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[ed108000-ed1087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   14.975221] sata_sis 0000:00:05.0: version 0.8
[   14.975248] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.975253] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   14.975328] scsi2 : sata_sis
[   14.975374] scsi3 : sata_sis
[   14.975443] ata3: SATA max UDMA/133 cmd 0x000000000001ac00 ctl 0x000000000001b002 bmdma 0x000000000001bc00 irq 17
[   14.975448] ata4: SATA max UDMA/133 cmd 0x000000000001b400 ctl 0x000000000001b802 bmdma 0x000000000001bc08 irq 17
[   15.004535] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   15.004542] Uniform CD-ROM driver Revision: 3.20
[   15.004742] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   15.008695] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   15.443944] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   15.452221] ata3.00: ATA-6: WDC WD400JD-22HKA0, 13.03G13, max UDMA/133
[   15.452224] ata3.00: 78165360 sectors, multi 16: LBA 
[   15.472200] ata3.00: configured for UDMA/133
[   15.787713] ata4: SATA link down (SStatus 0 SControl 300)
[   15.798399] scsi 2:0:0:0: Direct-Access     ATA      WDC WD400JD-22HK 13.0 PQ: 0 ANSI: 5
[   15.798852] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   15.805857] sd 2:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   15.805871] sd 2:0:0:0: [sda] Write Protect is off
[   15.805873] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.805884] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.805942] sd 2:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   15.805948] sd 2:0:0:0: [sda] Write Protect is off
[   15.805950] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.805960] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.805964]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   15.849646] sd 2:0:0:0: [sda] Attached SCSI disk
[   16.092345] Attempting manual resume
[   16.092349] swsusp: Resume From Partition 8:5
[   16.092351] PM: Checking swsusp image.
[   16.092566] PM: Resume from disk failed.
[   16.132804] kjournald starting.  Commit interval 5 seconds
[   16.132815] EXT3-fs: mounted filesystem with ordered data mode.
[   16.259507] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000aa6606]
[   23.768273] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.911705] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.272625] Loaded prism54 driver, version 1.2
[   24.272676] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.272692] prism54: pci_set_mwi(pdev) succeeded
[   24.455485] input: PC Speaker as /class/input/input2
[   24.467833] parport_pc 00:08: reported by Plug and Play ACPI
[   24.467884] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   24.831494] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[   25.099060] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   25.161739] intel8x0_measure_ac97_clock: measured 57442 usecs
[   25.161744] intel8x0: clocking to 48000
[   25.625491] lp0: using parport0 (interrupt-driven).
[   25.700843] Adding 619880k swap on /dev/sda5.  Priority:-1 extents:1 across:619880k
[   26.076771] EXT3 FS on sda3, internal journal
[   26.945185] input: Power Button (FF) as /class/input/input4
[   26.949327] ACPI: Power Button (FF) [PWRF]
[   26.970932] input: Power Button (CM) as /class/input/input5
[   26.975039] ACPI: Power Button (CM) [PWRB]
[   26.996788] input: Sleep Button (CM) as /class/input/input6
[   27.000918] ACPI: Sleep Button (CM) [FUTS]
[   27.040945] No dock devices found.
[   27.289122] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   27.289162] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2
[   27.289164] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6
[   27.289166] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   28.491800] ppdev: user-space parallel port driver
[   28.675309] eth1: resetting device...
[   28.675330] eth1: uploading firmware...
[   28.810783] eth1: firmware version: 1.0.4.3
usy :(

---

### Post by hikujk123 on 2008-03-20
Too much for one post:

[   28.810829] eth1: firmware upload complete
[   29.810773] eth1: no 'reset complete' IRQ seen - retrying
[   30.487171] eth0: Media Link On 100mbps full-duplex 
[   30.810133] eth1: no 'reset complete' IRQ seen - retrying
[   30.810135] eth1: interface reset failure
[   30.810137] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[   30.893840] audit(1206026381.357:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4565 profile="/usr/sbin/cupsd"
[   31.040402] Failure registering capabilities with primary security module.
[   31.237019] Bluetooth: Core ver 2.11
[   31.237125] NET: Registered protocol family 31
[   31.237127] Bluetooth: HCI device and connection manager initialized
[   31.237131] Bluetooth: HCI socket layer initialized
[   31.250627] Bluetooth: L2CAP ver 2.8
[   31.250632] Bluetooth: L2CAP socket layer initialized
[   31.315650] Bluetooth: RFCOMM socket layer initialized
[   31.315730] Bluetooth: RFCOMM TTY layer initialized
[   31.315733] Bluetooth: RFCOMM ver 1.8
[   31.516685] Marking TSC unstable due to cpufreq changes
[   31.518371] Time: acpi_pm clocksource has been installed.
[   33.853175] eth1: resetting device...
[   33.853192] eth1: uploading firmware...
[   33.922610] eth1: firmware version: 1.0.4.3
[   33.922652] eth1: firmware upload complete
[   34.742351] eth1: no 'reset complete' IRQ seen - retrying
[   35.559969] eth1: no 'reset complete' IRQ seen - retrying
[   35.559978] eth1: interface reset failure
[   35.559980] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[   37.779150] NET: Registered protocol family 17
[   41.688361] NET: Registered protocol family 10
[   41.688495] lo: Disabled Privacy Extensions
[   50.618679] eth0: no IPv6 routers present
[   64.893031] eth1: resetting device...
[   64.893048] eth1: uploading firmware...
[   64.960424] eth1: firmware version: 1.0.4.3
[   64.960462] eth1: firmware upload complete
[   65.875391] eth1: no 'reset complete' IRQ seen - retrying
[   66.820119] eth1: no 'reset complete' IRQ seen - retrying
[   66.820125] eth1: interface reset failure
[   66.820127] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[   96.256132] eth1: resetting device...
[   96.256148] eth1: uploading firmware...
[   96.334695] eth1: firmware version: 1.0.4.3
[   96.334733] eth1: firmware upload complete
[   97.152193] eth1: no 'reset complete' IRQ seen - retrying
[   97.969854] eth1: no 'reset complete' IRQ seen - retrying
[   97.969860] eth1: interface reset failure
[   97.969862] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[  126.962962] eth1: resetting device...
[  126.962987] eth1: uploading firmware...
[  127.060114] eth1: firmware version: 1.0.4.3
[  127.060156] eth1: firmware upload complete
[  127.875247] eth1: no 'reset complete' IRQ seen - retrying
[  128.692907] eth1: no 'reset complete' IRQ seen - retrying
[  128.692914] eth1: interface reset failure
[  128.692916] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[  242.186465] eth1: resetting device...
[  242.186482] eth1: uploading firmware...
[  242.253486] eth1: firmware version: 1.0.4.3
[  242.253524] eth1: firmware upload complete
[  243.069444] eth1: no 'reset complete' IRQ seen - retrying
[  243.893029] eth1: no 'reset complete' IRQ seen - retrying
[  243.893037] eth1: interface reset failure
[  243.893039] prism54: Your card/socket may be faulty, or IRQ line too b

---

### Post by hikujk123 on 2008-03-20
bump

---

### Post by scuba_steve_va on 2008-03-20
Well, I know jack squat about wireless on Linux (other that the fact that getting it running is often a nightmare), so I'll apologize in advance for not being to help get your card working...but perhaps a backup approach will be useful.

I use a wireless Ethernet bridge.  I use them for Windows PCs and my Ubuntu boxes.  I like them for many reasons, not the least of which is that I don't need to screw with drivers. I just plug in the box and it has no idea it is on a wireless network.   Sure, they are not as convenient for a laptop, but they work great on desktops.


Rather than buy a bridge, I buy WRT54GL access point routers (with the "L"...NOT just a vanilla WRT54G) and reflash the firmware with the Tomato open source firmware.  I then throw the router in bridge mode and plug in my Ubuntu box.  Presto...the most painless wireless solution for Ubuntu that you can find.



Okay...back to your bumping.

---

### Post by hikujk123 on 2008-03-20
I am not going to give up.  It works in the live CD!

---

### Post by handydan918 on 2008-03-20
> **Iandefor said:**
> Why what?

Why this.

> By the way, you should also open up /etc/modprobe.d/blacklist and remove the line that just says prism54. 

What's the point of removing it?

---

### Post by handydan918 on 2008-03-20
> **hikujk123 said:**
> 

Edit:  Is important to say that I am using the 64 bit version?

Ummm...
Yeah. If you can possibly be induced to run the 32 bit version, it might make your life easier. 64 bit has some issues with some applications and some drivers. Some people get along fine with it, others, not at all. 
In my view, 64 bit doesn't offer enough performance benefit on the desktop to justify the potential problems. 


I still think the general course of action is to blacklist the driver that doesn't work, and load the one that the live cd uses when it works.I will let the ex post facto experts instruct you on how, because my system apparently doesn't behave like anyone else's. i have never had a module load after adding it to the  /etc/modprobe.d/blacklist, but what do I know?

Luck!

---

### Post by hikujk123 on 2008-03-20
Please don't give up.  What should I type now?  I am confused because of differing directions.  I don't want to mess up my log in screen again.

---

### Post by hikujk123 on 2008-03-20
bump.  I know the title says quick fix, but I didn't know what I was getting into....:(

---

### Post by hikujk123 on 2008-03-20
bump

---

### Post by Iandefor on 2008-03-20
> **handydan918 said:**
> What's the point of removing it?...Because that's incorrect syntax for blacklist and will continue to return errors and be annoying? It needs to be "blacklist prism54", not just "prism54".

It's not strictly necessary but won't hurt.

---

### Post by badspell68 on 2008-03-21
I had many of the same problems and most were solved when I booted to Generic mode from Server mode (it did the same thing on my install the Live-CD work). When booting his the ESC key and you will be able to choose to boot to Generic. I now need to figure out how to have it boot to Generic automatically??

---

### Post by handydan918 on 2008-03-21
> **Iandefor said:**
> ...Because that's incorrect syntax for blacklist and will continue to return errors and be annoying? It needs to be "blacklist prism54", not just "prism54".

It's not strictly necessary but won't hurt.
Sounds like a kind of "baby out with the bath water" approach. i omitted the word blacklist and your solution is to abandon the whole attempt, 
Thanks for pointing out the omission, though.
And unless you just dropped in after page 4 or so, the whole idea of blacklisting that module was to try to load the one that actually works. 
So, with that in mind, do you have anything constructive to add, or would you prefer to just sit and snipe at those of us trying to resolve this issue?

---

### Post by hikujk123 on 2008-03-21
Please don't argue.  Most of us have spent hours on this post.  I would like to have this issue resolved soon.  If any of you would like to tell what me to type, I will listen.  I have a new install now and am ready to go.

---

### Post by hikujk123 on 2008-03-21
Bump.  I am switching to xubuntu (if that makes a difference).  I still will need help to resolve this issue.  I am switching for another reason.

---

### Post by hikujk123 on 2008-03-21
bump.

---

### Post by hikujk123 on 2008-03-21
bump

---

### Post by hikujk123 on 2008-03-21
Both of you were right.  Handydan was right in what we had to do (replace drivers).  Iandefor was right in how you black list a driver.  Even though I haven't heard from either side for a day, thanks anyway!  I may just removel windows from my computer.

---

