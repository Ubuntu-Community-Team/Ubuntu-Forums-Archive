---
title: "Sintonitzador de TV"
date: 2007-05-27
forum: Catalan Team
---

### Post by ventma on 2007-05-27
El sintonitzador de TV no consegueixo que funcioni a l'ubuntu. El reconeix però com a "unknown/generic" : card=0, tuner=1, i per això no em funcione quan obro el TVTIME. He provat de fer rmmod del bttv, per després tornar a configurar-lo, però no em deixa, hem diu: Resource temporarily unavailable. Com puc canviar els paràmetres del mòdul bttv? o be editar-lo per canviar-li els paràmetres de gpio.

---

### Post by pisuke on 2007-05-27
Quin model de sintonitzadora tens?

---

### Post by ventma on 2007-05-28
És un sintonitzador desconegut, amb Windows faig servir el MoreTV i he de ficar sint.desconegut i entrar els paràmetres de GPIO manualment (ni me'n recordo com vaig trobar aquests paràmetres), però ficant Miro PCTV també funciona; per tant el que necesito fer a ubuntu és poder introduir la card=1 i tuner=5 (Philips PAL), o bé poder editar la bttv introduint els paràmetres anteriors.

---

### Post by orestesmas on 2007-05-31
Pots carregar un mòdul amb uns paràmetres concrets usant l'ordre "insmod" o "modprobe" amb el nom del mòdul i els paràmetres (nom_del_paràmetre=valor)

Per saber quins paràmestres accepta un cert mòdul, fes "sudo modinfo nom_del_mòdul"

Pel bttv jo tinc (totes les línies que comencen per "parm"):

orestes@tintin:~$ sudo modinfo bttv
filename:       /lib/modules/2.6.18-4-amd64/kernel/drivers/media/video/bt8xx/bttv.ko
description:    bttv - v4l/v4l2 driver module for bt848/878 based cards
author:         Ralph Metzler & Marcus Metzler & Gerd Knorr
license:        GPL
vermagic:       2.6.18-4-amd64 SMP mod_unload gcc-4.1
depends:        video-buf,i2c-core,ir-common,videodev,tveeprom,v4l2-common,i2c-algo-bit,btcx-risc,firmware_class,compat_ioctl32
alias:          pci:v0000109Ed00000350sv*sd*bc*sc*i*
alias:          pci:v0000109Ed00000351sv*sd*bc*sc*i*
alias:          pci:v0000109Ed0000036Esv*sd*bc*sc*i*
alias:          pci:v0000109Ed0000036Fsv*sd*bc*sc*i*
parm:           rc5_key_timeout:int
parm:           rc5_remote_gap:int
parm:           repeat_period:int
parm:           repeat_delay:int
parm:           debug:int
parm:           i2c_scan:scan i2c bus at insmod time (int)
parm:           i2c_hw:int
parm:           i2c_debug:int
parm:           vbi_debug:vbi code debug messages, default is 0 (no) (int)
parm:           vbibufs:number of vbi buffers, range 2-32, default 4 (int)
parm:           audiomux:array of int
parm:           remote:array of int
parm:           svhs:array of int
parm:           tuner:specify installed tuner type (array of int)
parm:           pll:specify installed crystal (0=none, 28=28 MHz, 35=35 MHz) (array of int)
parm:           card:specify TV/grabber card model, see CARDLIST file for a list (array of int)
parm:           autoload:automatically load i2c modules like tuner.o, default is 1 (yes) (int)
parm:           audioall:int
parm:           gpiomask:int
parm:           latency:pci latency timer (int)
parm:           no_overlay:allow override overlay default (0 disables, 1 enables) [some VIA/SIS chipsets are known to have problem with overlay] (int)
parm:           vsfx:set VSFX pci config bit [yet another chipset flaw workaround] (int)
parm:           triton1:set ETBF pci config bit [enable bug compatibility for triton1 + others] (int)
parm:           radio:The TV card supports radio, default is 0 (no) (array of int)
parm:           coring:set the luma coring level, default is 0 (no) (int)
parm:           full_luma_range:use the full luma range, default is 0 (no) (int)
parm:           uv_ratio:ratio between u and v gains, default is 50 (int)
parm:           vcr_hack:enables the VCR hack (improves synch on poor VCR tapes), default is 0 (no) (int)
parm:           whitecrush_lower:sets the white crush lower value, default is 127 (int)
parm:           whitecrush_upper:sets the white crush upper value, default is 207 (int)
parm:           adc_crush:enables the luminance ADC crush, default is 1 (yes) (int)
parm:           chroma_agc:enables the AGC of chroma signal, default is 0 (no) (int)
parm:           automute:mute audio on bad/missing video signal, default is 1 (yes) (int)
parm:           lumafilter:int
parm:           combfilter:int
parm:           irq_iswitch:switch inputs in irq handler (int)
parm:           bigendian:byte order of the framebuffer, default is native endian (int)
parm:           v4l2:int
parm:           gbufsize:size of the capture buffers, default is 0x208000 (int)
parm:           gbuffers:number of capture buffers. range 2-32, default 8 (int)
parm:           vbi_nr:int
parm:           radio_nr:int
parm:           video_nr:int
parm:           fdsr:int
parm:           debug_latency:int
parm:           irq_debug:irq handler debug messages, default is 0 (no) (int)
parm:           bttv_debug:debug messages, default is 0 (no) (int)
parm:           bttv_gpio:log gpio changes, default is 0 (no) (int)
parm:           bttv_verbose:verbose startup messages, default is 1 (yes) (int)

---

### Post by ventma on 2007-05-31
Orestes, amb aquestes dades al bttv, et funciona el sintonitzador de TV ?

---

### Post by orestesmas on 2007-06-01
A veure. Aquestes dades només dónen la informació del mòdul bttv. Aquest mòdul el té tothom, perquè ve inclòs amb el kernel de linux. Que jo el tingui al disc no vol dir que el tingui carregat. Només se'm carregarà si tinc una tarja sintonitzadora de vídeo que tingui un dels xipsets suportats pel mòdul.

I bé, si, en tinc una. En el PC de sobretaula de casa tinc una sintonitzadora amb xipset bt878 que em va raonablement bé. Però no li haig de posar cap paràmetre a mà, me'ls detecta sol.

---

