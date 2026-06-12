---
title: "have tried to compile alsa sound drivers need help"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by audiofeen on 2008-02-19
i have tried to compile sound drivers for this X20Ia laptop
it has a realtek card and use's alc861 drivers i have downloaded from manufactures site and no joy, i have been to the alsa site and no joy at first it seem like it should work but no sound was coming out of speakers but now the sound card is not configured at all i can still identify it in terminal.
i have tried many sound troubleshooting topics for hda intel cards and even some not here is some of the topics i have tried.

[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29)

[https://help.ubuntu.com/community/So...ht=%28sound%29](https://help.ubuntu.com/community/So...ht=%28sound%29)

[https://help.ubuntu.com/community/?a...esearch=Titles](https://help.ubuntu.com/community/?a...esearch=Titles)

[http://ubuntuforums.org/showthread.php?t=257304](http://ubuntuforums.org/showthread.php?t=257304)

[http://ubuntuforums.org/showthread.php?t=501422](http://ubuntuforums.org/showthread.php?t=501422)


this is the latest i have tried from the alsa site the link to the doc i used, i didn't need to follow all of it because i have already downloaded the latest drivers for other help docs
some help please. :confused: 

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
agneta@agneta-laptop:~/src/alsa/alsa-driver-1.0.16$ make
make dep
make[1]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/ioctl32'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/ioctl32'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq'
make[4]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss'
make[4]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/acore'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/i2c'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/i2c/l3'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/i2c/l3'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/i2c/other'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/i2c/other'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/i2c'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/mpu401'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/mpu401'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/opl3'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/opl3'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/opl4'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/opl4'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/pcsp'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/pcsp'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/vx'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers/vx'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/drivers'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/ad1816a'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/ad1816a'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/ad1848'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/ad1848'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/cs423x'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/cs423x'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/es1688'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/es1688'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/gus'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/gus'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/msnd'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/msnd'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/opti9xx'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/opti9xx'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/sb'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/sb'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/wavefront'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa/wavefront'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/isa'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/synth'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/synth/emux'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/synth/emux'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/synth'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ac97'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ac97'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ali5451'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ali5451'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/asihpi'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/asihpi'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/au88x0'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/au88x0'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ca0106'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ca0106'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/cs46xx'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/cs46xx'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/cs5535audio'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/cs5535audio'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/echoaudio'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/echoaudio'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/emu10k1'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/emu10k1'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ice1712'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ice1712'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/korg1212'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/korg1212'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/mixart'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/mixart'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/nm256'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/nm256'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/oxygen'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/oxygen'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/pcxhr'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/pcxhr'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/pdplus'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/pdplus'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/riptide'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/riptide'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/rme9652'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/rme9652'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/trident'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/trident'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/vx222'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/vx222'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ymfpci'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci/ymfpci'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pci'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/codecs'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/codecs'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/core'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/core'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/fabrics'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/fabrics'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/soundbus'
make[4]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa/soundbus'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/aoa'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/at91'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/at91'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/codecs'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/codecs'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/fsl'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/fsl'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/pxa'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/pxa'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/s3c24xx'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/s3c24xx'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/sh'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc/sh'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/soc'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/usb'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/usb/caiaq'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/usb/caiaq'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/usb/usx2y'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/usb/usx2y'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/usb'
make[2]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pcmcia'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pcmcia/vx'
make[3]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pcmcia/vx'
make[2]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16/pcmcia'
make[1]: Leaving directory `/home/agneta/src/alsa/alsa-driver-1.0.16'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/agneta/src/alsa/alsa-driver-1.0.16  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/hwdep.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/memory_wrapper.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/memalloc.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/sgbuf.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/pcm.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/pcm_native.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/pcm_lib.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/pcm_timer.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/pcm_misc.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/pcm_memory.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/rtctimer.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/timer.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/wrappers.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/misc_driver.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/sound.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/init.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/memory.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/info.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/control.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/misc.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/device.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/isadma.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/sound_oss.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/info_oss.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/snd.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/snd-hwdep.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/snd-timer.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/snd-rtctimer.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/snd-pcm.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/snd-page-alloc.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/mixer_oss.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/pcm_oss.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/pcm_plugin.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/io.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/copy.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/linear.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/mulaw.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/route.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/rate.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/snd-mixer-oss.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/oss/snd-pcm-oss.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_device.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_midi_event.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_lock.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_clientmgr.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_memory.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_queue.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_fifo.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_prioq.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_timer.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_system.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_ports.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/seq_info.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/snd-seq.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/snd-seq-device.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/snd-seq-midi-event.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_init.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_timer.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_ioctl.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_event.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_rw.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_synth.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_midi.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_readq.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/seq_oss_writeq.o
  LD [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/acore/seq/oss/snd-seq-oss.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/hda_intel.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/hda_codec.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/vmaster.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/hda_proc.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/hda_hwdep.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/hda_generic.o
  CC [M]  /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/patch_realtek.o
In file included from /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:26,
                 from /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/patch_realtek.c:3:
/home/agneta/src/alsa/alsa-driver-1.0.16/include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/patch_realtek.c:3:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc_resume’:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:1941: warning: implicit declaration of function ‘snd_hda_resume_ctls’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:1943: warning: implicit declaration of function ‘snd_hda_resume_spdif_out’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:1945: warning: implicit declaration of function ‘snd_hda_resume_spdif_in’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc882_mux_enum_put’:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:4590: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc883_mux_enum_put’:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:5295: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc262_fujitsu_master_sw_put’:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:6610: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:6611: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc861vd_mux_enum_put’:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:8369: error: ‘struct hda_codec’ has no member named ‘in_resume’
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc662_mux_enum_put’:
/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:9138: error: ‘struct hda_codec’ has no member named ‘in_resume’
make[4]: *** [/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda/patch_realtek.o] Error 1
make[3]: *** [/home/agneta/src/alsa/alsa-driver-1.0.16/pci/hda] Error 2
make[2]: *** [/home/agneta/src/alsa/alsa-driver-1.0.16/pci] Error 2
make[1]: *** [_module_/home/agneta/src/alsa/alsa-driver-1.0.16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
agneta@agneta-laptop:~/src/alsa/alsa-driver-1.0.16$ make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/agneta/src/alsa/alsa-driver-1.0.16/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
rm: cannot remove `/usr/include/sound/hdsp.h': Permission denied
rm: cannot remove `/usr/include/sound/vx_core.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
rm: cannot remove `/usr/include/sound/asequencer.h': Permission denied
rm: cannot remove `/usr/include/sound/hwdep.h': Permission denied
rm: cannot remove `/usr/include/sound/emux_legacy.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm_params.h': Permission denied
rm: cannot remove `/usr/include/sound/util_mem.h': Permission denied
rm: cannot remove `/usr/include/sound/asoundef.h': Permission denied
rm: cannot remove `/usr/include/sound/mixer_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
rm: cannot remove `/usr/include/sound/soc.h': Permission denied
rm: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000.h': Permission denied
rm: cannot remove `/usr/include/sound/rawmidi.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_midi_event.h': Permission denied
rm: cannot remove `/usr/include/sound/driver.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm-indirect.h': Permission denied
rm: cannot remove `/usr/include/sound/core.h': Permission denied
rm: cannot remove `/usr/include/sound/cs8403.h': Permission denied
rm: cannot remove `/usr/include/sound/asound.h': Permission denied
rm: cannot remove `/usr/include/sound/opl3.h': Permission denied
rm: cannot remove `/usr/include/sound/gus.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4117.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/info.h': Permission denied
rm: cannot remove `/usr/include/sound/hdspm.h': Permission denied
rm: cannot remove `/usr/include/sound/emux_synth.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
rm: cannot remove `/usr/include/sound/cs8427.h': Permission denied
rm: cannot remove `/usr/include/sound/wavefront.h': Permission denied
rm: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_midi_emul.h': Permission denied
rm: cannot remove `/usr/include/sound/soundfont.h': Permission denied
rm: cannot remove `/usr/include/sound/minors.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4114.h': Permission denied
rm: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
rm: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_virmidi.h': Permission denied
rm: cannot remove `/usr/include/sound/mpu401.h': Permission denied
rm: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
rm: cannot remove `/usr/include/sound/i2c.h': Permission denied
rm: cannot remove `/usr/include/sound/control.h': Permission denied
rm: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied
rm: cannot remove `/usr/include/sound/opl4.h': Permission denied
rm: cannot remove `/usr/include/sound/es1688.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_oss_legacy.h': Permission denied
rm: cannot remove `/usr/include/sound/sb.h': Permission denied
rm: cannot remove `/usr/include/sound/cs4231.h': Permission denied
rm: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
rm: cannot remove `/usr/include/sound/soc-dapm.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1_synth.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4xxx-adda.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1848.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_kernel.h': Permission denied
rm: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_device.h': Permission denied
rm: cannot remove `/usr/include/sound/pt2258.h': Permission denied
rm: cannot remove `/usr/include/sound/version.h': Permission denied
rm: cannot remove `/usr/include/sound/uda1341.h': Permission denied
rm: cannot remove `/usr/include/sound/trident.h': Permission denied
rm: cannot remove `/usr/include/sound/snd_wavefront.h': Permission denied
rm: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/tlv.h': Permission denied
rm: cannot remove `/usr/include/sound/ak4531_codec.h': Permission denied
rm: cannot remove `/usr/include/sound/initval.h': Permission denied
rm: cannot remove `/usr/include/sound/hda_hwdep.h': Permission denied
rm: cannot remove `/usr/include/sound/memalloc.h': Permission denied
rm: cannot remove `/usr/include/sound/seq_oss.h': Permission denied
rm: cannot remove `/usr/include/sound/timer.h': Permission denied
rm: cannot remove `/usr/include/sound/cs4231-regs.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
rm: cannot remove `/usr/include/sound/pcm.h': Permission denied
install: cannot change owner and/or group of `/usr/include/sound': Operation not permitted
install: cannot remove `/usr/include/sound/ac97_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ad1816a.h': Permission denied
install: cannot remove `/usr/include/sound/ad1848.h': Permission denied
install: cannot remove `/usr/include/sound/ak4114.h': Permission denied
install: cannot remove `/usr/include/sound/ak4117.h': Permission denied
install: cannot remove `/usr/include/sound/ak4531_codec.h': Permission denied
install: cannot remove `/usr/include/sound/ak4xxx-adda.h': Permission denied
install: cannot remove `/usr/include/sound/asequencer.h': Permission denied
install: cannot remove `/usr/include/sound/asound.h': Permission denied
install: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
install: cannot remove `/usr/include/sound/asoundef.h': Permission denied
install: cannot remove `/usr/include/sound/control.h': Permission denied
install: cannot remove `/usr/include/sound/core.h': Permission denied
install: cannot remove `/usr/include/sound/cs4231-regs.h': Permission denied
install: cannot remove `/usr/include/sound/cs4231.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
install: cannot remove `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
install: cannot remove `/usr/include/sound/cs8403.h': Permission denied
install: cannot remove `/usr/include/sound/cs8427.h': Permission denied
install: cannot remove `/usr/include/sound/driver.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1_synth.h': Permission denied
install: cannot remove `/usr/include/sound/emu8000.h': Permission denied
install: cannot remove `/usr/include/sound/emu8000_reg.h': Permission denied
install: cannot remove `/usr/include/sound/emux_legacy.h': Permission denied
install: cannot remove `/usr/include/sound/emux_synth.h': Permission denied
install: cannot remove `/usr/include/sound/es1688.h': Permission denied
install: cannot remove `/usr/include/sound/gus.h': Permission denied
install: cannot remove `/usr/include/sound/hda_hwdep.h': Permission denied
install: cannot remove `/usr/include/sound/hdsp.h': Permission denied
install: cannot remove `/usr/include/sound/hdspm.h': Permission denied
install: cannot remove `/usr/include/sound/hwdep.h': Permission denied
install: cannot remove `/usr/include/sound/i2c.h': Permission denied
install: cannot remove `/usr/include/sound/info.h': Permission denied
install: cannot remove `/usr/include/sound/initval.h': Permission denied
install: cannot remove `/usr/include/sound/memalloc.h': Permission denied
install: cannot remove `/usr/include/sound/minors.h': Permission denied
install: cannot remove `/usr/include/sound/mixer_oss.h': Permission denied
install: cannot remove `/usr/include/sound/mpu401.h': Permission denied
install: cannot remove `/usr/include/sound/opl3.h': Permission denied
install: cannot remove `/usr/include/sound/opl4.h': Permission denied
install: cannot remove `/usr/include/sound/pcm-indirect.h': Permission denied
install: cannot remove `/usr/include/sound/pcm.h': Permission denied
install: cannot remove `/usr/include/sound/pcm_oss.h': Permission denied
install: cannot remove `/usr/include/sound/pcm_params.h': Permission denied
install: cannot remove `/usr/include/sound/pt2258.h': Permission denied
install: cannot remove `/usr/include/sound/rawmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sb.h': Permission denied
install: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
install: cannot remove `/usr/include/sound/seq_device.h': Permission denied
install: cannot remove `/usr/include/sound/seq_kernel.h': Permission denied
install: cannot remove `/usr/include/sound/seq_midi_emul.h': Permission denied
install: cannot remove `/usr/include/sound/seq_midi_event.h': Permission denied
install: cannot remove `/usr/include/sound/seq_oss.h': Permission denied
install: cannot remove `/usr/include/sound/seq_oss_legacy.h': Permission denied
install: cannot remove `/usr/include/sound/seq_virmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
install: cannot remove `/usr/include/sound/snd_wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/soc-dapm.h': Permission denied
install: cannot remove `/usr/include/sound/soc.h': Permission denied
install: cannot remove `/usr/include/sound/soundfont.h': Permission denied
install: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
install: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied
install: cannot remove `/usr/include/sound/tea6330t.h': Permission denied
install: cannot remove `/usr/include/sound/timer.h': Permission denied
install: cannot remove `/usr/include/sound/tlv.h': Permission denied
install: cannot remove `/usr/include/sound/trident.h': Permission denied
install: cannot remove `/usr/include/sound/uda1341.h': Permission denied
install: cannot remove `/usr/include/sound/util_mem.h': Permission denied
install: cannot remove `/usr/include/sound/version.h': Permission denied
install: cannot remove `/usr/include/sound/vx_core.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1
agneta@agneta-laptop:~/src/alsa/alsa-driver-1.0.16$

---

### Post by Hobo Joe on 2008-02-19
The 'Permission denied' error is because you didn't use 'sudo' in your commands.

However, there may be another way to fix your problem. Paste the output of this command:
```

sudo asoundconf list

```

---

### Post by audiofeen on 2008-02-20
hey joe 

i'll give it a go as soon as i am back home.

---

### Post by audiofeen on 2008-02-20
> **Hobo Joe said:**
> The 'Permission denied' error is because you didn't use 'sudo' in your commands.

However, there may be another way to fix your problem. Paste the output of this command:
```

sudo asoundconf list

```

hey joe i tried this and got this message how do i get around it?

agneta@agneta-laptop:~$ sudo asoundconf list
[sudo] password for agneta:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

---

### Post by spiderbatdad on 2008-02-20
You do not need sudo to run asoundconf list

What Hobo Joe wants you to do is, use the result of that command in the terminal like this: ```
asoundconf set-default-card result
``` where "result" is the actual result you received from the previous command. Then reboot. This will likely not work in your case, but worth a try.

You may only need to install the linux-backports to get you card working. Or if you have to rebuild alsa, I suggest the appropriate section of this guide. [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by audiofeen on 2008-02-20
i cant get past the first it keeps giving me the same warning and that i have to be a privileged superuser.

i just rebooted and am getting a message when i click on the sound applet
"no volume control gstreamer plugins and o/r devices found"

and it has an icon like it's muted

---

### Post by spiderbatdad on 2008-02-20
log yourself into the terminal as root with sudo su

---

### Post by spiderbatdad on 2008-02-20
thats probably gstreamer0.10-gnomevfs look for it in synaptic.

---

### Post by audiofeen on 2008-02-20
ok logged in as sudo su and still same message
agneta@agneta-laptop:~$ sudo su
[sudo] password for agneta:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@agneta-laptop:/home/agneta# sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

root@agneta-laptop:/home/agneta# asoundconf set-default-card result
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

---

### Post by audiofeen on 2008-02-20
should i update or remove gstreamer?

---

### Post by monte48lowes on 2008-02-20
I did notice that when you attempted to compile alsa, that some errors resulted. Additionally, to properly install when compliling from source:

```
sudo make install
```

There are some errors there though. Don't know for what.

Mike

---

### Post by spiderbatdad on 2008-02-20
ok I'm mixed up as to which method you are trying to use. I thought you were trying to compile alsa-sound-base, and it looked like you were missing the gnome-vfs. Then you logged in as root to run asoundconf. You should not need to be root for that.

---

