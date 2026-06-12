---
title: "Music Problems"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by perenshaw on 2005-10-09
I want to play mp3s in ubuntu, wether it be in rhythmbox or any other program, but not had any luck so far.

i am slightly familiar with terminal commands bla di bla so that's not a problem.

sum1 told me to type a list of different commands the first of which was:
sudo apt-get install gstreamer0.8-plugins

i know what this does but the problem was that this was displayed:

Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate

 n i don't know what's wrong or how to sort it, can any1 help with the whole process n any recommendations for which program to use, i've heard amaroK is good n how do i get it

as well as this there is no sound coming out of my speakers, i know this is not a hardware problem, ubuntu must not be recognizing them or summat, any help

please:smile:

---

### Post by Ampersand on 2005-10-09
Hi
Have you followed the instructions to add extra repositories from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)?

Once you've done that, you can get a variety of media players from the Synaptic package manager (in the System - Administration menu). They're in the Multimedia and Multimedia (universe) sections.

For the sound, run 'gnome-volume-control' and make sure nothing's muted to start with.

---

### Post by Wolki on 2005-10-09
[QUOTE=perenshaw]I want to play mp3s in ubuntu, wether it be in rhythmbox or any other program, but not had any luck so far.

i am slightly familiar with terminal commands bla di bla so that's not a problem.

sum1 told me to type a list of different commands the first of which was:
sudo apt-get install gstreamer0.8-plugins[/quote]

Don't just do what someone tells you, listen to the wiki:  [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Read the relevant sections (Getting started and codecs) and follow the advice, and you will see that everything works.

> process n any recommendations for which program to use, i've heard amaroK is good n how do i get it

If you want a library-based player the most popular choices are Rhythmox, Amarok, Muine and Banshee. Rhythmbox is the one included with ubuntuby default. Banshee is very similar to RB. Amarok is a KDE App with a ton of features and I can appreciate that, but i sometimes feel a little lost and find some actions more complicated than i would like). Muine has a "less is more" approach, focussing on the things a music player really needs and making the ui for that simple and thus fast. I like it a lot, but development has slowed recently.

If you don't want a library, beep-media-player (and if you're oldschool xmms) has a familiar ui, and Totem (and the other video players) plays music without problem too.

> as well as this there is no sound coming out of my speakers, i know this is not a hardware problem, ubuntu must not be recognizing them or summat, any help

Could have many reasons. Is your sound card compatible with linux?

One thing that sometimes happen is that the volume is muted. run "alsamixer" and have a look at the values for master and pcm.

---

### Post by perenshaw on 2005-10-09
sorted, thanks to both of ya, 

well apart from the speaker problem but mp3s are playin fine, i chose amaroK btw

wot i need is a linux driver for the c-media cmi8738 sound card, but don't know how to install it

---

### Post by poofyhairguy on 2005-10-09
[QUOTE=perenshaw]sorted, thanks to both of ya, 

well apart from the speaker problem but mp3s are playin fine, i chose amaroK btw

wot i need is a linux driver for the c-media cmi8738 sound card, but don't know how to install it[/QUOTE]


If the driver for a sound card does not work out of the box, that often means it is not supported. Sorry.

---

### Post by Wolki on 2005-10-09
[QUOTE=perenshaw]wot i need is a linux driver for the c-media cmi8738 sound card, but don't know how to install it[/QUOTE]

Well, a linux driver is here: [http://www.zdnet.de/treiber/man_prod/c-media_soundkarten-wc.html](http://www.zdnet.de/treiber/man_prod/c-media_soundkarten-wc.html)

Even better news: The driver is already in the kernel since 2.6, that means it's already installed.

The only problem is that it doesn't work ^^;;

You say you can play mp3s, but the sound doesn't work? not sure I understand that part yet.

Apart from that, post the output of "lsmod".

---

### Post by perenshaw on 2005-10-09
root@perenshaw:/home/perenshaw # lsmod
Module                  Size  Used by
ipt_limit               2688  7
iptable_mangle          2944  0
ipt_LOG                 6656  7
ipt_MASQUERADE          3584  0
iptable_nat            24648  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              6528  0
ip_conntrack_irc       71856  0
ip_conntrack_ftp       72624  0
ipt_state               2048  4
ip_conntrack           43668  6 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
nls_cp437               5888  1
isofs                  33720  1
udf                    77060  0
af_packet              20744  4
ipv6                  229504  6
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
snd_cmipci             29472  0
snd_opl3_lib           10112  1 snd_cmipci
snd_hwdep               9220  1 snd_opl3_lib
snd_mpu401_uart         7168  1 snd_cmipci
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
stv680                 25612  0
videodev                9728  1 stv680
joydev                  9408  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
usbhid                 29376  0
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_opl3_lib,snd_pcm
snd                    50276  12 snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
forcedeth              16128  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  5 stv680,usbhid,ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4608  2 snd_cmipci,analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
evdev                   9088  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  1
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  2
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  930
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by Wolki on 2005-10-09
Hm... i think it should work, the sound drivers are loaded...  What exactly doesn't work?

oh, you could try "sudo modprobe cmpci".

---

### Post by perenshaw on 2005-10-09
at the mo i'm upgradin to breezy so i'll wait for that to finish, couple o mins left. i get soud out when i plug speakers into onboard sound, nothing comes out when i use the sound card, i'll figure it out eventually

---

### Post by kemosabe79 on 2005-10-09
Sounds like a conflict. Try disabling your on-board sound in your BIOS.

---

### Post by perenshaw on 2005-10-09
it seems that quite a few people have got a problem with this particular sound card tho, i've been searching on the forum, but haven't found any solutions yet. dya mind helpin out - seein if u can find owt els on the forum that ya think mite work.

another thing is wen i do plug it into onboard sound it is a tiny bit fuzzy.

jus so u no, i'm usin the sound card cos i got 5.1 speakers in, although u prob guessed.

thanks 4 the help so far anyway:)

---

### Post by Wolki on 2005-10-09
[QUOTE=perenshaw]another thing is wen i do plug it into onboard sound it is a tiny bit fuzzy.
[/QUOTE]

I agree with what kemosabe said. Try disabling your onboard sound card, probably in the bios or by setting a jumper. Breezy has better support for multiple sound cards afaik, but a disabled sound card can't interfer :)
I have the fuzzy sound with my onboard card too. Fix it by lowering the master volume to ~75%.

---

### Post by perenshaw on 2005-10-10
All sorted.
I did the easiest thing, re-installed.
Upgraded to breezy again before messing about with anything else, and...

it worked! Yeye!

I now have 5.1 surround sound again wuppee, thanks 4 all the help guys, but in the end it just takes a fresh start to do the job sometimes.

[SIZE=6][SIZE=7]ubuntu[/SIZE]
[SIZE=2]if something goes wrong, 
reinstall - it only takes half 
an hour* [SIZE=1]as long as you've got
no important work to back up!

[SIZE=2]jus kiddin, i love ubuntu now that mi sounds workin, it really is more user friendly and faster than windows when it comes down to it.[/SIZE]:D
[/SIZE][/SIZE][/SIZE]

---

### Post by Wolki on 2005-10-10
[QUOTE=perenshaw]I now have 5.1 surround sound again wuppee, thanks 4 all the help guys, but in the end it just takes a fresh start to do the job sometimes.

[SIZE=6][SIZE=7]ubuntu[/SIZE]
[SIZE=2]if something goes wrong, 
reinstall - it only takes half 
an hour* [SIZE=1]as long as you've got
no important work to back up!

[SIZE=2]jus kiddin, i love ubuntu now that mi sounds workin, it really is more user friendly and faster than windows when it comes down to it.[/SIZE]:D
[/SIZE][/SIZE][/SIZE][/QUOTE]

I'm quite sure you would have gotten it to work without a reinstall, but yes, sometimes that's the easiest solution :)

Look into seperate /home/ partition for a way to reinstall without having to backup stuff ;)

---

