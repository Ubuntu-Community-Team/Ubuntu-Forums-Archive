---
title: "Yes another sounds thread (unibody MBP 15&quot;)"
date: 2009-08-23
forum: Apple Hardware Users
---

### Post by Ravernomina on 2009-08-23
Hello and yes this is another sound thread. I got a MBP Unibody a 15" 2009 model. Now I seem to be having trouble getting sound to work. i tried both forum threads about this, None sadly do not work. I tried the ALSA update and, trying the Unstable ALSA patch. I do have the cirrus Logic sound card. For the Sound patch, On my first attempt it said i had HDA Intel card. The second Try say Null output (pulse Audio) and i could tell that was Bad :P. Now i do not know if i'm doing something wrong or i missing something, would some 1 be kind enough to give me a little assistance Because I DEARLY MISS UBUNTU!!!!! So any one who thinks they know the Fix please post and tell me :).

Thank you and please help. Linux + &#63743; for life <3


P.S. Here are the threads.

Alsa update: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Alsa Patch: [http://ubuntuforums.org/showthread.php?t=1188849](http://ubuntuforums.org/showthread.php?t=1188849) (On page 10, Post # 98)

and if ur wondering the 5,4-,5,5-,5,2. Have the same sound cards.

Please assist I miss my Ubuntu :)..... With sound :o

---

### Post by Ravernomina on 2009-08-23
Bump

---

### Post by amd-64 on 2009-08-23
I had a null output situation when I deleted alsa from /lib/modules. I was stumped for a while but I found out that i should not delete all the soundcore modules from the kernel. 

Follow the alsa update guide carefully and make sure you reinstall the linux-image with all the soundcore stuff. Then post your lsmod output.

---

### Post by Ravernomina on 2009-08-23
lsmod Output:

```
Module                  Size  Used by
michael_mic            10496  4 
arc4                    9856  4 
ecb                    10752  4 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
hid_apple              14336  0 
usbhid                 42336  0 
applesmc               29616  0 
led_class              12036  1 applesmc
input_polldev          11912  1 applesmc
coretemp               13952  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel          34120  3 
snd_hda_codec          83584  1 snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14240  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7233756  38 
agpgart                42696  1 nvidia
snd                    66852  18 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
ieee80211_crypt_tkip    16896  0 
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm
uvcvideo               63368  0 
joydev                 18496  0 
usb_storage            99648  0 
shpchp                 40212  0 
btusb                  19608  2 
pcspkr                 10496  0 
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
appleir                12416  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
mbp_nvidia_bl          12176  0 
bcm5974                16512  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

This was it after the ALSA update i did not do the patch yet

---

### Post by Ravernomina on 2009-08-23
bump

---

### Post by amd-64 on 2009-08-23
Here are my sound modules below. I don't see snd_hda_codec_cirrus in your modules and you have all the oss modules which i did not need. I think the patch was included in the latest updates. 

```

snd                    75144  12 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          97280  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hda_codec_cirrus   22272  1 
snd_hda_intel          41184  2 
snd_hwdep              16392  1 snd_hda_codec
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm
snd_pcm                98952  2 snd_hda_intel,snd_hda_codec
snd_seq                66912  0 
snd_seq_device         16532  1 snd_seq
snd_timer              33168  2 snd_pcm,snd_seq

```


Here is what I suggest based on what I read and what worked for me. 


Follow the alsa patch link that you posted [http://ubuntuforums.org/showpost.php?p=7627817&postcount=98](http://ubuntuforums.org/showpost.php?p=7627817&postcount=98) but in the second step make sure you reinstall the latest kernel not the one in the thread. 

Download the latest *stable* snapshot [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

Make sure you are running the kernel you reinstalled, reboot if necessary. 
Compile alsa as posted --without-oss should get rid of the oss modules you currently have.

Hope this helps

---

### Post by Ravernomina on 2009-08-23
still did not work i got no sound and it still says ALSA NVIDIA

lsmod:

```
edward@Edward-macintosh:~$ lsmod
Module                  Size  Used by
michael_mic            10496  4 
arc4                    9856  4 
ecb                    10752  4 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
hid_apple              14336  0 
usbhid                 42336  0 
applesmc               29616  0 
led_class              12036  1 applesmc
input_polldev          11912  1 applesmc
coretemp               13952  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
nvidia               7233756  38 
agpgart                42696  1 nvidia
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63368  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211_crypt_tkip    16896  0 

```

---

### Post by Ravernomina on 2009-08-23
Bump

---

### Post by Ravernomina on 2009-08-23
bump

---

### Post by gradinaruvasile on 2009-08-23
Launch alsamixer in a terminal. Does it work? If it does, post a screenshot.

---

### Post by Ravernomina on 2009-08-23
it works :)


[IMG]http://i206.photobucket.com/albums/bb85/Raverdacada/Screenshot-edwardEdward-macintosh.png[/IMG]

---

### Post by gradinaruvasile on 2009-08-23
Also you might need to reinstall the sound packages...

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And the alsa 1.0.20 packages here:

[http://philip.magicalforest.se/dists/jaunty/all/](http://philip.magicalforest.se/dists/jaunty/all/)

(you need the i386 ones if using standard ubuntu, the amd64 ones if using 64 bit ubuntu)

---

### Post by gradinaruvasile on 2009-08-23
Ok. In a terminal:

```
speaker-test -t wav -c2
```

Do u hear anything?

---

### Post by Ravernomina on 2009-08-23
i do not hear anything

---

### Post by gradinaruvasile on 2009-08-23
> **Ravernomina said:**
> i do not hear anything

What is the output in the terminal? Post it please.

---

### Post by Ravernomina on 2009-08-23
```
speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
 1 - Front Right
Time per period = 2.861762
 0 - Front Left
 1 - Front Right
Time per period = 3.007950
 0 - Front Left
 1 - Front Right
Time per period = 3.007873
 0 - Front Left
 1 - Front Right
Time per period = 3.008075
 0 - Front Left
 1 - Front Right
Time per period = 3.007921
 0 - Front Left
 1 - Front Right
Time per period = 3.008057
 0 - Front Left
 1 - Front Right
Time per period = 3.008271
 0 - Front Left
 1 - Front Right
Time per period = 3.028279
 0 - Front Left
 1 - Front Right
Time per period = 3.008052
 0 - Front Left
 1 - Front Right
Time per period = 3.008290
 0 - Front Left
 1 - Front Right
Time per period = 3.007810
 0 - Front Left
 1 - Front Right
Time per period = 3.008075
 0 - Front Left
 1 - Front Right
Time per period = 3.007867
 0 - Front Left
 1 - Front Right
Time per period = 3.007522
 0 - Front Left
 1 - Front Right
Time per period = 3.009170
 0 - Front Left
 1 - Front Right
Time per period = 3.049537
 0 - Front Left
 1 - Front Right
Time per period = 2.986569
 0 - Front Left
 1 - Front Right
Time per period = 3.008076
 0 - Front Left
 1 - Front Right
Time per period = 3.007969
 0 - Front Left
 1 - Front Right
Time per period = 3.007919
 0 - Front Left
 1 - Front Right
Time per period = 3.008070
 0 - Front Left
 1 - Front Right
Time per period = 3.007822
 0 - Front Left
 1 - Front Right
Time per period = 3.008270
 0 - Front Left
 1 - Front Right
Time per period = 3.028616
 0 - Front Left
 1 - Front Right
Time per period = 3.029341
 0 - Front Left
 1 - Front Right
Time per period = 2.986761
 0 - Front Left
 1 - Front Right
Time per period = 3.007979
 0 - Front Left
 1 - Front Right
Time per period = 3.007967
 0 - Front Left
 1 - Front Right

```

---

### Post by gradinaruvasile on 2009-08-23
Well it seems to be working all right... Is there an external volume control or something?
Also, do u use pulseaudio as output? Is so, n a terminal launch

```
gnome-sound-properties
```

and set everything to alsa.

---

### Post by Ravernomina on 2009-08-23
all set on Alsa... If u look back at my other threads u will see whats going on. Some 1 said im missing the cirrus codec and i cannot seem to get it :(

---

### Post by Ravernomina on 2009-08-23
bump

---

### Post by gradinaruvasile on 2009-08-23
That sucks... 
Anyway, lasunch alsamixer again and then press tab twice. U should get a longer list (maybe). Enlarge the terminal to fit everything and post ascreenshot.

OTOH if its really a driver incompatibility issue u might try the 9.10 alpha ubuntu. That one has newer kernels and updated drivers.

---

### Post by gradinaruvasile on 2009-08-23
Found something...

[https://help.ubuntu.com/community/MacBook5-1/Intrepid#Sound](https://help.ubuntu.com/community/MacBook5-1/Intrepid#Sound)

look for the sound section...

Maybe helps.

---

### Post by Ravernomina on 2009-08-23
ill give karmic a try....

---

### Post by gradinaruvasile on 2009-08-23
First try the above link...

---

### Post by Ravernomina on 2009-08-23
i did no anvil :(

---

### Post by gradinaruvasile on 2009-08-23
Can u make that screenshot?

And other have the same problem as u...
A bug is filed here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337947](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337947)

---

### Post by Ravernomina on 2009-08-23
i have the Mac Book Pro 5,4 :P

---

### Post by Ravernomina on 2009-08-23
Karmic koala failed on me PLease help :(

---

### Post by gradinaruvasile on 2009-08-23
> **Ravernomina said:**
> Karmic koala failed on me PLease help :(

Meaning?
It starts in text mode? Or doesnt work at all?

---

### Post by Ravernomina on 2009-08-23
starts in text mode

i try ```
StartX
``` but it says it cannot connect to x.org sever

---

### Post by gradinaruvasile on 2009-08-23
Do u have a nvidia video card?

---

### Post by Ravernomina on 2009-08-23
yep GeForce 9400m

---

### Post by gradinaruvasile on 2009-08-23
I had a similar problem. I have an IGP nvidia 8200 and ubuntu 9.10 could not start x. It is a driver issue (opensource nv) it seems. Anyway i solved the problem by installing the proprietary drivers in live mode.
    I used a usb stick (2GB), made 2 partitions on it (800 MB and 1.2 GB), installed the live cd contents on the first (800MB) partition with usb disk creator, copied the driver d/l ed from nvidias site to the second partition, started the comp with it, got into text mode (x crashed), logged in with "ubuntu" user (the default live cd user), no password. Mounted the second partition (/dev/sdb2 in my case), ran the nvidia installer with sudo. Then started gdm with 

sudo service gdm start

And it was working... compiz and all.

PS. I used 2 partitions on the stick because in live cd  mode i couldn t mount the usbs boot partition...

---

### Post by Ravernomina on 2009-08-23
sadly i have no USB :l look like im screwed of course this only happens to me ;l

---

### Post by gradinaruvasile on 2009-08-23
U can do it with a live cd too. The only thing is that u will have to mount the partition that contains the driver.

---

### Post by Ravernomina on 2009-08-23
i have no USB Drive and i have 1 CD drive im on a laptop.

---

### Post by gradinaruvasile on 2009-08-23
> **Ravernomina said:**
> i have no USB Drive and i have 1 CD drive im on a laptop.

First d/l the latest driver from nvidias site. Remember its location on ur hard drive.
Boot your computer from the live cd. log in with "ubuntu"
Mount the partition where u have the driver downloaded. This is done with the mount command (first make a folder where to mount ur partition). The example uses /dev/sda1 (it probably is ur partition if u have only ubuntu installed):

```
sudo mkdir /media/drive
sudo mount /dev/sda1 /media/drive

cd /media/drive/nvidiadriverfolder 
chmod +x NVdrivername 
```       (here u can autocomplete, write NV and then TAB)
```
./NVdrivername
```

Select accept the agreement, do not download , and then accept to configure ur xorg.conf 

when done

```
sudo service gdm start
```

log in with "ubuntu" and no password (press enter)

---

### Post by Ravernomina on 2009-08-23
Bump

---

### Post by Ravernomina on 2009-08-23
Any ! Have any more solutions please post ffs!!!!!!

---

### Post by amd-64 on 2009-08-23
Unless your sound card is defective or somehow different, the alsa update solution should work. If you wish to diagnose this.

1. MAke sure your system is updated.     sudo apt-get dist-upgrade
2. Download the latest alsa stable snapshot 
```
 
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar xf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install

```
3. Restart your system
4. Go to system > preferences > sound
 and make sure your Device (last option) is playback: HDA NVIDIA (PulseAudio Mixer) 
5. If sound is not working post the output of 
```
find /lib/modules/ -name snd*
uname -a

```

---

### Post by Ravernomina on 2009-08-23
> **amd-64 said:**
> unless your sound card is defective or somehow different, the alsa update solution should work. If you wish to diagnose this.

1. Make sure your system is updated.     Sudo apt-get dist-upgrade
2. Download the latest alsa stable snapshot 
```
 
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar xf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install

```
3. Restart your system
4. Go to system > preferences > sound
 and make sure your device (last option) is playback: Hda nvidia (pulseaudio mixer) 
5. If sound is not working post the output of 
```
find /lib/modules/ -name snd*
uname -a

```
[size="7"][b][i][u]
omfg u are an angle that fixed it i got sound using alsa u are flippen amazing!!!! God bless u!!!! Are u jesus!?!?!?!?!? Omfg u are amazing!!!! Omfg u are amazing!!!!!! U are yes!!!!!! U are an epic win!!!! Thank you sooooooooooooooooooooooooooooooooooooooooooooooooooooo much!!!!!!![/u][/i][/b][/size]

---

### Post by amd-64 on 2009-08-23
Wow. Glad that it worked. Now you may enjoy the best set of speakers on a laptop.

---

### Post by Ravernomina on 2009-08-24
i will thank you :)

---

### Post by a1234 on 2009-09-21
This is my out put after running the instructionspoted without any error message. This is on my presitent not regular ubuntu. Appreciate if you can look at it. i re nano same xorg.conf everytime from last prompt.
Thanks in advance
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# find /lib/modules/ -name snd*
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.28-11-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-15-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-15-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-15-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-15-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko

---

### Post by a1234 on 2009-09-21
the other part

root@ubuntu:~# uname -a
Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
root@ubuntu:~#
Thanks again

---

### Post by viktara on 2009-09-22
I still only have sound from my headphone socket after following the instructions for the alsa snapshot approach.

Any help greatly appreciated!

---

### Post by besweeet on 2009-10-29
> **amd-64 said:**
> Unless your sound card is defective or somehow different, the alsa update solution should work. If you wish to diagnose this.

1. MAke sure your system is updated.     sudo apt-get dist-upgrade
2. Download the latest alsa stable snapshot 
```
 
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar xf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install

```3. Restart your system
4. Go to system > preferences > sound
 and make sure your Device (last option) is playback: HDA NVIDIA (PulseAudio Mixer) 
5. If sound is not working post the output of 
```
find /lib/modules/ -name snd*
uname -a

```


Installed Ubuntu 9.10 x64 a little while ago. Everything is working but audio (and the internal mic). I did what you posted in steps 1-4, but I don't get an output at all. Here's what I get from step 5:
```
brian@bj-ubuntu:~$ find /lib/modules/ -name snd*
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.31-14-generic/kernel/sound/acore/snd-page-alloc.ko
```

```
brian@bj-ubuntu:~$ uname -a
Linux bj-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

If I run gnome-alsamixer, it'll bring up the GNOME-ALSAMIXER window, but nothing will be in it. If I then go to Edit>Sound Card Properties, it'll crash, and the Terminal window that I opened gnome-alsamixer with gives me this:
```
(gnome-alsamixer:2373): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```

Any ideas? This is the last thing I need to get working on my MacBookPro5,3.

---

### Post by blucini on 2010-01-04
Same problem for a Macbook Pro 5,3 (ubuntu 9.10 64 bits). Upgrade to 2.6.31-16 did not make any change. Is there anybody who got sound working on this particular Macbook Pro model?

---

### Post by viktara on 2010-01-04
Hi,

After upgrading to Karmic and installing the alsa snapshot, the sound started working as per the alsa snapshot instructions.

I am using 32 bit however - so maybe that's the catch?

Regards


Vik

---

### Post by besweeet on 2010-01-04
I followed this guide for my 5,3 MBP and everything worked just fine (9.10 x64): [https://help.ubuntu.com/community/MacBookPro5-3/Karmic](https://help.ubuntu.com/community/MacBookPro5-3/Karmic)

---

