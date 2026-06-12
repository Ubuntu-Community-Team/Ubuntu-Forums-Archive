---
title: "Still having sound issues"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by JParkus on 2006-12-30
OK  i have been on this for about a week my sound is not working ive tried the following

parkus@parkus:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

and about 20 other commands 

i reinstalled alsa , and gstreamer also switched to kubuntu hoping that it would install the missing sound devices

the only thing that worked i cannot find again

it was something to do with device ids the way it was described to me is the computer thinks that something like my keyboard is set as my default sound card 

if anyone knows where the thread for this is or knows the command to switch it is please tell me 

i really am liking (k)ubuntu  i jsut need sound

---

### Post by Paradoxed on 2006-12-30
What is the result of "lsmod|grep snd"?

(sorry do this as well)

alsaconf

---

### Post by JParkus on 2006-12-30
parkus@parkus:~$ lsmod|grep snd
parkus@parkus:~$ sudo lsmod | grep snd
parkus@parkus:~$ sudo lsmod|grep snd
parkus@parkus:~$

im on the KDE desktop right know should i switch to gnome

---

### Post by Paradoxed on 2006-12-30
No need to switch.

without the sudo


lsmod | grep snd

---

### Post by JParkus on 2006-12-30
parkus@parkus:~$ lsmod|grep snd
parkus@parkus:~$ sudo lsmod | grep snd
parkus@parkus:~$ sudo lsmod|grep snd
parkus@parkus:~$ lsmod | grep snd
parkus@parkus:~$

still nothing

i didnt do this until i added the KDE desktop

---

### Post by Paradoxed on 2006-12-30
Okay then type this in

alsaconf

---

### Post by JParkus on 2006-12-30
parkus@parkus:~$ alsaconf
bash: alsaconf: command not found
parkus@parkus:~$ sudo alsaconf
sudo: alsaconf: command not found
parkus@parkus:~$

---

### Post by Paradoxed on 2006-12-30
Try in root

alsaconf


if it comes up with the same error then it sounds like you do not have alsa-util installed.

First - I assume you downloaded the latest versions of the three related source archives - alsa-driver, alsa-lib, alsa-util, etc... from [www.alsa-project.org](www.alsa-project.org).

bunzip, untar the sources... bzip2 -dc alsa-blah.tar.bz2 | tar xvf -

configure, compile, install the alsa-driver package first

      cd alsa-driver-*

      ./configure
      make
      make install

In the same directory - run the 'snddevices' script to add the necessary devices and symlinks, etc...

      ./snddevices 

Now install the alsa-lib package

      cd alsa-lib-*
      ./configure
      make
      make install 

Finally, install the alsa-util package

      cd alsa-util-*
      .configure
      make
      make install 

You need to set up your /etc/modules.conf before you have a hope of getting everything to work correctly.

---

### Post by JParkus on 2006-12-30
parkus@parkus:~$ root alsaconf
bash: root: command not found

---

### Post by Paradoxed on 2006-12-30
> **JParkus said:**
> parkus@parkus:~$ root alsaconf
bash: root: command not found


you need to type 

sudo su

it should ask for your password

then 
> alsaconf  hit enter
after it has found your soundcard type 
>  alsamixer 
 hit enter
set your levels using the m key to un-mute and the up/down arrows for volume levels
once your happy type " alsactl store " hit enter
this will save your settings

---

### Post by rajeev1204 on 2006-12-30
hi

when he says root he means type sudo, not root

sudo alsaconf


also try this [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) 

and this   [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by JParkus on 2006-12-30
ok ive tried reinstalling alsa via synaptic 
i downloaded the programs you told me about when i try to install them it says i already have the newest version

---

### Post by rajeev1204 on 2006-12-30
hi

Have u tried the 2 links in my post?

Also try this

go to system>preferences>multimedia systems selector and do a sound test with different devices

also rightclick on volume icon in taskbar and check to see if all settings are up.

Which is ur soundcard? onboard??

---

### Post by JParkus on 2006-12-30
alsaconf does nothing
alsamixer does nothing

i tried lspci and ?i cant remember the other command  antways heres what came up  hopefully it can help 


Module                  Size  Used by
nls_cp437               5888  0
isofs                  37688  0
udf                    88580  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
ipv6                  265856  6
af_packet              22920  2
tsdev                   8000  0
pcspkr                  2180  0
rtc                    13492  0
floppy                 62148  0
analog                 12320  0
gameport               15496  1 analog
i2c_piix4               9104  0
psmouse                36100  0
i2c_core               21904  1 i2c_piix4
serio_raw               7300  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
8139too                26880  0
mii                     5888  1 8139too
natsemi                28000  0
intel_agp              22940  1
agpgart                34888  1 intel_agp
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33808  0
usbcore               130820  2 uhci_hcd
ide_disk               17664  3
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
parkus@parkus:~$ lspci | fgrep 'audio'
parkus@parkus:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:03.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:00:04.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
parkus@parkus:~$ alsaconf
bash: alsaconf: command not found
parkus@parkus:~$

---

### Post by JParkus on 2006-12-30
it is onboard
im trying everthing i can on the links you sent me

---

### Post by rajeev1204 on 2006-12-30
hmm

sounds like ur soundcard has not been installed or something

do u have a dual boot? Is there sound in windows?

also lspci command doesnt list sound card i think. And alsaconf command doesnt work for me either.So leave it.


What motherboard do u use? Is it the intel 440 ls? I think its an old board. hmm . I will look around for more info if possible

U hang in there 

Which version of ubuntu are u using?

P.S. Maybe its asimple problem and be sure to look at all the obvious things .

---

### Post by JParkus on 2006-12-30
maybe i can make it easier for you to help i went through the links and a few more this is what worked

sudo modprobe snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388

it then says to insert the following(by the way after this it brought up alsamixer)

$ echo options [module-name] [module-options] >> /etc/modprobe.d/[module-name]

so im thinking "hey lets restart to see if it actually saved it "
im not so lucky i tried alsamixer i get 

parkus@parkus:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
parkus@parkus:~$ aplay -l
aplay: device_list:221: no soundcards found...

so i try the sudo mod...

now i get the following


WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
FATAL: Error inserting snd (/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.15-27-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.15-27-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
FATAL: Error inserting snd (/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
parkus@parkus:~$

---

### Post by rajeev1204 on 2006-12-30
hi

Iam a newbie when it comes to those things . I will try again tomorrow. I dont know whether it is safe to mess with modprob.
Have u tried to look for IRQ conflicts.? U can search for that too in the links. GOOD LUCK.Take care with that modprob thing . Make a backup or i think it does that automatically
bye

regards

rajeev

---

### Post by JParkus on 2006-12-30
thank you for the help

---

### Post by rajeev1204 on 2006-12-31
hi 

any luck?

---

