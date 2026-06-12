---
title: "how to use a external firewire iSight-Webcam with Ubuntu?"
date: 2009-05-17
forum: Apple Hardware Users
---

### Post by produnis on 2009-05-17
Hi folks,

I installed Ubuntu 9.04 on the 2nd HD of my Intel-MacPro.

Everything works fine, but there is on topic I just can't solve:

How to run my external Firewire-iSight-Webcam.

There are several docs out there, describing how to run the [BUILT-IN USB iSight with Ubuntu]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight"), but they won't work for me, as my iSight isn't built-in, but connected via Firewire to my Mac.

So, my question is:
Is there anybody out there, who made the external Firewire-iSight to run with Ubuntu?

Thanks in advance,

Produnis

---

### Post by cyberdork33 on 2009-05-18
This is the only how-to I know of for the external iSight:
[http://ubuntuforums.org/showthread.php?t=572039](http://ubuntuforums.org/showthread.php?t=572039)

---

### Post by produnis on 2009-05-18
thanks for answering me

I knew that page, and I have kind a problem described there...


I read [here]("http://osdir.com/ml/ports.mactel.user/2006-11/msg00046.html"), that the firewire-isight would run, if libdc1394 and coriander is installed.
I didn' find libdc1394 in synaptic, but installing libc6-dev and [libdc1394-13]("http://packages.ubuntu.com/jaunty/libdc1394-13")[ should be quite the same]("http://packages.ubuntu.com/jaunty/libdc1394-13").

So, I installed them both - and the following packages, which [I read here]("http://ubuntuforums.org/showpost.php?p=4649034&postcount=4"):
```
#sudo apt-get install dvgrab libavc1394-0 libdc1394-13 libdc1394-13-dev libfreebob0 libiec61883-0 libiec61883-dev libraw1394-8 libraw1394-dev coriander
```I followed the manual and added this to /etc/modules
```
raw1394
video1394
ohci1394
dv1394
```But if I try to 
```
sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394
```it gives me back```

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release
```If I start coriander, it gives me:
```
Warning: could not get a handle to your IEEE1394 card
Please check that:
- the card is present
- the IEEE1394 modules (ieee1394, ohci1394, raw1394 and video1934) are loaded
- you have read/write permissions on the /dev/raw1394 and /dev/video1394 devices

```If I type in (without &quot;#&quot;)...:
```
#sudo chmod -R 777 /dev/raw1394
#sudo chmod -R 777 /dev/video1394-0  # there is only this, I have no /dev/video1394 
```...first, and then start coriander, it gives me:
```
libdc1394 error: Failed to initialize libdc1394
Segmentation fault
```If I type in:
```
dmesg|grep video
```it gives me:
```
produnis@UbuntuPro:~$ dmesg|grep video
[    1.455603] pci 0000:08:00.0: Boot video device
[    8.634745] video1394: Installed video1394 module
```Anyone any suggestions what I could do?
thx in adv

---

### Post by cyberdork33 on 2009-05-19
make sure the ieee1394 module is loaded as well

'lsmod' will list the loaded modules.

Installing coriander seems to want to install libdc1394-22 (not -13). I would uninstall the -13 version.

You should not chmod /dev/* devices. Use "sudo" to start coriander instead.

I did not get that error when modprobing the 1394 modules. I don't think it is an issue you need to worry about anyway.

coriander seemed to startup OK for me after install the -22 version of libdc1394 (except that it could not find a camera... but that is expected since I do not have one.)

There is a source package for vloopback in the karmic Koala repos when you get to that point:
[http://packages.ubuntu.com/karmic/vloopback-source](http://packages.ubuntu.com/karmic/vloopback-source)

More info, but really sounds the same:
[http://thegrid.wordpress.com/how-to-use-isight-in-linux/](http://thegrid.wordpress.com/how-to-use-isight-in-linux/)

---

### Post by produnis on 2009-05-19
> **cyberdork33 said:**
> 
make sure the ieee1394 module is loaded as well
'lsmod' will list the loaded modules.

Thx for that, I modprobe ieee1394.
This is what lsmod gives me:

```
produnis@UbuntuPro:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
uinput                 15616  2 
video                  25360  0 
output                 11008  1 video
dv1394                 25948  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
raw1394                32732  0 
nvidia               7233756  38 
hid_apple              14336  0 
video1394              23740  0 
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i5000_edac             18060  0 
edac_core              47404  3 i5000_edac
pcspkr                 10496  0 
agpgart                42696  1 nvidia
usbhid                 42336  0 
shpchp                 40212  0 
applesmc               29360  0 
led_class              12036  1 applesmc
input_polldev          11912  1 applesmc
ohci1394               38576  2 dv1394,video1394
ieee1394               94660  4 dv1394,raw1394,video1394,ohci1394
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
produnis@UbuntuPro:~$ 
produnis@UbuntuPro:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
uinput                 15616  2 
video                  25360  0 
output                 11008  1 video
dv1394                 25948  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
raw1394                32732  0 
nvidia               7233756  38 
hid_apple              14336  0 
video1394              23740  0 
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i5000_edac             18060 a 0 
edac_core              47404  3 i5000_edac
pcspkr                 10496  0 
agpgart                42696  1 nvidia
usbhid                 42336  0 
shpchp                 40212  0 
applesmc               29360  0 
led_class              12036  1 applesmc
input_polldev          11912  1 applesmc
ohci1394               38576  2 dv1394,video1394
ieee1394               94660  4 dv1394,raw1394,video1394,ohci1394
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```Does it look ok?



> **cyberdork33 said:**
> 
Installing coriander seems to want to install libdc1394-22 (not -13). I would uninstall the -13 version.

Thx again, I uninstalled libdc1394-13.... I then figured out, that -22 was already installed at my system

> **cyberdork33 said:**
> 
coriander seemed to startup OK for me after install the -22 version of libdc1394 (except that it could not find a camera... but that is expected since I do not have one.)

Lucky you... I still get the error
```
libdc1394 error: Failed to initialize libdc1394
Segmentation fault
```Could it be, that this error occurs, because I don't have neither /dev/video1394 nor /dev/video0 ?
I only have /dev/video1394-0
Maybe coriander wants it without the -0  ?
This is how my /dev/ looks like:

```
produnis@UbuntuPro:/dev$ ls -la
insgesamt 4
drwxr-xr-x  15 root   root        4240 2009-05-19 21:10 .
drwxr-xr-x  22 root   root        4096 2009-05-15 19:56 ..
crw-rw----+  1 root   audio    14,  12 2009-05-19 21:09 adsp
crw-rw----+  1 root   audio    14,   4 2009-05-19 21:09 audio
drwxr-xr-x   2 root   root         680 2009-05-19 21:09 block
drwxr-xr-x   3 root   root          60 2009-05-19 21:09 bus
lrwxrwxrwx   1 root   root           3 2009-05-19 21:09 cdrom -> sr0
lrwxrwxrwx   1 root   root           3 2009-05-19 21:09 cdrw -> sr0
drwxr-xr-x   2 root   root        3600 2009-05-19 21:10 char
crw-------   1 root   root      5,   1 2009-05-19 21:10 console
lrwxrwxrwx   1 root   root          11 2009-05-19 21:09 core -> /proc/kcore
crw-rw----   1 root   root     10,  60 2009-05-19 21:09 cpu_dma_latency
drwxr-xr-x   6 root   root         120 2009-05-19 21:09 disk
crw-rw----+  1 root   audio    14,   3 2009-05-19 21:09 dsp
crw-rw----   1 root   root    171,  32 2009-05-19 21:09 dv1394-0
lrwxrwxrwx   1 root   root           3 2009-05-19 21:09 dvd -> sr0
lrwxrwxrwx   1 root   root           3 2009-05-19 21:09 dvdrw -> sr0
crw-rw----   1 root   root     10,  63 2009-05-19 21:09 ecryptfs
lrwxrwxrwx   1 root   root          13 2009-05-19 21:09 fd -> /proc/self/fd
crw-rw-rw-   1 root   root      1,   7 2009-05-19 21:09 full
crw-rw-rw-+  1 root   fuse     10, 229 2009-05-19 21:09 fuse
crw-rw----   1 root   root    251,   0 2009-05-19 21:09 hidraw0
crw-rw----   1 root   root    251,   1 2009-05-19 21:09 hidraw1
crw-rw----   1 root   root    251,   2 2009-05-19 21:09 hidraw2
crw-rw----   1 root   root     10, 228 2009-05-19 21:09 hpet
prw-------   1 root   root           0 2009-05-19 21:09 initctl
drwxr-xr-x   3 root   root         100 2009-05-19 21:09 .initramfs
-rw-r--r--   1 root   root           0 2009-05-19 21:09 .initramfs-tools
drwxr-xr-x   4 root   root         360 2009-05-19 21:10 input
crw-r-----   1 root   kmem      1,   2 2009-05-10 17:20 kmem
crw-rw----   1 root   root      1,  11 2009-05-19 21:09 kmsg
srw-rw-rw-   1 root   root           0 2009-05-19 21:10 log
brw-rw----   1 root   disk      7,   0 2009-05-10 17:20 loop0
brw-rw----   1 root   disk      7,   1 2009-05-19 21:09 loop1
brw-rw----   1 root   disk      7,   2 2009-05-19 21:09 loop2
brw-rw----   1 root   disk      7,   3 2009-05-19 21:09 loop3
brw-rw----   1 root   disk      7,   4 2009-05-19 21:09 loop4
brw-rw----   1 root   disk      7,   5 2009-05-19 21:09 loop5
brw-rw----   1 root   disk      7,   6 2009-05-19 21:09 loop6
brw-rw----   1 root   disk      7,   7 2009-05-19 21:09 loop7
drwxr-xr-x   2 root   root          60 2009-05-19 21:09 mapper
crw-r-----   1 root   kmem      1,   1 2009-05-19 21:09 mem
crw-rw----+  1 root   audio    14,   0 2009-05-19 21:09 mixer
drwxr-xr-x   2 root   root          60 2009-05-10 17:20 net
crw-rw----   1 root   root     10,  59 2009-05-19 21:09 network_latency
crw-rw----   1 root   root     10,  58 2009-05-19 21:09 network_throughput
crw-rw-rw-   1 root   root      1,   3 2009-05-10 17:20 null
crw-rw-rw-   1 root   root    195,   0 2009-05-19 21:10 nvidia0
crw-rw-rw-   1 root   root    195, 255 2009-05-19 21:10 nvidiactl
crw-rw----   1 root   root      1,  12 2009-05-19 21:09 oldmem
drwxr-xr-x   2 root   root          60 2009-05-19 21:09 pktcdvd
crw-r-----   1 root   kmem      1,   4 2009-05-19 21:09 port
crw-------   1 root   root    108,   0 2009-05-10 17:20 ppp
crw-rw----   1 root   root     10,   1 2009-05-19 21:09 psaux
crw-rw-rw-   1 root   tty       5,   2 2009-05-19 21:33 ptmx
drwxr-xr-x   2 root   root           0 2009-05-19 21:09 pts
brw-rw----   1 root   disk      1,   0 2009-05-19 21:09 ram0
brw-rw----   1 root   disk      1,   1 2009-05-19 21:09 ram1
brw-rw----   1 root   disk      1,  10 2009-05-19 21:09 ram10
brw-rw----   1 root   disk      1,  11 2009-05-19 21:09 ram11
brw-rw----   1 root   disk      1,  12 2009-05-19 21:09 ram12
brw-rw----   1 root   disk      1,  13 2009-05-19 21:09 ram13
brw-rw----   1 root   disk      1,  14 2009-05-19 21:09 ram14
brw-rw----   1 root   disk      1,  15 2009-05-19 21:09 ram15
brw-rw----   1 root   disk      1,   2 2009-05-19 21:09 ram2
brw-rw----   1 root   disk      1,   3 2009-05-19 21:09 ram3
brw-rw----   1 root   disk      1,   4 2009-05-19 21:09 ram4
brw-rw----   1 root   disk      1,   5 2009-05-19 21:09 ram5
brw-rw----   1 root   disk      1,   6 2009-05-19 21:09 ram6
brw-rw----   1 root   disk      1,   7 2009-05-19 21:09 ram7
brw-rw----   1 root   disk      1,   8 2009-05-19 21:09 ram8
brw-rw----   1 root   disk      1,   9 2009-05-19 21:09 ram9
crw-rw-rw-   1 root   root      1,   8 2009-05-19 21:09 random
crw-rw----   1 root   root    171,   0 2009-05-19 21:09 raw1394
lrwxrwxrwx   1 root   root           4 2009-05-19 21:09 rtc -> rtc0
crw-rw----   1 root   root    254,   0 2009-05-19 21:09 rtc0
lrwxrwxrwx   1 root   root           3 2009-05-19 21:09 scd0 -> sr0
brw-rw----   1 root   disk      8,   0 2009-05-19 21:09 sda
brw-rw----   1 root   disk      8,   1 2009-05-19 21:09 sda1
brw-rw----   1 root   disk      8,   2 2009-05-19 21:09 sda2
brw-rw----   1 root   disk      8,  16 2009-05-19 21:09 sdb
brw-rw----   1 root   disk      8,  17 2009-05-19 21:09 sdb1
brw-rw----   1 root   disk      8,  18 2009-05-19 21:09 sdb2
brw-rw----   1 root   disk      8,  19 2009-05-19 21:09 sdb3
crw-rw----+  1 root   audio    14,   1 2009-05-19 21:09 sequencer
crw-rw----+  1 root   audio    14,   8 2009-05-19 21:09 sequencer2
crw-rw----+  1 root   cdrom    21,   0 2009-05-19 21:09 sg0
crw-rw----   1 root   disk     21,   1 2009-05-19 21:09 sg1
crw-rw----   1 root   disk     21,   2 2009-05-19 21:09 sg2
drwxrwxrwt   2 root   root         100 2009-05-19 21:27 shm
crw-rw----   1 root   root     10, 231 2009-05-19 21:09 snapshot
drwxr-xr-x   2 root   root         200 2009-05-19 21:09 snd
lrwxrwxrwx   1 root   root          24 2009-05-19 21:09 sndstat -> /proc/asound/oss/sndstat
brw-rw----+  1 root   cdrom    11,   0 2009-05-19 21:09 sr0
lrwxrwxrwx   1 root   root          15 2009-05-19 21:09 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root   root          15 2009-05-19 21:09 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root   root          15 2009-05-19 21:09 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root   tty       5,   0 2009-05-19 21:27 tty
crw--w----   1 root   root      4,   0 2009-05-19 21:09 tty0
crw-------   1 root   root      4,   1 2009-05-19 21:10 tty1
crw--w----   1 root   tty       4,  10 2009-05-19 21:09 tty10
crw--w----   1 root   tty       4,  11 2009-05-19 21:09 tty11
crw--w----   1 root   tty       4,  12 2009-05-19 21:09 tty12
crw--w----   1 root   tty       4,  13 2009-05-19 21:09 tty13
crw--w----   1 root   tty       4,  14 2009-05-19 21:09 tty14
crw--w----   1 root   tty       4,  15 2009-05-19 21:09 tty15
crw--w----   1 root   tty       4,  16 2009-05-19 21:09 tty16
crw--w----   1 root   tty       4,  17 2009-05-19 21:09 tty17
crw--w----   1 root   tty       4,  18 2009-05-19 21:09 tty18
crw--w----   1 root   tty       4,  19 2009-05-19 21:09 tty19
crw-------   1 root   root      4,   2 2009-05-19 21:10 tty2
crw--w----   1 root   tty       4,  20 2009-05-19 21:09 tty20
crw--w----   1 root   tty       4,  21 2009-05-19 21:09 tty21
crw--w----   1 root   tty       4,  22 2009-05-19 21:09 tty22
crw--w----   1 root   tty       4,  23 2009-05-19 21:09 tty23
crw--w----   1 root   tty       4,  24 2009-05-19 21:09 tty24
crw--w----   1 root   tty       4,  25 2009-05-19 21:09 tty25
crw--w----   1 root   tty       4,  26 2009-05-19 21:09 tty26
crw--w----   1 root   tty       4,  27 2009-05-19 21:09 tty27
crw--w----   1 root   tty       4,  28 2009-05-19 21:09 tty28
crw--w----   1 root   tty       4,  29 2009-05-19 21:09 tty29
crw-------   1 root   root      4,   3 2009-05-19 21:10 tty3
crw--w----   1 root   tty       4,  30 2009-05-19 21:09 tty30
crw--w----   1 root   tty       4,  31 2009-05-19 21:09 tty31
crw--w----   1 root   tty       4,  32 2009-05-19 21:09 tty32
crw--w----   1 root   tty       4,  33 2009-05-19 21:09 tty33
crw--w----   1 root   tty       4,  34 2009-05-19 21:09 tty34
crw--w----   1 root   tty       4,  35 2009-05-19 21:09 tty35
crw--w----   1 root   tty       4,  36 2009-05-19 21:09 tty36
crw--w----   1 root   tty       4,  37 2009-05-19 21:09 tty37
crw--w----   1 root   tty       4,  38 2009-05-19 21:09 tty38
crw--w----   1 root   tty       4,  39 2009-05-19 21:09 tty39
crw-------   1 root   root      4,   4 2009-05-19 21:10 tty4
crw--w----   1 root   tty       4,  40 2009-05-19 21:09 tty40
crw--w----   1 root   tty       4,  41 2009-05-19 21:09 tty41
crw--w----   1 root   tty       4,  42 2009-05-19 21:09 tty42
crw--w----   1 root   tty       4,  43 2009-05-19 21:09 tty43
crw--w----   1 root   tty       4,  44 2009-05-19 21:09 tty44
crw--w----   1 root   tty       4,  45 2009-05-19 21:09 tty45
crw--w----   1 root   tty       4,  46 2009-05-19 21:09 tty46
crw--w----   1 root   tty       4,  47 2009-05-19 21:09 tty47
crw--w----   1 root   tty       4,  48 2009-05-19 21:09 tty48
crw--w----   1 root   tty       4,  49 2009-05-19 21:09 tty49
crw-------   1 root   root      4,   5 2009-05-19 21:10 tty5
crw--w----   1 root   tty       4,  50 2009-05-19 21:09 tty50
crw--w----   1 root   tty       4,  51 2009-05-19 21:09 tty51
crw--w----   1 root   tty       4,  52 2009-05-19 21:09 tty52
crw--w----   1 root   tty       4,  53 2009-05-19 21:09 tty53
crw--w----   1 root   tty       4,  54 2009-05-19 21:09 tty54
crw--w----   1 root   tty       4,  55 2009-05-19 21:09 tty55
crw--w----   1 root   tty       4,  56 2009-05-19 21:09 tty56
crw--w----   1 root   tty       4,  57 2009-05-19 21:09 tty57
crw--w----   1 root   tty       4,  58 2009-05-19 21:09 tty58
crw--w----   1 root   tty       4,  59 2009-05-19 21:09 tty59
crw-------   1 root   root      4,   6 2009-05-19 21:10 tty6
crw--w----   1 root   tty       4,  60 2009-05-19 21:09 tty60
crw--w----   1 root   tty       4,  61 2009-05-19 21:09 tty61
crw--w----   1 root   tty       4,  62 2009-05-19 21:09 tty62
crw--w----   1 root   tty       4,  63 2009-05-19 21:09 tty63
crw--w----   1 root   root      4,   7 2009-05-19 21:09 tty7
crw--w----   1 root   tty       4,   8 2009-05-19 21:10 tty8
crw--w----   1 root   tty       4,   9 2009-05-19 21:09 tty9
crw-rw----   1 root   dialout   4,  64 2009-05-19 21:09 ttyS0
crw-rw----   1 root   dialout   4,  65 2009-05-19 21:09 ttyS1
crw-rw----   1 root   dialout   4,  66 2009-05-19 21:09 ttyS2
crw-rw----   1 root   dialout   4,  67 2009-05-19 21:09 ttyS3
drwxr-xr-x   6 root   root         140 2009-05-19 21:12 .udev
crw-rw-rw-   1 root   root      1,   9 2009-05-19 21:10 urandom
crw-rw----   1 root   root    252,   1 2009-05-19 21:09 usbdev1.1_ep00
crw-rw----   1 root   root    252,   0 2009-05-19 21:09 usbdev1.1_ep81
crw-rw----   1 root   root    252,   3 2009-05-19 21:09 usbdev2.1_ep00
crw-rw----   1 root   root    252,   2 2009-05-19 21:09 usbdev2.1_ep81
crw-rw----   1 root   root    252,   5 2009-05-19 21:09 usbdev3.1_ep00
crw-rw----   1 root   root    252,   4 2009-05-19 21:09 usbdev3.1_ep81
crw-rw----   1 root   root    252,   7 2009-05-19 21:09 usbdev4.1_ep00
crw-rw----   1 root   root    252,   6 2009-05-19 21:09 usbdev4.1_ep81
crw-rw----   1 root   root    252,  11 2009-05-19 21:09 usbdev4.2_ep00
crw-rw----   1 root   root    252,  10 2009-05-19 21:09 usbdev4.2_ep81
crw-rw----   1 root   root    252,  13 2009-05-19 21:09 usbdev4.3_ep00
crw-rw----   1 root   root    252,  12 2009-05-19 21:09 usbdev4.3_ep81
crw-rw----   1 root   root    252,  16 2009-05-19 21:09 usbdev4.4_ep00
crw-rw----   1 root   root    252,  14 2009-05-19 21:09 usbdev4.4_ep81
crw-rw----   1 root   root    252,  15 2009-05-19 21:09 usbdev4.4_ep82
crw-rw----   1 root   root    252,   9 2009-05-19 21:09 usbdev5.1_ep00
crw-rw----   1 root   root    252,   8 2009-05-19 21:09 usbdev5.1_ep81
crw-rw----   1 root   root    253,   0 2009-05-19 21:09 usbmon0
crw-rw----   1 root   root    253,   1 2009-05-19 21:09 usbmon1
crw-rw----   1 root   root    253,   2 2009-05-19 21:09 usbmon2
crw-rw----   1 root   root    253,   3 2009-05-19 21:09 usbmon3
crw-rw----   1 root   root    253,   4 2009-05-19 21:09 usbmon4
crw-rw----   1 root   root    253,   5 2009-05-19 21:09 usbmon5
crw-rw----   1 root   tty       7,   0 2009-05-19 21:09 vcs
crw-rw----   1 root   tty       7,   1 2009-05-19 21:10 vcs1
crw-rw----   1 root   tty       7,   2 2009-05-19 21:10 vcs2
crw-rw----   1 root   tty       7,   3 2009-05-19 21:10 vcs3
crw-rw----   1 root   tty       7,   4 2009-05-19 21:10 vcs4
crw-rw----   1 root   tty       7,   5 2009-05-19 21:10 vcs5
crw-rw----   1 root   tty       7,   6 2009-05-19 21:10 vcs6
crw-rw----   1 root   tty       7,   7 2009-05-19 21:10 vcs7
crw-rw----   1 root   tty       7,   8 2009-05-19 21:09 vcs8
crw-rw----   1 root   tty       7, 128 2009-05-19 21:09 vcsa
crw-rw----   1 root   tty       7, 129 2009-05-19 21:10 vcsa1
crw-rw----   1 root   tty       7, 130 2009-05-19 21:10 vcsa2
crw-rw----   1 root   tty       7, 131 2009-05-19 21:10 vcsa3
crw-rw----   1 root   tty       7, 132 2009-05-19 21:10 vcsa4
crw-rw----   1 root   tty       7, 133 2009-05-19 21:10 vcsa5
crw-rw----   1 root   tty       7, 134 2009-05-19 21:10 vcsa6
crw-rw----   1 root   tty       7, 135 2009-05-19 21:10 vcsa7
crw-rw----   1 root   tty       7, 136 2009-05-19 21:09 vcsa8
crw-rw----   1 root   root    171,  16 2009-05-19 21:09 video1394-0
prw-r-----   1 syslog adm            0 2009-05-19 21:10 xconsole
crw-rw-rw-   1 root   root      1,   5 2009-05-19 21:09 zero
```

> **cyberdork33 said:**
> 
There is a source package for vloopback in the karmic Koala repos when you get to that point:
[http://packages.ubuntu.com/karmic/vloopback-source](http://packages.ubuntu.com/karmic/vloopback-source)
More info, but really sounds the same:
[http://thegrid.wordpress.com/how-to-use-isight-in-linux/](http://thegrid.wordpress.com/how-to-use-isight-in-linux/)
Thx for the links, I might get there if coriander starts up... ;-)

Do you have any further advices how I could bring up my iSight?

---

### Post by cyberdork33 on 2009-05-19
there appears to be a problem with your installation of libdc1394. Try removing all the packages, and just install corriander. I think it pulls libdc1394 itself...

remove:
```
sudo apt-get remove dvgrab libavc1394-0 libdc1394-13 libdc1394-13-dev libfreebob0 libiec61883-0 libiec61883-dev libraw1394-8 libraw1394-dev coriander
```

I used aptitude and just installed coriander:
```
sudo aptitude coriander
```

It got everything else it needed and seemed to run OK (as far as it can for me) with:
```
sudo coriander
```

---

### Post by produnis on 2009-05-20
ok, I did how you told me...

when I did the apt-get remove, the following additional packages have been removed:
```
  amarok audacity cheese coriander dvgrab ffmpeg gnome-media googleearth
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good kdebase-runtime
  kdebase-runtime-bin-kde4 kdemultimedia-kio-plugins khelpcenter4 libavc1394-0
  libavdevice52 libdc1394-22 libffado0 libfreebob0 libiec61883-0
  libiec61883-dev libjack0 libkcddb4 libmarble4 libqt4-webkit libraw1394-8
  libraw1394-dev marble merkaartor mplayer phonon phonon-backend-gstreamer
  rhythmbox totem totem-gstreamer totem-mozilla totem-plugins ubuntu-desktop
```

Well, unfortunately, after re-installing coriander, a sudo coriander gives me the same error as usual:
```
libdc1394 error: Failed to initialize libdc1394
Segmentation fault
```I really don't know what to do...
It seams, as if Ubuntu doesn't like a Firewire-iSight at all
;-(

---

### Post by cyberdork33 on 2009-05-20
Are you using KDE? there were a  lot of kde packages removed...

I don't know why you would get a segfault. Maybe if you can check 'dmesg | tail' after you try to run coriander.

---

### Post by produnis on 2009-05-21
I am using GNOME...

There seems to be a problem with the Firewire host:
```
produnis@UbuntuPro:/etc/modprobe.d$ dmesg |grep 1394
[    3.099019] ohci1394 0000:10:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.149757] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f2e04000-f2e047ff]  Max Packet=[4096]  IR/IT contexts=[4/8]
[    4.567364] ieee1394: config ROM CRC error
[    4.567411] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000a27000406c399]
[    4.567510] ieee1394: Host added: ID:BUS[0-02:1023]  GUID[0019e3fffe8ebf56]
[    8.872307] video1394: Installed video1394 module
[    8.939386] ieee1394: raw1394: /dev/raw1394 device initialized
[    9.483024] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
[ 1862.165728] coriander[5177]: segfault at 0 ip b794c3b7 sp bfef7ec0 error 4 in libdc1394.so.22.1.2[b793f000+2c000]
```

I am wondering about line 3: 
**ieee1394: config ROM CRC error**

Do you have any idea for that?

---

### Post by cyberdork33 on 2009-05-21
> **produnis said:**
> I am wondering about line 3: 
**ieee1394: config ROM CRC error**

Do you have any idea for that?
no, that seems to be fine. (see [http://lkml.indiana.edu/hypermail/linux/kernel/0805.0/0860.html](http://lkml.indiana.edu/hypermail/linux/kernel/0805.0/0860.html) There is actually a patch to get it stop writing it to the log because the message is so common and really harmless.)

The real culprit seems to be libdc1394. 
```
[ 1862.165728] coriander[5177]: segfault at 0 ip b794c3b7 sp bfef7ec0 error 4 in libdc1394.so.22.1.2[b793f000+2c000]
```

---

### Post by produnis on 2009-05-21
hmmmm... and there is no real solution for that problem, is there?

should I report that as a bug to ubuntu?

---

### Post by cyberdork33 on 2009-05-21
> **produnis said:**
> hmmmm... and there is no real solution for that problem, is there?

should I report that as a bug to ubuntu?
not that I know of. You can try filing a bug.

---

### Post by produnis on 2009-05-21
Thanks a lot that you tried to help me!!!!
I just reported my problem as [bug379088]("https://bugs.launchpad.net/ubuntu/+source/libdc1394-22/+bug/379088")...

Hopefully, there will be something like a patch...

---

### Post by lorent_tt on 2009-06-04
Hi
don't worry you're not alone
I'm in the same situation with my Quad Opteron
Still looking for a clue...

Did you test Kino ?
Because on my computer Kino is working great !!!
Why ???
May be the issue is not really from 1394 bus ???

---

