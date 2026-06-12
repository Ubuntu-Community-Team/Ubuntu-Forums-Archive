---
title: "Problemes actualitzant de Feisty a Gutsy"
date: 2007-10-26
forum: Catalan Team
---

### Post by guillemsola on 2007-10-26
Doncs, si, sabia que la tentació seria massa forta i que acabaria passant així que he actualitzat de la F a la G.

Per començar no m'arrenca bé, encara no tinc clar perquè a vegades no arranca. He tret de l'fstab una partició amb ntfs que es veu que li donava mal de caps. Crec haver entès que ha d'estar amb 3gntfs per anar bé.
Penso que desprès d'això ja li costa menys arrancar però encara no les tinc totes. On van a parar els missatges d'arrencada? es que passen massa ràpid.

L'openoffice es penjava a l'imprimir però aixó ho he solucionat posant una aparença per defecte com el clearlook.

Tinc dues tarjetes de so i "la bona" una ewx2496 (ice1712) ha deixat de sonar. Està al sistema però al intentar-la fer sonar diu que el recurs no està disponible

Amb el lspci -v diu <access denied> pero tb ho diu de la que si sona.

> 
01:07.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 19
        I/O ports at c000 [size=64]
        Capabilities: <access denied>

01:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: TERRATEC Electronic GmbH EWX 24/96
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at c800 [size=32]
        I/O ports at cc00 [size=16]
        I/O ports at d000 [size=16]
        I/O ports at d400 [size=64]
        Capabilities: <access denied>



He provat a fer alguns dpkg-reconfigure i modprobe snd-1712 i coses per l'estil però no li fa efecte. Alguna idea de pq diu "no s'ha pogut obrir el recurs per a l'escriptura" a l'intentar accedir-hi desde administració/so? Amb la festy anava perfecte.

En fi serafí. hauré de reinstalar de nou? Haurà valgut la pena el canvi? Sabia que si no el feia reventaria! ara només em queda esperar quant valor tinc per aguantar actualitzar el portàtil tb!!! Com si no sapigués el que hi ha...

Gràcies, necessitava que algú m'escoltes... XD

---

### Post by papapep on 2007-10-26
Amb els dos comentaris que fas sobre els missatges d'error amb el lspci i intentant accedir a Sistema > Preferències > So té pinta de que tinguis un problema de permisos.
L'usuari que fas servir és el que vas crear en instal·lar, o és un que has creat posteriorment??

Quin procediment has fet servir per passar de Feisty a Gutsy?

Edició 01:44h:

Hauries de mirar si tens els següents mòduls instal·lats:

 soundcore 
 snd-ice1712  
 snd-pcm-oss 
 snd-mixer-oss 
 snd-seq-oss

Per això, fes en un terminal:

```
lsmod |grep snd
```

Amb això llistaràs tots els mòduls que tens instal·lats que contingui la cadena de text "snd" dins la seva descripció o nom, i veurem si et falta alguna cosa. (tot i això el tema dels permisos segueix fent mala espina. Ja veurem...)

---

### Post by guillemsola on 2007-10-26
Tots aquests mòduls estan al sistema.

> 
snd_ice1712            65140  1 
snd_ice17xx_ak4xxx      5120  1 snd_ice1712
snd_ak4xxx_adda         8832  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9984  1 snd_ice1712
snd_i2c                 6656  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9600  1 snd_ice1712
snd_ens1371            27680  1 
snd_seq_dummy           4740  0 
gameport               16776  1 snd_ens1371
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_ac97_codec        100644  2 snd_ice1712,snd_ens1371
snd_rawmidi            25728  3 snd_mpu401_uart,snd_ens1371,snd_seq_midi
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  1 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                80388  4 snd_ice1712,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              24324  2 snd_seq,snd_pcm
snd_page_alloc         11400  1 snd_pcm
snd                    54660  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_i2c,snd_mpu401_uart,snd_ens1371,snd_seq_oss,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  2 snd


Respecte al que has dit de l'usuari he observat que si faig sudo lspci -v aleshores ja no diu que l'acces estigui denegat

> 
01:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: TERRATEC Electronic GmbH EWX 24/96
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at c800 [size=32]
        I/O ports at cc00 [size=16]
        I/O ports at d000 [size=16]
        I/O ports at d400 [size=64]
        Capabilities: [80] Power Management version 1


L'usuari que tinc és el mateix que tenia a festy

Per actualitzar vaig fer una actualització de paquets de la festy i després vaig actualitzar. Això si tot des de l'entorn gràfic.

salut!

EDITAT:

Per mes inri resulta que a l'ordinador tinc un altre usuari per a la dona, per veure si així s'anima a fer servir l'ubuntu i sorpresa! en aquest usuari el so funciona al 100%. Sembla doncs que el problema son els permisos. De totes formes segons l'admin. de permisos el meu usuari els té per fer anar dispositius de so.

---

