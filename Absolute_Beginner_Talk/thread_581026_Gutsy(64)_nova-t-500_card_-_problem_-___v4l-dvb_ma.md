---
title: "Gutsy(64) nova-t-500 card - problem -   v4l-dvb make"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by jb5 on 2007-10-19
Hi.
I'm trying to get my nova-t-500 card working on a fresh install of gutsy 64bit.

I have followed the this [guide](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI) successfully on Feisty(64).

However, on my gutsy installation when I issue the *make* command I get the following error/s..

```
  
----------cut---------------------------
  CC [M]  /home/jb/v4l-dvb/v4l/pvrusb2-cx2584x-v4l.o
  CC [M]  /home/jb/v4l-dvb/v4l/pvrusb2-wm8775.o
  CC [M]  /home/jb/v4l-dvb/v4l/pvrusb2-sysfs.o
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c:927: warning: 'struct kobj_uevent_env' declared inside parameter list
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c:927: warning: its scope is only this definition or declaration, which is probably not what you want
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c: In function 'pvr2_sysfs_class_create':
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c:953: warning: assignment from incompatible pointer type
  CC [M]  /home/jb/v4l-dvb/v4l/pvrusb2-debugifc.o
  CC [M]  /home/jb/v4l-dvb/v4l/pwc-if.o
  CC [M]  /home/jb/v4l-dvb/v4l/pwc-misc.o
  CC [M]  /home/jb/v4l-dvb/v4l/pwc-ctrl.o
  CC [M]  /home/jb/v4l-dvb/v4l/pwc-v4l.o


--------------------cut---------------------------------------

  LD [M]  /home/jb/v4l-dvb/v4l/snd-bt87x.o
  CC [M]  /home/jb/v4l-dvb/v4l/aci.o
/home/jb/v4l-dvb/v4l/aci.c:67:26: error: sound_config.h: No such file or directory
/home/jb/v4l-dvb/v4l/aci.c: In function 'busy_wait':
/home/jb/v4l-dvb/v4l/aci.c:160: warning: implicit declaration of function 'set_current_state'
/home/jb/v4l-dvb/v4l/aci.c:160: error: 'TASK_UNINTERRUPTIBLE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:160: error: (Each undeclared identifier is reported only once
/home/jb/v4l-dvb/v4l/aci.c:160: error: for each function it appears in.)
/home/jb/v4l-dvb/v4l/aci.c:161: warning: implicit declaration of function 'schedule_timeout'
/home/jb/v4l-dvb/v4l/aci.c: In function 'aci_mixer_ioctl':
/home/jb/v4l-dvb/v4l/aci.c:377: error: 'SOUND_MIXER_WRITE_VOLUME' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:379: error: 'SOUND_MIXER_WRITE_CD' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:381: error: 'SOUND_MIXER_WRITE_MIC' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:383: error: 'SOUND_MIXER_WRITE_LINE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:385: error: 'SOUND_MIXER_WRITE_SYNTH' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:387: error: 'SOUND_MIXER_WRITE_PCM' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:389: warning: implicit declaration of function 'MIXER_WRITE'
/home/jb/v4l-dvb/v4l/aci.c:389: error: 'SOUND_MIXER_RADIO' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:389: error: case label does not reduce to an integer constant
/home/jb/v4l-dvb/v4l/aci.c:390: error: 'SOUND_MIXER_WRITE_LINE1' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:392: error: 'SOUND_MIXER_WRITE_LINE2' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:394: error: 'SOUND_MIXER_WRITE_BASS' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:401: error: 'SOUND_MIXER_WRITE_TREBLE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:408: error: 'SOUND_MIXER_WRITE_IGAIN' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:424: error: 'SOUND_MIXER_WRITE_OGAIN' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:443: error: 'SOUND_MIXER_WRITE_RECSRC' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:448: error: 'SOUND_MASK_PCM' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:453: error: 'SOUND_MASK_CD' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:453: error: 'SOUND_MASK_MIC' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:453: error: 'SOUND_MASK_LINE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:454: error: 'SOUND_MASK_SYNTH' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:454: error: 'SOUND_MASK_LINE2' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:456: error: 'SOUND_MASK_RADIO' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:458: error: 'SOUND_MASK_LINE1' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:463: error: 'SOUND_MIXER_READ_DEVMASK' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:464: error: 'SOUND_MASK_VOLUME' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:470: error: 'SOUND_MASK_IGAIN' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:471: error: 'SOUND_MASK_BASS' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:471: error: 'SOUND_MASK_TREBLE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:475: error: 'SOUND_MASK_OGAIN' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:485: error: 'SOUND_MIXER_READ_STEREODEVS' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:500: error: 'SOUND_MIXER_READ_RECMASK' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:510: error: 'SOUND_MIXER_READ_RECSRC' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:538: error: 'SOUND_MIXER_READ_CAPS' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:541: error: 'SOUND_MIXER_READ_VOLUME' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:543: error: 'SOUND_MIXER_READ_CD' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:545: error: 'SOUND_MIXER_READ_MIC' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:547: error: 'SOUND_MIXER_READ_LINE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:549: error: 'SOUND_MIXER_READ_SYNTH' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:551: error: 'SOUND_MIXER_READ_PCM' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:553: warning: implicit declaration of function 'MIXER_READ'
/home/jb/v4l-dvb/v4l/aci.c:553: error: case label does not reduce to an integer constant
/home/jb/v4l-dvb/v4l/aci.c:554: error: 'SOUND_MIXER_READ_LINE1' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:556: error: 'SOUND_MIXER_READ_LINE2' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:558: error: 'SOUND_MIXER_READ_BASS' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:563: error: 'SOUND_MIXER_READ_TREBLE' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:568: error: 'SOUND_MIXER_READ_IGAIN' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:584: error: 'SOUND_MIXER_READ_OGAIN' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c: At top level:
/home/jb/v4l-dvb/v4l/aci.c:595: error: variable 'aci_mixer_operations' has initializer but incomplete type
/home/jb/v4l-dvb/v4l/aci.c:597: error: unknown field 'owner' specified in initializer
/home/jb/v4l-dvb/v4l/aci.c:597: warning: excess elements in struct initializer
/home/jb/v4l-dvb/v4l/aci.c:597: warning: (near initialization for 'aci_mixer_operations')
/home/jb/v4l-dvb/v4l/aci.c:598: error: unknown field 'id' specified in initializer
/home/jb/v4l-dvb/v4l/aci.c:598: warning: excess elements in struct initializer
/home/jb/v4l-dvb/v4l/aci.c:598: warning: (near initialization for 'aci_mixer_operations')
/home/jb/v4l-dvb/v4l/aci.c:599: error: unknown field 'ioctl' specified in initializer
/home/jb/v4l-dvb/v4l/aci.c:600: warning: excess elements in struct initializer
/home/jb/v4l-dvb/v4l/aci.c:600: warning: (near initialization for 'aci_mixer_operations')
/home/jb/v4l-dvb/v4l/aci.c: In function 'attach_aci':
/home/jb/v4l-dvb/v4l/aci.c:622: warning: implicit declaration of function 'request_region'
/home/jb/v4l-dvb/v4l/aci.c:698: warning: implicit declaration of function 'sound_install_mixer'
/home/jb/v4l-dvb/v4l/aci.c:698: error: 'MIXER_DRIVER_VERSION' undeclared (first use in this function)
/home/jb/v4l-dvb/v4l/aci.c:700: error: invalid application of 'sizeof' to incomplete type 'struct mixer_operations' 
/home/jb/v4l-dvb/v4l/aci.c:709: warning: implicit declaration of function 'release_region'
/home/jb/v4l-dvb/v4l/aci.c: In function 'unload_aci':
/home/jb/v4l-dvb/v4l/aci.c:715: warning: implicit declaration of function 'sound_unload_mixerdev'
make[3]: *** [/home/jb/v4l-dvb/v4l/aci.o] Error 1
make[2]: *** [_module_/home/jb/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jb/v4l-dvb/v4l'
make: *** [all] Error 2
jb@eric:~/v4l-dvb$ 



```

The gutsy installation is as clean as possible. Simply added the drivers to get my speedtouch modem working and enabled several repositories via add/remove menu and nothing else.

Any help gratefully received!

---

### Post by 001100 on 2007-10-19
im not much of a hardware specailist but this might help try downloading ubuntu 7.10 32bit and then try again, the card might nit be supported in a 64bit operating system. PLEASE USE A TORRENT WHEN DOWNLODING THE UBUNTU .ISO(s) the servers are quite overloaded.

---

### Post by jb5 on 2007-10-19
Hmm. That's just the problem. Had it working on feisty 64 bit. :confused:

---

### Post by xc3RnbFO8P on 2007-10-19
here is another guide, [http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux]("http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux") I used it on a Gusty 32 bit though.

I have had problem with v4l before.

I delete v4l-dvb folder and install it again.

---

### Post by jb5 on 2007-10-20
Ok -Thanks Ringi.
Taking my cue from the wiki.efficientpc guide above and ignoring the additional "for ubuntu users only" steps in the guide I used previously [see note], I get a little further. Unfortunately I still get the following error

```

/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c:927: warning: 'struct kobj_uevent_env' declared inside parameter list
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c:927: warning: its scope is only this definition or declaration, which is probably not what you want
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c: In function 'pvr2_sysfs_class_create':
/home/jb/v4l-dvb/v4l/pvrusb2-sysfs.c:953: warning: assignment from incompatible pointer type

```

*make* now completes, but *sudo make load* falls over, presumably because of the above error!

A bit of searching throws up a number of [hits.](http://www.google.co.uk/search?hl=en&q=assignment+from+incompatible+pointer+type+v4l-dvb&btnG=Search&meta=) I don't know if this will help clue someone in to a possible solution or even a recommendation that I abandon Gutsy64 for the time being, or not. 

**********************************************************************************
[note] This additional step was only recently introduced following an update to Feisty!! see [thread](http://ubuntuforums.org/showthread.php?p=3496616#post3496616)

---

### Post by jb5 on 2007-10-20
I think that I may be cursed! LOL

I'm getting the same error on Gutsy32bit! :confused:

Ringi - did you upgrade to Gutsy or was it a fresh install??

Also I notice that the link to the alternative guide (efficientPC) is now 404: page not found.

This is the output when I try to 

*sudo make install*

```
make -C /home/jb/v4l-dvb/v4l install
make[1]: Entering directory `/home/jb/v4l-dvb/v4l'
Stripping debug info from files
-e 
Removing obsolete files from /lib/modules/2.6.22-14-generic/kernel/drivers/media/video:
video-buf.ko video-buf-dvb.ko 
Installing kernel modules under /lib/modules/2.6.22-14-generic/kernel/drivers/media/:
        dvb/dvb-usb/: dvb-usb-opera.ko dvb-usb-cxusb.ko dvb-usb-vp7045.ko 
                dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko dvb-usb-dib0700.ko 
                dvb-usb-a800.ko dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko 
                dvb-usb-au6610.ko dvb-usb-digitv.ko dvb-usb.ko 
                dvb-usb-dibusb-mc.ko dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko 
                dvb-usb-dtt200u.ko dvb-usb-vp702x.ko dvb-usb-umt-010.ko 
                dvb-usb-dibusb-mb.ko dvb-usb-gl861.ko dvb-usb-m920x.ko 
        dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko 
                budget-av.ko budget.ko budget-core.ko 
                budget-ci.ko 
        video/et61x251/: et61x251.ko 
        video/cpia2/: cpia2.ko 
        dvb/cinergyT2/: cinergyT2.ko 
        dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko 
        video/ivtv/: ivtvfb.ko ivtv.ko 
        dvb/frontends/: nxt6000.ko dib7000m.ko mt2060.ko 
                mt2131.ko s5h1420.ko nxt200x.ko 
                mt352.ko s5h1409.ko tda827x.ko 
                sp887x.ko dibx000_common.ko isl6421.ko 
                mt312.ko or51132.ko dib3000mb.ko 
                tda1004x.ko dib3000mc.ko sp8870.ko 
                l64781.ko dib7000p.ko ves1x93.ko 
                tda8083.ko dib0070.ko ves1820.ko 
                stv0297.ko tda10086.ko cx22700.ko 
                zl10353.ko qt1010.ko cx24110.ko 
                stv0299.ko dvb-pll.ko lgdt330x.ko 
                cx24123.ko cx22702.ko lnbp21.ko 
                tda10023.ko tua6100.ko bcm3510.ko 
                tda10021.ko or51211.ko mt2266.ko 
                tda826x.ko 
        video/bt8xx/: bttv.ko 
        video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko 
                cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko 
                cx88-dvb.ko 
        dvb/pluto2/: pluto2.ko 
        video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko 
                ultracam.ko konicawc.ko quickcam_messenger.ko 
        video/sn9c102/: sn9c102.ko 
        dvb/dvb-core/: dvb-core.ko 
        video/: vpx3220.ko videobuf-dma-sg.ko bt856.ko 
                upd64083.ko stradis.ko videobuf-core.ko 
                tda9840.ko saa7191.ko cx2341x.ko 
                wm8775.ko meye.ko w9968cf.ko 
                tea5761.ko saa7185.ko tuner.ko 
                tda8290.ko tuner-simple.ko zr364xx.ko 
                ks0127.ko stv680.ko videobuf-dvb.ko 
                tvaudio.ko tea6420.ko bt866.ko 
                cafe_ccic.ko saa5246a.ko msp3400.ko 
                zr36016.ko tcm825x.ko wm8739.ko 
                dpc7146.ko saa5249.ko cpia_pp.ko 
                mt20xx.ko tda7432.ko w9966.ko 
                upd64031a.ko ir-kbd-i2c.ko ov511.ko 
                tuner-3036.ko tea6415c.ko dabusb.ko 
                bt819.ko tea5767.ko cpia_usb.ko 
                videodev.ko zr36060.ko tda9875.ko 
                adv7175.ko mxb.ko vivi.ko 
                cs53l32a.ko btcx-risc.ko se401.ko 
                saa7110.ko saa7115.ko saa6588.ko 
                saa7111.ko tvmixer.ko v4l2-common.ko 
                saa7114.ko hexium_orion.ko hexium_gemini.ko 
                tvp5150.ko vp27smpx.ko adv7170.ko 
                videocodec.ko ov7670.ko saa7127.ko 
                zr36067.ko v4l1-compat.ko videobuf-vmalloc.ko 
                compat_ioctl32.ko v4l2-int-device.ko zr36050.ko 
                c-qcam.ko tveeprom.ko cpia.ko 
                tlv320aic23b.ko bw-qcam.ko 
        video/cx23885/: cx23885.ko 
        video/usbvision/: usbvision.ko 
        common/: saa7146_vv.ko ir-common.ko saa7146.ko 
        video/em28xx/: em28xx.ko 
        video/pvrusb2/: pvrusb2.ko 
        radio/: dsbr100.ko radio-maestro.ko radio-maxiradio.ko 
                radio-gemtek-pci.ko 
        dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko 
                dst.ko 
        video/cx25840/: cx25840.ko 
        dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko 
        dvb/ttusb-budget/: dvb-ttusb-budget.ko 
        video/pwc/: pwc.ko 
        video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko 
                saa7134-dvb.ko saa7134.ko 
        video/ovcamchip/: ovcamchip.ko 
        video/zc0301/: zc0301.ko 
/sbin/depmod -a 2.6.22-14-generic 
make[1]: Leaving directory `/home/jb/v4l-dvb/v4l'
jb@eric:~/v4l-dvb$ 

```

and then when I *sudo make load*

```
make -C /home/jb/v4l-dvb/v4l load
make[1]: Entering directory `/home/jb/v4l-dvb/v4l'
scripts/rmmod.pl load
found 206 modules
/sbin/modprobe soundcore
/sbin/modprobe video-buf-dvb
FATAL: Module video_buf_dvb not found.
/sbin/modprobe cfbimgblt
/sbin/modprobe i2c-algo-bit
/sbin/modprobe cfbfillrect
/sbin/modprobe cfbcopyarea
/sbin/modprobe i2c-core
/sbin/modprobe video-buf
FATAL: Module video_buf not found.
/sbin/modprobe snd
/sbin/modprobe snd-page-alloc
/sbin/modprobe usbcore
/sbin/modprobe parport
/sbin/modprobe sony-laptop
/sbin/modprobe snd-pcm
/sbin/insmod ./nxt6000.ko
/sbin/insmod ./ttusbdecfe.ko
/sbin/insmod ./dib0070.ko
/sbin/insmod ./tda826x.ko
/sbin/insmod ./ttpci-eeprom.ko
/sbin/insmod ./cx24123.ko
/sbin/insmod ./saa7146.ko
/sbin/insmod ./tea6420.ko
/sbin/insmod ./dabusb.ko
/sbin/insmod ./bt866.ko
/sbin/insmod ./saa7191.ko
/sbin/insmod ./saa7111.ko
/sbin/insmod ./tda827x.ko
/sbin/insmod ./cx24110.ko
/sbin/insmod ./ir-common.ko
/sbin/insmod ./tveeprom.ko
/sbin/insmod ./l64781.ko
/sbin/insmod ./ovcamchip.ko
/sbin/insmod ./tlv320aic23b.ko
/sbin/insmod ./videobuf-core.ko
/sbin/insmod ./saa7110.ko
/sbin/insmod ./mt2131.ko
/sbin/insmod ./bt819.ko
/sbin/insmod ./tvmixer.ko
/sbin/insmod ./tda9840.ko
/sbin/insmod ./tda8290.ko
/sbin/insmod ./sp8870.ko
/sbin/insmod ./v4l2-int-device.ko
/sbin/insmod ./tuner-simple.ko
/sbin/insmod ./dvb-pll.ko
insmod: error inserting './dvb-pll.ko': -1 File exists
/sbin/insmod ./saa6588.ko
/sbin/insmod ./v4l2-common.ko
/sbin/insmod ./vpx3220.ko
/sbin/insmod ./bcm3510.ko
/sbin/insmod ./ves1820.ko
/sbin/insmod ./nxt200x.ko
/sbin/insmod ./tda9875.ko
/sbin/insmod ./tea5761.ko
/sbin/insmod ./tda1004x.ko
/sbin/insmod ./cx88-vp3054-i2c.ko
/sbin/insmod ./qt1010.ko
/sbin/insmod ./dvb-core.ko
insmod: error inserting './dvb-core.ko': -1 File exists
/sbin/insmod ./v4l1-compat.ko
/sbin/insmod ./mt312.ko
/sbin/insmod ./saa6752hs.ko
/sbin/insmod ./tea5767.ko
/sbin/insmod ./mt352.ko
/sbin/insmod ./tda10086.ko
/sbin/insmod ./s5h1420.ko
/sbin/insmod ./videocodec.ko
/sbin/insmod ./cx22700.ko
/sbin/insmod ./cx22702.ko
/sbin/insmod ./dvb-usb-af9005-remote.ko
/sbin/insmod ./tda10021.ko
/sbin/insmod ./zl10353.ko
/sbin/insmod ./mt2060.ko
/sbin/insmod ./btcx-risc.ko
/sbin/insmod ./tuner-3036.ko
/sbin/insmod ./isl6421.ko
/sbin/insmod ./mt20xx.ko
/sbin/insmod ./saa7114.ko
/sbin/insmod ./tua6100.ko
/sbin/insmod ./tda10023.ko
/sbin/insmod ./tea6415c.ko
/sbin/insmod ./snd-bt87x.ko
/sbin/insmod ./dibx000_common.ko
insmod: error inserting './dibx000_common.ko': -1 File exists
/sbin/insmod ./ks0127.ko
/sbin/insmod ./lnbp21.ko
/sbin/insmod ./mt2266.ko
/sbin/insmod ./s5h1409.ko
/sbin/insmod ./btaudio.ko
/sbin/insmod ./saa7185.ko
/sbin/insmod ./tda8083.ko
/sbin/insmod ./adv7170.ko
/sbin/insmod ./dib3000mb.ko
/sbin/insmod ./bt856.ko
/sbin/insmod ./stv0297.ko
/sbin/insmod ./sp887x.ko
/sbin/insmod ./adv7175.ko
/sbin/insmod ./ves1x93.ko
/sbin/insmod ./videobuf-vmalloc.ko
/sbin/insmod ./tda7432.ko
/sbin/insmod ./zr36016.ko
/sbin/insmod ./lgdt330x.ko
/sbin/insmod ./msp3400.ko
/sbin/insmod ./cx2341x.ko
/sbin/insmod ./saa7127.ko
/sbin/insmod ./tvp5150.ko
/sbin/insmod ./cs53l32a.ko
/sbin/insmod ./zr36050.ko
/sbin/insmod ./b2c2-flexcop.ko
insmod: error inserting './b2c2-flexcop.ko': -1 Unknown symbol in module
/sbin/insmod ./or51211.ko
/sbin/insmod ./ir-kbd-i2c.ko
/sbin/insmod ./tcm825x.ko
/sbin/insmod ./dib7000p.ko
insmod: error inserting './dib7000p.ko': -1 File exists
/sbin/insmod ./dvb-ttusb-budget.ko
insmod: error inserting './dvb-ttusb-budget.ko': -1 Unknown symbol in module
/sbin/insmod ./videobuf-dma-sg.ko
/sbin/insmod ./tvaudio.ko
/sbin/insmod ./upd64031a.ko
/sbin/insmod ./dvb-usb.ko
insmod: error inserting './dvb-usb.ko': -1 File exists
/sbin/insmod ./wm8775.ko
/sbin/insmod ./dib7000m.ko
insmod: error inserting './dib7000m.ko': -1 File exists
/sbin/insmod ./vp27smpx.ko
/sbin/insmod ./saa7115.ko
/sbin/insmod ./dib3000mc.ko
insmod: error inserting './dib3000mc.ko': -1 File exists
/sbin/insmod ./pluto2.ko
insmod: error inserting './pluto2.ko': -1 Unknown symbol in module
/sbin/insmod ./upd64083.ko
/sbin/insmod ./tuner.ko
/sbin/insmod ./stv0299.ko
/sbin/insmod ./cinergyT2.ko
/sbin/insmod ./ov7670.ko
/sbin/insmod ./zr36060.ko
/sbin/insmod ./ttusb_dec.ko
insmod: error inserting './ttusb_dec.ko': -1 Unknown symbol in module
/sbin/insmod ./budget-core.ko
/sbin/insmod ./videodev.ko
/sbin/insmod ./cx25840.ko
/sbin/insmod ./compat_ioctl32.ko
/sbin/insmod ./or51132.ko
/sbin/insmod ./wm8739.ko
/sbin/insmod ./w9966.ko
/sbin/insmod ./dvb-usb-dibusb-common.ko
insmod: error inserting './dvb-usb-dibusb-common.ko': -1 Unknown symbol in module
/sbin/insmod ./saa5246a.ko
/sbin/insmod ./dvb-usb-ttusb2.ko
insmod: error inserting './dvb-usb-ttusb2.ko': -1 Unknown symbol in module
/sbin/insmod ./dvb-usb-vp7045.ko
insmod: error inserting './dvb-usb-vp7045.ko': -1 Unknown symbol in module
/sbin/insmod ./saa7146_vv.ko
/sbin/insmod ./zr364xx.ko
/sbin/insmod ./ivtv.ko
/sbin/insmod ./sn9c102.ko
/sbin/insmod ./usbvision.ko
/sbin/insmod ./cx88xx.ko
/sbin/insmod ./em28xx.ko
/sbin/insmod ./pvrusb2.ko
/sbin/insmod ./videobuf-dvb.ko
insmod: error inserting './videobuf-dvb.ko': -1 Unknown symbol in module
/sbin/insmod ./dvb-usb-af9005.ko
insmod: error inserting './dvb-usb-af9005.ko': -1 Unknown symbol in module
/sbin/insmod ./cpia.ko
/sbin/insmod ./c-qcam.ko
/sbin/insmod ./meye.ko
/sbin/insmod ./b2c2-flexcop-pci.ko
insmod: error inserting './b2c2-flexcop-pci.ko': -1 Unknown symbol in module
/sbin/insmod ./bttv.ko
/sbin/insmod ./dvb-usb-opera.ko
insmod: error inserting './dvb-usb-opera.ko': -1 Unknown symbol in module
/sbin/insmod ./dvb-usb-cxusb.ko
insmod: error inserting './dvb-usb-cxusb.ko': -1 Unknown symbol in module
/sbin/insmod ./dvb-usb-gp8psk.ko
insmod: error inserting './dvb-usb-gp8psk.ko': -1 Unknown symbol in module
/sbin/insmod ./budget-ci.ko
insmod: error inserting './budget-ci.ko': -1 Unknown symbol in module
/sbin/insmod ./zc0301.ko
/sbin/insmod ./saa7134.ko
/sbin/insmod ./dsbr100.ko
/sbin/insmod ./radio-gemtek-pci.ko
/sbin/insmod ./radio-maxiradio.ko
/sbin/insmod ./et61x251.ko
/sbin/insmod ./dvb-usb-vp702x.ko
insmod: error inserting './dvb-usb-vp702x.ko': -1 Unknown symbol in module
/sbin/insmod ./dvb-usb-dib0700.ko
insmod: error inserting './dvb-usb-dib0700.ko': -1 File exists
/sbin/insmod ./dvb-usb-m920x.ko
insmod: error inserting './dvb-usb-m920x.ko': -1 Unknown symbol in module
/sbin/insmod ./dvb-usb-au6610.ko
insmod: error inserting './dvb-usb-au6610.ko': -1 Unknown symbol in module
/sbin/insmod ./saa5249.ko
/sbin/insmod ./cafe_ccic.ko
/sbin/insmod ./radio-maestro.ko
/sbin/insmod ./usbvideo.ko
/sbin/insmod ./vivi.ko
/sbin/insmod ./b2c2-flexcop-usb.ko
insmod: error inserting './b2c2-flexcop-usb.ko': -1 Unknown symbol in module
/sbin/insmod ./budget.ko
insmod: error inserting './budget.ko': -1 Unknown symbol in module
/sbin/insmod ./stv680.ko
/sbin/insmod ./dvb-usb-digitv.ko
insmod: error inserting './dvb-usb-digitv.ko': -1 Unknown symbol in module
/sbin/insmod ./bw-qcam.ko
/sbin/insmod ./pwc.ko
/sbin/insmod ./se401.ko
/sbin/insmod ./zr36067.ko
insmod: error inserting './zr36067.ko': -1 No such device
/sbin/insmod ./cpia2.ko
/sbin/insmod ./snd-tea575x-tuner.ko
/sbin/insmod ./cx23885.ko
insmod: error inserting './cx23885.ko': -1 Unknown symbol in module
/sbin/insmod ./stradis.ko
/sbin/insmod ./dvb-usb-dtt200u.ko
insmod: error inserting './dvb-usb-dtt200u.ko': -1 Unknown symbol in module
/sbin/insmod ./ov511.ko
/sbin/insmod ./w9968cf.ko
/sbin/insmod ./dvb-usb-gl861.ko
insmod: error inserting './dvb-usb-gl861.ko': -1 Unknown symbol in module
/sbin/insmod ./vicam.ko
/sbin/insmod ./budget-patch.ko
insmod: error inserting './budget-patch.ko': -1 Unknown symbol in module
/sbin/insmod ./saa7134-empress.ko
/sbin/insmod ./dvb-usb-dibusb-mc.ko
insmod: error inserting './dvb-usb-dibusb-mc.ko': -1 Unknown symbol in module
/sbin/insmod ./quickcam_messenger.ko
/sbin/insmod ./hexium_gemini.ko
/sbin/insmod ./ibmcam.ko
/sbin/insmod ./saa7134-alsa.ko
/sbin/insmod ./dvb-usb-a800.ko
insmod: error inserting './dvb-usb-a800.ko': -1 Unknown symbol in module
/sbin/insmod ./cpia_pp.ko
/sbin/insmod ./konicawc.ko
/sbin/insmod ./cpia_usb.ko
/sbin/insmod ./dvb-usb-nova-t-usb2.ko
insmod: error inserting './dvb-usb-nova-t-usb2.ko': -1 Unknown symbol in module
/sbin/insmod ./ivtvfb.ko
insmod: error inserting './ivtvfb.ko': -1 No such device
/sbin/insmod ./ultracam.ko
/sbin/insmod ./dvb-usb-umt-010.ko
insmod: error inserting './dvb-usb-umt-010.ko': -1 Unknown symbol in module
/sbin/insmod ./dpc7146.ko
/sbin/insmod ./bt878.ko
/sbin/insmod ./cx8800.ko
/sbin/insmod ./budget-av.ko
insmod: error inserting './budget-av.ko': -1 Unknown symbol in module
/sbin/insmod ./cx8802.ko
/sbin/insmod ./hexium_orion.ko
/sbin/insmod ./dvb-usb-dibusb-mb.ko
insmod: error inserting './dvb-usb-dibusb-mb.ko': -1 Unknown symbol in module
/sbin/insmod ./mxb.ko
/sbin/insmod ./dvb-ttpci.ko
insmod: error inserting './dvb-ttpci.ko': -1 Unknown symbol in module
/sbin/insmod ./saa7134-dvb.ko
insmod: error inserting './saa7134-dvb.ko': -1 Unknown symbol in module
/sbin/insmod ./cx88-alsa.ko
/sbin/insmod ./cx88-dvb.ko
insmod: error inserting './cx88-dvb.ko': -1 Unknown symbol in module
/sbin/insmod ./dst.ko
/sbin/insmod ./dvb-bt8xx.ko
insmod: error inserting './dvb-bt8xx.ko': -1 Unknown symbol in module
/sbin/insmod ./cx88-blackbird.ko
insmod: error inserting './cx88-blackbird.ko': -1 No such device
/sbin/insmod ./dst_ca.ko
make[1]: Leaving directory `/home/jb/v4l-dvb/v4l'
jb@eric:~/v4l-dvb$ 


```

---

### Post by jb5 on 2007-10-22
Wow - thank goodness for clonezilla!!!!

That last version of v4l-dvb that will *make* without errors in Gutsy64 is version [6374](http://linuxtv.org/hg/v4l-dvb/log), all others up to and including 6383 fail with the following error.
```
/home/jb/v4l-dvb-a5f47a8fdc2a/v4l/pvrusb2-sysfs.c:927: warning: 'struct kobj_uevent_env' declared inside parameter list
/home/jb/v4l-dvb-a5f47a8fdc2a/v4l/pvrusb2-sysfs.c:927: warning: its scope is only this definition or declaration, which is probably not what you want
/home/jb/v4l-dvb-a5f47a8fdc2a/v4l/pvrusb2-sysfs.c: In function 'pvr2_sysfs_class_create':
/home/jb/v4l-dvb-a5f47a8fdc2a/v4l/pvrusb2-sysfs.c:953: warning: assignment from incompatible pointer type

```

---

### Post by alleycat69 on 2007-10-23
Hi all,

I am also having the same arror where when compliing the "make" command using 32 bit Gutsy it fails at :

 CC [M]  /home/jb/v4l-dvb/v4l/aci.o
/home/jb/v4l-dvb/v4l/aci.c:67:26: error: sound_config.h: No such file or directory

It was all working great under fiesty, is there any quick fix :)

I hope there is a solution to the problem soon as my technical knowledge is well not great with Linux, and I really need to get my Myth box completed.

Meeeoooww..

---

### Post by dalejefferson on 2007-10-23
> **alleycat69 said:**
> Hi all,

I am also having the same arror where when compliing the "make" command using 32 bit Gutsy it fails at :

 CC [M]  /home/jb/v4l-dvb/v4l/aci.o
/home/jb/v4l-dvb/v4l/aci.c:67:26: error: sound_config.h: No such file or directory

It was all working great under fiesty, is there any quick fix :)

I hope there is a solution to the problem soon as my technical knowledge is well not great with Linux, and I really need to get my Myth box completed.

Meeeoooww..

Hi All,

Sorry i've taken down the efficientpc wiki and i'm updating the Mythtv wiki instead.

I've just added a fix for this bug
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Hope this helps

---

### Post by alleycat69 on 2007-10-23
Hi dale

Your wisdom and help is really appriciated , Thank you so much for the fast fix and response 

Cat

---

### Post by dalejefferson on 2007-10-24
> **alleycat69 said:**
> Hi dale

Your wisdom and help is really appriciated , Thank you so much for the fast fix and response 

Cat

No problem,  thanks for your kind words :D

---

