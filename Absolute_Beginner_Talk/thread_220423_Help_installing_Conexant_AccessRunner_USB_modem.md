---
title: "Help installing Conexant AccessRunner USB modem"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by GaryReggae on 2006-07-21
Hi folks,

I am completely new to the world of Linux although I've got a fairly in-depth experience of computing using Windows.

I thought I'd give an alternative OS a try.  Ubuntu (Dapper Drake) was very easy to install and I find the GUI very easy to use.  It recognised all my hardware except my USB Modem, Conexant AccessRunner DSL.  

Now I'm sure USB modems are a common issue here but I haven't yet found any instructions for getting this working.  A Google or search of this forum reveals drivers and other info but it might as well as well be Dutch to me.  One site has no instructions, another tells me to compile kernels and do SuDo and even the page in the UbuntuWiki documentation tells you to extract the firmware using some kind of software which needs installing.  However, it really doesn't tell me how to install the software.

What I need is an absolute idiots guide, eg "Click on the X button", type in "Y", "go to Networking on the System menu".

If anyone could tell me what to do or point me in the direction of a beginner friendly set of instructions then that would be great.  I don't mind using the command prompt as I've dabbled with MS-DOS but you need to tell me exactly what to type.

I hope somebody can help, otherwise I shall have no option other   than to return to the unreliable world of WinXP as an OS with no internet is useless to me.  I know that buying a router is an 'easy' fix but I'd really rather not as my USB modem works fine and I already have enough cables snaking behind my comp thank you!

Thanks,

Gary

---

### Post by GaryReggae on 2006-07-22
After a lengthy trawl through these forums, I managed to find something that looked promising : [http://www.ubuntuforums.org/showthread.php?t=145138](http://www.ubuntuforums.org/showthread.php?t=145138)

I followed all the steps but my modem still doesn't work - 

I extracted the firmware from the CnxEtU.sys on the driver CD to cxacru-fw.bin and then copied the .bin file to /lib/firmware/ - I assume this worked as it came up with a 'firmware found at [location]' message.

I then wrote the script exactly as posted on the aforementioned thread and saved it as /usr/local/sbin/checkADSL.sh  Originally, when I ran the script, it came up with errors but these were due to typing errors!  When I run the corrected script, it doesn't come up with anything - I assume this means there are no errors?

I then created a file named 'Freeola' in /etc/ppp/peers/ (Freeola being the name of my ISP).  I made sure that the VPI and VCI numbers were correct (the same ones I had to put in to get the thing to work in Win)

Finally, I added the bit to the end of /etc/network/interfaces exactly as detailed and added my DSL username/password to the chap-secrets and pap-secrets files in /etc/ppp/

While I can't say I undertood all of what I was doing, I followed the instructions precisely.  I found the command prompt usage fairly straightforward and I can now copy files, change the permissions, change the owner and navigate and list directories using the terminal.  

I have made sure that all the files I have added/changed have full rwxrwxrwx permissions.

What I have done has achieved something - the light on the modem is now on while I am in Ubuntu, however, when I go into the Networking control panel, PPP is disabled.  I click on 'Activate' but it says that it cannot find the device.

I then decided to try some newer modem drivers so I got the exact driver from DriverGuide.com (Windows versions only) for my Mercury AUS 18CX modem (the chipset is the AccessRunner and indeed in WinXP, the Device Mgr lists it as a Conexant AccessRunner).  I then tried to extract the firmware from the newer CnxEtU.sys file and interestingly, it came up with a message that it could not find any AccessRunner firmware.

However, I would have thought the modem would work using the software on the CD as these drivers work find in WinXP so they must be correct drivers for this modem, surely?

Any ideas?](*,)

---

### Post by zxee on 2006-07-22
"There be a lot of big words there, we be but humble pirates..."
:) Welcome to linux and ubuntu!
Let me restate some of your issue; you're using a usb modem through dsl-is that correct? In other words this is not a dial up connection. Ok. Have you checked out the sourceforge page on your modem? Go here: [http://sourceforge.net/projects/accessrunner](http://sourceforge.net/projects/accessrunner)
I hope that helps to some degree and again, welcome.

---

### Post by GaryReggae on 2006-07-22
Hi Zxee, many thanks for your reply.  Yes, you're right, the USB modem in question is for DSL, not dial up.

I have had a look at the Sourceforge page and downloaded the driver file but the instructions don't make a lot of sense to me:

> Notes: First public release of the usbatm kernel subsystem including cxacru. To use it unpack the archive in the root of the kernel tree (it will replace some files in drivers/usb/atm) and rebuild. Note: due to a small lag in development speedtch doesn't work with the current usbatm, and is not included in this release. NOTE: the package can be used only as an integral part of the Linux kernel source tree, thus the kernel license terms apply to it.

What is the 'Kernel Tree'?  I will try extracting the files I downloaded to /dev/usb/atm/ but I don't hold out a lot of hope as  it looks more complicated to me.  

What is Speedtch?  Do I need it?

Anyway, I'll edit this post in a few minutes when I've tried it.  Thanks again for your help!

EDIT: No luck - I could even find the folder to extrace it to. :(  Any ideas?

---

### Post by zxee on 2006-07-22
Sorry I may have inadvertantly sent you off in the wrong direction. I thought the sourceforge driver was something useful but apparently not. I did a search at [www.linmodems.org](www.linmodems.org) but their drivers are dial up not dsl. I'm not an expert in dsl so I should bow out. You could post the results of lsmod and lsusb perhaps that will get the ball rolling.

---

### Post by GaryReggae on 2006-07-23
OK thanks.

Right, here's what I get when I type 'lsmod' at the command prompt:

> Module                  Size  Used by
nls_cp437               5888  1
isofs                  37688  1
udf                    88452  0
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
lp                     11844  0
af_packet              22920  2
tsdev                   8000  0
psmouse                36228  0
serio_raw               7300  0
usbhid                 38368  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
usblp                  13056  0
floppy                 62148  0
rtc                    13492  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
pcspkr                  2180  0
i2c_viapro              8980  0
via_ircc               26900  0
irda                  186940  1 via_ircc
crc_ccitt               2304  1 irda
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117156  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
via_rhine              23940  0
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
bt878                  10552  0
mii                     5888  1 via_rhine
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
tuner                  42276  0
tvaudio                23836  0
snd_bt87x              14664  0
bttv                  164304  1 bt878
video_buf              22148  1 bttv
i2c_algo_bit            9608  1 bttv
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
v4l2_common             6016  1 bttv
btcx_risc               5128  1 bttv
snd_pcm                89864  4 snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_osssnd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
nvidia               4550772  0
tveeprom               15248  1 bttv
i2c_core               21904  8 i2c_acpi_ec,i2c_viapro,tuner,tvaudio,bttv,i2c_algo_bit,nvidia,tveeprom
emu10k1_gp              3840  0
gameport               15496  2 emu10k1_gp
snd                    55268  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_seq_device,snd_hwdep,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  3 snd_emu10k1,snd_bt87x,snd_pcm
videodev                9856  1 bttv
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
via_agp                 9856  1
agpgart                34888  2 nvidia,via_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0
usbcore               129668  5 usbhid,usblp,ehci_hcd,uhci_hcd
ide_cd                 33028  1
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  4
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


I don't know what most of that means but it looks like some kind of hardware database.

Here is the result of lsusb:

> Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04b8:0818 Seiko Epson Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1267:0210 Logic3 / SpectraVideo plc
Bus 001 Device 001: ID 0000:0000


The Epson device is my multifunction printer and I am fairly certain that the Logic 3 is my mouse (which is USB).  The offending DSL modem is not in that list.

Interesting, the damn thing has been playing up in WinXP over the last couple of days, refusing to connect unless I reboot, hanging up on me and once not working until I uplug it and put it back in.  I really am tempted to get a cheap DSL router.  Will any DSL router work in Ubuntu or are there only certain ones that are OK?  I want to get a fairly cheap one. 

Thanks,

Gary

---

### Post by zxee on 2006-07-23
You might want to check here: [http://www.linuxcompatible.org/](http://www.linuxcompatible.org/)
You can also do a search on any router you find including the word linux.
Of course you can ask here. Start a new thread asking what's a known good DSL router.

---

### Post by GaryReggae on 2006-07-24
Thanks, will do.

---

