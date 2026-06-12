---
title: "Sound card issues"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by uruk912 on 2008-02-08
Alright i got my wireless to work via ndiswrapper witch im so happy about but the next one would be to get my sound card to work. Now im not sure what to type to get sound card specs so if some one will comment me back on this i will type the command in and post the specs. Oh also this is an Acer Aspire 5315 notebook. has intell cellron processer. so if any one has any ideas plz tell me thanks in advance.
uruk

---

### Post by jaytek13 on 2008-02-08
Can you do ```
lsmod | grep '^snd'
``` at the command line and post your output here?

Also, are you getting any error messages or simply not able to hear anything when you play it?

---

### Post by uruk912 on 2008-02-08
ruk912@uruk912-laptop:~$ lsmod grep '^snd'
Usage: lsmod
uruk912@uruk912-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  0 
ipv6                  273892  10 
af_packet              24840  4 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
button                  8976  0 
container               5504  0 
dock                   10656  0 
battery                11012  0 
ndiswrapper           185240  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  2 
snd_pcm_oss            44672  1 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
psmouse                39952  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sd_mod                 30336  3 
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ahci                   23300  2 
ata_piix               17540  0 
libata                125168  3 ata_generic,ahci,ata_piix
scsi_mod              147084  4 sd_mod,sg,sr_mod,libata
tg3                   110980  0 
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



And i dont hear anything at all and i didnt know how to make the stright up and down line like you did.

---

### Post by jaytek13 on 2008-02-08
You need what is called a pipe in the lsmod command that I listed. | is above the enter key and requires a shift press on US keyboards.

If you prefer you can always copy and paste the code I posted.

---

### Post by agim on 2008-02-08
There is a button above the enter key. Shift and press it. Without the shift, its just a forward slash key ( \ ).

Its a great asset when working with the command line, it pipes the output of one command (in this case lsmod) into the input of another command (grep '^snd').

I have some sound issues too, I hope this post can help us both.

---

### Post by uruk912 on 2008-02-08
uruk912@uruk912-laptop:~$ lsmod | grep '^snd'
snd_hda_intel         263712  2 
snd_pcm_oss            44672  1 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


Yeah didnt think of that lol but yeah i need pipe? will u post a link to it so i can understand it?

---

### Post by jaytek13 on 2008-02-08
> **uruk912 said:**
> uruk912@uruk912-laptop:~$ lsmod | grep '^snd'
snd_hda_intel         263712  2 
snd_pcm_oss            44672  1 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


Yeah didnt think of that lol but yeah i need pipe? will u post a link to it so i can understand it?

[http://en.wikipedia.org/wiki/Pipeline_(Unix](http://en.wikipedia.org/wiki/Pipeline_(Unix)) is the wiki...

in short, when you type what I posted, lsmod | grep '^snd' "piped" the information to grep. lsmod is simply a command. grep is kind of a way, simply to speak, of formatting that information. '^snd' were the "arguments" for that, meaning in that specific command I only wanted things listed that started with snd. 

It appears your sound card has been detected. What happens when you
```
sudo modprobe snd_hda_intel
```
?

---

### Post by uruk912 on 2008-02-08
nothing litterly nothing
uruk912@uruk912-laptop:~$ sudo modprobe snd_hda_intel
[sudo] password for uruk912:
uruk912@uruk912-laptop:~$

---

### Post by jaytek13 on 2008-02-08
> **uruk912 said:**
> nothing litterly nothing
uruk912@uruk912-laptop:~$ sudo modprobe snd_hda_intel
[sudo] password for uruk912:
uruk912@uruk912-laptop:~$

Nothing is technically good. It means that module loaded without issue. No errors can be a good thing, sometimes... although others, like now, it can mean it might be very difficult to figure this problem out. 

Have you made sure of your volume levels? What distro are you using? Like, Ubuntu or Kubuntu?

---

### Post by uruk912 on 2008-02-08
Ubuntu and i can adjust the volume lvl with the buttions on my laptop and it shows the volume thing on the bar.

---

### Post by jaytek13 on 2008-02-08
> **uruk912 said:**
> Ubuntu and i can adjust the volume lvl with the buttions on my laptop and it shows the volume thing on the bar.


And you're sure it's not muted? It can be kind of confusing. The 'mute' option isn't readily visible, really. If you right click on the volume thingy (how technical, eh?) and configure it you should be able to figure out if it is or not. It's like a circle with a line through it, for mute.

We have to rule out the simple things first.

---

### Post by uruk912 on 2008-02-08
No but thier are two volumes i can pick i can pick the HDA intell (Alsa mixer) or Realtek ID 268 (oss mixer)

---

