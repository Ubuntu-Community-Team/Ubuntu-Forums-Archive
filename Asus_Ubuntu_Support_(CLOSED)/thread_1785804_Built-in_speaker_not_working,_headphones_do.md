---
title: "Built-in speaker not working, headphones do"
date: 2011-06-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by atgcko on 2011-06-18
Hello guys,
I have a problem with my built in speaker on asus eee 1005 pxd, i'm running xubuntu 11.04. When I unplug the headphones, the built-in speaker isn't working. I've checked in alsamixer, it's set to 100%. I've also tried to modprobe the alsa modules available. No result.  Under Windows (I have a dual boot) it's working correctly. I suspect the package oss-compat, which was installed automatically when I installed tuxguitar - roughly after the installation of the packages associated with tuxguitar it stopped working.

Here's my lspci

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Here's modprobe -l | egrep "/sound/" :

kernel/sound/soundcore.ko
kernel/sound/core/snd.ko
kernel/sound/core/snd-hwdep.ko
kernel/sound/core/snd-timer.ko
kernel/sound/core/snd-hrtimer.ko
kernel/sound/core/snd-pcm.ko
kernel/sound/core/snd-page-alloc.ko
kernel/sound/core/snd-rawmidi.ko
kernel/sound/core/seq/snd-seq.ko
kernel/sound/core/seq/snd-seq-device.ko
kernel/sound/core/seq/snd-seq-dummy.ko
kernel/sound/core/seq/snd-seq-virmidi.ko
kernel/sound/core/seq/snd-seq-midi-event.ko
kernel/sound/core/seq/snd-seq-midi.ko
kernel/sound/core/seq/snd-seq-midi-emul.ko
kernel/sound/i2c/other/snd-ak4117.ko
kernel/sound/i2c/other/snd-ak4xxx-adda.ko
kernel/sound/i2c/other/snd-ak4114.ko
kernel/sound/i2c/other/snd-ak4113.ko
kernel/sound/i2c/other/snd-pt2258.ko
kernel/sound/i2c/other/snd-tea575x-tuner.ko
kernel/sound/i2c/snd-tea6330t.ko
kernel/sound/i2c/snd-i2c.ko
kernel/sound/i2c/snd-cs8427.ko
kernel/sound/drivers/snd-dummy.ko
kernel/sound/drivers/snd-aloop.ko
kernel/sound/drivers/snd-virmidi.ko
kernel/sound/drivers/snd-serial-u16550.ko
kernel/sound/drivers/snd-mtpav.ko
kernel/sound/drivers/snd-mts64.ko
kernel/sound/drivers/snd-portman2x4.ko
kernel/sound/drivers/opl3/snd-opl3-lib.ko
kernel/sound/drivers/opl3/snd-opl3-synth.ko
kernel/sound/drivers/opl4/snd-opl4-lib.ko
kernel/sound/drivers/opl4/snd-opl4-synth.ko
kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
kernel/sound/drivers/mpu401/snd-mpu401.ko
kernel/sound/drivers/vx/snd-vx-lib.ko
kernel/sound/drivers/pcsp/snd-pcsp.ko
kernel/sound/isa/snd-adlib.ko
kernel/sound/isa/snd-als100.ko
kernel/sound/isa/snd-azt2320.ko
kernel/sound/isa/snd-cmi8330.ko
kernel/sound/isa/snd-es18xx.ko
kernel/sound/isa/snd-opl3sa2.ko
kernel/sound/isa/snd-sc6000.ko
kernel/sound/isa/snd-sscape.ko
kernel/sound/isa/ad1816a/snd-ad1816a.ko
kernel/sound/isa/ad1848/snd-ad1848.ko
kernel/sound/isa/cs423x/snd-cs4231.ko
kernel/sound/isa/cs423x/snd-cs4236.ko
kernel/sound/isa/es1688/snd-es1688.ko
kernel/sound/isa/es1688/snd-es1688-lib.ko
kernel/sound/isa/galaxy/snd-azt1605.ko
kernel/sound/isa/galaxy/snd-azt2316.ko
kernel/sound/isa/gus/snd-gusclassic.ko
kernel/sound/isa/gus/snd-gus-lib.ko
kernel/sound/isa/gus/snd-gusmax.ko
kernel/sound/isa/gus/snd-gusextreme.ko
kernel/sound/isa/gus/snd-interwave.ko
kernel/sound/isa/gus/snd-interwave-stb.ko
kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
kernel/sound/isa/msnd/snd-msnd-lib.ko
kernel/sound/isa/msnd/snd-msnd-classic.ko
kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
kernel/sound/isa/opti9xx/snd-opti93x.ko
kernel/sound/isa/opti9xx/snd-miro.ko
kernel/sound/isa/sb/snd-sb-common.ko
kernel/sound/isa/sb/snd-sb16-dsp.ko
kernel/sound/isa/sb/snd-sb8-dsp.ko
kernel/sound/isa/sb/snd-sb8.ko
kernel/sound/isa/sb/snd-sb16.ko
kernel/sound/isa/sb/snd-sbawe.ko
kernel/sound/isa/sb/snd-jazz16.ko
kernel/sound/isa/sb/snd-sb16-csp.ko
kernel/sound/isa/sb/snd-emu8000-synth.ko
kernel/sound/isa/wavefront/snd-wavefront.ko
kernel/sound/isa/wss/snd-wss-lib.ko
kernel/sound/pci/snd-ad1889.ko
kernel/sound/pci/snd-als300.ko
kernel/sound/pci/snd-als4000.ko
kernel/sound/pci/snd-atiixp.ko
kernel/sound/pci/snd-atiixp-modem.ko
kernel/sound/pci/snd-azt3328.ko
kernel/sound/pci/snd-bt87x.ko
kernel/sound/pci/snd-cmipci.ko
kernel/sound/pci/snd-cs4281.ko
kernel/sound/pci/snd-cs5530.ko
kernel/sound/pci/snd-ens1370.ko
kernel/sound/pci/snd-ens1371.ko
kernel/sound/pci/snd-es1938.ko
kernel/sound/pci/snd-es1968.ko
kernel/sound/pci/snd-fm801.ko
kernel/sound/pci/snd-intel8x0.ko
kernel/sound/pci/snd-intel8x0m.ko
kernel/sound/pci/snd-maestro3.ko
kernel/sound/pci/snd-rme32.ko
kernel/sound/pci/snd-rme96.ko
kernel/sound/pci/snd-sis7019.ko
kernel/sound/pci/snd-sonicvibes.ko
kernel/sound/pci/snd-via82xx.ko
kernel/sound/pci/snd-via82xx-modem.ko
kernel/sound/pci/ac97/snd-ac97-codec.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/asihpi/snd-asihpi.ko
kernel/sound/pci/au88x0/snd-au8810.ko
kernel/sound/pci/au88x0/snd-au8820.ko
kernel/sound/pci/au88x0/snd-au8830.ko
kernel/sound/pci/aw2/snd-aw2.ko
kernel/sound/pci/ctxfi/snd-ctxfi.ko
kernel/sound/pci/ca0106/snd-ca0106.ko
kernel/sound/pci/cs46xx/snd-cs46xx.ko
kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
kernel/sound/pci/lx6464es/snd-lx6464es.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/echoaudio/snd-indigoiox.ko
kernel/sound/pci/echoaudio/snd-indigodjx.ko
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/ice1712/snd-ice1712.ko
kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
kernel/sound/pci/ice1712/snd-ice1724.ko
kernel/sound/pci/korg1212/snd-korg1212.ko
kernel/sound/pci/mixart/snd-mixart.ko
kernel/sound/pci/nm256/snd-nm256.ko
kernel/sound/pci/oxygen/snd-oxygen-lib.ko
kernel/sound/pci/oxygen/snd-oxygen.ko
kernel/sound/pci/oxygen/snd-virtuoso.ko
kernel/sound/pci/pcxhr/snd-pcxhr.ko
kernel/sound/pci/riptide/snd-riptide.ko
kernel/sound/pci/rme9652/snd-rme9652.ko
kernel/sound/pci/rme9652/snd-hdsp.ko
kernel/sound/pci/rme9652/snd-hdspm.ko
kernel/sound/pci/trident/snd-trident.ko
kernel/sound/pci/ymfpci/snd-ymfpci.ko
kernel/sound/pci/vx222/snd-vx222.ko
kernel/sound/synth/snd-util-mem.ko
kernel/sound/synth/emux/snd-emux-synth.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usbmidi-lib.ko
kernel/sound/usb/misc/snd-ua101.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/sound/pcmcia/vx/snd-vxpocket.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
kernel/sound/soc/snd-soc-core.ko
kernel/sound/soc/codecs/snd-soc-88pm860x.ko
kernel/sound/soc/codecs/snd-soc-ad1836.ko
kernel/sound/soc/codecs/snd-soc-ad193x.ko
kernel/sound/soc/codecs/snd-soc-ad73311.ko
kernel/sound/soc/codecs/snd-soc-ads117x.ko
kernel/sound/soc/codecs/snd-soc-ak4104.ko
kernel/sound/soc/codecs/snd-soc-ak4535.ko
kernel/sound/soc/codecs/snd-soc-ak4642.ko
kernel/sound/soc/codecs/snd-soc-ak4671.ko
kernel/sound/soc/codecs/snd-soc-cs42l51.ko
kernel/sound/soc/codecs/snd-soc-cs4270.ko
kernel/sound/soc/codecs/snd-soc-cx20442.ko
kernel/sound/soc/codecs/snd-soc-da7210.ko
kernel/sound/soc/codecs/snd-soc-l3.ko
kernel/sound/soc/codecs/snd-soc-max98088.ko
kernel/sound/soc/codecs/snd-soc-pcm3008.ko
kernel/sound/soc/codecs/snd-soc-alc5623.ko
kernel/sound/soc/codecs/snd-soc-spdif.ko
kernel/sound/soc/codecs/snd-soc-ssm2602.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
kernel/sound/soc/codecs/snd-soc-uda134x.ko
kernel/sound/soc/codecs/snd-soc-uda1380.ko
kernel/sound/soc/codecs/snd-soc-wl1273.ko
kernel/sound/soc/codecs/snd-soc-wm8350.ko
kernel/sound/soc/codecs/snd-soc-wm8400.ko
kernel/sound/soc/codecs/snd-soc-wm8510.ko
kernel/sound/soc/codecs/snd-soc-wm8523.ko
kernel/sound/soc/codecs/snd-soc-wm8580.ko
kernel/sound/soc/codecs/snd-soc-wm8711.ko
kernel/sound/soc/codecs/snd-soc-wm8727.ko
kernel/sound/soc/codecs/snd-soc-wm8728.ko
kernel/sound/soc/codecs/snd-soc-wm8731.ko
kernel/sound/soc/codecs/snd-soc-wm8737.ko
kernel/sound/soc/codecs/snd-soc-wm8741.ko
kernel/sound/soc/codecs/snd-soc-wm8750.ko
kernel/sound/soc/codecs/snd-soc-wm8753.ko
kernel/sound/soc/codecs/snd-soc-wm8770.ko
kernel/sound/soc/codecs/snd-soc-wm8776.ko
kernel/sound/soc/codecs/snd-soc-wm8804.ko
kernel/sound/soc/codecs/snd-soc-wm8900.ko
kernel/sound/soc/codecs/snd-soc-wm8903.ko
kernel/sound/soc/codecs/snd-soc-wm8904.ko
kernel/sound/soc/codecs/snd-soc-wm8940.ko
kernel/sound/soc/codecs/snd-soc-wm8955.ko
kernel/sound/soc/codecs/snd-soc-wm8960.ko
kernel/sound/soc/codecs/snd-soc-wm8961.ko
kernel/sound/soc/codecs/snd-soc-wm8962.ko
kernel/sound/soc/codecs/snd-soc-wm8971.ko
kernel/sound/soc/codecs/snd-soc-wm8974.ko
kernel/sound/soc/codecs/snd-soc-wm8978.ko
kernel/sound/soc/codecs/snd-soc-wm8985.ko
kernel/sound/soc/codecs/snd-soc-wm8988.ko
kernel/sound/soc/codecs/snd-soc-wm8990.ko
kernel/sound/soc/codecs/snd-soc-wm8993.ko
kernel/sound/soc/codecs/snd-soc-wm8994.ko
kernel/sound/soc/codecs/snd-soc-wm8995.ko
kernel/sound/soc/codecs/snd-soc-wm9081.ko
kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
kernel/sound/soc/codecs/snd-soc-max9877.ko
kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
kernel/sound/soc/codecs/snd-soc-wm2000.ko
kernel/sound/soc/codecs/snd-soc-wm9090.ko
kernel/sound/ac97_bus.ko

Here's modprobe -l | egrep "/staging/" in case it had something to do with it

kernel/drivers/staging/lirc/lirc_bt829.ko
kernel/drivers/staging/lirc/lirc_igorplugusb.ko
kernel/drivers/staging/lirc/lirc_imon.ko
kernel/drivers/staging/lirc/lirc_it87.ko
kernel/drivers/staging/lirc/lirc_ite8709.ko
kernel/drivers/staging/lirc/lirc_sasem.ko
kernel/drivers/staging/lirc/lirc_serial.ko
kernel/drivers/staging/lirc/lirc_sir.ko
kernel/drivers/staging/lirc/lirc_ttusbir.ko
kernel/drivers/staging/lirc/lirc_zilog.ko
kernel/drivers/staging/et131x/et131x.ko
kernel/drivers/staging/slicoss/slicoss.ko
kernel/drivers/staging/go7007/go7007.ko
kernel/drivers/staging/go7007/go7007-usb.ko
kernel/drivers/staging/go7007/s2250.ko
kernel/drivers/staging/go7007/s2250-loader.ko
kernel/drivers/staging/go7007/wis-saa7113.ko
kernel/drivers/staging/go7007/wis-ov7640.ko
kernel/drivers/staging/go7007/wis-saa7115.ko
kernel/drivers/staging/go7007/wis-tw9903.ko
kernel/drivers/staging/go7007/wis-uda1342.ko
kernel/drivers/staging/go7007/wis-sony-tuner.ko
kernel/drivers/staging/go7007/wis-tw2804.ko
kernel/drivers/staging/cx25821/cx25821.ko
kernel/drivers/staging/cx25821/cx25821-alsa.ko
kernel/drivers/staging/tm6000/tm6000.ko
kernel/drivers/staging/tm6000/tm6000-alsa.ko
kernel/drivers/staging/tm6000/tm6000-dvb.ko
kernel/drivers/staging/dabusb/dabusb.ko
kernel/drivers/staging/usbvideo/usbvideo.ko
kernel/drivers/staging/usbvideo/vicam.ko
kernel/drivers/staging/se401/se401.ko
kernel/drivers/staging/usbip/usbip_common_mod.ko
kernel/drivers/staging/usbip/vhci-hcd.ko
kernel/drivers/staging/usbip/usbip.ko
kernel/drivers/staging/winbond/w35und.ko
kernel/drivers/staging/wlan-ng/prism2_usb.ko
kernel/drivers/staging/echo/echo.ko
kernel/drivers/staging/brcm80211/brcm80211.ko
kernel/drivers/staging/rt2860/rt2860sta.ko
kernel/drivers/staging/rt2870/rt2870sta.ko
kernel/drivers/staging/comedi/comedi.ko
kernel/drivers/staging/comedi/kcomedilib/kcomedilib.ko
kernel/drivers/staging/comedi/drivers/pcm_common.ko
kernel/drivers/staging/comedi/drivers/comedi_bond.ko
kernel/drivers/staging/comedi/drivers/comedi_test.ko
kernel/drivers/staging/comedi/drivers/comedi_parport.ko
kernel/drivers/staging/comedi/drivers/serial2002.ko
kernel/drivers/staging/comedi/drivers/skel.ko
kernel/drivers/staging/comedi/drivers/acl7225b.ko
kernel/drivers/staging/comedi/drivers/pcl711.ko
kernel/drivers/staging/comedi/drivers/pcl724.ko
kernel/drivers/staging/comedi/drivers/pcl725.ko
kernel/drivers/staging/comedi/drivers/pcl726.ko
kernel/drivers/staging/comedi/drivers/pcl730.ko
kernel/drivers/staging/comedi/drivers/pcl812.ko
kernel/drivers/staging/comedi/drivers/pcl816.ko
kernel/drivers/staging/comedi/drivers/pcl818.ko
kernel/drivers/staging/comedi/drivers/pcm3724.ko
kernel/drivers/staging/comedi/drivers/pcm3730.ko
kernel/drivers/staging/comedi/drivers/rti800.ko
kernel/drivers/staging/comedi/drivers/rti802.ko
kernel/drivers/staging/comedi/drivers/das16m1.ko
kernel/drivers/staging/comedi/drivers/das16.ko
kernel/drivers/staging/comedi/drivers/das800.ko
kernel/drivers/staging/comedi/drivers/das1800.ko
kernel/drivers/staging/comedi/drivers/das6402.ko
kernel/drivers/staging/comedi/drivers/dt2801.ko
kernel/drivers/staging/comedi/drivers/dt2811.ko
kernel/drivers/staging/comedi/drivers/dt2814.ko
kernel/drivers/staging/comedi/drivers/dt2815.ko
kernel/drivers/staging/comedi/drivers/dt2817.ko
kernel/drivers/staging/comedi/drivers/dt282x.ko
kernel/drivers/staging/comedi/drivers/dmm32at.ko
kernel/drivers/staging/comedi/drivers/fl512.ko
kernel/drivers/staging/comedi/drivers/aio_aio12_8.ko
kernel/drivers/staging/comedi/drivers/aio_iiro_16.ko
kernel/drivers/staging/comedi/drivers/c6xdigio.ko
kernel/drivers/staging/comedi/drivers/mpc624.ko
kernel/drivers/staging/comedi/drivers/adq12b.ko
kernel/drivers/staging/comedi/drivers/ni_at_a2150.ko
kernel/drivers/staging/comedi/drivers/ni_at_ao.ko
kernel/drivers/staging/comedi/drivers/ni_atmio.ko
kernel/drivers/staging/comedi/drivers/ni_atmio16d.ko
kernel/drivers/staging/comedi/drivers/pcmad.ko
kernel/drivers/staging/comedi/drivers/pcmda12.ko
kernel/drivers/staging/comedi/drivers/pcmmio.ko
kernel/drivers/staging/comedi/drivers/pcmuio.ko
kernel/drivers/staging/comedi/drivers/multiq3.ko
kernel/drivers/staging/comedi/drivers/poc.ko
kernel/drivers/staging/comedi/drivers/8255.ko
kernel/drivers/staging/comedi/drivers/addi_apci_035.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1032.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1500.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1516.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1564.ko
kernel/drivers/staging/comedi/drivers/addi_apci_16xx.ko
kernel/drivers/staging/comedi/drivers/addi_apci_2016.ko
kernel/drivers/staging/comedi/drivers/addi_apci_2032.ko
kernel/drivers/staging/comedi/drivers/addi_apci_2200.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3001.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3120.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3501.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3xxx.ko
kernel/drivers/staging/comedi/drivers/adl_pci6208.ko
kernel/drivers/staging/comedi/drivers/adl_pci7230.ko
kernel/drivers/staging/comedi/drivers/adl_pci7296.ko
kernel/drivers/staging/comedi/drivers/adl_pci7432.ko
kernel/drivers/staging/comedi/drivers/adl_pci8164.ko
kernel/drivers/staging/comedi/drivers/adl_pci9111.ko
kernel/drivers/staging/comedi/drivers/adl_pci9118.ko
kernel/drivers/staging/comedi/drivers/adv_pci1710.ko
kernel/drivers/staging/comedi/drivers/adv_pci1723.ko
kernel/drivers/staging/comedi/drivers/adv_pci_dio.ko
kernel/drivers/staging/comedi/drivers/amplc_dio200.ko
kernel/drivers/staging/comedi/drivers/amplc_pc236.ko
kernel/drivers/staging/comedi/drivers/amplc_pc263.ko
kernel/drivers/staging/comedi/drivers/amplc_pci224.ko
kernel/drivers/staging/comedi/drivers/amplc_pci230.ko
kernel/drivers/staging/comedi/drivers/contec_pci_dio.ko
kernel/drivers/staging/comedi/drivers/dt3000.ko
kernel/drivers/staging/comedi/drivers/unioxx5.ko
kernel/drivers/staging/comedi/drivers/gsc_hpdi.ko
kernel/drivers/staging/comedi/drivers/icp_multi.ko
kernel/drivers/staging/comedi/drivers/ii_pci20kc.ko
kernel/drivers/staging/comedi/drivers/daqboard2000.ko
kernel/drivers/staging/comedi/drivers/jr3_pci.ko
kernel/drivers/staging/comedi/drivers/ke_counter.ko
kernel/drivers/staging/comedi/drivers/cb_pcidas64.ko
kernel/drivers/staging/comedi/drivers/cb_pcidas.ko
kernel/drivers/staging/comedi/drivers/cb_pcidda.ko
kernel/drivers/staging/comedi/drivers/cb_pcidio.ko
kernel/drivers/staging/comedi/drivers/cb_pcimdas.ko
kernel/drivers/staging/comedi/drivers/cb_pcimdda.ko
kernel/drivers/staging/comedi/drivers/me4000.ko
kernel/drivers/staging/comedi/drivers/me_daq.ko
kernel/drivers/staging/comedi/drivers/ni_6527.ko
kernel/drivers/staging/comedi/drivers/ni_65xx.ko
kernel/drivers/staging/comedi/drivers/ni_660x.ko
kernel/drivers/staging/comedi/drivers/ni_670x.ko
kernel/drivers/staging/comedi/drivers/ni_pcidio.ko
kernel/drivers/staging/comedi/drivers/ni_pcimio.ko
kernel/drivers/staging/comedi/drivers/rtd520.ko
kernel/drivers/staging/comedi/drivers/s526.ko
kernel/drivers/staging/comedi/drivers/s626.ko
kernel/drivers/staging/comedi/drivers/ssv_dnp.ko
kernel/drivers/staging/comedi/drivers/cb_das16_cs.ko
kernel/drivers/staging/comedi/drivers/das08_cs.ko
kernel/drivers/staging/comedi/drivers/ni_daq_700.ko
kernel/drivers/staging/comedi/drivers/ni_daq_dio24.ko
kernel/drivers/staging/comedi/drivers/ni_labpc_cs.ko
kernel/drivers/staging/comedi/drivers/ni_mio_cs.ko
kernel/drivers/staging/comedi/drivers/quatech_daqp_cs.ko
kernel/drivers/staging/comedi/drivers/dt9812.ko
kernel/drivers/staging/comedi/drivers/usbdux.ko
kernel/drivers/staging/comedi/drivers/usbduxfast.ko
kernel/drivers/staging/comedi/drivers/vmk80xx.ko
kernel/drivers/staging/comedi/drivers/mite.ko
kernel/drivers/staging/comedi/drivers/ni_tio.ko
kernel/drivers/staging/comedi/drivers/ni_tiocmd.ko
kernel/drivers/staging/comedi/drivers/ni_labpc.ko
kernel/drivers/staging/comedi/drivers/das08.ko
kernel/drivers/staging/comedi/drivers/comedi_fc.ko
kernel/drivers/staging/asus_oled/asus_oled.ko
kernel/drivers/staging/panel/panel.ko
kernel/drivers/staging/rtl8187se/r8187se.ko
kernel/drivers/staging/rtl8192u/r8192u_usb.ko
kernel/drivers/staging/rtl8192e/r8192e_pci.ko
kernel/drivers/staging/rtl8712/r8712u.ko
kernel/drivers/staging/rts_pstor/rts_pstor.ko
kernel/drivers/staging/frontier/tranzport.ko
kernel/drivers/staging/frontier/alphatrack.ko
kernel/drivers/staging/pohmelfs/pohmelfs.ko
kernel/drivers/staging/autofs/autofs.ko
kernel/drivers/staging/phison/phison.ko
kernel/drivers/staging/line6/line6usb.ko
kernel/drivers/staging/serqt_usb2/serqt_usb2.ko
kernel/drivers/staging/smbfs/smbfs.ko
kernel/drivers/staging/quatech_usb2/quatech_usb2.ko
kernel/drivers/staging/vt6656/vt6656_stage.ko
kernel/drivers/staging/hv/hv_vmbus.ko
kernel/drivers/staging/hv/hv_timesource.ko
kernel/drivers/staging/hv/hv_storvsc.ko
kernel/drivers/staging/hv/hv_blkvsc.ko
kernel/drivers/staging/hv/hv_netvsc.ko
kernel/drivers/staging/hv/hv_utils.ko
kernel/drivers/staging/vme/bridges/vme_ca91cx42.ko
kernel/drivers/staging/vme/bridges/vme_tsi148.ko
kernel/drivers/staging/vme/devices/vme_user.ko
kernel/drivers/staging/vme/boards/vme_vmivme7805.ko
kernel/drivers/staging/vme/vme.ko
kernel/drivers/staging/sep/sep_driver.ko
kernel/drivers/staging/iio/accel/adis16201.ko
kernel/drivers/staging/iio/accel/adis16203.ko
kernel/drivers/staging/iio/accel/adis16204.ko
kernel/drivers/staging/iio/accel/adis16209.ko
kernel/drivers/staging/iio/accel/adis16220.ko
kernel/drivers/staging/iio/accel/adis16240.ko
kernel/drivers/staging/iio/accel/kxsd9.ko
kernel/drivers/staging/iio/accel/lis3l02dq.ko
kernel/drivers/staging/iio/accel/sca3000.ko
kernel/drivers/staging/iio/adc/max1363.ko
kernel/drivers/staging/iio/adc/ad799x.ko
kernel/drivers/staging/iio/adc/ad7476.ko
kernel/drivers/staging/iio/adc/ad7887.ko
kernel/drivers/staging/iio/adc/ad7150.ko
kernel/drivers/staging/iio/adc/ad7152.ko
kernel/drivers/staging/iio/adc/ad7291.ko
kernel/drivers/staging/iio/adc/ad7298.ko
kernel/drivers/staging/iio/adc/ad7314.ko
kernel/drivers/staging/iio/adc/ad7745.ko
kernel/drivers/staging/iio/adc/ad7816.ko
kernel/drivers/staging/iio/adc/adt75.ko
kernel/drivers/staging/iio/adc/adt7310.ko
kernel/drivers/staging/iio/adc/adt7410.ko
kernel/drivers/staging/iio/addac/adt7316.ko
kernel/drivers/staging/iio/addac/adt7316-spi.ko
kernel/drivers/staging/iio/addac/adt7316-i2c.ko
kernel/drivers/staging/iio/dac/ad5624r_spi.ko
kernel/drivers/staging/iio/dac/ad5446.ko
kernel/drivers/staging/iio/dds/ad5930.ko
kernel/drivers/staging/iio/dds/ad9832.ko
kernel/drivers/staging/iio/dds/ad9834.ko
kernel/drivers/staging/iio/dds/ad9850.ko
kernel/drivers/staging/iio/dds/ad9852.ko
kernel/drivers/staging/iio/dds/ad9910.ko
kernel/drivers/staging/iio/dds/ad9951.ko
kernel/drivers/staging/iio/gyro/adis16060.ko
kernel/drivers/staging/iio/gyro/adis16080.ko
kernel/drivers/staging/iio/gyro/adis16130.ko
kernel/drivers/staging/iio/gyro/adis16260.ko
kernel/drivers/staging/iio/gyro/adis16251.ko
kernel/drivers/staging/iio/imu/adis16300.ko
kernel/drivers/staging/iio/imu/adis16350.ko
kernel/drivers/staging/iio/imu/adis16400.ko
kernel/drivers/staging/iio/light/tsl2563.ko
kernel/drivers/staging/iio/light/isl29018.ko
kernel/drivers/staging/iio/magnetometer/ak8975.ko
kernel/drivers/staging/iio/magnetometer/hmc5843.ko
kernel/drivers/staging/iio/meter/ade7753.ko
kernel/drivers/staging/iio/meter/ade7754.ko
kernel/drivers/staging/iio/meter/ade7758.ko
kernel/drivers/staging/iio/meter/ade7759.ko
kernel/drivers/staging/iio/meter/ade7854.ko
kernel/drivers/staging/iio/meter/ade7854-i2c.ko
kernel/drivers/staging/iio/meter/ade7854-spi.ko
kernel/drivers/staging/iio/resolver/ad2s90.ko
kernel/drivers/staging/iio/resolver/ad2s120x.ko
kernel/drivers/staging/iio/resolver/ad2s1210.ko
kernel/drivers/staging/iio/trigger/iio-trig-periodic-rtc.ko
kernel/drivers/staging/iio/trigger/iio-trig-gpio.ko
kernel/drivers/staging/iio/industrialio.ko
kernel/drivers/staging/iio/ring_sw.ko
kernel/drivers/staging/cs5535_gpio/cs5535_gpio.ko
kernel/drivers/staging/zram/zram.ko
kernel/drivers/staging/wlags49_h2/wlags49_h2_cs.ko
kernel/drivers/staging/wlags49_h25/wlags49_h25_cs.ko
kernel/drivers/staging/samsung-laptop/samsung-laptop.ko
kernel/drivers/staging/sm7xx/sm7xx.ko
kernel/drivers/staging/dt3155v4l/dt3155v4l.ko
kernel/drivers/staging/crystalhd/crystalhd.ko
kernel/drivers/staging/cxt1e1/cxt1e1.ko
kernel/drivers/staging/ti-st/bt_drv.ko
kernel/drivers/staging/xgifb/xgifb.ko
kernel/drivers/staging/easycap/easycap.ko
kernel/drivers/staging/quickstart/quickstart.ko
kernel/drivers/staging/sbe-2t3e3/sbe-2t3e3.ko
kernel/drivers/staging/keucr/keucr.ko
kernel/drivers/staging/bcm/bcm_wimax.ko
kernel/drivers/staging/ft1000/ft1000-usb/ft1000.ko
kernel/drivers/staging/speakup/speakup_acntsa.ko
kernel/drivers/staging/speakup/speakup_acntpc.ko
kernel/drivers/staging/speakup/speakup_apollo.ko
kernel/drivers/staging/speakup/speakup_audptr.ko
kernel/drivers/staging/speakup/speakup_bns.ko
kernel/drivers/staging/speakup/speakup_dectlk.ko
kernel/drivers/staging/speakup/speakup_decext.ko
kernel/drivers/staging/speakup/speakup_decpc.ko
kernel/drivers/staging/speakup/speakup_dtlk.ko
kernel/drivers/staging/speakup/speakup_keypc.ko
kernel/drivers/staging/speakup/speakup_ltlk.ko
kernel/drivers/staging/speakup/speakup_soft.ko
kernel/drivers/staging/speakup/speakup_spkout.ko
kernel/drivers/staging/speakup/speakup_txprt.ko
kernel/drivers/staging/speakup/speakup_dummy.ko
kernel/drivers/staging/speakup/speakup.ko
kernel/drivers/staging/cptm1217/clearpad_tm1217.ko
kernel/drivers/staging/ste_rmi4/synaptics_i2c_rmi4.ko

Here's  dpkg --get-selections | egrep "alsa|pulse|oss" :
alsa-base					install
alsa-oss					deinstall
alsa-utils					install
bluez-alsa					install
gstreamer0.10-alsa				install
gstreamer0.10-pulseaudio			install
libpulse-browse0				install
libpulse-mainloop-glib0				install
libpulse0					install
libsdl1.2debian-alsa				deinstall
oss-compat					install
pulseaudio					install
pulseaudio-esound-compat			install
pulseaudio-module-x11				install
pulseaudio-utils				install
vlc-plugin-pulse				install

(there are cca 1300 packages on my system installed, didn't wanna list all of them, so i hope this filter doesn't exclude something that might be important )

I'll provide any additional info if needed

Thank you very much for your help!

Regards

ATGcko

---

### Post by lidex on 2011-06-18
Please use code tags for large blocks of text. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by mobruu on 2011-09-11
Hijacking this thread and hope that is ok.

Having problems with no sound from internal speakers.
 
Running Kubuntu..

Here's my output:
 
[http://www.alsa-project.org/db/?f=ed409951d1297731e8272ab6d7a0b3935df9257a](http://www.alsa-project.org/db/?f=ed409951d1297731e8272ab6d7a0b3935df9257a)


Thanks for any help .. :-)

---

### Post by lidex on 2011-09-19
> **mobruu said:**
> Hijacking this thread and hope that is ok.

Having problems with no sound from internal speakers.
 
Running Kubuntu..

Here's my output:
 
[http://www.alsa-project.org/db/?f=ed409951d1297731e8272ab6d7a0b3935df9257a](http://www.alsa-project.org/db/?f=ed409951d1297731e8272ab6d7a0b3935df9257a)


Thanks for any help .. :-)
I'll answer to that but next time start a new thread.
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

