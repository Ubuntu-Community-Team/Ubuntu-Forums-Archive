---
title: "lubuntu, Quantal, no alsamixer or sound"
date: 2012-10-03
forum: Apple Hardware Users
---

### Post by 2blue on 2012-10-03
On a freshly installed lubuntu quantal ppc I have no alsamixer in terminal. I have reinstalled alsa-utils package and ran the command "sudo rm /etc/modrpobe.d/blacklist.local.conf" which did the trick in 12.04. I still have no sound or audio icon on taskbar, but alsamixer showed up in terminal for a while with a message; "this sound device does not have any controls". Today after a reboot, alsamixer no longer shows in terminal and is back to; "cannot open mixer: No such file or directory" (yes, I typed in "alsamixer").

I posted this in the Ubuntu+1 section, but no replies. I suspect it is more general iBook G4 issue, perhaps with some quantal qirks, but I don`t understand what is listed in the ppc faq page. 

Any idea on how to go about it?

---

### Post by 2blue on 2012-10-04
This is what lsmod show: 

[PHP]:~$ lsmod
Module                  Size  Used by
isofs                  33786  1 
arc4                    1293  2 
btusb                  13186  0 
joydev                 10796  0 
b43                   361772  0 
mac_hid                 3617  0 
rtc_generic             1291  0 
ams                     8952  0 
mac80211              488045  1 b43
input_polldev           3920  1 ams
appletouch              9478  0 
bnep                   12196  2 
rfcomm                 37419  12 
parport_pc             35692  0 
bluetooth             203250  22 btusb,bnep,rfcomm
ppdev                   7506  0 
lp                      8871  0 
parport                36849  3 parport_pc,ppdev,lp
cfg80211              189258  2 b43,mac80211
apm_emu                 1400  0 
apm_emulation           7056  2 apm_emu
snd_powermac           63922  0 
bcma                   29338  1 b43
snd_pcm                83299  1 snd_powermac
snd_seq_midi            5380  0 
snd_rawmidi            22648  1 snd_seq_midi
snd_seq_midi_event      7003  1 snd_seq_midi
snd_seq                59154  2 snd_seq_midi,snd_seq_midi_event
snd_timer              21771  2 snd_pcm,snd_seq
snd_seq_device          6638  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68504  6 snd_powermac,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7187  1 snd
snd_page_alloc          7172  1 snd_pcm
hid_generic              865  0 
usbhid                 42009  0 
hid                    86015  2 hid_generic,usbhid
firewire_ohci          34665  0 
firewire_core          62189  1 firewire_ohci
sungem                 29702  0 
sungem_phy             11741  1 sungem
crc_itu_t               1459  1 firewire_core
ssb                    49967  1 b43
uninorth_agp            [/PHP]

---

### Post by 2blue on 2012-10-04
[This]("http://imagebin.org/230890") is how my modprobe.d folder looks like.

---

### Post by rsavage on 2012-10-04
PowerPC sound modules got updated in 12.10.  You will need to research what happened to them as I have absolutley no idea or interest in doing said research.  Look at the PowerPC kernel developers mailing list.  That is the point of being a tester - to find stuff out!

---

### Post by 2blue on 2012-10-04
well, after some reading, and a suggestion in an email I reinstalled alsa-utils, libasound2 and tried to launch alsamixer -a basic. This G4 seems to behave different than others, and I get the message:

[PHP]alsamixer -a basic
ALSA lib simple_abst.c:131:(try_open_full) Unable to open library '/usr/lib/powerpc-linux-gnu/alsa-lib/smixer/smixer-python.so'
cannot open mixer: No such device or address
[/PHP]

Yes, something has happened and I am searching for any info I can find. 

:-k

---

### Post by windscape on 2012-10-04
Hi,

Try installing/re-installing the libasound2-python package, since Googling smixer-python.so 12.10 seems to suggest that is the package containing that library that alsamixer is trying to open.

---

### Post by 2blue on 2012-10-04
.

---

### Post by 2blue on 2012-10-04
Thanks windscape.

I installed libasound2 python package, it wasn`t preinstalled (should it be?), but to no effect. I should get a full list of package dependencies.

Edit: After a reboot, this is what alsamixer -a basic shows now. 

 alsamixer -a basic
ALSA lib python.c:991:(alsa_mixer_simple_finit) Unable to find python module '/usr/lib/powerpc-linux-gnu/alsa-lib/smixer/python/main.py'
cannot open mixer: No such device

---

### Post by windscape on 2012-10-04
Hi,

I have the same error in Xubuntu 12.04.1 on amd64, so I think that parameter doesn't actually work in Ubuntu.

To perhaps get some more information, could you please provide the output of the command dmesg

It will probably be quite a bit of output, so please paste it to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and supply the URL.

---

### Post by 2blue on 2012-10-04
I can: hope there is something useful [there]("http://paste.ubuntu.com/1261183/").

---

### Post by nm_geo on 2012-10-05
> **2blue said:**
> I can: hope there is something useful [there]("http://paste.ubuntu.com/1261183/").

 12.261199] snd-powermac no longer handles any machines with a layout-id property in the device-tree, use snd-aoa.

That might be a problem.  You will probably need to do some blacklisting and remove some blacklisting as well.  I think it would be wise to at least see what is blacklisted. I would comment out with # things that I wanted to work not remove a complete blacklist file.

Look through this link too.

[http://debian.2.n7.nabble.com/no-sound-on-macmini-G4-on-wheezy-sid-td1996795.html](http://debian.2.n7.nabble.com/no-sound-on-macmini-G4-on-wheezy-sid-td1996795.html)

Sorry but my old PowerBook G4 work fine so I have no more experience to add.

---

