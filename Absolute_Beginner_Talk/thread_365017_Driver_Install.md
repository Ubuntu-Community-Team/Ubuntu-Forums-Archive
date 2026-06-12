---
title: "Driver Install"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-02-19
Hi everyone,

I have some wireless card problems that I hope I can fix by installing the driver.

I have Realtek 8185.

I found this:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352)

I see a linux driver and a windows one.

I have NdisWrapper installed.  When I view the readme of the linux driver, all of the commands for setting up connections and security etc. are done in terminal.  Does this mean that the GUI of network manager would not work with this driver?  would I be better off using the windows driver and ndiswrapper?

Thanks


Readme from Driver ATTACHED

---

### Post by renzokuken on 2007-02-19
gui should still work fine.

i have the realtek 8187 chipset. the linux drivers didnt work for me, but the WIN98 drivers with ndiswrapper worked perfectly though.

i had to blacklist the rtl, r8187 and rtl8187 modules though. you may have to do something similar.

i'm not sure how comparable my 8187 is with your 8185 though

---

### Post by brandoncolorado on 2007-02-19
When I try to install the windows driver in ndiswrapper nothing happens.  I choose the inf file and there is no error or anything.  I wonder if this is because I need to blacklist?

---

### Post by renzokuken on 2007-02-19
type 

```
ndiswrapper -l
```

and let me know what the output is (its a lower case "L" above btw)

---

### Post by brandoncolorado on 2007-02-19
> **renzokuken said:**
> type 

```
ndiswrapper -l
```

and let me know what the output is (its a lower case "L" above btw)

brandon@brandon-laptop:~$ ndiswrapper -l
No drivers installed
brandon@brandon-laptop:~$


I am online with WEP working, signal strength is pinned at 30% and will not change.


When I right click on network manager and choose properties,

It has driver listed as RTL8180.

---

### Post by renzokuken on 2007-02-19
can you post the output of

```
lsmod
```

---

### Post by brandoncolorado on 2007-02-19
> **renzokuken said:**
> can you post the output of

```
lsmod
```

brandon@brandon-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  257632  8 
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
powernow_k8            10888  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  1 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
af_packet              21768  6 
dm_mod                 60088  5 
md_mod                 78740  0 
fuse                   41864  2 
parport_pc             36132  0 
lp                     11972  0 
parport                37320  2 parport_pc,lp
joydev                 10304  0 
tsdev                   8256  0 
snd_hda_intel          18580  1 
snd_hda_codec         163712  1 snd_hda_intel
r818x                  93708  0 
psmouse                40072  0 
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
serio_raw               7300  0 
ieee80211_rtl          82696  1 r818x
nvidia               6827412  32 
snd_pcm                80520  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_hda_intel,snd_pcm
evdev                  10496  2 
agpgart                33456  1 nvidia
i2c_core               22288  2 i2c_ec,nvidia
pcspkr                  3072  0 
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
rtc                    12596  0 
ext3                  138888  1 
jbd                    55700  1 ext3
forcedeth              30220  0 
ehci_hcd               32520  0 
ohci_hcd               20740  0 
usbcore               130304  3 ehci_hcd,ohci_hcd
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  1 ide_cd
ide_disk               17664  3 
generic                 5252  0 
amd74xx                14364  0 [permanent]
sata_nv                10116  0 
libata                 73228  1 sata_nv
scsi_mod              141320  1 libata
thermal                14600  0 
processor              26028  2 powernow_k8,thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability

---

### Post by brandoncolorado on 2007-02-19
Also, with this setup, my connection is fine and stable in Windows, but in Ubuntu I drop my connection or cannot connect at all while I am at school.  Seems maybe like a power management thing or something.  How can I get ndiswrapper to accept the driver without knowing why it is blank after inputting the .inf file?

---

### Post by renzokuken on 2007-02-20
ok, your lsmod shows that it has loaded the **ieee80211_rtl 82696 1 r818x** for wireless and ndiswrapper is not being used.

you'll need to blacklist this module (and maybe others) and try and get ndiswrapper working properly again.

what are the files you have for the windows driver? there should be an inf and probably a .sys file too.

---

### Post by brandoncolorado on 2007-02-20
I was having trouble with the 8185 drivers off of the Realtek website, so I got the specific ones from Gateway's website.

D00584-001-002

net8185.inf

rtl8185.sys

Today, my problem with wireless is this:  I can stay online for about a minute, then I have to uncheck the box for enable wireless in network manager and re-check it and then my wireless works for one minute about.

Thanks for all of your help.

---

### Post by renzokuken on 2007-02-21
this may not be actually be wireless related issue. 

i have heard that some people resolved this by changing their router settings. 

get into the router and look for a setting called "beacon interval" or something. dropping this from 100 to 10 helped my wireless

EDIT: .....or was it the other way round? well have a play and see if it helps.

---

### Post by brandoncolorado on 2007-02-21
This is an issue that happens at my school.  I sit in class where everyone has laptops.  Everyone's works, even mine works with Windows.  There are other students with my same laptop who sit with me and their laptops work.  It happens in the same places (Same classes, same seats usually) so I am thinking that this is an issue with power or something.  Drop, reconnect, drop, reconnect. :(

---

### Post by brandoncolorado on 2007-02-25
Any other ideas? :(

---

