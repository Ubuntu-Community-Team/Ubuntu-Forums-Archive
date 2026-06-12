---
title: "updating alsa"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Anarchy965 on 2007-06-26
Supposedly, my soundcard (EMU 1212m) works with version 1.0.14 of alsa. Can someone explain how to update alsa to the latest version?

---

### Post by KIAaze on 2007-06-27
Go to [http://www.alsa-project.org/]("http://www.alsa-project.org/")

Download the latest tarballs (.tar.gz and .tar.bz2 files) of each of the things on the right (driver, library, utilities, etc).

[You probably don't need all of those, but since I don't know which one you need, just take them all]

Extract them.
You can use the following commands:
```
tar -xjvf file.tar.bz2
tar -xzvf file.tar.gz

```

Go into each of the created directories and execute the following commands there everytime:
```
./configure
make
make install

```

You might have to install some parts before the others.
Watch out for the error messages.

If there are some you don't understand, post them here.

---

### Post by Anarchy965 on 2007-06-27
How do I do excecute a command in a directory? Sorry, I'm very new with Linux.

---

### Post by KIAaze on 2007-06-27
You open a terminal, switch to the directory by typing cd <dir>, type in the command and press enter.
You really should read these articles:
[http://www.psychocats.net/ubuntu/terminal]("http://www.psychocats.net/ubuntu/terminal")
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")
[http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html")

Anyway, I just wrote a script (not yet tested), which hopefully should work:

_installalsa.sh:_
```
#! /bin/bash
#shellscript to install alsa v1.0.14, not fully tested

#create alsa build directory and go there
mkdir ~/alsa
cd ~/alsa

#download all files
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2

#extract, configure, compile and install them
for f in *.tar.bz2;
do
	tar -xjvf $f
        base=`basename $f .tar.bz2`
        cd base
        ./configure
        make
        make install
done

```

Open a text editor, copy paste the script into it and save it as "installalsa.sh" in your home directory.
Open a terminal and type the following commands:
```
chmod 755 ~/installalsa.sh
cd ~
./installalsa.sh

```

If there are error messages in the output, post them here.

---

### Post by KIAaze on 2007-06-27
Oops, there's an error in my script.
It's "tar -xjvf $f", not "tar -xjvf f".

I corrected it in my previous post. Copy the new version.

---

### Post by Anarchy965 on 2007-06-27
I'm trying the script now. thanks.

---

### Post by Anarchy965 on 2007-06-27
It didn't work. Can someone else help us out?

---

### Post by KIAaze on 2007-06-27
I just realized I forgot something else: "cd .." to go back in the main alsa build directory.

Here's the new version:

```
#! /bin/bash
#shellscript to install alsa, not fully tested

#create alsa build directory and go there
mkdir ~/alsa
cd ~/alsa

#download all files
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2

#remove older error.log
rm ~/alsa/error.log

#extract, configure, compile and install them
for f in *.tar.bz2;
do
	tar -xjvf $f
        base=`basename $f .tar.bz2`
        cd base
        echo "==configure $base==" >>~/alsa/error.log
        ./configure 2>>~/alsa/error.log
        echo "==make $base==" >>~/alsa/error.log
        make 2>>~/alsa/error.log
        echo "==install $base==" >>~/alsa/error.log
        make install 2>>~/alsa/error.log
        cd ..
done

```

Unfortunately, I'm not on my own PC with Ubuntu right now, so I can't really test it fully.
(I'm getting some error messages with the script here, but since I don't have root permissions it will be hard to solve.)

Please post the error messages you get here.
I even added an error log generation to the script.
So you can just post the output of the following commands after the script completes:
```
cat ~/alsa/error.log

```

---

### Post by BHelts on 2007-06-27
you can check out [this post.]("http://ubuntuforums.org/showthread.php?t=475013")

look at the post at the bottom.  step by step how to update all of ALSA.  once that is done, it may be required that you update your /etc/modprobe.d/alsa-base to fit your sound card.

---

### Post by Anarchy965 on 2007-06-27
Ok I tried the script. here's the log I got when I put in ```
cat ~/alsa/error.log
```

```
alsa-driver-1.0.14/alsa-kernel/usb/caiaq/caiaq-device.c
alsa-driver-1.0.14/alsa-kernel/usb/caiaq/caiaq-input.h
alsa-driver-1.0.14/alsa-kernel/usb/caiaq/caiaq-midi.c
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usbus428ctldefs.h
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usx2y.h
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usbusx2y.h
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/Makefile
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usbusx2yaudio.c
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usX2Yhwdep.h
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usx2yhwdeppcm.h
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usX2Yhwdep.c
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
alsa-driver-1.0.14/alsa-kernel/usb/usx2y/usbusx2y.c
alsa-driver-1.0.14/alsa-kernel/core/
alsa-driver-1.0.14/alsa-kernel/core/control.c
alsa-driver-1.0.14/alsa-kernel/core/info.c
alsa-driver-1.0.14/alsa-kernel/core/pcm_misc.c
alsa-driver-1.0.14/alsa-kernel/core/rawmidi.c
alsa-driver-1.0.14/alsa-kernel/core/oss/
alsa-driver-1.0.14/alsa-kernel/core/oss/plugin_ops.h
alsa-driver-1.0.14/alsa-kernel/core/oss/mulaw.c
alsa-driver-1.0.14/alsa-kernel/core/oss/mixer_oss.c
alsa-driver-1.0.14/alsa-kernel/core/oss/linear.c
alsa-driver-1.0.14/alsa-kernel/core/oss/io.c
alsa-driver-1.0.14/alsa-kernel/core/oss/pcm_oss.c
alsa-driver-1.0.14/alsa-kernel/core/oss/pcm_plugin.c
alsa-driver-1.0.14/alsa-kernel/core/oss/Makefile
alsa-driver-1.0.14/alsa-kernel/core/oss/route.c
alsa-driver-1.0.14/alsa-kernel/core/oss/rate.c
alsa-driver-1.0.14/alsa-kernel/core/oss/pcm_plugin.h
alsa-driver-1.0.14/alsa-kernel/core/oss/copy.c
alsa-driver-1.0.14/alsa-kernel/core/seq/
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_memory.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_clientmgr.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_midi_event.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_info.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_ioctl.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_synth.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_readq.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_rw.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_init.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_readq.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_writeq.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_synth.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/Makefile
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_timer.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_midi.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_midi.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_event.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_writeq.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_event.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_device.h
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss_timer.c
alsa-driver-1.0.14/alsa-kernel/core/seq/oss/seq_oss.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_compat.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_info.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_midi_emul.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_timer.h
alsa-driver-1.0.14/alsa-kernel/core/seq/instr/
alsa-driver-1.0.14/alsa-kernel/core/seq/instr/Makefile
alsa-driver-1.0.14/alsa-kernel/core/seq/instr/ainstr_iw.c
alsa-driver-1.0.14/alsa-kernel/core/seq/instr/ainstr_simple.c
alsa-driver-1.0.14/alsa-kernel/core/seq/instr/ainstr_gf1.c
alsa-driver-1.0.14/alsa-kernel/core/seq/instr/ainstr_fm.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_system.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_prioq.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_lock.c
alsa-driver-1.0.14/alsa-kernel/core/seq/Makefile
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_queue.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_memory.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_fifo.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_queue.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_fifo.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_virmidi.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_prioq.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_device.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_timer.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_ports.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_system.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_midi.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_clientmgr.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_dummy.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_lock.h
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_ports.c
alsa-driver-1.0.14/alsa-kernel/core/seq/seq_instr.c
alsa-driver-1.0.14/alsa-kernel/core/misc.c
alsa-driver-1.0.14/alsa-kernel/core/memory.c
alsa-driver-1.0.14/alsa-kernel/core/pcm_memory.c
alsa-driver-1.0.14/alsa-kernel/core/pcm_timer.c
alsa-driver-1.0.14/alsa-kernel/core/sound.c
alsa-driver-1.0.14/alsa-kernel/core/pcm.c
alsa-driver-1.0.14/alsa-kernel/core/Makefile
alsa-driver-1.0.14/alsa-kernel/core/memalloc.c
alsa-driver-1.0.14/alsa-kernel/core/device.c
alsa-driver-1.0.14/alsa-kernel/core/control_compat.c
alsa-driver-1.0.14/alsa-kernel/core/isadma.c
alsa-driver-1.0.14/alsa-kernel/core/sgbuf.c
alsa-driver-1.0.14/alsa-kernel/core/pcm_native.c
alsa-driver-1.0.14/alsa-kernel/core/pcm_compat.c
alsa-driver-1.0.14/alsa-kernel/core/init.c
alsa-driver-1.0.14/alsa-kernel/core/info_oss.c
alsa-driver-1.0.14/alsa-kernel/core/Kconfig
alsa-driver-1.0.14/alsa-kernel/core/pcm_lib.c
alsa-driver-1.0.14/alsa-kernel/core/hwdep.c
alsa-driver-1.0.14/alsa-kernel/core/timer.c
alsa-driver-1.0.14/alsa-kernel/core/sound_oss.c
alsa-driver-1.0.14/alsa-kernel/core/rtctimer.c
alsa-driver-1.0.14/alsa-kernel/core/timer_compat.c
alsa-driver-1.0.14/alsa-kernel/core/hwdep_compat.c
alsa-driver-1.0.14/alsa-kernel/core/rawmidi_compat.c
alsa-driver-1.0.14/alsa-kernel/mips/
alsa-driver-1.0.14/alsa-kernel/mips/Makefile
alsa-driver-1.0.14/alsa-kernel/mips/Kconfig
alsa-driver-1.0.14/alsa-kernel/mips/au1x00.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/
alsa-driver-1.0.14/alsa-kernel/pcmcia/Makefile
alsa-driver-1.0.14/alsa-kernel/pcmcia/Kconfig
alsa-driver-1.0.14/alsa-kernel/pcmcia/vx/
alsa-driver-1.0.14/alsa-kernel/pcmcia/vx/vxpocket.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/vx/Makefile
alsa-driver-1.0.14/alsa-kernel/pcmcia/vx/vxpocket.h
alsa-driver-1.0.14/alsa-kernel/pcmcia/vx/vxp_mixer.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/vx/vxp_ops.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/Makefile
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_core.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.h
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c
alsa-driver-1.0.14/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_pcm.c
alsa-driver-1.0.14/alsa-kernel/sparc/
alsa-driver-1.0.14/alsa-kernel/sparc/dbri.c
alsa-driver-1.0.14/alsa-kernel/sparc/cs4231.c
alsa-driver-1.0.14/alsa-kernel/sparc/Makefile
alsa-driver-1.0.14/alsa-kernel/sparc/amd7930.c
alsa-driver-1.0.14/alsa-kernel/sparc/Kconfig
alsa-driver-1.0.14/alsa-kernel/Kconfig
alsa-driver-1.0.14/alsa-kernel/sound_firmware.c
alsa-driver-1.0.14/alsa-kernel/Documentation/
alsa-driver-1.0.14/alsa-kernel/Documentation/Joystick.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/hda_codec.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/clocking.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/overview.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/codec.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/dapm.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/pops_clicks.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/machine.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/DAI.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/soc/platform.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/Bt87x.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/VIA82xx-mixer.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/hdspm.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/ControlNames.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/serial-u16550.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/seq_oss.html
alsa-driver-1.0.14/alsa-kernel/Documentation/emu10k1-jack.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/OSS-Emulation.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/CMIPCI.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/Procfile.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/Audigy-mixer.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/DocBook/
alsa-driver-1.0.14/alsa-kernel/Documentation/DocBook/alsa-driver-api.tmpl
alsa-driver-1.0.14/alsa-kernel/Documentation/DocBook/writing-an-alsa-driver.tmpl
alsa-driver-1.0.14/alsa-kernel/Documentation/Audiophile-Usb.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/ALSA-Configuration.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/MIXART.txt
alsa-driver-1.0.14/alsa-kernel/Documentation/SB-Live-mixer.txt
alsa-driver-1.0.14/alsa-kernel/sound_core.c
alsa-driver-1.0.14/alsa-kernel/sh/
alsa-driver-1.0.14/alsa-kernel/sh/aica.c
alsa-driver-1.0.14/alsa-kernel/sh/aica.h
alsa-driver-1.0.14/alsa-kernel/sh/Makefile
alsa-driver-1.0.14/alsa-kernel/sh/Kconfig
alsa-driver-1.0.14/alsa-kernel/include/
alsa-driver-1.0.14/alsa-kernel/include/soc.h
alsa-driver-1.0.14/alsa-kernel/include/sb16_csp.h
alsa-driver-1.0.14/alsa-kernel/include/asoundef.h
alsa-driver-1.0.14/alsa-kernel/include/seq_kernel.h
alsa-driver-1.0.14/alsa-kernel/include/initval.h
alsa-driver-1.0.14/alsa-kernel/include/cs4231.h
alsa-driver-1.0.14/alsa-kernel/include/ak4xxx-adda.h
alsa-driver-1.0.14/alsa-kernel/include/emux_synth.h
alsa-driver-1.0.14/alsa-kernel/include/seq_virmidi.h
alsa-driver-1.0.14/alsa-kernel/include/hwdep.h
alsa-driver-1.0.14/alsa-kernel/include/core.h
alsa-driver-1.0.14/alsa-kernel/include/wavefront.h
alsa-driver-1.0.14/alsa-kernel/include/opl4.h
alsa-driver-1.0.14/alsa-kernel/include/hdsp.h
alsa-driver-1.0.14/alsa-kernel/include/pcm.h
alsa-driver-1.0.14/alsa-kernel/include/util_mem.h
alsa-driver-1.0.14/alsa-kernel/include/seq_oss.h
alsa-driver-1.0.14/alsa-kernel/include/ainstr_iw.h
alsa-driver-1.0.14/alsa-kernel/include/emux_legacy.h
alsa-driver-1.0.14/alsa-kernel/include/seq_oss_legacy.h
alsa-driver-1.0.14/alsa-kernel/include/Kbuild
alsa-driver-1.0.14/alsa-kernel/include/minors.h
alsa-driver-1.0.14/alsa-kernel/include/emu8000.h
alsa-driver-1.0.14/alsa-kernel/include/wavefront_fx.h
alsa-driver-1.0.14/alsa-kernel/include/ac97_codec.h
alsa-driver-1.0.14/alsa-kernel/include/pt2258.h
alsa-driver-1.0.14/alsa-kernel/include/sfnt_info.h
alsa-driver-1.0.14/alsa-kernel/include/cs8403.h
alsa-driver-1.0.14/alsa-kernel/include/seq_midi_event.h
alsa-driver-1.0.14/alsa-kernel/include/ainstr_fm.h
alsa-driver-1.0.14/alsa-kernel/include/uda1341.h
alsa-driver-1.0.14/alsa-kernel/include/pcm-indirect.h
alsa-driver-1.0.14/alsa-kernel/include/seq_midi_emul.h
alsa-driver-1.0.14/alsa-kernel/include/trident.h
alsa-driver-1.0.14/alsa-kernel/include/cs46xx_dsp_scb_types.h
alsa-driver-1.0.14/alsa-kernel/include/soc-dapm.h
alsa-driver-1.0.14/alsa-kernel/include/ak4117.h
alsa-driver-1.0.14/alsa-kernel/include/rawmidi.h
alsa-driver-1.0.14/alsa-kernel/include/ainstr_gf1.h
alsa-driver-1.0.14/alsa-kernel/include/memalloc.h
alsa-driver-1.0.14/alsa-kernel/include/asound_fm.h
alsa-driver-1.0.14/alsa-kernel/include/ainstr_simple.h
alsa-driver-1.0.14/alsa-kernel/include/ad1848.h
alsa-driver-1.0.14/alsa-kernel/include/i2c.h
alsa-driver-1.0.14/alsa-kernel/include/emu10k1.h
alsa-driver-1.0.14/alsa-kernel/include/timer.h
alsa-driver-1.0.14/alsa-kernel/include/ak4531_codec.h
alsa-driver-1.0.14/alsa-kernel/include/hdspm.h
alsa-driver-1.0.14/alsa-kernel/include/pcm_params.h
alsa-driver-1.0.14/alsa-kernel/include/emu8000_reg.h
alsa-driver-1.0.14/alsa-kernel/include/mpu401.h
alsa-driver-1.0.14/alsa-kernel/include/cs46xx_dsp_spos.h
alsa-driver-1.0.14/alsa-kernel/include/cs46xx.h
alsa-driver-1.0.14/alsa-kernel/include/mixer_oss.h
alsa-driver-1.0.14/alsa-kernel/include/ymfpci.h
alsa-driver-1.0.14/alsa-kernel/include/snd_wavefront.h
alsa-driver-1.0.14/alsa-kernel/include/tlv.h
alsa-driver-1.0.14/alsa-kernel/include/seq_device.h
alsa-driver-1.0.14/alsa-kernel/include/ak4114.h
alsa-driver-1.0.14/alsa-kernel/include/cs8427.h
alsa-driver-1.0.14/alsa-kernel/include/sb.h
alsa-driver-1.0.14/alsa-kernel/include/pcm_oss.h
alsa-driver-1.0.14/alsa-kernel/include/opl3.h
alsa-driver-1.0.14/alsa-kernel/include/es1688.h
alsa-driver-1.0.14/alsa-kernel/include/control.h
alsa-driver-1.0.14/alsa-kernel/include/driver.h
alsa-driver-1.0.14/alsa-kernel/include/emu10k1_synth.h
alsa-driver-1.0.14/alsa-kernel/include/vx_core.h
alsa-driver-1.0.14/alsa-kernel/include/ad1816a.h
alsa-driver-1.0.14/alsa-kernel/include/sscape_ioctl.h
alsa-driver-1.0.14/alsa-kernel/include/asequencer.h
alsa-driver-1.0.14/alsa-kernel/include/gus.h
alsa-driver-1.0.14/alsa-kernel/include/info.h
alsa-driver-1.0.14/alsa-kernel/include/soundfont.h
alsa-driver-1.0.14/alsa-kernel/include/tea575x-tuner.h
alsa-driver-1.0.14/alsa-kernel/include/seq_instr.h
alsa-driver-1.0.14/alsa-kernel/include/asound.h
alsa-driver-1.0.14/alsa-kernel/include/cs46xx_dsp_task_types.h
alsa-driver-1.0.14/alsa-kernel/include/tea6330t.h
alsa-driver-1.0.14/usb/
alsa-driver-1.0.14/usb/usbaudio.inc
alsa-driver-1.0.14/usb/usbaudio.patch
alsa-driver-1.0.14/usb/usbcompat.c
alsa-driver-1.0.14/usb/Makefile
alsa-driver-1.0.14/usb/usbmidi.patch
alsa-driver-1.0.14/usb/caiaq/
alsa-driver-1.0.14/usb/caiaq/caiaq-input.c
alsa-driver-1.0.14/usb/caiaq/Makefile
alsa-driver-1.0.14/usb/caiaq/caiaq-audio.c
alsa-driver-1.0.14/usb/caiaq/caiaq-device.c
alsa-driver-1.0.14/usb/caiaq/caiaq-midi.c
alsa-driver-1.0.14/usb/usbmidi.inc1
alsa-driver-1.0.14/usb/usbmixer.patch
alsa-driver-1.0.14/usb/usbaudio.inc1
alsa-driver-1.0.14/usb/usx2y/
alsa-driver-1.0.14/usb/usx2y/usx2yhwdeppcm.patch
alsa-driver-1.0.14/usb/usx2y/usbusx2y.patch
alsa-driver-1.0.14/usb/usx2y/usX2Yhwdep.patch
alsa-driver-1.0.14/usb/usx2y/Makefile
alsa-driver-1.0.14/usb/usx2y/usbusx2yaudio.patch
alsa-driver-1.0.14/usb/usbmidi.inc
alsa-driver-1.0.14/version
alsa-driver-1.0.14/support/
alsa-driver-1.0.14/support/isapnp/
alsa-driver-1.0.14/support/isapnp/isapnp_proc.c
alsa-driver-1.0.14/support/isapnp/isapnp.txt
alsa-driver-1.0.14/support/isapnp/Makefile
alsa-driver-1.0.14/support/isapnp/isapnp.h
alsa-driver-1.0.14/support/isapnp/isapnp_test.c
alsa-driver-1.0.14/support/isapnp/isapnp_quirks.c
alsa-driver-1.0.14/support/isapnp/isapnp.c
alsa-driver-1.0.14/support/pnp/
alsa-driver-1.0.14/support/pnp/pnp.h
alsa-driver-1.0.14/support/pnp/Makefile
alsa-driver-1.0.14/support/pnp/pnp.c
alsa-driver-1.0.14/support/Makefile
alsa-driver-1.0.14/doc/
alsa-driver-1.0.14/doc/SOUNDCARDS
alsa-driver-1.0.14/doc/README.1st
alsa-driver-1.0.14/doc/INSTALL.asihpi-alsa
alsa-driver-1.0.14/doc/Makefile
alsa-driver-1.0.14/doc/README.riptide
alsa-driver-1.0.14/doc/serialmidi.txt
alsa-driver-1.0.14/doc/DocBook/
alsa-driver-1.0.14/doc/DocBook/Makefile
alsa-driver-1.0.14/doc/README.asihpi-alsa
alsa-driver-1.0.14/mips/
alsa-driver-1.0.14/mips/Makefile
alsa-driver-1.0.14/mips/au1x00.c
alsa-driver-1.0.14/pcmcia/
alsa-driver-1.0.14/pcmcia/Makefile
alsa-driver-1.0.14/pcmcia/vx/
alsa-driver-1.0.14/pcmcia/vx/vxpocket.conf
alsa-driver-1.0.14/pcmcia/vx/vxpocket.c
alsa-driver-1.0.14/pcmcia/vx/Makefile
alsa-driver-1.0.14/pcmcia/vx/vxpocket-2.6.16.c
alsa-driver-1.0.14/pcmcia/vx/vxpocket.h
alsa-driver-1.0.14/pcmcia/vx/vxp_mixer.c
alsa-driver-1.0.14/pcmcia/vx/vxp_ops.c
alsa-driver-1.0.14/pcmcia/vx/vx_entry.inc1
alsa-driver-1.0.14/pcmcia/vx/vxpocket_old.c
alsa-driver-1.0.14/pcmcia/vx/vx_entry.inc
alsa-driver-1.0.14/pcmcia/pdaudiocf/
alsa-driver-1.0.14/pcmcia/pdaudiocf/Makefile
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf.c
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf_core.c
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf.conf
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf_old.c
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf.h
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf_irq.c
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf_pcm.c
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf.patch
alsa-driver-1.0.14/pcmcia/pdaudiocf/pdaudiocf-2.6.16.c
alsa-driver-1.0.14/cvscompile
alsa-driver-1.0.14/sparc/
alsa-driver-1.0.14/sparc/dbri.c
alsa-driver-1.0.14/sparc/cs4231.c
alsa-driver-1.0.14/sparc/Makefile
alsa-driver-1.0.14/sparc/amd7930.c
alsa-driver-1.0.14/README
alsa-driver-1.0.14/kconfig-vers
alsa-driver-1.0.14/utils/
alsa-driver-1.0.14/utils/alsa-driver.spec.in
alsa-driver-1.0.14/utils/module-options
alsa-driver-1.0.14/utils/kredirect.c
alsa-driver-1.0.14/utils/alsasound.posix.in
alsa-driver-1.0.14/utils/buildrpm
alsa-driver-1.0.14/utils/link-modules
alsa-driver-1.0.14/utils/insert
alsa-driver-1.0.14/utils/convert_isapnp_ids
alsa-driver-1.0.14/utils/patches/
alsa-driver-1.0.14/utils/patches/patch.Makefile.top.2.4.0-test10
alsa-driver-1.0.14/utils/patches/pcsp-kernel-2.6.15-01.diff
alsa-driver-1.0.14/utils/patches/patch.Makefile.2.4.1
alsa-driver-1.0.14/utils/patches/rtc-2.4.16.patch
alsa-driver-1.0.14/utils/patches/rtc-2.2.16.dif
alsa-driver-1.0.14/utils/patches/soundcore.2.4.patch
alsa-driver-1.0.14/utils/patches/pcsp-kernel-2.6.19-01.diff
alsa-driver-1.0.14/utils/patches/pcsp-kernel-2.6.14-01.diff
alsa-driver-1.0.14/utils/patches/rtc-2.4.20.patch
alsa-driver-1.0.14/utils/patches/patch.mem.c.2.3.34
alsa-driver-1.0.14/utils/patches/byteswap.h
alsa-driver-1.0.14/utils/patches/pcsp-kernel-2.6.17-03.diff
alsa-driver-1.0.14/utils/patches/pnp-suspend-2.6.15-rc1.diff
alsa-driver-1.0.14/utils/patches/rtc-2.4.9.dif
alsa-driver-1.0.14/utils/patches/patch.Makefile.top.2.4.1
alsa-driver-1.0.14/utils/patches/patch.Makefile.2.4.0-test10
alsa-driver-1.0.14/utils/patches/rtc-2.4.23.patch
alsa-driver-1.0.14/utils/patches/patch.Makefile.2.4.2
alsa-driver-1.0.14/utils/patches/soundcore.2.4.20.patch
alsa-driver-1.0.14/utils/patches/pcsp-kernel-2.6.18-01.diff
alsa-driver-1.0.14/utils/patches/rtc-2.4.25.patch
alsa-driver-1.0.14/utils/patches/rtc-suse-7.0-2.2.16.dif
alsa-driver-1.0.14/utils/Makefile
alsa-driver-1.0.14/utils/buildrpm.in
alsa-driver-1.0.14/utils/alsasound
alsa-driver-1.0.14/utils/old/
alsa-driver-1.0.14/utils/old/export-symbols.in
alsa-driver-1.0.14/utils/old/export-symbols.perl
alsa-driver-1.0.14/utils/mod-deps
alsa-driver-1.0.14/utils/patch-alsa
alsa-driver-1.0.14/utils/mod-deps.c
alsa-driver-1.0.14/utils/alsasound.in
alsa-driver-1.0.14/utils/oss-move
alsa-driver-1.0.14/utils/remove
alsa-driver-1.0.14/utils/alsasound.posix
alsa-driver-1.0.14/modules/
alsa-driver-1.0.14/modules/.keepme
alsa-driver-1.0.14/aclocal.m4
alsa-driver-1.0.14/SUPPORTED_KERNELS
alsa-driver-1.0.14/sh/
alsa-driver-1.0.14/sh/aica.c
alsa-driver-1.0.14/sh/Makefile
alsa-driver-1.0.14/include/
alsa-driver-1.0.14/include/compat_cs.h
alsa-driver-1.0.14/include/hal2.h
alsa-driver-1.0.14/include/compat_64.h
alsa-driver-1.0.14/include/i2c-id_compat.h
alsa-driver-1.0.14/include/isa_compat.h
alsa-driver-1.0.14/include/config1.h.in
alsa-driver-1.0.14/include/platform_device_compat.h
alsa-driver-1.0.14/include/syscalls_26.h
alsa-driver-1.0.14/include/pci_ids_compat.h.in
alsa-driver-1.0.14/include/i2c-id_compat.h.in
alsa-driver-1.0.14/include/asm/
alsa-driver-1.0.14/include/Makefile
alsa-driver-1.0.14/include/adriver.h
alsa-driver-1.0.14/include/firmware_compat.h
alsa-driver-1.0.14/include/autoconf-extra.h.in
alsa-driver-1.0.14/include/autoconf-extra.h
alsa-driver-1.0.14/include/old/
alsa-driver-1.0.14/include/old/gf1.h
alsa-driver-1.0.14/include/old/ultra_todo.h
alsa-driver-1.0.14/include/version.h.in
alsa-driver-1.0.14/include/config.h
alsa-driver-1.0.14/include/media/
alsa-driver-1.0.14/include/version.h
alsa-driver-1.0.14/include/modules/
alsa-driver-1.0.14/include/modules/.keepme
alsa-driver-1.0.14/include/config.h.in
alsa-driver-1.0.14/include/config1.h
alsa-driver-1.0.14/include/pci_ids_compat.h
alsa-driver-1.0.14/include/uda1380.h
alsa-driver-1.0.14/include/linux/
alsa-driver-1.0.14/include/latency_compat.h
alsa-driver-1.0.14/include/bitmap_compat.h
alsa-driver-1.0.14/include/compat_22.h
alsa-driver-1.0.14/include/mutex_compat.h
alsa-driver-1.0.14/include/err_compat.h
alsa-driver-1.0.14/include/device_compat.h
alsa-driver-1.0.14/include/ppc-prom-hack.h
alsa-driver-1.0.14/COPYING
alsa-driver-1.0.14/Rules.make1
alsa-driver-1.0.14/install-sh
alsa-driver-1.0.14/WARNING
alsa-driver-1.0.14/Rules.make
alsa-driver-1.0.14/FAQ
alsa-driver-1.0.14/CARDS-STATUS
./installalsa.sh: line 24: cd: base: No such file or directory
tar: alsa-firmware-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./installalsa.sh: line 24: cd: base: No such file or directory
tar: alsa-lib-1.0.14a.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./installalsa.sh: line 24: cd: base: No such file or directory
tar: alsa-plugins-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./installalsa.sh: line 24: cd: base: No such file or directory
tar: alsa-tools-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./installalsa.sh: line 24: cd: base: No such file or directory
tar: alsa-utils-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./installalsa.sh: line 24: cd: base: No such file or directory
alex@ubuntu-desktop:~$ cat ~/alsa/error.log
==configure alsa-driver-1.0.14==
./installalsa.sh: line 26: ./configure: No such file or directory
==make alsa-driver-1.0.14==
make: *** No targets specified and no makefile found.  Stop.
==install alsa-driver-1.0.14==
make: *** No rule to make target `install'.  Stop.
==configure alsa-firmware-1.0.14==
./installalsa.sh: line 26: ./configure: No such file or directory
==make alsa-firmware-1.0.14==
make: *** No targets specified and no makefile found.  Stop.
==install alsa-firmware-1.0.14==
make: *** No rule to make target `install'.  Stop.
==configure alsa-lib-1.0.14a==
./installalsa.sh: line 26: ./configure: No such file or directory
==make alsa-lib-1.0.14a==
make: *** No targets specified and no makefile found.  Stop.
==install alsa-lib-1.0.14a==
make: *** No rule to make target `install'.  Stop.
==configure alsa-plugins-1.0.14==
./installalsa.sh: line 26: ./configure: No such file or directory
==make alsa-plugins-1.0.14==
make: *** No targets specified and no makefile found.  Stop.
==install alsa-plugins-1.0.14==
make: *** No rule to make target `install'.  Stop.
==configure alsa-tools-1.0.14==
./installalsa.sh: line 26: ./configure: No such file or directory
==make alsa-tools-1.0.14==
make: *** No targets specified and no makefile found.  Stop.
==install alsa-tools-1.0.14==
make: *** No rule to make target `install'.  Stop.
==configure alsa-utils-1.0.14==
./installalsa.sh: line 26: ./configure: No such file or directory
==make alsa-utils-1.0.14==
make: *** No targets specified and no makefile found.  Stop.
==install alsa-utils-1.0.14==
make: *** No rule to make target `install'.  Stop.

```

---

### Post by KIAaze on 2007-06-27
Argh, I just saw two other errors and made one improvement.
Well, you are currently witnessing a live script creation and debugging. ^^

I would suggest trying out BHelts' suggestion for now.
[B][but don't use sudo for ./configure and make. Only for make install!]
[/B]

If his solution doesn't work, here's the latest version of my script (which now only downloads if the files are missing to save time):
```
#! /bin/bash
#shellscript to install alsa, not fully tested

#create alsa build directory and go there
mkdir ~/alsa
cd ~/alsa

#download all files
wget -nc ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2

#remove older error.log
rm ~/alsa/error.log

#extract, configure, compile and install them
for f in *.tar.bz2;
do
	tar -xjvf $f
        base=`basename $f .tar.bz2`
        cd $base
        echo "==configure $base==" >>~/alsa/error.log
        ./configure 2>>~/alsa/error.log
        echo "==make $base==" >>~/alsa/error.log
        make 2>>~/alsa/error.log
        echo "==install $base==" >>~/alsa/error.log
        sudo make install 2>>~/alsa/error.log
        cd ..
done

```

---

### Post by KIAaze on 2007-06-27
Added (and removed) some stuff after reading BHelts tutorial, so that it hopefully works this time:

[delete all the tar.bz2 files in ~/alsa before, so that the script doesn't try to compile useless alsa files]

```
#! /bin/bash
#shellscript to install alsa, not fully tested

#install dependencies
sudo apt-get install build-essential ncurses-dev
sudo apt-get install linux-headers-`uname -r`

#create alsa build directory and go there
mkdir ~/alsa
cd ~/alsa

#download all files
wget -nc ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2

#remove older error.log
rm ~/alsa/error.log

#extract, configure, compile and install them
for f in *.tar.bz2;
do
	tar -xjvf $f
        base=`basename $f .tar.bz2`
        cd $base
        echo "==configure $base==" >>~/alsa/error.log
        ./configure 2>>~/alsa/error.log
        echo "==make $base==" >>~/alsa/error.log
        make 2>>~/alsa/error.log
        echo "==install $base==" >>~/alsa/error.log
        sudo make install 2>>~/alsa/error.log
        cd ..
done

```

---

### Post by Scarath on 2007-06-28
Hi
I was having sound problems and as i new to linux installing things is still a bit tricky for me. This code was a great help and seemed to work well, everything got downloaded and installed i think ....... however my sound troubles persist, must be something else lol.

---

### Post by KIAaze on 2007-06-28
No error message when it ran and none in error.log? :D
Please tell me, I wanna know!

If there are no errors in the script, I think I'll add it to the wiki. (I'll try it on my own PC as soon as I can.)
Another improvement would be to find the latest stable version automatically. :)
(or at least so that you can enter it manually)

---

### Post by okkie on 2007-08-28
i do not know who to thank now but thanks anyway.after this alsa update/install my sound is back to normal.
i can in fact not even find the thread.too old i suppose.forum too complicated

---

### Post by dwrunyon on 2007-09-19
Thanks for the script!

- How do you change the module to your card once you've updated ALSA? My card (E-MU 1820) was not supported in the last ALSA, is supposed to be in this new one, but I don't know how to set it.

- I have already re-booted after the update, but Synaptic still shows the last version of ALSA?

Much appreciated,
Daniel

---

### Post by KIAaze on 2007-09-20
> - How do you change the module to your card once you've updated ALSA? My card (E-MU 1820) was not supported in the last ALSA, is supposed to be in this new one, but I don't know how to set it.


I don't know. :/
Does the sound work or not? Or do you just want to use a specific sound card for it?

Have you tried out the instructions here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I just noticed that it uses
> sudo ./configure --with-cards=hda-intel
and not simply "./configure".
So maybe it's better to follow the intructions there than to use my script.


> - I have already re-booted after the update, but Synaptic still shows the last version of ALSA?


I'm not sure, but I think synaptic doesn't take into account installations made from source (because this is what the script does).
A solution might be to use "checkinstall" instead of "make install".
This creates a .deb package after installation which can be reused and also makes sure that everything is correct in synaptics.
(but you need to install "checkinstall" from synaptic first eventually)

Here's the same script as previously with the checkinstall method:
```
#! /bin/bash
#shellscript to install alsa, not fully tested

#install dependencies
sudo apt-get install build-essential ncurses-dev
sudo apt-get install linux-headers-`uname -r`

#create alsa build directory and go there
mkdir ~/alsa
cd ~/alsa

#download all files
wget -nc ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.14.tar.bz2
wget -nc ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/pyalsa/pyalsa-1.0.14.tar.bz2
#wget -nc ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2

#remove older error.log
rm ~/alsa/error.log

#extract, configure, compile and install them
for f in *.tar.bz2;
do
	tar -xjvf $f
        base=`basename $f .tar.bz2`
        cd $base
        echo "==configure $base==" >>~/alsa/error.log
        ./configure 2>>~/alsa/error.log
        echo "==make $base==" >>~/alsa/error.log
        make 2>>~/alsa/error.log
        echo "==install $base==" >>~/alsa/error.log
        sudo checkinstall 2>>~/alsa/error.log
        cd ..
done

```

---

### Post by dwrunyon on 2007-10-01
Thank you very much for your helping!

Nope, sound just doesn't work. I've had to give it up (Linux) for the time being because I just don't have the free time to tinker endlessly. I think that within another few versions my present hardware will be better supported... the EMU cards are a real hangup as is. I've seen where the fellow who added the support to ALSA has only gotten some very, very basic functionality, but I need to be able to use a LOT of the functionality to accomplish what I am doing (multitrack recording/audio editing).

Again, thank you very much... I will mark this in case I decide to tinker some more!

---

