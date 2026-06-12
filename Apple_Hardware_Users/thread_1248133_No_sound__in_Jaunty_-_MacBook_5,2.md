---
title: "No sound  in Jaunty - MacBook 5,2"
date: 2009-08-23
forum: Apple Hardware Users
---

### Post by ubuntuubuntu on 2009-08-23
Hello,
I have just installed Ubuntu Jaunty in a MacBook 5,2, and the sound is not working at all. Could someone help me out?

Thanks in advance!

---

### Post by anti_gravity99 on 2009-08-24
I'm trying to figure out how to install jaunty on my macbook 5,2. Any info on you did to get it working would be appreciated. Here is a link that I've been looking at that might help. [https://help.ubuntu.com/community/MacBook5-1/Jaunty](https://help.ubuntu.com/community/MacBook5-1/Jaunty)

---

### Post by amd-64 on 2009-08-25
Give this a try 

[http://ubuntuforums.org/showthread.php?p=7834207#post7834207](http://ubuntuforums.org/showthread.php?p=7834207#post7834207)

---

### Post by ubuntuubuntu on 2009-08-26
It didn't work... I don't have the option HDA NVIDIA (PulseAudio Mixer). The ones I get are: 

Capture: HDA NVidia - ALC889A Analog (PulseAudio Mixer)
Capture: Monitor of HDA NVidia - ALC889A Analog (PulseAudio Mixer)
HDA NVidia (Alsa mixer)
PlaybackL HDA NVidia - ALC889A Analog (PulseAudio Mixer)

I've tried these options, but they didn't work.

My output of find /lib/modules/ -name snd* is:

> 
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-page-alloc.ko


My output of uname -a is:

> 
Linux a-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux


Does this give you any clue? Thank you so much!

---

### Post by bmb6agb on 2009-08-27
I have the same problem with kernel 2.6.28.15 on a 17" Macbook Pro 5.2. I had the sound working fine with kernel 2.6.28.14. The Update Manager updated me to 2.6.28.15-generic and phut - no sound. I recompiled the alsa driver with the headers for the new kernel, but still no sound. So I currently I use the grub menu to boot with 2.6.28.14-generic and the sound works fine. I guess there must be a bug in the kernel of 2.6.28.15-generic.

---

### Post by CityTop on 2009-08-27
I have the same problem - mine is a MacBook Pro 5,3 15". No sound at all in Jaunty.

I am very new to Ubuntu.

bmb6agb, could you please give some details about the solution that works for you? How do you set up boot with the older kernel? Any other consequences for system performance?

I followed this guide:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid#Sound](https://help.ubuntu.com/community/MacBook5-1/Intrepid#Sound)

to no avail... do I need to uninstall any of this stuff?

Thanks!
Peter

---

### Post by bmb6agb on 2009-08-27
If you still have the previous kernel, it should appear in the list of kernels that appear in the grub menu when your machine boots. Simply select the 2.6.28.14-generic kernel and let your machine continue booting. 

I can't guarantee that this will work for you - remember that my sound was working, and therefore correctly configured, before the kernel upgrade.

---

### Post by amd-64 on 2009-08-27
CityTop

In the 5,3 MacBook Pro, you have a Cirrus chip which requires updating the alsa drivers as in post #3 above.

---

### Post by CityTop on 2009-08-27
Thanks very much! Do I need to uninstall the update I made previously?

---

### Post by CityTop on 2009-08-27
Sorry, the changes I had made were these:

[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound)

applying to MacBook Pro 5,2 (which is presumably different from the MBP 5,3 I have)

amd-64 - I tried to update the Alsa drivers as per your post. It did not work. First, I could not select HDA NVidia at all in Sound Preferences. I then **undid** this part of the above thread:

```

Now make an upmix from 20 to 51. Edit asound.conf

gksudo gedit /etc/asound.conf

Add following PCMs

pcm.out {
        type route
        slave.pcm "hw:0,0";
        slave.channels 6
        ttable {
                0.0 1
                1.1 1
                2.2 1
                3.3 1
                4.4 1
                0.5 0.5
                1.5 0.5
        }
}

pcm.!default {
    type pulse
}

Change PulseAudio configuration to use 6 channels and 'out' upmix instead of hw:0,0 
```

After this, I could get the HDA NVidia. But when I try to select HDA NVidia Cirrus Analog in the Sound Preferences, I get an error from playback test:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

This is the output from point 5 in your post:

peter@Laptop01Lin:~$ find /lib/modules/ -name snd*
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-11-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-11-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-11-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-11-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
peter@Laptop01Lin:~$ uname -a
Linux Laptop01Lin 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
peter@Laptop01Lin:~$ 

Any idea where to go from here?

Thanks!

---

### Post by amd-64 on 2009-08-27
make sure you are using the 2.6.28-15 kernel and see if the module gets loaded. For me

```

lsmod | grep cirrus
snd                    75144  15 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          97280  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hda_codec_cirrus    22272  1 

```

My /etc/asound.conf file is exactly what you posted above.

---

