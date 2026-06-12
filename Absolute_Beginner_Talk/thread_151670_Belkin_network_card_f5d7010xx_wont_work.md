---
title: "Belkin network card f5d7010xx wont work"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Pauloasis on 2006-03-28
Hi this is my First post so appoligise if I am doing it wrong. I have just been searching the internet for an answer to my network card problem . basicaly I am trying to learn linux , I have desided that Ubuntu is a reasonable desktop system . my problem is and has been the same with every linux disto I try, the Belkin network card f5d7010xx

so far On Ubuntu I can see it in the device window and when I remove it the device dissapears so I know its working in that respect however in the window it is marked as a PCi when its a removable network card . I dont have a clue yet about the code in linux I just need to get the internet up and runing before I can learn any thing about linux . The machine is an IBM thinkpad R40E I am using it simply for Linux so can format the whole thing over and over any help would be greatly appriciated . Chers Paul

---

### Post by trent dillman on 2006-03-28
Plug your card in, and then post the output of the following commands:

```

lspci
lsmod

```

You'll probably need to install the Windows drivers, which requires ndiswrapper.

```

sudo apt-get install ndiswrapper-utils ndisgtk

```

---

### Post by Pauloasis on 2006-03-28
lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5901 100Base-TX (rev 01)
0000:00:0c.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
pauloasis@ubuntu:~$
pauloasis@ubuntu:~$
pauloasis@ubuntu:~$
pauloasis@ubuntu:~$
pauloasis@ubuntu:~$ lsmod
Module                  Size  Used by
radeon                 78080  1
drm                    64884  2 radeon
ppdev                   9764  0
ipv6                  251200  6
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
isofs                  35960  0
udf                    90820  0
pcmcia                 26568  2
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
ibm_acpi               17684  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
rtc                    12344  0
pcspkr                  3396  0
yenta_socket           25292  2
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_ali1535             6948  0
i2c_ali15x3             7428  0
i2c_core               21200  3 i2c_acpi_ec,i2c_ali1535,i2c_ali15x3
snd_ali5451            24740  1
snd_ac97_codec         83932  1 snd_ali5451
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  1 snd_pcm
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
ati_agp                 9036  1
agpgart                34792  2 drm,ati_agp
dm_mod                 57692  0
tsdev                   7776  0
evdev                   9664  0
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  0
lp                     12292  0
parport                35912  3 ppdev,parport_pc,lp
md                     45584  0
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
tg3                    96772  0
ohci_hcd               20644  0
usbcore               117884  2 ohci_hcd
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  3
ide_generic             1376  0
alim15x3               12204  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   26896  722
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
pauloasis@ubuntu:~$

i typed in  " sudo apt-get install ndiswrapper-utils ndisgtk  "  it asked me for a password , i typed my user password   but nothing

---

### Post by NetMatrix on 2006-03-28
It gave you no response?

---

### Post by trent dillman on 2006-03-28
Look at my steps in [http://ubuntuforums.org/showthread.php?t=151459](http://ubuntuforums.org/showthread.php?t=151459)

Also, try installing build-essentials from synaptic first.

---

### Post by Pauloasis on 2006-03-28
HI  I really have no idea at all about  lInux  , I am ok with  Win xp    like click  and install , however  what the heck  do I  do  with a  tar.tar file .  I  have  ndiswrapper-1.10 .  I  only  have  XP  on line   the  Umbuntu  diss is on laptop. I want to get on line  with laptop so  I can  sit  downstairs  and  learn  it. I really am a novice with this  system . I  am going to look at the links you supplied  thank you

---

### Post by trent dillman on 2006-03-28
No net connection from Ubuntu? Visit packages.ubuntu.com and download ndiswrapper-utils and ndisgtk before you try compiling from source. Download the packages and any dependencies they have, then install them by copying them to your home folder, then open a terminal (Applications > Accessories > Terminal).

Install using ```
sudo dpkg -i ndis*.deb
```

---

### Post by Pauloasis on 2006-03-28
Thanks  , your  really being helpful. I  mean I have no  internet conection  on my laptop , thats were teh  Ubuntu is installed  . I have to use XP   then  copy  the files to  disk .. I  will follow  what  you  have advised  . thanks

---

### Post by Pauloasis on 2006-03-29
I now have  ndiswrapper  installed   I  have copied  the belkin drivers to  a folder called belkin  I typed the  following  ndiswrapper -i home/pauloasis/belkindrivers/bcmw15.inf
 it then reported 
instaling  bcmw15o     unable to  create directory /etc/ndiswrapper/bcmw15o. make sure your running as root 


I know have internet access via  network  cable  to router  but still cant get  wirless to work  . This has taken  three weeks  and  to date  all i have managed  is to get ndsiwrapper to  load  lol  HELP>>>>

---

### Post by trent dillman on 2006-03-30
try 

```

sudo ndiswrapper -i home/pauloasis/belkindrivers/bcmwl5.inf

```

---

### Post by Pauloasis on 2006-04-02
Almost but not quite there,  have installed Suse 10 (  will add Umbuntu after I get  card to work ) and used the  ndiswrapper , used original drivers  from  win xp  driver disk  , also configured the card and it show up in network connections  as not disabled . have  etho active  and on line but still no luck with getting network card to work  Is there something  I should  now do in the confi files ? on the wireless card  I have one light on . so  close now I think .

---

### Post by antd on 2006-04-03
I can tell you that I never got my same card to work. I installed all the inf files.

1. WinXP native
2. CD
3. From the Dell site
4. From the Belkin site

---

### Post by Pauloasis on 2006-04-03
what  do you  mean ?  winxp native ?  I only used the driver from the  Belkin CD  . have you  got your card to work ? If so  how did you  do it  . thanks 
Paul

---

