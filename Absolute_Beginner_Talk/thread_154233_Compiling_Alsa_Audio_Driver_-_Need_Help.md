---
title: "Compiling Alsa Audio Driver - Need Help"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-02
Hello all!

I am trying to get some sound out of Ubuntu.
I am trying to compile the alsa source & I get the following errors:

root@ubuntu:/home/elena/Desktop/alsa-driver-1.0.4# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/elena/Desktop/alsa-driver-1.0.4
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
root@ubuntu:/home/elena/Desktop/alsa-driver-1.0.4#

I have already installed the following packages:

1. linux-headers-2.6.19-9
2. linux-kernel-headers

My Ubuntu PC is a 64bit, but I have installed the Regular Ubuntu 5.10 Breezy.
The above package #1 has three versions, I do NOT know if I have installed the correct one...

Any ideas how to make this work????

Thanks.

---

### Post by gordong11 on 2006-04-02
Try this...but use whatever driver your sound card is... check alsamixer. This may help

[http://www.ubuntuforums.org/showthread.php?t=153823](http://www.ubuntuforums.org/showthread.php?t=153823)



there like 50+ drivers to choose from

---

### Post by WickedImp on 2006-04-02
Hmmm... wondering what happened to your ubuntu. Normally just selecting 'linux-686' and 'linux-headers-686' should do the trick (or whatever u will need from linux-* and linux-headers-*). This will maybe help you out with the configure script. But anyway: why compiling your own alsa kernel modules and stuff??? ubuntu kernels are packed with everything you need. Run the following command, please:
```
find /lib/modules/`uname -r` -iname "*snd*"
```
This should give you a lot of modules which are all ALSA. Also the packages alsa-base and alsa-utils should be installed. And the following command should tell you what drivers are loaded for your hardware:
```
lsmod | grep snd
```
normally you will get soundcore, snd_pcm_oss, etc...! means some hardware was found by your ubuntu and is ready to rock. By the way, what is your sound hardware?
Maybe you can provide more information?

---

### Post by dvarsam on 2006-04-02
Hello!

Thank you for your replies!

My _Mobo_ is an **ASUS P5LD2-VM**, if that helps.

I will try to look at the thread you suggested...

I will post back...

---

### Post by dvarsam on 2006-04-02
Dear "WickedImp".

I did what you suggested & got the following:

root@ubuntu:/# find /lib/modules/`uname -r` -iname "*snd*"

> 
/lib/modules/2.6.12-9-386/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-simple.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-fm.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-gf1.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-iw.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-instr.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/snd-rtctimer.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.12-9-386/kernel/sound/core/snd.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.12-9-386/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1816a/snd-ad1816a-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gus-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.12-9-386/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/vx/snd-vx-cs.ko
/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/vx/snd-vxp440.ko
/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.12-9-386/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.12-9-386/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.12-9-386/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.12-9-386/kernel/sound/usb/usx2y/snd-usb-usx2y.ko


root@ubuntu:/# lsmod |grep snd

> 
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm


root@ubuntu:/#

I have no clue what to do next, so I would appreciate if you could help...

Thanks.

---

### Post by WickedImp on 2006-04-03
Ok and the system found snd_hda_intel and snd_hda_codec. I think your mobo got intel onboard chips. Means if you got no sound something else is wrong. Cause your sound card drivers are already loaded!

Please try alsamixer - it will give you a console mixer which is telling you exactly which hardware is used (on top left of the screen). And you will see all controls you can use (select with left and right cursor key - up and down will make it louder or more quit). I bed you will see a 'MM' on the bottom of the main controls (master, pcm, or whatever). MM means muted on both channels (left/right - controlled with q and e in the selected control).

Unmute your controls by pressing M.

Ok - all this is just a guess of what maybe happened to you. But you definetly not need to compile the drivers on your own (forgive me for my grammar this morning - not my main language pack :P )!

What else could it be? What desktop system aree you using? GNome or KDE?

---

### Post by dvarsam on 2006-04-03
Hello & Thanks for your Reply!!!

[QUOTE=WickedImp]
Ok and the system found snd_hda_intel and snd_hda_codec.
I think your mobo got intel onboard chips.
Means if you got no sound something else is wrong.
Cause your sound card drivers are already loaded!
Please try "alsamixer" - it will give you a console mixer which is telling you exactly which hardware is used (on top left of the screen).
[/QUOTE]

I tried typing on the Terminal window: "**alsamixer**".

And this is what I found:

Card: HDA Intel
Chip: Realtec ALC882
View: [Playback] Capture All
Item: Headphone

1. Headphon is: 00
2. PCM is: 100<>100
3. Front is: 0<>0         (MM)
4. Front Mi is: 74<>74
5. Surround is: 0<>0    (MM)
6. Center is: 0            (MM)
7. LFE is: 0                (MM)
8. Side is: 0<>0          (MM)

It looks like that #3 (what I want) were Muted...

So, I used the "up" keyboard arrow, to increase it...

All the others, I left them "AS IS" (or untouched).

However, I wonder if I should increase the "LFE"... what is that anyway?

To get out of the "**alsamixer**", I pressed on the keyboard, the "**ESC**" key twice...

I even went back in to check, that my changes were saved... YES they were!

I used the program "Soundjuicer" to try to play a CD-Rom.

I got NO sound playing...
(I wonder if I got deff in the meantime & I don't know about it yet? lol):) 

At the same time, I have got installed the "w32codecs"...

But... I have NO sound man....

I even went (while playing the CD) & experimented plugging the Speaker wire on EVERY motherboard's "plug" - just in CASE I had plugged it in the wrong whole...

Again, NO sound...

> 
And you will see all controls you can use (select with left and right cursor key - up and down will make it louder or more quit).
I bed you will see a 'MM' on the bottom of the main controls (master, pcm, or whatever).
MM means muted on both channels (left/right - controlled with q and e in the selected control).
Unmute your controls by pressing M.

Ok - all this is just a guess of what maybe happened to you.


Even though you were VERY right & seemed that EVERYTHING were muted...

Still, I get NO sound....

And I checked the program "Soundjuicer" (CD player), it is NOT muted...

Nor are the Speakers on my Monitor...

> What else could it be?
What desktop system aree you using?
GNome or KDE?

I am using Ubuntu v5.10 Breezy Desktop Gnome (not KDE) Regular Install on a 64bit chipset & Motherboard: ASUS P5LD2-VM.

Thanks for your help!!!

You are awesome!!!

I did not know about the "alsamixer" command, to use on the Terminal...

However, I am still stuck... Any ideas how would I go now about it?

Thanks.

---

### Post by WickedImp on 2006-04-03
ha, ha, ha! yes i still got some ideas. maybe you just didn't write it: but did you unmute your front channel? it was muted and you didn't write anything about pressing the M-key :) there should not be any MM in the output channels at all (for the starting)

hmmm... one quick check is:
```
ls /dev > /dev/dsp
```

should give you a modem like sound :P if you hear anything then oss emulation via your alsa drivers is working.

and then! if you still get no sound anywhere! yeah then I do not know what's going on at your machine :P

---

### Post by dvarsam on 2006-04-03
[QUOTE=WickedImp]...maybe you just didn't write it:...
... but did you unmute your front channel?...
...it was muted and you didn't write anything about pressing the M-key :)
There should not be any MM in the output channels at all (for the starting)...
[/QUOTE]

YES !!!
YES !!!

I just forgot to type the "**M**" key on the keyboard...

YOU ARE AWESOME !!!!!!

IT WORKS !!!

Hip Hip: Hurray!!!!!!

I just selected the:

> 3. Front is: 0<>0 (MM)

Then, typed the "M" key on my keyboard:

& the above "#3" is changed to:

> 3. Front is: 0<>0 (00)

Thanks!!!

I also got some squeeky noise, when I typed:

> ls /dev > /dev/dsp

YOU ARE AMAZING, MAN !!!

GREAT WORK!!!

P.S.2> Without you, I would STILL be looking a "needle in stack of hay" man...

P.S.2> All I have to do now is find how to make the LAN work & I should be set... Zillion Thanks!!!

---

### Post by amitroy5 on 2006-04-04
For some reason, I still do not get any sound. I went though this thread and tried to unmute everything. But I am not sure why nothing is playing. Can anyone help? Thanks!

---

### Post by dvarsam on 2006-04-05
[QUOTE=amitroy5]For some reason, I still do not get any sound. I went though this thread and tried to unmute everything. But I am not sure why nothing is playing. Can anyone help? Thanks![/QUOTE]

If you need help man, you have to give us either a screenshot of your Desktop or write down what I wrote, like:

1. Headphon is: 00
2. PCM is: 100<>100
3. Front is: 0<>0 (MM)
4. Front Mi is: 74<>74
5. Surround is: 0<>0 (MM)
6. Center is: 0 (MM)
7. LFE is: 0 (MM)
8. Side is: 0<>0 (MM)

Help us, to help you!

---

### Post by WickedImp on 2006-04-07
Hi there. Sorry that my answer took so long (busy, busy, busy). I think you already found snd_* in /lib/modules and that the grep command gave you some loaded sound modules. I would like to know what the command exactly gives you. Also try the following please:
```
cat /proc/asound/cards
```
thi sshould give you all available cards found by the loaded drivers/modules. would be nice if you could post your outputs (grep and cat) here. also more information about your system would be nice: kde or gnome? 'uname -r'? ubuntu release?

Cya

---

### Post by dvarsam on 2006-04-08
Dear WickedImp,

                      my problem is Solved!!!

Thanks!

P.S.> Another user, called "armitroy" posted here & you are confusing "my output" with his problem "case"...
He has not posted yet his "output", so I think you are trying to solve _his_ problem with _my_ "output"...

His case is different...

So, "armitroy", maybe you need to "post" your output like I did & maybe "wickedimp" or "me" could help you...

---

