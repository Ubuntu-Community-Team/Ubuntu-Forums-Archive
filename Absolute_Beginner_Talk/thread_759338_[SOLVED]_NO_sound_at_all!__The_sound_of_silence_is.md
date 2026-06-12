---
title: "[SOLVED] NO sound at all!  The sound of silence is deafening."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by bcasanov on 2008-04-19
I have Hardy Heron with the latest update and it's getting to the point where I can't stand it anymore.  I have gone many days without sound since I upgraded, and I thought this would be fixed by the time Hardy reached Release Candidate status.  I have a Dell 1420N that perhaps a lot of people have, and everything works, except the sound.  

The result of lspci | grep -i audio is:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

I went to Preferences>>Sound, and tested every device choice on there, and sadly, still no sound.

---

### Post by warbread on 2008-04-19
I don't see why it wouldn't be working.  Nothing outputs?  Volume manager doesn't work?  What exactly is wrong?

Try taking any largish file (a few hundred megs should do it) and typing into terminal:

```
cat /name/of/file > /dev/dsp
```

---

### Post by bcasanov on 2008-04-19
Hi warbread, thanks for responding!

Wow, I actually got some sound output!!!!!

It was a garbled sound that sounded like the sound of static combined with a broken motor.  If I go to a console and input alsamixer, I get all the controls and everything.  Surround was muted, so I unmuted it. 

 Now, I went to Preferences>>Sound, and now, thank goodness, I heard the wonderful sound of a beep as I clicked on Test.  I have Sound Events>>Sound playback, Music and Movies>>Sound playback, Audio Conferencing>>Sound playback all set to Autodetect.  

Okay, now I am going to Firefox and I have opened a Youtube video.  And tadaa!  I finally hear sound!!!  

Wow, I don't know what the command you gave me does, but incredibly, it makes me hear sound now!  

I am still cautiously optimistic as I will restart the computer and see if the settings are still there and if I can continue to hear sound.  For now, I really want to thank you for getting me this far!

---

### Post by bcasanov on 2008-04-19
Unfortunately, when I restarted, I no longer hear sound!  How can I solve this?

---

### Post by bcasanov on 2008-04-19
I also tested the command again, using the same file, and now, unfortunately, I hear no sound.  I tried the same command with another file, and I still do not hear any sound.

---

### Post by bcasanov on 2008-04-19
Just so that you know and in case it is relevant, I have the kernel version 2.6.24-16-generic, which I found out through the command uname -r.

---

### Post by waggingwabbit on 2008-04-19
well for me turning off IEC in alsamixer and setting the card i want as my default card solved my problems. it was like asoundconf set-default-card audigy2 for me. but im on gutsy though

---

### Post by bcasanov on 2008-04-19
How do you turn off IEC in alsamixer?  I found no mention of it when I checked through alsamixer in the terminal.

---

### Post by warbread on 2008-04-20
The command I gave you just dumps the output of a file into the sound card.  I was just ruling out hardware fault.

[This bug report]("https://bugs.launchpad.net/ubuntu/+bug/122560") seems to have the answer. From Michael Richards:

```

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a

```

Try that.

---

### Post by bcasanov on 2008-04-20
warbread, thank you very much for helping me!  I went through each of the commands you gave me, and there were some errors in the output, and when I restarted after I input the last command, I still could not hear sound.  What do you think could be the problem?

Would you like me to go back and redo each of the commands and post the output of each here?

Regards, 

Brenda

---

### Post by warbread on 2008-04-20
Yes, please.

---

### Post by bcasanov on 2008-04-20
Here are the outputs of each command:

sudo apt-get install alsa-source ```
Reading package lists... Done
Building dependency tree
Reading state information... Done
alsa-source is already the newest version.
The following packages were automatically installed and are no longer required:
  libflashsupport
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
cd && mkdir alsa-patched && cd alsa-patched ```
mkdir: cannot create directory `alsa-patched': File exists
```
tar -jxvf /usr/src/alsa-driver.tar.bz2 (I want to note that because the output is so large, I think it was somewhat truncated in the console.)```
modules/alsa-driver/alsa-kernel/aoa/
modules/alsa-driver/alsa-kernel/aoa/aoa.h
modules/alsa-driver/alsa-kernel/aoa/aoa-gpio.h
modules/alsa-driver/alsa-kernel/aoa/Makefile
modules/alsa-driver/alsa-kernel/aoa/core/
modules/alsa-driver/alsa-kernel/aoa/core/snd-aoa-core.c
modules/alsa-driver/alsa-kernel/aoa/core/snd-aoa-gpio-pmf.c
modules/alsa-driver/alsa-kernel/aoa/core/Makefile
modules/alsa-driver/alsa-kernel/aoa/core/snd-aoa-alsa.h
modules/alsa-driver/alsa-kernel/aoa/core/snd-aoa-gpio-feature.c
modules/alsa-driver/alsa-kernel/aoa/core/snd-aoa-alsa.c
modules/alsa-driver/alsa-kernel/aoa/Kconfig
modules/alsa-driver/alsa-kernel/aoa/codecs/
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-toonie.c
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-onyx.c
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-tas-basstreble.h
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-tas.h
modules/alsa-driver/alsa-kernel/aoa/codecs/Makefile
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-tas-gain-table.h
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-tas.c
modules/alsa-driver/alsa-kernel/aoa/codecs/Kconfig
modules/alsa-driver/alsa-kernel/aoa/codecs/snd-aoa-codec-onyx.h
modules/alsa-driver/alsa-kernel/aoa/fabrics/
modules/alsa-driver/alsa-kernel/aoa/fabrics/Makefile
modules/alsa-driver/alsa-kernel/aoa/fabrics/snd-aoa-fabric-layout.c
modules/alsa-driver/alsa-kernel/aoa/fabrics/Kconfig
modules/alsa-driver/alsa-kernel/aoa/soundbus/
modules/alsa-driver/alsa-kernel/aoa/soundbus/sysfs.c
modules/alsa-driver/alsa-kernel/aoa/soundbus/Makefile
modules/alsa-driver/alsa-kernel/aoa/soundbus/soundbus.h
modules/alsa-driver/alsa-kernel/aoa/soundbus/Kconfig
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-core.c
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-pcm.c
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-interface.h
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/Makefile
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-control.c
modules/alsa-driver/alsa-kernel/aoa/soundbus/i2sbus/i2sbus.h
modules/alsa-driver/alsa-kernel/aoa/soundbus/core.c
modules/alsa-driver/alsa-kernel/kernel/
modules/alsa-driver/alsa-kernel/kernel/CREDITS
modules/alsa-driver/alsa-kernel/kernel/arch/
modules/alsa-driver/alsa-kernel/kernel/arch/arm/
modules/alsa-driver/alsa-kernel/kernel/arch/arm/mach-pxa/
modules/alsa-driver/alsa-kernel/kernel/arch/arm/mach-pxa/mainstone.c
modules/alsa-driver/alsa-kernel/kernel/drivers/
modules/alsa-driver/alsa-kernel/kernel/drivers/usb/
modules/alsa-driver/alsa-kernel/kernel/drivers/usb/gadget/
modules/alsa-driver/alsa-kernel/kernel/drivers/usb/gadget/gmidi.c
modules/alsa-driver/alsa-kernel/kernel/drivers/media/
modules/alsa-driver/alsa-kernel/kernel/drivers/media/video/
modules/alsa-driver/alsa-kernel/kernel/drivers/media/video/saa7134/
modules/alsa-driver/alsa-kernel/kernel/drivers/media/video/saa7134/saa7134.h
modules/alsa-driver/alsa-kernel/kernel/drivers/media/video/saa7134/saa7134-alsa.c
modules/alsa-driver/alsa-kernel/kernel/drivers/media/video/cx88/
modules/alsa-driver/alsa-kernel/kernel/drivers/media/video/cx88/cx88-alsa.c
modules/alsa-driver/alsa-kernel/kernel/drivers/input/
modules/alsa-driver/alsa-kernel/kernel/drivers/input/touchscreen/
modules/alsa-driver/alsa-kernel/kernel/drivers/input/touchscreen/ucb1400_ts.c
modules/alsa-driver/alsa-kernel/kernel/include/
modules/alsa-driver/alsa-kernel/kernel/include/asm-arm/
modules/alsa-driver/alsa-kernel/kernel/include/asm-arm/arch-omap/
modules/alsa-driver/alsa-kernel/kernel/include/asm-arm/arch-omap/omap-alsa.h
modules/alsa-driver/alsa-kernel/kernel/include/asm-arm/arch-omap/eac.h
modules/alsa-driver/alsa-kernel/kernel/include/asm-arm/arch-pxa/
modules/alsa-driver/alsa-kernel/kernel/include/asm-arm/arch-pxa/audio.h
modules/alsa-driver/alsa-kernel/kernel/include/linux/
modules/alsa-driver/alsa-kernel/kernel/include/linux/spi/
modules/alsa-driver/alsa-kernel/kernel/include/linux/spi/at73c213.h
modules/alsa-driver/alsa-kernel/kernel/include/linux/i2c-id.h
modules/alsa-driver/alsa-kernel/kernel/include/linux/pci_ids.h
modules/alsa-driver/alsa-kernel/kernel/MAINTAINERS
modules/alsa-driver/alsa-kernel/parisc/
modules/alsa-driver/alsa-kernel/parisc/harmony.c
modules/alsa-driver/alsa-kernel/parisc/harmony.h
modules/alsa-driver/alsa-kernel/parisc/Makefile
modules/alsa-driver/alsa-kernel/parisc/Kconfig
modules/alsa-driver/alsa-kernel/pci/
modules/alsa-driver/alsa-kernel/pci/ens1370.c
modules/alsa-driver/alsa-kernel/pci/trident/
modules/alsa-driver/alsa-kernel/pci/trident/trident_memory.c
modules/alsa-driver/alsa-kernel/pci/trident/Makefile
modules/alsa-driver/alsa-kernel/pci/trident/trident_main.c
modules/alsa-driver/alsa-kernel/pci/trident/trident.c
modules/alsa-driver/alsa-kernel/pci/oxygen/
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen.c
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen_regs.h
modules/alsa-driver/alsa-kernel/pci/oxygen/Makefile
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen.h
modules/alsa-driver/alsa-kernel/pci/oxygen/cm9780.h
modules/alsa-driver/alsa-kernel/pci/oxygen/virtuoso.c
modules/alsa-driver/alsa-kernel/pci/oxygen/hifier.c
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen_lib.c
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen_io.c
modules/alsa-driver/alsa-kernel/pci/oxygen/ak4396.h
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen_pcm.c
modules/alsa-driver/alsa-kernel/pci/oxygen/oxygen_mixer.c
modules/alsa-driver/alsa-kernel/pci/atiixp.c
modules/alsa-driver/alsa-kernel/pci/ca0106/
modules/alsa-driver/alsa-kernel/pci/ca0106/ca0106_mixer.c
modules/alsa-driver/alsa-kernel/pci/ca0106/Makefile
modules/alsa-driver/alsa-kernel/pci/ca0106/ca0106_main.c
modules/alsa-driver/alsa-kernel/pci/ca0106/ca0106_proc.c
modules/alsa-driver/alsa-kernel/pci/ca0106/ca0106.h
modules/alsa-driver/alsa-kernel/pci/ca0106/ca_midi.h
modules/alsa-driver/alsa-kernel/pci/ca0106/ca_midi.c
modules/alsa-driver/alsa-kernel/pci/es1968.c
modules/alsa-driver/alsa-kernel/pci/rme32.c
modules/alsa-driver/alsa-kernel/pci/als300.c
modules/alsa-driver/alsa-kernel/pci/intel8x0m.c
modules/alsa-driver/alsa-kernel/pci/ad1889.h
modules/alsa-driver/alsa-kernel/pci/riptide/
modules/alsa-driver/alsa-kernel/pci/riptide/riptide.c
modules/alsa-driver/alsa-kernel/pci/riptide/Makefile
modules/alsa-driver/alsa-kernel/pci/via82xx_modem.c
modules/alsa-driver/alsa-kernel/pci/azt3328.c
modules/alsa-driver/alsa-kernel/pci/cs5530.c
modules/alsa-driver/alsa-kernel/pci/intel8x0.c
modules/alsa-driver/alsa-kernel/pci/au88x0/
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_wt.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_xtalk.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au8820.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_mixer.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_a3ddata.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au8830.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_mpu401.c
modules/alsa-driver/alsa-kernel/pci/au88x0/Makefile
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_xtalk.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au8810.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_core.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au8810.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_a3d.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_synth.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_pcm.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_eq.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_eqdata.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_eq.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_a3d.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au8820.h
modules/alsa-driver/alsa-kernel/pci/au88x0/au88x0_game.c
modules/alsa-driver/alsa-kernel/pci/au88x0/au8830.c
modules/alsa-driver/alsa-kernel/pci/ice1712/
modules/alsa-driver/alsa-kernel/pci/ice1712/delta.c
modules/alsa-driver/alsa-kernel/pci/ice1712/hoontech.h
modules/alsa-driver/alsa-kernel/pci/ice1712/juli.c
modules/alsa-driver/alsa-kernel/pci/ice1712/ews.c
modules/alsa-driver/alsa-kernel/pci/ice1712/revo.c
modules/alsa-driver/alsa-kernel/pci/ice1712/hoontech.c
modules/alsa-driver/alsa-kernel/pci/ice1712/prodigy_hifi.c
modules/alsa-driver/alsa-kernel/pci/ice1712/amp.h
modules/alsa-driver/alsa-kernel/pci/ice1712/se.h
modules/alsa-driver/alsa-kernel/pci/ice1712/se.c
modules/alsa-driver/alsa-kernel/pci/ice1712/ice1724.c
modules/alsa-driver/alsa-kernel/pci/ice1712/juli.h
modules/alsa-driver/alsa-kernel/pci/ice1712/Makefile
modules/alsa-driver/alsa-kernel/pci/ice1712/revo.h
modules/alsa-driver/alsa-kernel/pci/ice1712/prodigy192.h
modules/alsa-driver/alsa-kernel/pci/ice1712/vt1720_mobo.c
modules/alsa-driver/alsa-kernel/pci/ice1712/aureon.h
modules/alsa-driver/alsa-kernel/pci/ice1712/prodigy192.c
modules/alsa-driver/alsa-kernel/pci/ice1712/phase.h
modules/alsa-driver/alsa-kernel/pci/ice1712/pontis.h
modules/alsa-driver/alsa-kernel/pci/ice1712/aureon.c
modules/alsa-driver/alsa-kernel/pci/ice1712/stac946x.h
modules/alsa-driver/alsa-kernel/pci/ice1712/ice1712.c
modules/alsa-driver/alsa-kernel/pci/ice1712/wtm.c
modules/alsa-driver/alsa-kernel/pci/ice1712/prodigy_hifi.h
modules/alsa-driver/alsa-kernel/pci/ice1712/ews.h
modules/alsa-driver/alsa-kernel/pci/ice1712/ice1712.h
modules/alsa-driver/alsa-kernel/pci/ice1712/ak4xxx.c
modules/alsa-driver/alsa-kernel/pci/ice1712/envy24ht.h
modules/alsa-driver/alsa-kernel/pci/ice1712/amp.c
modules/alsa-driver/alsa-kernel/pci/ice1712/delta.h
modules/alsa-driver/alsa-kernel/pci/ice1712/wtm.h
modules/alsa-driver/alsa-kernel/pci/ice1712/vt1720_mobo.h
modules/alsa-driver/alsa-kernel/pci/ice1712/phase.c
modules/alsa-driver/alsa-kernel/pci/ice1712/pontis.c
modules/alsa-driver/alsa-kernel/pci/es1938.c
modules/alsa-driver/alsa-kernel/pci/ad1889.c
modules/alsa-driver/alsa-kernel/pci/maestro3.c
modules/alsa-driver/alsa-kernel/pci/ymfpci/
modules/alsa-driver/alsa-kernel/pci/ymfpci/ymfpci_main.c
modules/alsa-driver/alsa-kernel/pci/ymfpci/Makefile
modules/alsa-driver/alsa-kernel/pci/ymfpci/ymfpci.c
modules/alsa-driver/alsa-kernel/pci/ymfpci/ymfpci_image.h
modules/alsa-driver/alsa-kernel/pci/Makefile
modules/alsa-driver/alsa-kernel/pci/nm256/
modules/alsa-driver/alsa-kernel/pci/nm256/Makefile
modules/alsa-driver/alsa-kernel/pci/nm256/nm256_coef.c
modules/alsa-driver/alsa-kernel/pci/nm256/nm256.c
modules/alsa-driver/alsa-kernel/pci/ali5451/
modules/alsa-driver/alsa-kernel/pci/ali5451/ali5451.c
modules/alsa-driver/alsa-kernel/pci/ali5451/Makefile
modules/alsa-driver/alsa-kernel/pci/cs46xx/
modules/alsa-driver/alsa-kernel/pci/cs46xx/dsp_spos.c
modules/alsa-driver/alsa-kernel/pci/cs46xx/dsp_spos.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/dsp_spos_scb_lib.c
modules/alsa-driver/alsa-kernel/pci/cs46xx/Makefile
modules/alsa-driver/alsa-kernel/pci/cs46xx/cs46xx_lib.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/cwcdma.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/cwcbinhack.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/cwcasync.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/cwcsnoop.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/cwc4630.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/imgs/cwcdma.asp
modules/alsa-driver/alsa-kernel/pci/cs46xx/cs46xx.c
modules/alsa-driver/alsa-kernel/pci/cs46xx/cs46xx_image.h
modules/alsa-driver/alsa-kernel/pci/cs46xx/cs46xx_lib.c
modules/alsa-driver/alsa-kernel/pci/cs4281.c
modules/alsa-driver/alsa-kernel/pci/vx222/
modules/alsa-driver/alsa-kernel/pci/vx222/vx222.h
modules/alsa-driver/alsa-kernel/pci/vx222/vx222_ops.c
modules/alsa-driver/alsa-kernel/pci/vx222/Makefile
modules/alsa-driver/alsa-kernel/pci/vx222/vx222.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1_main.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1_callback.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1_synth.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1_patch.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/irq.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/io.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emumixer.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/memory.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emufx.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/Makefile
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emuproc.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1x.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/tina2.h
modules/alsa-driver/alsa-kernel/pci/emu10k1/emumpu401.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/emu10k1_synth_local.h
modules/alsa-driver/alsa-kernel/pci/emu10k1/p16v.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/p16v.h
modules/alsa-driver/alsa-kernel/pci/emu10k1/emupcm.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/timer.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/voice.c
modules/alsa-driver/alsa-kernel/pci/emu10k1/p17v.h
modules/alsa-driver/alsa-kernel/pci/bt87x.c
modules/alsa-driver/alsa-kernel/pci/via82xx.c
modules/alsa-driver/alsa-kernel/pci/ac97/
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_proc.c
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_patch.c
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_codec.c
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_local.h
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_patch.h
modules/alsa-driver/alsa-kernel/pci/ac97/Makefile
modules/alsa-driver/alsa-kernel/pci/ac97/ak4531_codec.c
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_id.h
modules/alsa-driver/alsa-kernel/pci/ac97/ac97_pcm.c
modules/alsa-driver/alsa-kernel/pci/rme9652/
modules/alsa-driver/alsa-kernel/pci/rme9652/hdspm.c
modules/alsa-driver/alsa-kernel/pci/rme9652/hdsp.c
modules/alsa-driver/alsa-kernel/pci/rme9652/rme9652.c
modules/alsa-driver/alsa-kernel/pci/rme9652/Makefile
modules/alsa-driver/alsa-kernel/pci/rme96.c
modules/alsa-driver/alsa-kernel/pci/sonicvibes.c
modules/alsa-driver/alsa-kernel/pci/cs5535audio/
modules/alsa-driver/alsa-kernel/pci/cs5535audio/cs5535audio.c
modules/alsa-driver/alsa-kernel/pci/cs5535audio/Makefile
modules/alsa-driver/alsa-kernel/pci/cs5535audio/cs5535audio.h
modules/alsa-driver/alsa-kernel/pci/cs5535audio/cs5535audio_pcm.c
modules/alsa-driver/alsa-kernel/pci/cs5535audio/cs5535audio_pm.c
modules/alsa-driver/alsa-kernel/pci/fm801.c
modules/alsa-driver/alsa-kernel/pci/Kconfig
modules/alsa-driver/alsa-kernel/pci/azt3328.h
modules/alsa-driver/alsa-kernel/pci/sis7019.h
modules/alsa-driver/alsa-kernel/pci/hda/
modules/alsa-driver/alsa-kernel/pci/hda/hda_generic.c
modules/alsa-driver/alsa-kernel/pci/hda/patch_sigmatel.c
modules/alsa-driver/alsa-kernel/pci/hda/hda_local.h
modules/alsa-driver/alsa-kernel/pci/hda/patch_analog.c
modules/alsa-driver/alsa-kernel/pci/hda/vmaster.c
modules/alsa-driver/alsa-kernel/pci/hda/hda_proc.c
modules/alsa-driver/alsa-kernel/pci/hda/patch_conexant.c
modules/alsa-driver/alsa-kernel/pci/hda/patch_via.c
modules/alsa-driver/alsa-kernel/pci/hda/patch_cmedia.c
modules/alsa-driver/alsa-kernel/pci/hda/Makefile
modules/alsa-driver/alsa-kernel/pci/hda/hda_patch.h
modules/alsa-driver/alsa-kernel/pci/hda/patch_realtek.c
modules/alsa-driver/alsa-kernel/pci/hda/hda_intel.c
modules/alsa-driver/alsa-kernel/pci/hda/hda_codec.c
modules/alsa-driver/alsa-kernel/pci/hda/hda_codec.h
modules/alsa-driver/alsa-kernel/pci/hda/patch_atihdmi.c
modules/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.c
modules/alsa-driver/alsa-kernel/pci/hda/patch_si3054.c
modules/alsa-driver/alsa-kernel/pci/ens1371.c
modules/alsa-driver/alsa-kernel/pci/als4000.c
modules/alsa-driver/alsa-kernel/pci/cmipci.c
modules/alsa-driver/alsa-kernel/pci/sis7019.c
modules/alsa-driver/alsa-kernel/pci/mixart/
modules/alsa-driver/alsa-kernel/pci/mixart/mixart.h
modules/alsa-driver/alsa-kernel/pci/mixart/mixart_hwdep.c
modules/alsa-driver/alsa-kernel/pci/mixart/Makefile
modules/alsa-driver/alsa-kernel/pci/mixart/mixart_mixer.h
modules/alsa-driver/alsa-kernel/pci/mixart/mixart_mixer.c
modules/alsa-driver/alsa-kernel/pci/mixart/mixart.c
modules/alsa-driver/alsa-kernel/pci/mixart/mixart_core.h
modules/alsa-driver/alsa-kernel/pci/mixart/mixart_core.c
modules/alsa-driver/alsa-kernel/pci/mixart/mixart_hwdep.h
modules/alsa-driver/alsa-kernel/pci/atiixp_modem.c
modules/alsa-driver/alsa-kernel/pci/korg1212/
modules/alsa-driver/alsa-kernel/pci/korg1212/Makefile
modules/alsa-driver/alsa-kernel/pci/korg1212/korg1212.c
modules/alsa-driver/alsa-kernel/pci/korg1212/korg1212-firmware.h
modules/alsa-driver/alsa-kernel/pci/pcxhr/
modules/alsa-driver/alsa-kernel/pci/pcxhr/Makefile
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr.c
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr_hwdep.c
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr_mixer.h
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr_mixer.c
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr_core.c
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr_core.h
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr_hwdep.h
modules/alsa-driver/alsa-kernel/pci/pcxhr/pcxhr.h
modules/alsa-driver/alsa-kernel/pci/echoaudio/
modules/alsa-driver/alsa-kernel/pci/echoaudio/darla24.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echo3g.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/indigoio.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/layla20_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/darla20_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/midi.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echoaudio.h
modules/alsa-driver/alsa-kernel/pci/echoaudio/gina24_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/gina20.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/Makefile
modules/alsa-driver/alsa-kernel/pci/echoaudio/mia.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/mia_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/indigoio_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/mona_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echo3g_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echoaudio_dsp.h
modules/alsa-driver/alsa-kernel/pci/echoaudio/indigodj_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/indigo.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echoaudio_gml.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/indigo_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/mona.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/layla24_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echoaudio_3g.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/gina24.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echoaudio.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/layla24.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/gina20_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/indigodj.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/darla24_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/echoaudio_dsp.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/darla20.c
modules/alsa-driver/alsa-kernel/pci/echoaudio/layla20.c
modules/alsa-driver/alsa-kernel/Makefile
modules/alsa-driver/alsa-kernel/drivers/
modules/alsa-driver/alsa-kernel/drivers/pcm-indirect2.c
modules/alsa-driver/alsa-kernel/drivers/virmidi.c
modules/alsa-driver/alsa-kernel/drivers/portman2x4.c
modules/alsa-driver/alsa-kernel/drivers/mts64.c
modules/alsa-driver/alsa-kernel/drivers/opl4/
modules/alsa-driver/alsa-kernel/drivers/opl4/opl4_local.h
modules/alsa-driver/alsa-kernel/drivers/opl4/Makefile
modules/alsa-driver/alsa-kernel/drivers/opl4/opl4_proc.c
modules/alsa-driver/alsa-kernel/drivers/opl4/opl4_lib.c
modules/alsa-driver/alsa-kernel/drivers/opl4/opl4_synth.c
modules/alsa-driver/alsa-kernel/drivers/opl4/opl4_seq.c
modules/alsa-driver/alsa-kernel/drivers/opl4/opl4_mixer.c
modules/alsa-driver/alsa-kernel/drivers/opl4/yrw801.c
modules/alsa-driver/alsa-kernel/drivers/pcm-indirect2.h
modules/alsa-driver/alsa-kernel/drivers/Makefile
modules/alsa-driver/alsa-kernel/drivers/ml403-ac97cr.c
modules/alsa-driver/alsa-kernel/drivers/Kconfig
modules/alsa-driver/alsa-kernel/drivers/serial-u16550.c
modules/alsa-driver/alsa-kernel/drivers/vx/
modules/alsa-driver/alsa-kernel/drivers/vx/Makefile
modules/alsa-driver/alsa-kernel/drivers/vx/vx_cmd.c
modules/alsa-driver/alsa-kernel/drivers/vx/vx_core.c
modules/alsa-driver/alsa-kernel/drivers/vx/vx_cmd.h
modules/alsa-driver/alsa-kernel/drivers/vx/vx_uer.c
modules/alsa-driver/alsa-kernel/drivers/vx/vx_mixer.c
modules/alsa-driver/alsa-kernel/drivers/vx/vx_hwdep.c
modules/alsa-driver/alsa-kernel/drivers/vx/vx_pcm.c
modules/alsa-driver/alsa-kernel/drivers/opl3/
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_synth.c
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_lib.c
modules/alsa-driver/alsa-kernel/drivers/opl3/Makefile
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_oss.c
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_seq.c
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_midi.c
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_voice.h
modules/alsa-driver/alsa-kernel/drivers/opl3/opl3_drums.c
modules/alsa-driver/alsa-kernel/drivers/mtpav.c
modules/alsa-driver/alsa-kernel/drivers/mpu401/
modules/alsa-driver/alsa-kernel/drivers/mpu401/mpu401.c
modules/alsa-driver/alsa-kernel/drivers/mpu401/mpu401_uart.c
modules/alsa-driver/alsa-kernel/drivers/mpu401/Makefile
modules/alsa-driver/alsa-kernel/drivers/dummy.c
modules/alsa-driver/alsa-kernel/last.c
modules/alsa-driver/alsa-kernel/ac97_bus.c
modules/alsa-driver/alsa-kernel/usb/
modules/alsa-driver/alsa-kernel/usb/usbmixer_maps.c
modules/alsa-driver/alsa-kernel/usb/usbquirks.h
modules/alsa-driver/alsa-kernel/usb/usbmixer.c
modules/alsa-driver/alsa-kernel/usb/Makefile
modules/alsa-driver/alsa-kernel/usb/usbmidi.c
modules/alsa-driver/alsa-kernel/usb/Kconfig
modules/alsa-driver/alsa-kernel/usb/usbaudio.h
modules/alsa-driver/alsa-kernel/usb/usbaudio.c
modules/alsa-driver/alsa-kernel/usb/caiaq/
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-midi.h
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-input.c
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-device.h
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-control.c
modules/alsa-driver/alsa-kernel/usb/caiaq/Makefile
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-audio.h
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-control.h
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-audio.c
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-device.c
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-input.h
modules/alsa-driver/alsa-kernel/usb/caiaq/caiaq-midi.c
modules/alsa-driver/alsa-kernel/usb/usx2y/
modules/alsa-driver/alsa-kernel/usb/usx2y/usbus428ctldefs.h
modules/alsa-driver/alsa-kernel/usb/usx2y/usx2y.h
modules/alsa-driver/alsa-kernel/usb/usx2y/usbusx2y.h
modules/alsa-driver/alsa-kernel/usb/usx2y/Makefile
modules/alsa-driver/alsa-kernel/usb/usx2y/usbusx2yaudio.c
modules/alsa-driver/alsa-kernel/usb/usx2y/usX2Yhwdep.h
modules/alsa-driver/alsa-kernel/usb/usx2y/usx2yhwdeppcm.h
modules/alsa-driver/alsa-kernel/usb/usx2y/usX2Yhwdep.c
modules/alsa-driver/alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
modules/alsa-driver/alsa-kernel/usb/usx2y/usbusx2y.c
modules/alsa-driver/alsa-kernel/core/
modules/alsa-driver/alsa-kernel/core/control.c
modules/alsa-driver/alsa-kernel/core/info.c
modules/alsa-driver/alsa-kernel/core/pcm_misc.c
modules/alsa-driver/alsa-kernel/core/rawmidi.c
modules/alsa-driver/alsa-kernel/core/oss/
modules/alsa-driver/alsa-kernel/core/oss/mulaw.c
modules/alsa-driver/alsa-kernel/core/oss/mixer_oss.c
modules/alsa-driver/alsa-kernel/core/oss/linear.c
modules/alsa-driver/alsa-kernel/core/oss/io.c
modules/alsa-driver/alsa-kernel/core/oss/pcm_oss.c
modules/alsa-driver/alsa-kernel/core/oss/pcm_plugin.c
modules/alsa-driver/alsa-kernel/core/oss/Makefile
modules/alsa-driver/alsa-kernel/core/oss/route.c
modules/alsa-driver/alsa-kernel/core/oss/rate.c
modules/alsa-driver/alsa-kernel/core/oss/pcm_plugin.h
modules/alsa-driver/alsa-kernel/core/oss/copy.c
modules/alsa-driver/alsa-kernel/core/seq/
modules/alsa-driver/alsa-kernel/core/seq/seq_memory.c
modules/alsa-driver/alsa-kernel/core/seq/seq_clientmgr.h
modules/alsa-driver/alsa-kernel/core/seq/seq.c
modules/alsa-driver/alsa-kernel/core/seq/seq_midi_event.c
modules/alsa-driver/alsa-kernel/core/seq/seq_info.h
modules/alsa-driver/alsa-kernel/core/seq/oss/
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_ioctl.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_synth.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_readq.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_rw.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_init.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_readq.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_writeq.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_synth.c
modules/alsa-driver/alsa-kernel/core/seq/oss/Makefile
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_timer.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_midi.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_midi.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_event.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_writeq.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_event.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_device.h
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss_timer.c
modules/alsa-driver/alsa-kernel/core/seq/oss/seq_oss.c
modules/alsa-driver/alsa-kernel/core/seq/seq_compat.c
modules/alsa-driver/alsa-kernel/core/seq/seq_info.c
modules/alsa-driver/alsa-kernel/core/seq/seq_midi_emul.c
modules/alsa-driver/alsa-kernel/core/seq/seq_timer.h
modules/alsa-driver/alsa-kernel/core/seq/seq_system.c
modules/alsa-driver/alsa-kernel/core/seq/seq_prioq.h
modules/alsa-driver/alsa-kernel/core/seq/seq_lock.c
modules/alsa-driver/alsa-kernel/core/seq/Makefile
modules/alsa-driver/alsa-kernel/core/seq/seq_queue.c
modules/alsa-driver/alsa-kernel/core/seq/seq_memory.h
modules/alsa-driver/alsa-kernel/core/seq/seq_fifo.c
modules/alsa-driver/alsa-kernel/core/seq/seq_queue.h
modules/alsa-driver/alsa-kernel/core/seq/seq_fifo.h
modules/alsa-driver/alsa-kernel/core/seq/seq_virmidi.c
modules/alsa-driver/alsa-kernel/core/seq/seq_prioq.c
modules/alsa-driver/alsa-kernel/core/seq/seq_device.c
modules/alsa-driver/alsa-kernel/core/seq/seq_timer.c
modules/alsa-driver/alsa-kernel/core/seq/seq_ports.h
modules/alsa-driver/alsa-kernel/core/seq/seq_system.h
modules/alsa-driver/alsa-kernel/core/seq/seq_midi.c
modules/alsa-driver/alsa-kernel/core/seq/seq_clientmgr.c
modules/alsa-driver/alsa-kernel/core/seq/seq_dummy.c
modules/alsa-driver/alsa-kernel/core/seq/seq_lock.h
modules/alsa-driver/alsa-kernel/core/seq/seq_ports.c
modules/alsa-driver/alsa-kernel/core/misc.c
modules/alsa-driver/alsa-kernel/core/memory.c
modules/alsa-driver/alsa-kernel/core/pcm_memory.c
modules/alsa-driver/alsa-kernel/core/pcm_timer.c
modules/alsa-driver/alsa-kernel/core/sound.c
modules/alsa-driver/alsa-kernel/core/pcm.c
modules/alsa-driver/alsa-kernel/core/Makefile
modules/alsa-driver/alsa-kernel/core/memalloc.c
modules/alsa-driver/alsa-kernel/core/device.c
modules/alsa-driver/alsa-kernel/core/control_compat.c
modules/alsa-driver/alsa-kernel/core/isadma.c
modules/alsa-driver/alsa-kernel/core/sgbuf.c
modules/alsa-driver/alsa-kernel/core/pcm_native.c
modules/alsa-driver/alsa-kernel/core/pcm_compat.c
modules/alsa-driver/alsa-kernel/core/init.c
modules/alsa-driver/alsa-kernel/core/info_oss.c
modules/alsa-driver/alsa-kernel/core/Kconfig
modules/alsa-driver/alsa-kernel/core/pcm_lib.c
modules/alsa-driver/alsa-kernel/core/hwdep.c
modules/alsa-driver/alsa-kernel/core/timer.c
modules/alsa-driver/alsa-kernel/core/sound_oss.c
modules/alsa-driver/alsa-kernel/core/rtctimer.c
modules/alsa-driver/alsa-kernel/core/timer_compat.c
modules/alsa-driver/alsa-kernel/core/hwdep_compat.c
modules/alsa-driver/alsa-kernel/core/rawmidi_compat.c
modules/alsa-driver/alsa-kernel/mips/
modules/alsa-driver/alsa-kernel/mips/Makefile
modules/alsa-driver/alsa-kernel/mips/Kconfig
modules/alsa-driver/alsa-kernel/mips/au1x00.c
modules/alsa-driver/alsa-kernel/pcmcia/
modules/alsa-driver/alsa-kernel/pcmcia/Makefile
modules/alsa-driver/alsa-kernel/pcmcia/Kconfig
modules/alsa-driver/alsa-kernel/pcmcia/vx/
modules/alsa-driver/alsa-kernel/pcmcia/vx/vxpocket.c
modules/alsa-driver/alsa-kernel/pcmcia/vx/Makefile
modules/alsa-driver/alsa-kernel/pcmcia/vx/vxpocket.h
modules/alsa-driver/alsa-kernel/pcmcia/vx/vxp_mixer.c
modules/alsa-driver/alsa-kernel/pcmcia/vx/vxp_ops.c
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/Makefile
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.c
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_core.c
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.h
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c
modules/alsa-driver/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_pcm.c
modules/alsa-driver/alsa-kernel/sparc/
modules/alsa-driver/alsa-kernel/sparc/dbri.c
modules/alsa-driver/alsa-kernel/sparc/cs4231.c
modules/alsa-driver/alsa-kernel/sparc/Makefile
modules/alsa-driver/alsa-kernel/sparc/amd7930.c
modules/alsa-driver/alsa-kernel/sparc/Kconfig
modules/alsa-driver/alsa-kernel/Kconfig
modules/alsa-driver/alsa-kernel/sound_firmware.c
modules/alsa-driver/alsa-kernel/Documentation/
modules/alsa-driver/alsa-kernel/Documentation/Joystick.txt
modules/alsa-driver/alsa-kernel/Documentation/hda_codec.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/
modules/alsa-driver/alsa-kernel/Documentation/soc/clocking.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/overview.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/codec.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/dapm.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/pops_clicks.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/machine.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/DAI.txt
modules/alsa-driver/alsa-kernel/Documentation/soc/platform.txt
modules/alsa-driver/alsa-kernel/Documentation/Bt87x.txt
modules/alsa-driver/alsa-kernel/Documentation/VIA82xx-mixer.txt
modules/alsa-driver/alsa-kernel/Documentation/hdspm.txt
modules/alsa-driver/alsa-kernel/Documentation/ControlNames.txt
modules/alsa-driver/alsa-kernel/Documentation/serial-u16550.txt
modules/alsa-driver/alsa-kernel/Documentation/seq_oss.html
modules/alsa-driver/alsa-kernel/Documentation/emu10k1-jack.txt
modules/alsa-driver/alsa-kernel/Documentation/powersave.txt
modules/alsa-driver/alsa-kernel/Documentation/OSS-Emulation.txt
modules/alsa-driver/alsa-kernel/Documentation/CMIPCI.txt
modules/alsa-driver/alsa-kernel/Documentation/Procfile.txt
modules/alsa-driver/alsa-kernel/Documentation/Audigy-mixer.txt
modules/alsa-driver/alsa-kernel/Documentation/DocBook/
modules/alsa-driver/alsa-kernel/Documentation/DocBook/alsa-driver-api.tmpl
modules/alsa-driver/alsa-kernel/Documentation/DocBook/writing-an-alsa-driver.tmpl
modules/alsa-driver/alsa-kernel/Documentation/Audiophile-Usb.txt
modules/alsa-driver/alsa-kernel/Documentation/ALSA-Configuration.txt
modules/alsa-driver/alsa-kernel/Documentation/MIXART.txt
modules/alsa-driver/alsa-kernel/Documentation/SB-Live-mixer.txt
modules/alsa-driver/alsa-kernel/sound_core.c
modules/alsa-driver/alsa-kernel/sh/
modules/alsa-driver/alsa-kernel/sh/aica.c
modules/alsa-driver/alsa-kernel/sh/aica.h
modules/alsa-driver/alsa-kernel/sh/Makefile
modules/alsa-driver/alsa-kernel/sh/Kconfig
modules/alsa-driver/alsa-kernel/include/
modules/alsa-driver/alsa-kernel/include/soc.h
modules/alsa-driver/alsa-kernel/include/sb16_csp.h
modules/alsa-driver/alsa-kernel/include/asoundef.h
modules/alsa-driver/alsa-kernel/include/seq_kernel.h
modules/alsa-driver/alsa-kernel/include/initval.h
modules/alsa-driver/alsa-kernel/include/cs4231.h
modules/alsa-driver/alsa-kernel/include/ak4xxx-adda.h
modules/alsa-driver/alsa-kernel/include/emux_synth.h
modules/alsa-driver/alsa-kernel/include/seq_virmidi.h
modules/alsa-driver/alsa-kernel/include/hwdep.h
modules/alsa-driver/alsa-kernel/include/core.h
modules/alsa-driver/alsa-kernel/include/wavefront.h
modules/alsa-driver/alsa-kernel/include/opl4.h
modules/alsa-driver/alsa-kernel/include/hdsp.h
modules/alsa-driver/alsa-kernel/include/pcm.h
modules/alsa-driver/alsa-kernel/include/util_mem.h
modules/alsa-driver/alsa-kernel/include/seq_oss.h
modules/alsa-driver/alsa-kernel/include/cs4231-regs.h
modules/alsa-driver/alsa-kernel/include/emux_legacy.h
modules/alsa-driver/alsa-kernel/include/seq_oss_legacy.h
modules/alsa-driver/alsa-kernel/include/Kbuild
modules/alsa-driver/alsa-kernel/include/minors.h
modules/alsa-driver/alsa-kernel/include/emu8000.h
modules/alsa-driver/alsa-kernel/include/ac97_codec.h
modules/alsa-driver/alsa-kernel/include/pt2258.h
modules/alsa-driver/alsa-kernel/include/sfnt_info.h
modules/alsa-driver/alsa-kernel/include/cs8403.h
modules/alsa-driver/alsa-kernel/include/seq_midi_event.h
modules/alsa-driver/alsa-kernel/include/uda1341.h
modules/alsa-driver/alsa-kernel/include/pcm-indirect.h
modules/alsa-driver/alsa-kernel/include/seq_midi_emul.h
modules/alsa-driver/alsa-kernel/include/trident.h
modules/alsa-driver/alsa-kernel/include/cs46xx_dsp_scb_types.h
modules/alsa-driver/alsa-kernel/include/soc-dapm.h
modules/alsa-driver/alsa-kernel/include/ak4117.h
modules/alsa-driver/alsa-kernel/include/rawmidi.h
modules/alsa-driver/alsa-kernel/include/memalloc.h
modules/alsa-driver/alsa-kernel/include/asound_fm.h
modules/alsa-driver/alsa-kernel/include/ad1848.h
modules/alsa-driver/alsa-kernel/include/i2c.h
modules/alsa-driver/alsa-kernel/include/emu10k1.h
modules/alsa-driver/alsa-kernel/include/timer.h
modules/alsa-driver/alsa-kernel/include/ak4531_codec.h
modules/alsa-driver/alsa-kernel/include/hdspm.h
modules/alsa-driver/alsa-kernel/include/pcm_params.h
modules/alsa-driver/alsa-kernel/include/emu8000_reg.h
modules/alsa-driver/alsa-kernel/include/mpu401.h
modules/alsa-driver/alsa-kernel/include/cs46xx_dsp_spos.h
modules/alsa-driver/alsa-kernel/include/cs46xx.h
modules/alsa-driver/alsa-kernel/include/mixer_oss.h
modules/alsa-driver/alsa-kernel/include/ymfpci.h
modules/alsa-driver/alsa-kernel/include/snd_wavefront.h
modules/alsa-driver/alsa-kernel/include/hda_hwdep.h
modules/alsa-driver/alsa-kernel/include/tlv.h
modules/alsa-driver/alsa-kernel/include/seq_device.h
modules/alsa-driver/alsa-kernel/include/ak4114.h
modules/alsa-driver/alsa-kernel/include/cs8427.h
modules/alsa-driver/alsa-kernel/include/sb.h
modules/alsa-driver/alsa-kernel/include/pcm_oss.h
modules/alsa-driver/alsa-kernel/include/opl3.h
modules/alsa-driver/alsa-kernel/include/es1688.h
modules/alsa-driver/alsa-kernel/include/control.h
modules/alsa-driver/alsa-kernel/include/driver.h
modules/alsa-driver/alsa-kernel/include/emu10k1_synth.h
modules/alsa-driver/alsa-kernel/include/vx_core.h
modules/alsa-driver/alsa-kernel/include/ad1816a.h
modules/alsa-driver/alsa-kernel/include/sscape_ioctl.h
modules/alsa-driver/alsa-kernel/include/asequencer.h
modules/alsa-driver/alsa-kernel/include/gus.h
modules/alsa-driver/alsa-kernel/include/info.h
modules/alsa-driver/alsa-kernel/include/soundfont.h
modules/alsa-driver/alsa-kernel/include/tea575x-tuner.h
modules/alsa-driver/alsa-kernel/include/asound.h
modules/alsa-driver/alsa-kernel/include/cs46xx_dsp_task_types.h
modules/alsa-driver/alsa-kernel/include/tea6330t.h
modules/alsa-driver/usb/
modules/alsa-driver/usb/usbaudio.inc
modules/alsa-driver/usb/usbaudio.patch
modules/alsa-driver/usb/usbcompat.c
modules/alsa-driver/usb/Makefile
modules/alsa-driver/usb/usbmidi.patch
modules/alsa-driver/usb/caiaq/
modules/alsa-driver/usb/caiaq/caiaq-input.patch
modules/alsa-driver/usb/caiaq/caiaq-control.c
modules/alsa-driver/usb/caiaq/Makefile
modules/alsa-driver/usb/caiaq/caiaq-device.patch
modules/alsa-driver/usb/caiaq/caiaq-audio.patch
modules/alsa-driver/usb/caiaq/caiaq-midi.c
modules/alsa-driver/usb/usbmidi.inc1
modules/alsa-driver/usb/usbmixer.patch
modules/alsa-driver/usb/usbaudio.inc1
modules/alsa-driver/usb/usx2y/
modules/alsa-driver/usb/usx2y/usx2yhwdeppcm.patch
modules/alsa-driver/usb/usx2y/usbusx2y.patch
modules/alsa-driver/usb/usx2y/usX2Yhwdep.patch
modules/alsa-driver/usb/usx2y/Makefile
modules/alsa-driver/usb/usx2y/usbusx2yaudio.patch
modules/alsa-driver/usb/usbmidi.inc
modules/alsa-driver/version
modules/alsa-driver/support/
modules/alsa-driver/support/isapnp/
modules/alsa-driver/support/isapnp/isapnp_proc.c
modules/alsa-driver/support/isapnp/isapnp.txt
modules/alsa-driver/support/isapnp/Makefile
modules/alsa-driver/support/isapnp/isapnp.h
modules/alsa-driver/support/isapnp/isapnp_test.c
modules/alsa-driver/support/isapnp/isapnp_quirks.c
modules/alsa-driver/support/isapnp/isapnp.c
modules/alsa-driver/support/pnp/
modules/alsa-driver/support/pnp/pnp.h
modules/alsa-driver/support/pnp/Makefile
modules/alsa-driver/support/pnp/pnp.c
modules/alsa-driver/support/Makefile
modules/alsa-driver/doc/
modules/alsa-driver/doc/SOUNDCARDS
modules/alsa-driver/doc/README.1st
modules/alsa-driver/doc/INSTALL.asihpi-alsa
modules/alsa-driver/doc/Makefile
modules/alsa-driver/doc/README.riptide
modules/alsa-driver/doc/serialmidi.txt
modules/alsa-driver/doc/DocBook/
modules/alsa-driver/doc/DocBook/Makefile
modules/alsa-driver/doc/README.asihpi-alsa
modules/alsa-driver/mips/
modules/alsa-driver/mips/Makefile
modules/alsa-driver/mips/au1x00.c
modules/alsa-driver/pcmcia/
modules/alsa-driver/pcmcia/Makefile
modules/alsa-driver/pcmcia/vx/
modules/alsa-driver/pcmcia/vx/vxpocket.conf
modules/alsa-driver/pcmcia/vx/vxpocket.c
modules/alsa-driver/pcmcia/vx/Makefile
modules/alsa-driver/pcmcia/vx/vxpocket-2.6.16.c
modules/alsa-driver/pcmcia/vx/vxpocket.h
modules/alsa-driver/pcmcia/vx/vxp_mixer.c
modules/alsa-driver/pcmcia/vx/vxp_ops.c
modules/alsa-driver/pcmcia/vx/vx_entry.inc1
modules/alsa-driver/pcmcia/vx/vxpocket_old.c
modules/alsa-driver/pcmcia/vx/vx_entry.inc
modules/alsa-driver/pcmcia/pdaudiocf/
modules/alsa-driver/pcmcia/pdaudiocf/Makefile
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf.c
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf_core.c
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf.conf
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf_old.c
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf.h
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf_irq.c
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf_pcm.c
modules/alsa-driver/pcmcia/pdaudiocf/pdaudiocf-2.6.16.c
modules/alsa-driver/cvscompile
modules/alsa-driver/sparc/
modules/alsa-driver/sparc/dbri.c
modules/alsa-driver/sparc/cs4231.c
modules/alsa-driver/sparc/Makefile
modules/alsa-driver/sparc/amd7930.c
modules/alsa-driver/README
modules/alsa-driver/kconfig-vers
modules/alsa-driver/utils/
modules/alsa-driver/utils/alsa-driver.spec.in
modules/alsa-driver/utils/module-options
modules/alsa-driver/utils/kredirect.c
modules/alsa-driver/utils/alsasound.posix.in
modules/alsa-driver/utils/buildrpm
modules/alsa-driver/utils/link-modules
modules/alsa-driver/utils/insert
modules/alsa-driver/utils/convert_isapnp_ids
modules/alsa-driver/utils/patches/
modules/alsa-driver/utils/patches/patch.Makefile.top.2.4.0-test10
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.15-01.diff
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.22-01.diff
modules/alsa-driver/utils/patches/patch.Makefile.2.4.1
modules/alsa-driver/utils/patches/rtc-2.4.16.patch
modules/alsa-driver/utils/patches/rtc-2.2.16.dif
modules/alsa-driver/utils/patches/soundcore.2.4.patch
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.21-02.diff
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.19-01.diff
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.14-01.diff
modules/alsa-driver/utils/patches/rtc-2.4.20.patch
modules/alsa-driver/utils/patches/patch.mem.c.2.3.34
modules/alsa-driver/utils/patches/byteswap.h
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.17-03.diff
modules/alsa-driver/utils/patches/pnp-suspend-2.6.15-rc1.diff
modules/alsa-driver/utils/patches/rtc-2.4.9.dif
modules/alsa-driver/utils/patches/patch.Makefile.top.2.4.1
modules/alsa-driver/utils/patches/patch.Makefile.2.4.0-test10
modules/alsa-driver/utils/patches/rtc-2.4.23.patch
modules/alsa-driver/utils/patches/patch.Makefile.2.4.2
modules/alsa-driver/utils/patches/soundcore.2.4.20.patch
modules/alsa-driver/utils/patches/pcsp-kernel-2.6.18-01.diff
modules/alsa-driver/utils/patches/rtc-2.4.25.patch
modules/alsa-driver/utils/patches/rtc-suse-7.0-2.2.16.dif
modules/alsa-driver/utils/Makefile
modules/alsa-driver/utils/buildrpm.in
modules/alsa-driver/utils/alsasound
modules/alsa-driver/utils/old/
modules/alsa-driver/utils/old/export-symbols.in
modules/alsa-driver/utils/old/export-symbols.perl
modules/alsa-driver/utils/mod-deps
modules/alsa-driver/utils/patch-alsa
modules/alsa-driver/utils/mod-deps.c
modules/alsa-driver/utils/alsasound.in
modules/alsa-driver/utils/oss-move
modules/alsa-driver/utils/remove
modules/alsa-driver/utils/alsasound.posix
modules/alsa-driver/modules/
modules/alsa-driver/modules/.keepme
modules/alsa-driver/aclocal.m4
modules/alsa-driver/SUPPORTED_KERNELS
modules/alsa-driver/sh/
modules/alsa-driver/sh/aica.c
modules/alsa-driver/sh/Makefile
modules/alsa-driver/include/
modules/alsa-driver/include/compat_cs.h
modules/alsa-driver/include/hal2.h
modules/alsa-driver/include/compat_64.h
modules/alsa-driver/include/i2c-id_compat.h
modules/alsa-driver/include/isa_compat.h
modules/alsa-driver/include/config1.h.in
modules/alsa-driver/include/platform_device_compat.h
modules/alsa-driver/include/syscalls_26.h
modules/alsa-driver/include/kthread_compat.h
modules/alsa-driver/include/pci_ids_compat.h.in
modules/alsa-driver/include/i2c-id_compat.h.in
modules/alsa-driver/include/asm/
modules/alsa-driver/include/Makefile
modules/alsa-driver/include/adriver.h
modules/alsa-driver/include/firmware_compat.h
modules/alsa-driver/include/autoconf-extra.h.in
modules/alsa-driver/include/autoconf-extra.h
modules/alsa-driver/include/old/
modules/alsa-driver/include/old/ainstr_iw.h
modules/alsa-driver/include/old/gf1.h
modules/alsa-driver/include/old/ainstr_fm.h
modules/alsa-driver/include/old/ainstr_gf1.h
modules/alsa-driver/include/old/ainstr_simple.h
modules/alsa-driver/include/old/ultra_todo.h
modules/alsa-driver/include/old/seq_instr.h
modules/alsa-driver/include/version.h.in
modules/alsa-driver/include/config.h
modules/alsa-driver/include/media/
modules/alsa-driver/include/version.h
modules/alsa-driver/include/modules/
modules/alsa-driver/include/modules/.keepme
modules/alsa-driver/include/config.h.in
modules/alsa-driver/include/config1.h
modules/alsa-driver/include/pci_ids_compat.h
modules/alsa-driver/include/uda1380.h
modules/alsa-driver/include/linux/
modules/alsa-driver/include/latency_compat.h
modules/alsa-driver/include/bitmap_compat.h
modules/alsa-driver/include/compat_22.h
modules/alsa-driver/include/mutex_compat.h
modules/alsa-driver/include/err_compat.h
modules/alsa-driver/include/device_compat.h
modules/alsa-driver/include/ppc-prom-hack.h
modules/alsa-driver/COPYING
modules/alsa-driver/Rules.make1
modules/alsa-driver/install-sh
modules/alsa-driver/WARNING
modules/alsa-driver/Rules.make
modules/alsa-driver/FAQ
modules/alsa-driver/CARDS-STATUS
modules/alsa-driver/.pc/
modules/alsa-driver/.pc/.version
modules/alsa-driver/.pc/add_onda_a69g_ac97_support.patch/
modules/alsa-driver/.pc/add_onda_a69g_ac97_support.patch/alsa-kernel/
modules/alsa-driver/.pc/add_onda_a69g_ac97_support.patch/alsa-kernel/pci/
modules/alsa-driver/.pc/add_onda_a69g_ac97_support.patch/alsa-kernel/pci/atiixp.c
modules/alsa-driver/.pc/add_onda_a69g_ac97_support.patch/.timestamp
modules/alsa-driver/.pc/applied-patches
modules/alsa-driver/.pc/alpha_build_fixes.patch/
modules/alsa-driver/.pc/alpha_build_fixes.patch/isa/
modules/alsa-driver/.pc/alpha_build_fixes.patch/isa/msnd/
modules/alsa-driver/.pc/alpha_build_fixes.patch/isa/msnd/msnd_pinnacle.c
modules/alsa-driver/.pc/alpha_build_fixes.patch/.timestamp
modules/alsa-driver/.pc/disable_gcc_version_check1.patch/
modules/alsa-driver/.pc/disable_gcc_version_check1.patch/configure.in
modules/alsa-driver/.pc/disable_gcc_version_check1.patch/.timestamp
modules/alsa-driver/.pc/disable_gcc_version_check2.patch/
modules/alsa-driver/.pc/disable_gcc_version_check2.patch/configure
modules/alsa-driver/.pc/disable_gcc_version_check2.patch/.timestamp
modules/alsa-driver/.pc/core_oss_framepointer.patch/
modules/alsa-driver/.pc/core_oss_framepointer.patch/alsa-kernel/
modules/alsa-driver/.pc/core_oss_framepointer.patch/alsa-kernel/core/
modules/alsa-driver/.pc/core_oss_framepointer.patch/alsa-kernel/core/oss/
modules/alsa-driver/.pc/core_oss_framepointer.patch/alsa-kernel/core/oss/Makefile
modules/alsa-driver/.pc/core_oss_framepointer.patch/.timestamp
modules/alsa-driver/.pc/debian_makefile_depmod.patch/
modules/alsa-driver/.pc/debian_makefile_depmod.patch/Makefile
modules/alsa-driver/.pc/debian_makefile_depmod.patch/.timestamp
modules/alsa-driver/.pc/post_16_20080307.patch/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/hda_codec.h
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/hda_intel.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_analog.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_atihdmi.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_cmedia.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_conexant.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_realtek.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_si3054.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_sigmatel.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/patch_via.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/hda_codec.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/hda_local.h
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/hda_proc.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/hda/hda_patch.h
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/delta.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/delta.h
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/hoontech.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/ice1712.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/phase.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ice1712/revo.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ac97/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ac97/ac97_patch.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ac97/ac97_pcm.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/intel8x0.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/bt87x.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/rme9652/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/rme9652/hdsp.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/rme9652/hdspm.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/oxygen/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/oxygen/hifier.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/oxygen/virtuoso.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ali5451/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ali5451/ali5451.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ca0106/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ca0106/ca0106_main.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ca0106/ca0106_mixer.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/cmipci.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/ens1370.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/es1968.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/fm801.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/maestro3.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/rme32.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/rme96.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/au88x0/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/au88x0/au88x0_pcm.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/emu10k1/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/emu10k1/emu10k1x.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/emu10k1/emuproc.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/pcxhr/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/pcxhr/pcxhr_core.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/riptide/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/pci/riptide/riptide.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/fsl/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/fsl/mpc8610_hpcd.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/codecs/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/codecs/tlv320aic3x.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/codecs/wm9712.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/codecs/wm8753.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/soc-dapm.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/pxa/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/pxa/corgi.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/pxa/poodle.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/pxa/spitz.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/soc/pxa/tosa.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/usx2y/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/usx2y/usX2Yhwdep.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/usx2y/usx2yhwdeppcm.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/caiaq/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/caiaq/caiaq-device.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/usb/caiaq/caiaq-control.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/Documentation/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/Documentation/ALSA-Configuration.txt
modules/alsa-driver/.pc/post_16_20080307.patch/sound/spi/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/spi/at73c213.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/include/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/include/ac97_codec.h
modules/alsa-driver/.pc/post_16_20080307.patch/sound/include/asoundef.h
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/seq/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/seq/seq_clientmgr.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/seq/seq_device.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/seq/oss/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/seq/oss/seq_oss_synth.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/sound.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/core/timer.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/ppc/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/ppc/daca.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/ppc/tumbler.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/drivers/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/drivers/mpu401/
modules/alsa-driver/.pc/post_16_20080307.patch/sound/drivers/mpu401/mpu401_uart.c
modules/alsa-driver/.pc/post_16_20080307.patch/sound/drivers/dummy.c
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/Kconfig
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/pcsp.c
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/pcsp.h
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/pcsp_input.h
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/pcsp_lib.c
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/pcsp_mixer.c
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/pcsp/pcsp_input.c
modules/alsa-driver/.pc/post_16_20080307.patch/drivers/aloop-kernel.c
modules/alsa-driver/.pc/post_16_20080307.patch/usb/
modules/alsa-driver/.pc/post_16_20080307.patch/usb/usx2y/
modules/alsa-driver/.pc/post_16_20080307.patch/usb/usx2y/usX2Yhwdep.patch
modules/alsa-driver/.pc/post_16_20080307.patch/usb/usx2y/usx2yhwdeppcm.patch
modules/alsa-driver/.pc/post_16_20080307.patch/usb/caiaq/
modules/alsa-driver/.pc/post_16_20080307.patch/usb/caiaq/caiaq-device.patch
modules/alsa-driver/.pc/post_16_20080307.patch/pci/
modules/alsa-driver/.pc/post_16_20080307.patch/pci/intel8x0.patch
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/usb/
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/usb/usbaudio.c
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/usb/usbquirks.h
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/isa/
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/isa/sb/
modules/alsa-driver/.pc/post_16_20080307.patch/alsa-kernel/isa/sb/sb8_main.c
modules/alsa-driver/.pc/post_16_20080307.patch/.timestamp
modules/alsa-driver/.pc/add_suspend_quirk_hp_nc6220_nw8240.patch/
modules/alsa-driver/.pc/add_suspend_quirk_hp_nc6220_nw8240.patch/sound/
modules/alsa-driver/.pc/add_suspend_quirk_hp_nc6220_nw8240.patch/sound/pci/
modules/alsa-driver/.pc/add_suspend_quirk_hp_nc6220_nw8240.patch/sound/pci/intel8x0.c
modules/alsa-driver/.pc/add_suspend_quirk_hp_nc6220_nw8240.patch/.timestamp
modules/alsa-driver/.pc/refix_lp_68659_by_disabling_dxs_for_0x1458a002.patch/
modules/alsa-driver/.pc/refix_lp_68659_by_disabling_dxs_for_0x1458a002.patch/sound/
modules/alsa-driver/.pc/refix_lp_68659_by_disabling_dxs_for_0x1458a002.patch/sound/pci/
modules/alsa-driver/.pc/refix_lp_68659_by_disabling_dxs_for_0x1458a002.patch/sound/pci/via82xx.c
modules/alsa-driver/.pc/refix_lp_68659_by_disabling_dxs_for_0x1458a002.patch/.timestamp

```
cd modules/alsa-driver/
```
~/modules/alsa-driver$
```
wget -O alsa-kernel/pci/hda/patch_analog.c [http://launchpadlibrarian.net/9021234/patch_analog.c](http://launchpadlibrarian.net/9021234/patch_analog.c)
```
--02:23:42--  http://launchpadlibrarian.net/9021234/patch_analog.c
           => `alsa-kernel/pci/hda/patch_analog.c'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 99,992 (98K) [text/plain]

100%[====================================>] 99,992       177.79K/s

02:23:43 (177.33 KB/s) - `alsa-kernel/pci/hda/patch_analog.c' saved [99992/99992]

```
./configure --with-cards=hda-intel && make
```
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/diazbeat/modules/alsa-driver
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.24-16-generic/build
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-generic
checking for built-in ALSA... no
checking for existing ALSA module... no
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-16-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.16
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/home/diazbeat/modules/alsa-driver'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #2 succeeded at 156 (offset -1 lines).
Hunk #3 succeeded at 168 (offset -1 lines).
Hunk #4 succeeded at 178 (offset -1 lines).
Hunk #5 succeeded at 209 (offset -1 lines).
Hunk #6 succeeded at 494 (offset -1 lines).
Hunk #7 succeeded at 534 with fuzz 2 (offset -1 lines).
Hunk #8 succeeded at 993 (offset -1 lines).
Hunk #9 succeeded at 1022 (offset -1 lines).
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 898 (offset -12 lines).
Hunk #3 succeeded at 914 (offset -12 lines).
Hunk #4 succeeded at 926 (offset -12 lines).
Hunk #5 succeeded at 980 (offset -12 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #4 succeeded at 1582 (offset -20 lines).
Hunk #5 succeeded at 2817 (offset -42 lines).
Hunk #6 succeeded at 2837 (offset -42 lines).
Hunk #7 succeeded at 2867 (offset -42 lines).
Hunk #8 succeeded at 2894 (offset -42 lines).
Hunk #9 succeeded at 2910 (offset -42 lines).
Hunk #10 succeeded at 2940 (offset -42 lines).
Hunk #11 succeeded at 3026 (offset -42 lines).
Hunk #12 succeeded at 3045 (offset -42 lines).
Hunk #13 succeeded at 3059 (offset -42 lines).
Hunk #14 succeeded at 3117 (offset -42 lines).
Hunk #15 succeeded at 3145 (offset -42 lines).
Hunk #16 succeeded at 3203 (offset -42 lines).
Hunk #17 succeeded at 3232 (offset -42 lines).
Hunk #18 succeeded at 3262 (offset -42 lines).
Hunk #19 succeeded at 3339 (offset -42 lines).
Hunk #20 succeeded at 3371 (offset -42 lines).
Hunk #21 succeeded at 3437 (offset -42 lines).
Hunk #22 succeeded at 3466 (offset -42 lines).
Hunk #23 succeeded at 3507 (offset -42 lines).
Hunk #24 succeeded at 3657 (offset -42 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #3 succeeded at 712 (offset -7 lines).
Hunk #4 succeeded at 775 (offset -11 lines).
Hunk #5 succeeded at 1383 (offset -11 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1291 (offset 2 lines).
Hunk #4 succeeded at 1375 (offset 2 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #4 succeeded at 173 (offset -4 lines).
Hunk #5 succeeded at 247 (offset -4 lines).
Hunk #6 succeeded at 259 (offset -4 lines).
Hunk #7 succeeded at 276 (offset -4 lines).
Hunk #8 succeeded at 294 (offset -4 lines).
Hunk #9 succeeded at 343 (offset -4 lines).
Hunk #10 succeeded at 354 (offset -4 lines).
Hunk #11 succeeded at 380 (offset -4 lines).
Hunk #12 succeeded at 487 (offset -4 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 990 (offset -2 lines).
Hunk #4 succeeded at 1912 (offset -2 lines).
Hunk #5 succeeded at 1957 (offset -2 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/acore/ioctl32'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/acore/ioctl32'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 2589 (offset -1 lines).
Hunk #4 succeeded at 2640 (offset -1 lines).
Hunk #5 succeeded at 2763 (offset -1 lines).
Hunk #6 succeeded at 2946 (offset -1 lines).
Hunk #7 succeeded at 3073 (offset -1 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/acore/oss'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[4]: Entering directory `/home/diazbeat/modules/alsa-driver/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: Leaving directory `/home/diazbeat/modules/alsa-driver/acore/seq/oss'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/acore/seq'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/acore'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/i2c'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/i2c/l3'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/i2c/l3'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/i2c/other'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/i2c'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/drivers/mpu401'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/drivers/opl3'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/drivers/opl4'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/drivers/opl4'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/drivers/pcsp'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/drivers/pcsp'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/drivers/vx'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/drivers'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/isa'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/ad1816a'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/ad1816a'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/ad1848'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/ad1848'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/cs423x'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/cs423x'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/es1688'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/es1688'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/gus'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/gus'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/msnd'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/msnd'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/opti9xx'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/opti9xx'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/sb'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa/wavefront'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/isa'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/synth'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/synth'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1669 (offset -2 lines).
Hunk #3 succeeded at 1714 (offset -2 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1309 (offset 2 lines).
Hunk #3 succeeded at 1352 (offset 2 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3133 (offset -43 lines).
Hunk #3 succeeded at 3428 (offset -43 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2118 (offset -13 lines).
Hunk #3 succeeded at 2494 (offset -13 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #2 succeeded at 1426 (offset 23 lines).
Hunk #3 succeeded at 1607 (offset 23 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #5 succeeded at 3141 (offset 13 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #2 succeeded at 2747 (offset 2 lines).
Hunk #3 succeeded at 2933 (offset 2 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2433 (offset -3 lines).
Hunk #3 succeeded at 2443 (offset -3 lines).
Hunk #4 succeeded at 2458 (offset -3 lines).
Hunk #5 succeeded at 2469 (offset -3 lines).
Hunk #6 succeeded at 2480 (offset -3 lines).
Hunk #7 succeeded at 2563 (offset -3 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1182 (offset 2 lines).
Hunk #3 succeeded at 1242 (offset 2 lines).
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/ac97'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2209 (offset 4 lines).
Hunk #3 succeeded at 2379 (offset 4 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/ali5451'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/asihpi'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/asihpi'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 342 (offset 1 line).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/au88x0'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1361 (offset 8 lines).
Hunk #4 succeeded at 1730 (offset 8 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/ca0106'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/cs46xx'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/cs46xx'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/cs5535audio'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/cs5535audio'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1897 (offset -29 lines).
Hunk #2 succeeded at 1960 (offset -29 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/echoaudio'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #5 succeeded at 1446 (offset 8 lines).
Hunk #6 succeeded at 1754 (offset 8 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 942 (offset 2 lines).
Hunk #3 succeeded at 1630 (offset 2 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/emu10k1'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 309 (offset 30 lines).
Hunk #3 succeeded at 347 (offset 30 lines).
Hunk #4 succeeded at 362 (offset 30 lines).
Hunk #5 succeeded at 378 (offset 30 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/hda'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/ice1712'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/ice1712'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2353 (offset 4 lines).
Hunk #3 succeeded at 2514 (offset 4 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/korg1212'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/mixart'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/mixart'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/nm256'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/nm256'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/oxygen'
copying file alsa-kernel/pci/oxygen/virtuoso.c
patching file virtuoso.c
Hunk #3 succeeded at 455 (offset 1 line).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/oxygen'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/pcxhr'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/pcxhr'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/pdplus'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/pdplus'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2236 (offset 2 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/riptide'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/rme9652'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/rme9652'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/trident'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/trident'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/vx222'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2049 (offset 5 lines).
Hunk #3 succeeded at 2071 (offset 5 lines).
Hunk #4 succeeded at 2411 (offset 5 lines).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci/ymfpci'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/pci'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/aoa'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/aoa/codecs'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/aoa/codecs'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/aoa/core'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/aoa/core'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/aoa/fabrics'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/aoa/fabrics'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/aoa/soundbus'
make[4]: Entering directory `/home/diazbeat/modules/alsa-driver/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/diazbeat/modules/alsa-driver/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/aoa/soundbus'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/aoa'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/soc'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/soc/at91'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc/at91'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/soc/codecs'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc/codecs'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/soc/fsl'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc/fsl'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/soc/pxa'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc/pxa'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/soc/s3c24xx'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc/s3c24xx'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/soc/sh'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc/sh'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/soc'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #2 succeeded at 69 (offset -1 lines).
Hunk #3 succeeded at 685 (offset 26 lines).
Hunk #4 succeeded at 712 (offset 26 lines).
Hunk #5 succeeded at 793 (offset 26 lines).
Hunk #6 succeeded at 808 (offset 26 lines).
Hunk #7 succeeded at 1186 (offset 26 lines).
Hunk #8 succeeded at 2108 (offset 26 lines).
Hunk #9 succeeded at 2127 (offset 26 lines).
Hunk #10 succeeded at 2139 (offset 26 lines).
Hunk #11 succeeded at 2152 (offset 26 lines).
Hunk #12 succeeded at 2720 (offset 33 lines).
Hunk #13 succeeded at 2792 (offset 33 lines).
Hunk #14 succeeded at 3080 (offset 33 lines).
Hunk #15 succeeded at 3151 (offset 33 lines).
Hunk #16 succeeded at 3272 (offset 33 lines).
Hunk #17 succeeded at 3290 (offset 33 lines).
Hunk #18 succeeded at 3304 (offset 33 lines).
Hunk #19 succeeded at 3317 (offset 33 lines).
Hunk #20 succeeded at 3521 (offset 33 lines).
Hunk #21 succeeded at 3614 (offset 33 lines).
Hunk #22 succeeded at 3751 (offset 33 lines).
Hunk #23 succeeded at 3812 (offset 33 lines).
Hunk #24 succeeded at 3831 (offset 33 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 227 (offset 2 lines).
Hunk #3 succeeded at 251 (offset 2 lines).
Hunk #4 succeeded at 350 (offset 8 lines).
Hunk #5 succeeded at 1465 (offset 103 lines).
Hunk #6 succeeded at 1814 (offset 108 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
Hunk #2 succeeded at 462 (offset 1 line).
Hunk #3 succeeded at 520 (offset 1 line).
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
copying file alsa-kernel/usb/caiaq/caiaq-input.c
patching file caiaq-input.c
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/usb/caiaq'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #11 succeeded at 1057 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
Hunk #9 succeeded at 732 (offset 1 line).
Hunk #10 succeeded at 745 (offset 1 line).
Hunk #11 succeeded at 815 (offset 1 line).
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/usb/usx2y'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/usb'
make[2]: Entering directory `/home/diazbeat/modules/alsa-driver/pcmcia'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/diazbeat/modules/alsa-driver/pcmcia/vx'
make[3]: Leaving directory `/home/diazbeat/modules/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/home/diazbeat/modules/alsa-driver/pcmcia'
make[1]: Leaving directory `/home/diazbeat/modules/alsa-driver'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/diazbeat/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/hwdep.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/memory_wrapper.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/memalloc.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/sgbuf.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/pcm.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/pcm_native.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/pcm_lib.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/pcm_timer.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/pcm_misc.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/pcm_memory.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/rtctimer.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/timer.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/wrappers.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/misc_driver.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/sound.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/init.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/memory.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/info.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/control.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/misc.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/device.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/isadma.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/sound_oss.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/info_oss.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/snd.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/snd-hwdep.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/snd-timer.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/snd-rtctimer.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/snd-pcm.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/snd-page-alloc.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/mixer_oss.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/pcm_oss.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/pcm_plugin.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/io.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/copy.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/linear.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/mulaw.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/route.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/oss/rate.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/oss/snd-mixer-oss.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/oss/snd-pcm-oss.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_device.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_midi_event.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_lock.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_clientmgr.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_memory.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_queue.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_fifo.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_prioq.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_timer.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_system.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_ports.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/seq_info.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/seq/snd-seq.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/seq/snd-seq-device.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/seq/snd-seq-midi-event.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_init.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_timer.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_ioctl.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_event.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_rw.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_synth.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_midi.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_readq.o
  CC [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/seq_oss_writeq.o
  LD [M]  /home/diazbeat/modules/alsa-driver/acore/seq/oss/snd-seq-oss.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/hda_intel.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/hda_codec.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/vmaster.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/hda_proc.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/hda_hwdep.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/hda_generic.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/patch_realtek.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/patch_cmedia.o
  CC [M]  /home/diazbeat/modules/alsa-driver/pci/hda/patch_analog.o
In file included from /home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:22,
                 from /home/diazbeat/modules/alsa-driver/pci/hda/patch_analog.c:3:
/home/diazbeat/modules/alsa-driver/include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/diazbeat/modules/alsa-driver/pci/hda/patch_analog.c:3:
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c: In function &#8216;ad198x_playback_pcm_open&#8217;:
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:155: error: too few arguments to function &#8216;snd_hda_multi_out_analog_open&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c: In function &#8216;ad198x_resume&#8217;:
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:329: error: implicit declaration of function &#8216;snd_hda_resume_ctls&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:331: error: implicit declaration of function &#8216;snd_hda_resume_spdif_out&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:333: error: implicit declaration of function &#8216;snd_hda_resume_spdif_in&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c: In function &#8216;ad198x_eapd_put&#8217;:
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:387: error: &#8216;struct hda_codec&#8217; has no member named &#8216;in_resume&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c: In function &#8216;ad1988_spdif_playback_source_put&#8217;:
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:1924: error: &#8216;struct hda_codec&#8217; has no member named &#8216;in_resume&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:1929: error: &#8216;struct hda_codec&#8217; has no member named &#8216;in_resume&#8217;
/home/diazbeat/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_analog.c:1935: error: &#8216;struct hda_codec&#8217; has no member named &#8216;in_resume&#8217;
make[4]: *** [/home/diazbeat/modules/alsa-driver/pci/hda/patch_analog.o] Error 1
make[3]: *** [/home/diazbeat/modules/alsa-driver/pci/hda] Error 2
make[2]: *** [/home/diazbeat/modules/alsa-driver/pci] Error 2
make[1]: *** [_module_/home/diazbeat/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2

```
sudo make install
```
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/diazbeat/modules/alsa-driver/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.24-16-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.24-16-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.24-16-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.24-16-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/diazbeat/modules/alsa-driver/acore'
mkdir -p /lib/modules/2.6.24-16-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.24-16-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/diazbeat/modules/alsa-driver/acore'
make: *** [install-modules] Error 1

```
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
```
cp: cannot stat `./modules/snd-hda-intel.ko': No such file or directory
```
sudo depmod -a (no output)

---

### Post by _aXXe_ on 2008-04-20
If you are using an Intel chip on a laptop or as in my case a desktop PC you might want to look at this page. Please read ALL the information before trying to make sure it fits your needs.


[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

### Post by bcasanov on 2008-04-20
Thank you for the link, _aXXe_!  I'm checking the information out right now.

---

### Post by bcasanov on 2008-04-20
I tried out the modified script which takes the latest rc version of alsa, and is for any kernel version.  This modified script was given in one of the comments.  Like another person who commented, I encountered some errors: ```
 dpkg: error processing /usr/src/alsa/alsa-lib-1.0.16/alsa-lib_1.0.16-cust-1_i386.deb (--install):
 trying to overwrite `/usr/share/alsa/alsa.conf', which is also in package libasound2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /usr/src/alsa/alsa-lib-1.0.16/alsa-lib_1.0.16-cust-1_i386.deb
```

---

### Post by bcasanov on 2008-04-20
Well, I'm going to sign off for tonight, as it's already very late, but tomorrow, I'm back to provide feedback about the progress of sound on this computer and to implement your advice.

I just wanted to say how much I appreciate all of your kind and patient help!

---

### Post by Hieronymus on 2008-04-20
Brenda,

I had the same problem with my sound unde ubuntu 7.10. I have the following hardware:

```

jeroen@jeroen-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

The solutions for me was quite simple:

```

apt-get install linux-sound-base alsa-base alsa-utils

```

The add the following line at the end of /etc/modprobe.d/alsa-base
*options snd-hda-intel model=auto*

Then do a reboot and all works fine. 

Maybe it'll do the trick for you as well. 

Regards, 

Jeroen

---

### Post by kroustou on 2008-04-20
thank you!:guitar:

---

### Post by bcasanov on 2008-04-20
Jeroen, oh my goodness, your suggestion worked!!!  Thank you!!!!!  Sorry for gushing, but I have been going without sound for so long that I thought I would never get it to work.  The sound came roaring back through the speakers loud and clear when I rebooted.   I appreciate everyone's help!  The kindness and patience of this community speaks for itself!

---

### Post by bcasanov on 2008-04-20
I have marked this thread as solved so that others with similar hardware can go through here and find the solution to their problem, if it applies.

---

### Post by Hieronymus on 2008-04-20
No problem, glad to be at service

Jeroen

---

### Post by RossAndGarfunkel on 2008-04-26
I'm having the same problem, but when I enter Jereon's code, I get

```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

The thing is that I am root. xP

i'm sure there's some basic detail i'm missing here.

---

### Post by casaduana on 2008-04-26
Not to take anything away from the excellent solution, try writing in terminal: "sudo apt-get install linux-sound-base alsa-base alsa-utils" (the quotes are to designate the beginning and end of what you write in terminal or console. The system will reply back and ask for your password, write it, hit enter and everything should work. Anytime you get the error you got try "sudo" before the command.

---

### Post by RossAndGarfunkel on 2008-04-26
> **casaduana said:**
> Not to take anything away from the excellent solution, try writing in terminal: "sudo apt-get install linux-sound-base alsa-base alsa-utils" (the quotes are to designate the beginning and end of what you write in terminal or console. The system will reply back and ask for your password, write it, hit enter and everything should work. Anytime you get the error you got try "sudo" before the command.

Seems something else is my problem...it just tells me that I all three of those files are up to date. Still no sound.

---

### Post by Glucklich on 2008-04-26
Hi, I have the same problem you had. But unfortunately, I don't get a thing about codes and stuff. Would you tell me, step by step, what I need to do to get the audio back? I really would appreciate one of those "for dummy's" book right now :P

---

### Post by Glucklich on 2008-04-26
Oh, I got it. I found a console, wrote the code, and it gave me the same thing as Garfunkel. No files for update, nothing. What else can be the problem? Really, we need help!

---

### Post by bcasanov on 2008-04-26
Hi Glucklich and Garfunkel!  I know how terrible it feels without sound.  I went through the same process, so let me help you guys out!  If the terminal tells you that those files are up to date, then you don't need to worry about the step of the process Jeroen said in which you install those programs.  You need to go to the next step in his instructions, and here's what you can do.  Copy and paste this code into the terminal: 

(If you have Ubuntu installed) > sudo gedit /etc/modprobe.d/alsa-base
(If you have Kubuntu installed) > sudo kate /etc/modprobe.d/alsa-base
This command will open a text editor with the configuration file for alsa-base.  Put the cursor at the end of the file, and hit Enter to put in a new line, then copy and paste this code: > options snd-hda-intel model=auto Save the file, and next, reboot your computer, and like me, you should hear the sound come back with a vengeance.  Let me know if this works for you.

---

### Post by RossAndGarfunkel on 2008-04-26
> **bcasanov said:**
> Hi Glucklich and Garfunkel!  I know how terrible it feels without sound.  I went through the same process, so let me help you guys out!  If the terminal tells you that those files are up to date, then you don't need to worry about the step of the process Jeroen said in which you install those programs.  You need to go to the next step in his instructions, and here's what you can do.  Copy and paste this code into the terminal: 

(If you have Ubuntu installed) 
(If you have Kubuntu installed) 
This command will open a text editor with the configuration file for alsa-base.  Put the cursor at the end of the file, and hit Enter to put in a new line, then copy and paste this code:  Save the file, and next, reboot your computer, and like me, you should hear the sound come back with a vengeance.  Let me know if this works for you.
Nope, still silent.

---

### Post by bcasanov on 2008-04-26
Oh, that really sucks!  Can you check if you have Surround muted?  If you have Surround muted, please unmute it and then check for sound.  Double-click on the volume control icon in the taskbar and unmute Surround by clicking on the little volume icon below the volume-adjusting lever if the icon shows a red X over it.  If Surround is not showing up as an option, go to Edit>>Preferences, and then select Surround from the list to have it show up.  Also, check if any other options, like PCM, are muted.

---

### Post by RossAndGarfunkel on 2008-04-26
> **bcasanov said:**
> Oh, that really sucks!  Can you check if you have Surround muted?  If you have Surround muted, please unmute it and then check for sound.  Double-click on the volume control icon in the taskbar and unmute Surround by clicking on the little volume icon below the volume-adjusting lever if the icon shows a red X over it.  If Surround is not showing up as an option, go to Edit>>Preferences, and then select Surround from the list to have it show up.  Also, check if any other options, like PCM, are muted.

Yep, checked it. It's not a volume problem.

And i'm on a laptop, so unless my speakers magically died at the same moment I installed 8.04, it's not a hardware problem.

---

### Post by bcasanov on 2008-04-27
Is the laptop a Dell 1420 or 1420N?  I have a 1420N.

---

### Post by RossAndGarfunkel on 2008-04-27
> **bcasanov said:**
> Is the laptop a Dell 1420 or 1420N?  I have a 1420N.

It's an Acer 5600.

---

### Post by bcasanov on 2008-04-27
What soundcard do you have?

---

### Post by RossAndGarfunkel on 2008-04-27
> **bcasanov said:**
> What soundcard do you have?

I'm not sure. I think it's some kind of Intel HD audio card.

---

### Post by bcasanov on 2008-04-27
Since you're not quite sure, please post here the result of the following command: > lspci | grep -i audio
This command tells the kind of audio device you have.

---

### Post by tiger88my on 2008-04-27
Hi,

This is my first time on ubuntu (or any linux system), I apologise for any dumb questions / statements in advance!

I seem to be having the same issue, i.e. no sound! I've tried everything that was suggested on the past few pages to no avail. 

I've entered the following command to get my soundcard type:

> lspci | grep -i audio 

and got the following result
> 05:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

Hope someone can help me! 

Thanks!

---

### Post by RossAndGarfunkel on 2008-04-27
> **bcasanov said:**
> Since you're not quite sure, please post here the result of the following command: 
This command tells the kind of audio device you have.

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

---

### Post by Cannaregio on 2008-04-28
Well, For what it is worth, here is how I solved my "[COLOR="Blue"]no sound at all[/COLOR]" problem, through a different approach, on a sony vaio with a INTEL 82801DB. 

Sound disappeared totally when updating to Hardy from Gutsy.
Tried many modifications (adding a line at the end of /etc/modprobe.d/alsa-base along the lines of options snd-hda-intel model=xyz etcetera), didn't work.
What worked was adding users (and myself) to the pulse groups (and restarting !!)

So go to System --> Administration --> Users and groups
Manage groups, unlock and choose properties for each pulse group.
Then add all the users that should have sound.
Then restart/reboot.

Hope it helps. It helped me!

Why the installation did not add users [COLOR="#0000ff"]by default[/COLOR] beats me.

---

### Post by gantellus on 2008-05-03
For me, the problem has not already been solved too :(

MB Asus P5B Plus...

```
mihail@mihail-desktop:~$ hwinfo --sound
27: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.kURRCMIOEo3
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "ASUSTeK HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "HD Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81ec 
  Revision: 0x02
  Memory Range: 0xfebf8000-0xfebfbfff (rw,non-prefetchable)
  IRQ: 22 (no events)
  Module Alias: "pci:v00008086d0000284Bsv00001043sd000081ECbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

None of the suggested solutions worked for me.. 7.04 and 7.10 worked perfect :(

---

