---
title: "sound card problem"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by venkatrav on 2007-12-04
Yet another sound card problem.......

I have this HP laptop.....

my card  details::::

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

though ubuntu recognizes the hardware....I am not able to hear any sounds.....
when I checked the ALSA for the support I did not find the NVidia chip that uses Conexant chip for sound. 

let me know a solution for this problem........when I do a modprobe I do not find any module related to conexant.......

My modprobe o/p

/lib/modules/2.6.22-14-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.22-14-generic/updates/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.22-14-generic/updates/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd-page-alloc.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/instr/snd-ainstr-simple.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/instr/snd-ainstr-fm.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-instr.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd-hwdep.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd-pcm.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd-rtctimer.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd-rawmidi.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/snd-timer.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.22-14-generic/updates/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.22-14-generic/updates/sound/soc/snd-soc-core.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/snd-mts64.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/snd-dummy.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.22-14-generic/updates/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-als300.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-es1968.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-ad1889.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-rme96.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-maestro3.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-ens1371.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-cmipci.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-ens1370.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-via82xx.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-als4000.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-atiixp.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-cs4281.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-azt3328.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-es1938.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-fm801.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-rme32.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-bt87x.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.22-14-generic/updates/sound/synth/snd-util-mem.ko
/lib/modules/2.6.22-14-generic/updates/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/snd-i2c.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.22-14-generic/updates/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.22-14-generic/updates/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.22-14-generic/updates/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.22-14-generic/updates/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.22-14-generic/updates/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.22-14-generic/updates/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko

help is needed..........

thanks
Rav

---

### Post by linuxwizard on 2007-12-04
Look over see if your computer is in this bug report.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

