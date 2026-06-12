---
title: "No touchpad tab in settings"
date: 2013-11-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bernard-carignan1 on 2013-11-19
Hello,

My notebook is an  ASUS model X551CA running Ubuntu 12.04 64 bit.
I don't use a mouse, I'm using my touchpad as a mouse, however, there is no "touchpad" tab in "mouse and touchpad" of the "system settings".
So I can't use very useful touchpad functions such as 2 finger scrolling and disable touchpad while typing.

Can anyone help me fix this please?

Thank you very much for your time

Bernard

---

### Post by varunendra on 2013-11-20
Hello Bernard, Welcome to the forums!

Please open a terminal (Ctrl-Alt-T), run the following commands and post back their outputs-
```
xinput
cat /proc/bus/input/devices
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by zeppike on 2013-12-21
Hi I have the same problem. Here are the outputs you have asked for. Thank you for your help!

```

sapi@sapi-pc:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Elantech Touchpad                  	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=9	[slave  keyboard (3)]

```
```
sapi@sapi-pc:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input4
U: Uniq=
H: Handlers=rfkill kbd event4 
B: PROP=0
B: EV=100013
B: KEY=800000000000 0 0 a1606c00900000 8200027800501000 e000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Elantech Touchpad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=04f2 Product=b404 Version=6963
N: Name="USB2.0 HD UVC WebCam"
P: Phys=usb-0000:00:1a.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input12
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

```
```
sapi@sapi-pc:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247165  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
nls_iso8859_1          12713  2 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79962  1 
coretemp               13596  0 
kvm_intel             137899  0 
arc4                   12573  2 
kvm                   455932  1 kvm_intel
ath9k                 151796  0 
mac80211              630977  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              422432  2 ath9k,ath9k_common
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               82214  0 
snd_hwdep              13668  1 snd_hda_codec
videobuf2_core         40785  1 uvcvideo
ghash_clmulni_intel    13259  0 
videodev              130053  2 uvcvideo,videobuf2_core
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  620571  3 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
cryptd                 20501  1 ghash_clmulni_intel
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
drm_kms_helper         49597  1 i915
drm                   287564  4 i915,drm_kms_helper
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_nb_wmi            12854  0 
cfg80211              525326  3 ath9k,mac80211,ath
asus_wmi               24581  1 asus_nb_wmi
microcode              23017  0 
sparse_keymap          13890  1 asus_wmi
i2c_algo_bit           13564  1 i915
mei                    41820  0 
psmouse                97873  0 
video                  19652  2 i915,asus_wmi
wmi                    19256  1 asus_wmi
serio_raw              13215  0 
mac_hid                13253  0 
lpc_ich                17144  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   25879  4 
r8169                  68716  0 
libahci                31606  1 ahci

```

---

### Post by varunendra on 2013-12-22
Welcome to the forums zeppike!

Have you updated Ubuntu yet? Try that first, and if the updates don't fix the problem, please try -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```
This will simply unload then reload the touchpad driver. If a simple driver remove-reload cycle doesn't help, try it again with a parameter this time -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

If that also doesn't make it work, another thing to try is -
```
xinput float "PS/2 Elantech Touchpad"
xinput reattach "PS/2 Elantech Touchpad" "Virtual core pointer"
```

All of above are temporary workarounds that will have to be done on every boot. If any of them helps, we can make them permanent for the time being and hope it gets actually 'fixed' in forthcoming updates.

---

### Post by zeppike on 2014-01-05
Sadly eider of the driver reloads worked. I don't know if anything can be done for this touch-pad, I hope we can figure something out. It is not a major problem, and I can't spend too many time with it, because the machine is not mine, I just installed Ubuntu on it, for a friend of mine.
Thank you for your time and help!

---

### Post by varunendra on 2014-01-05
Have you checked the obvious? That is - the Fn-key combination (usually Fn+F9 for Asus) to toggle touchpad on/off.

If yes, and the combination switch has no effect, please post back the outputs of -
```
grep -i touchpad /var/log/syslog
grep -i touchpad /var/log/Xorg.0.log
```

---

### Post by srini-vassan on 2014-01-22
You can try install **Synaptiks from ubuntu SW center. For me it worked 80% except right click (on Asus X552EA laptop). Vertical & horizontal scrolling worked better.**

---

### Post by aartau on 2014-03-03
The solution is posted here- [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1166442]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442")[COLOR=#000000] Comment #137.

After you click on the link, make sure you click on "view all ... comments" to load attachments within postings.[/COLOR]

---

