---
title: "Soundcard Drivers"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2006-07-02
Right, I've noticed that I've been having sound problems since I've updated to Dapper that seem to be going on and off. At first they wern't too bad but they started to get a bit anoying after a few weeks. Earlier today I had the genious idea that it was my sound card so I decided to try and install the latest driver. My built in sound is Realtek AC97 so I go to the website and download it. I decide that since I'm not that great in Linux I'll use the provided install script. So off into my terminal I go, I then cd into the directory and run ./install. I get a load of cannot create directory errors so I switch into root then run it. And now my sound card is completly undetected and I still can't install it. 

I also know how to fix my soundproblems thanks to [this](http://ubuntuforums.org/showthread.php?t=193174&highlight=%22AC97+driver%22) thread making me feel like I fool. 

Here's the console output if it will help anyone.

```
        fi
/bin/sh ../libtool --mode=link gcc  -g -O2   -o aserver  aserver.o ../src/libasound.la
mkdir .libs
gcc -g -O2 -o .libs/aserver aserver.o  ../src/.libs/libasound.so -lm -ldl -lpthread
creating aserver
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/aserver'
Making all in alsalisp
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/alsalisp'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/alisp    -g -O2 -MT alsalisp.o -MD -MP -MF ".deps/alsalisp.Tpo" \
          -c -o alsalisp.o `test -f 'alsalisp.c' || echo './'`alsalisp.c; \
        then mv -f ".deps/alsalisp.Tpo" ".deps/alsalisp.Po"; \
        else rm -f ".deps/alsalisp.Tpo"; exit 1; \
        fi
/bin/sh ../libtool --mode=link gcc  -g -O2   -o alsalisp  alsalisp.o ../src/libasound.la
mkdir .libs
gcc -g -O2 -o .libs/alsalisp alsalisp.o  ../src/.libs/libasound.so -lm -ldl -lpthread
creating alsalisp
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/alsalisp'
Making all in test
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/test'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/test'
Making all in utils
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/utils'
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9'
Making install in doc
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc'
Making install in pictures
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc/pictures'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc/pictures'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc/pictures'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc/pictures'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/doc'
Making install in include
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
Making install in sound
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include/sound'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include/sound'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/include/alsa/sound
 /usr/bin/install -c -m 644 ainstr_fm.h /usr/include/alsa/sound/ainstr_fm.h
 /usr/bin/install -c -m 644 ainstr_gf1.h /usr/include/alsa/sound/ainstr_gf1.h
 /usr/bin/install -c -m 644 ainstr_simple.h /usr/include/alsa/sound/ainstr_simple.h
 /usr/bin/install -c -m 644 ainstr_iw.h /usr/include/alsa/sound/ainstr_iw.h
 /usr/bin/install -c -m 644 asound_fm.h /usr/include/alsa/sound/asound_fm.h
 /usr/bin/install -c -m 644 hdsp.h /usr/include/alsa/sound/hdsp.h
 /usr/bin/install -c -m 644 sb16_csp.h /usr/include/alsa/sound/sb16_csp.h
 /usr/bin/install -c -m 644 sscape_ioctl.h /usr/include/alsa/sound/sscape_ioctl.h
 /usr/bin/install -c -m 644 emu10k1.h /usr/include/alsa/sound/emu10k1.h
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include/sound'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include/sound'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/include/alsa
 /usr/bin/install -c -m 644 asoundlib.h /usr/include/alsa/asoundlib.h
 /usr/bin/install -c -m 644 asoundef.h /usr/include/alsa/asoundef.h
 /usr/bin/install -c -m 644 version.h /usr/include/alsa/version.h
 /usr/bin/install -c -m 644 global.h /usr/include/alsa/global.h
 /usr/bin/install -c -m 644 input.h /usr/include/alsa/input.h
 /usr/bin/install -c -m 644 output.h /usr/include/alsa/output.h
 /usr/bin/install -c -m 644 error.h /usr/include/alsa/error.h
 /usr/bin/install -c -m 644 conf.h /usr/include/alsa/conf.h
 /usr/bin/install -c -m 644 pcm.h /usr/include/alsa/pcm.h
 /usr/bin/install -c -m 644 pcm_old.h /usr/include/alsa/pcm_old.h
 /usr/bin/install -c -m 644 pcm_plugin.h /usr/include/alsa/pcm_plugin.h
 /usr/bin/install -c -m 644 rawmidi.h /usr/include/alsa/rawmidi.h
 /usr/bin/install -c -m 644 timer.h /usr/include/alsa/timer.h
 /usr/bin/install -c -m 644 hwdep.h /usr/include/alsa/hwdep.h
 /usr/bin/install -c -m 644 control.h /usr/include/alsa/control.h
 /usr/bin/install -c -m 644 mixer.h /usr/include/alsa/mixer.h
 /usr/bin/install -c -m 644 seq_event.h /usr/include/alsa/seq_event.h
 /usr/bin/install -c -m 644 seq.h /usr/include/alsa/seq.h
 /usr/bin/install -c -m 644 seqmid.h /usr/include/alsa/seqmid.h
 /usr/bin/install -c -m 644 seq_midi_event.h /usr/include/alsa/seq_midi_event.h
 /usr/bin/install -c -m 644 conv.h /usr/include/alsa/conv.h
 /usr/bin/install -c -m 644 instr.h /usr/include/alsa/instr.h
 /usr/bin/install -c -m 644 iatomic.h /usr/include/alsa/iatomic.h
 /usr/bin/install -c -m 644 pcm_ordinary.h /usr/include/alsa/pcm_ordinary.h
 /usr/bin/install -c -m 644 mixer_ordinary.h /usr/include/alsa/mixer_ordinary.h
 /usr/bin/install -c -m 644 alisp.h /usr/include/alsa/alisp.h
 /usr/bin/install -c -m 644 pcm_external.h /usr/include/alsa/pcm_external.h
 /usr/bin/install -c -m 644 pcm_ioplug.h /usr/include/alsa/pcm_ioplug.h
 /usr/bin/install -c -m 644 pcm_extplug.h /usr/include/alsa/pcm_extplug.h
make  install-data-hook
make[4]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
test -d /usr/include/sys || mkdir -p /usr/include/sys
/usr/bin/install -c -m 644 sys.h /usr/include/sys/asoundlib.h
make[4]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/include'
Making install in src
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src'
Making install in control
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/control'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/control'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/control'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/control'
Making install in mixer
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/mixer'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/mixer'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/mixer'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/mixer'
Making install in ordinary_mixer
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_mixer'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_mixer'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_mixer'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_mixer'
Making install in pcm
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/pcm'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/pcm'
make[4]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/pcm'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/pcm'
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/pcm'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/pcm'
Making install in ordinary_pcm
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_pcm'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_pcm'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_pcm'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/ordinary_pcm'
Making install in rawmidi
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/rawmidi'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/rawmidi'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/rawmidi'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/rawmidi'
Making install in timer
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/timer'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/timer'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/timer'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/timer'
Making install in hwdep
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/hwdep'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/hwdep'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/hwdep'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/hwdep'
Making install in seq
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/seq'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/seq'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/seq'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/seq'
Making install in instr
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/instr'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/instr'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/instr'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/instr'
Making install in compat
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/compat'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/compat'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/compat'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/compat'
Making install in conf
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf'
Making install in cards
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/cards'
make[4]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/cards'
make[4]: Nothing to be done for `install-exec-am'.
/bin/sh ../../../mkinstalldirs /usr/share/alsa/cards/SI7018
 /usr/bin/install -c -m 644 SI7018/sndoc-mixer.alisp /usr/share/alsa/cards/SI7018/sndoc-mixer.alisp
 /usr/bin/install -c -m 644 SI7018/sndop-mixer.alisp /usr/share/alsa/cards/SI7018/sndop-mixer.alisp
/bin/sh ../../../mkinstalldirs /usr/share/alsa/cards
 /usr/bin/install -c -m 644 aliases.conf /usr/share/alsa/cards/aliases.conf
 /usr/bin/install -c -m 644 AACI.conf /usr/share/alsa/cards/AACI.conf
 /usr/bin/install -c -m 644 ATIIXP.conf /usr/share/alsa/cards/ATIIXP.conf
 /usr/bin/install -c -m 644 ATIIXP-SPDMA.conf /usr/share/alsa/cards/ATIIXP-SPDMA.conf
 /usr/bin/install -c -m 644 ATIIXP-MODEM.conf /usr/share/alsa/cards/ATIIXP-MODEM.conf
 /usr/bin/install -c -m 644 AU8810.conf /usr/share/alsa/cards/AU8810.conf
 /usr/bin/install -c -m 644 AU8820.conf /usr/share/alsa/cards/AU8820.conf
 /usr/bin/install -c -m 644 AU8830.conf /usr/share/alsa/cards/AU8830.conf
 /usr/bin/install -c -m 644 Audigy.conf /usr/share/alsa/cards/Audigy.conf
 /usr/bin/install -c -m 644 Audigy2.conf /usr/share/alsa/cards/Audigy2.conf
 /usr/bin/install -c -m 644 Aureon51.conf /usr/share/alsa/cards/Aureon51.conf
 /usr/bin/install -c -m 644 Aureon71.conf /usr/share/alsa/cards/Aureon71.conf
 /usr/bin/install -c -m 644 CA0106.conf /usr/share/alsa/cards/CA0106.conf
 /usr/bin/install -c -m 644 CMI8338.conf /usr/share/alsa/cards/CMI8338.conf
 /usr/bin/install -c -m 644 CMI8338-SWIEC.conf /usr/share/alsa/cards/CMI8338-SWIEC.conf
 /usr/bin/install -c -m 644 CMI8738-MC6.conf /usr/share/alsa/cards/CMI8738-MC6.conf
 /usr/bin/install -c -m 644 CMI8738-MC8.conf /usr/share/alsa/cards/CMI8738-MC8.conf
 /usr/bin/install -c -m 644 CS46xx.conf /usr/share/alsa/cards/CS46xx.conf
 /usr/bin/install -c -m 644 EMU10K1.conf /usr/share/alsa/cards/EMU10K1.conf
 /usr/bin/install -c -m 644 EMU10K1X.conf /usr/share/alsa/cards/EMU10K1X.conf
 /usr/bin/install -c -m 644 ENS1370.conf /usr/share/alsa/cards/ENS1370.conf
 /usr/bin/install -c -m 644 ENS1371.conf /usr/share/alsa/cards/ENS1371.conf
 /usr/bin/install -c -m 644 ES1968.conf /usr/share/alsa/cards/ES1968.conf
 /usr/bin/install -c -m 644 FM801.conf /usr/share/alsa/cards/FM801.conf
 /usr/bin/install -c -m 644 GUS.conf /usr/share/alsa/cards/GUS.conf
 /usr/bin/install -c -m 644 HDA-Intel.conf /usr/share/alsa/cards/HDA-Intel.conf
 /usr/bin/install -c -m 644 ICE1712.conf /usr/share/alsa/cards/ICE1712.conf
 /usr/bin/install -c -m 644 ICE1724.conf /usr/share/alsa/cards/ICE1724.conf
 /usr/bin/install -c -m 644 ICH.conf /usr/share/alsa/cards/ICH.conf
 /usr/bin/install -c -m 644 ICH4.conf /usr/share/alsa/cards/ICH4.conf
 /usr/bin/install -c -m 644 ICH-MODEM.conf /usr/share/alsa/cards/ICH-MODEM.conf
 /usr/bin/install -c -m 644 Maestro3.conf /usr/share/alsa/cards/Maestro3.conf
 /usr/bin/install -c -m 644 NFORCE.conf /usr/share/alsa/cards/NFORCE.conf
 /usr/bin/install -c -m 644 PC-Speaker.conf /usr/share/alsa/cards/PC-Speaker.conf
 /usr/bin/install -c -m 644 PMacToonie.conf /usr/share/alsa/cards/PMacToonie.conf
 /usr/bin/install -c -m 644 RME9636.conf /usr/share/alsa/cards/RME9636.conf
 /usr/bin/install -c -m 644 RME9652.conf /usr/share/alsa/cards/RME9652.conf
 /usr/bin/install -c -m 644 SI7018.conf /usr/share/alsa/cards/SI7018.conf
 /usr/bin/install -c -m 644 TRID4DWAVENX.conf /usr/share/alsa/cards/TRID4DWAVENX.conf
 /usr/bin/install -c -m 644 YMF744.conf /usr/share/alsa/cards/YMF744.conf
 /usr/bin/install -c -m 644 VIA686A.conf /usr/share/alsa/cards/VIA686A.conf
 /usr/bin/install -c -m 644 VIA8233.conf /usr/share/alsa/cards/VIA8233.conf
 /usr/bin/install -c -m 644 VIA8233A.conf /usr/share/alsa/cards/VIA8233A.conf
 /usr/bin/install -c -m 644 VIA8237.conf /usr/share/alsa/cards/VIA8237.conf
 /usr/bin/install -c -m 644 VX222.conf /usr/share/alsa/cards/VX222.conf
 /usr/bin/install -c -m 644 VXPocket.conf /usr/share/alsa/cards/VXPocket.conf
 /usr/bin/install -c -m 644 VXPocket440.conf /usr/share/alsa/cards/VXPocket440.conf
 /usr/bin/install -c -m 644 aliases.alisp /usr/share/alsa/cards/aliases.alisp
make[4]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/cards'
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/cards'
Making install in pcm
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/pcm'
make[4]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/pcm'
make[4]: Nothing to be done for `install-exec-am'.
/bin/sh ../../../mkinstalldirs /usr/share/alsa/pcm
 /usr/bin/install -c -m 644 default.conf /usr/share/alsa/pcm/default.conf
 /usr/bin/install -c -m 644 front.conf /usr/share/alsa/pcm/front.conf
 /usr/bin/install -c -m 644 rear.conf /usr/share/alsa/pcm/rear.conf
 /usr/bin/install -c -m 644 center_lfe.conf /usr/share/alsa/pcm/center_lfe.conf
 /usr/bin/install -c -m 644 side.conf /usr/share/alsa/pcm/side.conf
 /usr/bin/install -c -m 644 surround40.conf /usr/share/alsa/pcm/surround40.conf
 /usr/bin/install -c -m 644 surround41.conf /usr/share/alsa/pcm/surround41.conf
 /usr/bin/install -c -m 644 surround50.conf /usr/share/alsa/pcm/surround50.conf
 /usr/bin/install -c -m 644 surround51.conf /usr/share/alsa/pcm/surround51.conf
 /usr/bin/install -c -m 644 surround71.conf /usr/share/alsa/pcm/surround71.conf
 /usr/bin/install -c -m 644 iec958.conf /usr/share/alsa/pcm/iec958.conf
 /usr/bin/install -c -m 644 modem.conf /usr/share/alsa/pcm/modem.conf
 /usr/bin/install -c -m 644 dmix.conf /usr/share/alsa/pcm/dmix.conf
 /usr/bin/install -c -m 644 dsnoop.conf /usr/share/alsa/pcm/dsnoop.conf
make[4]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/pcm'
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf/pcm'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf'
make[4]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf'
make[4]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/share/alsa
 /usr/bin/install -c -m 644 alsa.conf /usr/share/alsa/alsa.conf
 /usr/bin/install -c -m 644 sndo-mixer.alisp /usr/share/alsa/sndo-mixer.alisp
make[4]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf'
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/conf'
Making install in alisp
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/alisp'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/alisp'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/alisp'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src/alisp'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src'
make[3]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src'
/bin/sh ../mkinstalldirs /usr/lib
 /bin/sh ../libtool --mode=install /usr/bin/install -c  libasound.la /usr/lib/libasound.la
/usr/bin/install -c .libs/libasound.so.2.0.0 /usr/lib/libasound.so.2.0.0
(cd /usr/lib && rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2)
(cd /usr/lib && rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so)
/usr/bin/install -c .libs/libasound.lai /usr/lib/libasound.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src'
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/src'
Making install in aserver
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/aserver'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/aserver'
/bin/sh ../mkinstalldirs /usr/bin
  /bin/sh ../libtool --mode=install /usr/bin/install -c aserver /usr/bin/aserver
/usr/bin/install -c .libs/aserver /usr/bin/aserver
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/aserver'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/aserver'
Making install in alsalisp
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/alsalisp'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/alsalisp'
/bin/sh ../mkinstalldirs /usr/bin
  /bin/sh ../libtool --mode=install /usr/bin/install -c alsalisp /usr/bin/alsalisp
/usr/bin/install -c .libs/alsalisp /usr/bin/alsalisp
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/alsalisp'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/alsalisp'
Making install in test
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/test'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/test'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/test'
Making install in utils
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/utils'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/utils'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/share/aclocal
 /usr/bin/install -c -m 644 alsa.m4 /usr/share/aclocal/alsa.m4
/bin/sh ../mkinstalldirs /usr/lib/pkgconfig
 /usr/bin/install -c -m 644 alsa.pc /usr/lib/pkgconfig/alsa.pc
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/utils'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9/utils'
make[1]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9'
make[2]: Entering directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9'
make[1]: Leaving directory `/home/christoph/realtek-linux-audiopack-3.5-6/alsa-lib-1.0.9'
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.9... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
Remove Folder.....
./install: line 89: alsaconf: command not found

```

Right now I'm thinking I need to install alsaconf, but when I found it it just runs the program and doesn't install. Should I move this into one of my bin folders so it can run as a program when it gets to that point or the installation?

---

