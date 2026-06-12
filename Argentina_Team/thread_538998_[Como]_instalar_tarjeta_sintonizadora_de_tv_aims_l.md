---
title: "[Como] instalar tarjeta sintonizadora de tv aims lab video highway tr 288 en Ubuntu"
date: 2007-08-30
forum: Argentina Team
---

### Post by LikeVinyl on 2007-08-30
Hola humanistas amigos!

Hoy aprenderemos [Como] instalar tarjeta sintonizadora de tv aims lab video highway tr 288 en Ubuntu Kubuntu Xubuntu 7.04

Tal cual nos indica el título, el ejemplo que utilizaremos será para instalar una tarjeta aims lab video highway xtreme tr 288; Esta tarjeta de captura o sintonizador de tv, utiliza el chip BT848 que junto al BT878 y el BT879 fabricados por conexant, es uno de los más difundidos en este tipo de dispositivos.

**Antes de empezar**

Asumiremos que utilizamos Ubuntu, Kubuntu, Edubuntu o Xubuntu en su versión 7.04 Feisty Fawn o cualquier distribución basada en Ubuntu Feisty Fawn 7.04. Hago esta aclaración porque tanto el soporte del api v4l -video for linux- incluído en el núcleo y el módulo bttv.o que controlará nuestra tarjeta, se encuentran disponibles por defecto en esta versión y esperamos que se mantengan en el futúro. Sin embargo, según nuestro grado de conocimientos, esta guía puede usarse como referencia para otras distribuciones.

Manos a la obra!

**Verificando dispositivos**

Lo primero que haremos, será abrir una terminal dentro de X e invocar el comando lspci para verificar que nuestra tarjeta fué detectada físicamente por nuestro núcleo / ordenador.
 
```
$ lspci 
```

Si todo es correcto, para nuestro ejemplo, tendría que devolver la siguiente salida:

02:0c.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 12)

    *Esta línea puede aparecer en cualquier posición según la configuración de nuestro sistema.

Excelente! esto significa que únicamente haremos pequeños cambios en la configuración de nuestro sistema y que no requeriremos recompilar nuestro núcleo o devolver la tarjeta al vendedor. 

Por otro lado, si no devuelve esta línea, todo tiene solución pero no la daré en este [Como] ya que pretendo facilitarle las cosas a los humanistas amigos -Usuarios de Ubuntu GNU/Linux- y no orientarlo a usuarios expertos que utilicen otras distribuciones. -que además no necesitarán una guía como ésta-.

**Iniciando la Instalación**

Es hora de relajarse, ya sabemos que nuestra tarjeta / hardware funciona y solo quedan algunos pasos antes de finalizar. 

Ahora necesitaremos un buen programa o software que nos permita ver nuestros programas favoritos, en este caso y como dije antes, a facilitar las cosas! instalaremos TVTime; TVTime incorpora muchas características, entre las más destacadas: ver norma PAL-Nc -y no morir en el intento-, hacer capturas de pantalla, cambiar la resolución al vuelo, cambiar filtros de entrada y otras más que no vienen al caso.

Para instalar TVTime, nuevamente abriremos una terminal dentro de X e invocaremos el siguiente comando:

```
$ sudo aptitude install tvtime 
```

Apenas terminada la descarga, se abrirá una pantalla con los siguientes contenidos:

Configuración de paquetes

**Configuración de tvtime**

Los usuarios norteamericanos deberían seleccionar NTSC. La mayoría de las zonas del mundo usan PAL.

Seleccione el estándar de televisión para su localización

    NTSC
    PAL
    SECAM
    PAL-Nc
    PAL-M
    PAL-N
    NTSC-JP
    PAL-60

 <Aceptar>                  <Cancelar>

Continuamos,

En esa ventana, solo seleccionaremos la norma que corresponde a nuestro país y pulsaremos el botón <Aceptar>, yo vivo en Argentina y mi norma es PAL-Nc. En la siguiente ventana tendremos las opciones:

    Cable
    Retransmición
    Cable con más de 100 canales

Nuevamente seleccionaremos la opción que corresponda y pulsaremos <Aceptar>, para mi caso seleccionaré Cable.

Ya tenemos TVTime! -pero no es time de ver tv porque aún no terminamos-

**Probando tarjeta sintonizadora**

Ahora, invocaremos los siguientes comandos para asegurarnos que nuestra tarjeta no se detectó incorrectamente, para ello quitaremos el módulo bttv de nuestro núcleo y lo cargaremos nuevamente con los parámetros que necesita.

Entonces, desde una terminal dentro de X invocaremos los siguientes comandos:

```
$ sudo rmmod bttv 
```
```
$ sudo rmmod tuner 
```

Perfecto, con eso quitamos los módulos y en este paso los cargaremos nuevamente. Entonces, desde una terminal dentro de X, invocaremos el siguiente comando:

```
$ sudo modprobe bttv card=14 tuner=2 
```

**¿Que es card=14 y tuner=2?**

La respuesta es sencilla, estos números corresponden al tipo de tarjeta y tipo de sintonizador que utiliza; Como en este ejemplo estamos instalando una tarjeta Aims Lab Video Highway tr 288, agregamos los parámetros que corresponden según la tabla de tarjetas y sintonizadores soportados que aparece al final de este documento.

**Verificando módulos**

A continuación verificaremos la carga del módulo ¡Preparar los tambores! abrir una terminal dentro de X y e invocar el siguiente comando:

```
$ dmesg | grep bttv && dmesg | grep tuner 
```

Si todo es correcto, tendría que mostrarnos la siguiente salida:

[   16.296465] bttv: driver version 0.9.16 loaded
[   16.296472] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   16.296559] bttv: Bt8xx card found (0).
[   16.296595] bttv0: Bt848 (rev 18) at 0000:02:0c.0, irq: 21, latency: 64, mmio: 0xf7eff000
[   16.296606] bttv0: using: Aimslab Video Highway Xtreme (VHX) [card=14,insmod option]
[   16.296640] bttv0: gpio: en=00000000, out=00000000 in=00ff3fff [init]
[   16.297572] bttv0: using tuner=2
[   16.297645] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   16.298471] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   16.299308] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   16.403343] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   16.936512] bttv0: registered device video0
[   16.936560] bttv0: registered device vbi0
[   16.936602] bttv0: registered device radio0
[   16.936625] bttv0: PLL: 28636363 => 35468950 .. ok
[  631.504231] bttv0: PLL can sleep, using XTAL (28636363).
[82675.962761] bttv0: unloading
[84832.901130] bttv: driver version 0.9.16 loaded
[84832.901138] bttv: using 8 buffers with 2080k (520 pages) each for capture
[84832.901512] bttv: Bt8xx card found (0).
[84832.901620] bttv0: Bt848 (rev 18) at 0000:02:0c.0, irq: 21, latency: 64, mmio: 0xf7eff000
[84832.901953] bttv0: using: Aimslab Video Highway Xtreme (VHX) [card=14,insmod option]
[84832.901987] bttv0: gpio: en=00000000, out=00000000 in=00ff3fff [init]
[84832.929444] bttv0: using tuner=2
[84832.929923] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[84832.931088] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[84832.931941] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[84832.949952] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[84832.961425] bttv0: registered device video0
[84832.961572] bttv0: registered device vbi0
[84832.961698] bttv0: registered device radio0
[84832.961849] bttv0: PLL: 28636363 => 35468950 .. ok
[84841.225296] bttv0: PLL can sleep, using XTAL (28636363).
[   16.297572] bttv0: using tuner=2
[   16.925625] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   16.925629] tuner 0-0060: chip found @ 0xc0 (bt848 #0 [sw])
[   16.925661] tuner 0-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   16.925665] tuner 0-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[84832.913691] tuner 0-0060: All bytes are equal. It is not a TEA5767
[84832.913703] tuner 0-0060: chip found @ 0xc0 (bt848 #0 [sw])
[84832.929444] bttv0: using tuner=2
[84832.929903] tuner 0-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))

Maravilloso! Excelente! ¡Que emoción! En fin, ya estamos finalizando...

**Configuración**

Falta el último paso, es necesario indicarle a nuestro querido Ubuntu GNU/Linux que cargue los módulos y su correspondiente configuración en el arranque de nuestro sistema; De otro modo, tendríamos que cargarlos manualmente cada vez que reiniciemos y querramos ver tv ¿engorroso no?

Entonces, desde un terminal dentro de X, invocaremos el siguiente comando:

```
$ sudo gedit /etc/modprobe.d/options 
```

Agregaremos la siguiente línea:

```
options bttv card=14 tuner=2 
``` 

Guardamos el archivo, cerramos y reiniciamos nuestro ordenador.

**Anexo Tabla de tarjetas y sinonizadores soportados.**

Tarjetas soportadas por el módulo bttv:

card=0 *** UNKNOWN/GENERIC ***
card=1 MIRO PCTV
card=2 Hauppauge (bt848)
card=3 STB, Gateway P/N 6000699 (bt848)
card=4 Intel Create and Share PCI/ Smart Video Recorder III
card=5 Diamond DTV2000
card=6 AVerMedia TVPhone
card=7 MATRIX-Vision MV-Delta
card=8 Lifeview FlyVideo II (Bt848) LR26 / MAXI TV Video PCI2 LR26
card=9 IMS/IXmicro TurboTV
card=10 Hauppauge (bt878)                                   [0070:13eb,0070:3900,2636:10b4]
card=11 MIRO PCTV pro
card=12 ADS Technologies Channel Surfer TV (bt848)
card=13 AVerMedia TVCapture 98                           [1461:0002,1461:0004,1461:0300]
card=14 Aimslab Video Highway Xtreme (VHX)
card=15 Zoltrix TV-Max                                          [a1a0:a0fc]
card=16 Prolink Pixelview PlayTV (bt878)
card=17 Leadtek WinView 601
card=18 AVEC Intercapture
card=19 Lifeview FlyVideo II EZ /FlyKit LR38 Bt848 (capture only)
card=20 CEI Raffles Card
card=21 Lifeview FlyVideo 98/ Lucky Star Image World ConferenceTV LR50
card=22 Askey CPH050/ Phoebe Tv Master + FM      [14ff:3002]
card=23 Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 [14c7:0101]
card=24 Askey CPH05X/06X (bt878) [many vendors]  [144f:3002,144f:3005,144f:5000,14ff:3000]
card=25 Terratec TerraTV+ Version 1.0 (Bt848)/ Terra TValue Version 1.0/ Vobis TV-Boostar
card=26 Hauppauge WinCam newer (bt878)
card=27 Lifeview FlyVideo 98/ MAXI TV Video PCI2 LR50
card=28 Terratec TerraTV+ Version 1.1 (bt878)               [153b:1127,1852:1852]
card=29 Imagenation PXC200                                  [1295:200a]
card=30 Lifeview FlyVideo 98 LR50                           [1f7f:1850]
card=31 Formac iProTV, Formac ProTV I (bt848)
card=32 Intel Create and Share PCI/ Smart Video Recorder III
card=33 Terratec TerraTValue Version Bt878                  [153b:1117,153b:1118,153b:1119,153b:111a,153b:1134,153b:5018]
card=34 Leadtek WinFast 2000/ WinFast 2000 XP               [107d:6606,107d:6609,6606:217d,f6ff:fff6]
card=35 Lifeview FlyVideo 98 LR50 / Chronos Video Shuttle II [1851:1850,1851:a050]
card=36 Lifeview FlyVideo 98FM LR50 / Typhoon TView TV/FM Tuner [1852:1852]
card=37 Prolink PixelView PlayTV pro
card=38 Askey CPH06X TView99                                [144f:3000,144f:a005,a04f:a0fc]
card=39 Pinnacle PCTV Studio/Rave                           [11bd:0012,bd11:1200,bd11:ff00,11bd:ff12]
card=40 STB TV PCI FM, Gateway P/N 6000704 (bt878), 3Dfx VoodooTV 100 [10b4:2636,10b4:2645,121a:3060]
card=41 AVerMedia TVPhone 98                                [1461:0001,1461:0003]
card=42 ProVideo PV951                                      [aa0c:146c]
card=43 Little OnAir TV
card=44 Sigma TVII-FM
card=45 MATRIX-Vision MV-Delta 2
card=46 Zoltrix Genie TV/FM                                 [15b0:4000,15b0:400a,15b0:400d,15b0:4010,15b0:4016]
card=47 Terratec TV/Radio+                                  [153b:1123]
card=48 Askey CPH03x/ Dynalink Magic TView
card=49 IODATA GV-BCTV3/PCI                                 [10fc:4020]
card=50 Prolink PV-BT878P+4E / PixelView PlayTV PAK / Lenco MXTV-9578 CP
card=51 Eagle Wireless Capricorn2 (bt878A)
card=52 Pinnacle PCTV Studio Pro
card=53 Typhoon TView RDS + FM Stereo / KNC1 TV Station RDS
card=54 Lifeview FlyVideo 2000 /FlyVideo A2/ Lifetec LT 9415 TV [LR90]
card=55 Askey CPH031/ BESTBUY Easy TV
card=56 Lifeview FlyVideo 98FM LR50                         [a051:41a0]
card=57 GrandTec Grand Video Capture (Bt848)              [4344:4142]
card=58 Askey CPH060/ Phoebe TV Master Only (No FM)
card=59 Askey CPH03x TV Capturer
card=60 Modular Technology MM100PCTV
card=61 AG Electronics GMV1                                 [15cb:0101]
card=62 Askey CPH061/ BESTBUY Easy TV (bt878)
card=63 ATI TV-Wonder                                       [1002:0001]
card=64 ATI TV-Wonder VE                                    [1002:0003]
card=65 Lifeview FlyVideo 2000S LR90
card=66 Terratec TValueRadio                                [153b:1135,153b:ff3b]
card=67 IODATA GV-BCTV4/PCI                                 [10fc:4050]
card=68 3Dfx VoodooTV FM (Euro)                             [10b4:2637]
card=69 Active Imaging AIMMS
card=70 Prolink Pixelview PV-BT878P+ (Rev.4C,8E)
card=71 Lifeview FlyVideo 98EZ (capture only) LR51          [1851:1851]
card=72 Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [1554:4011]
card=73 Sensoray 311                                        [6000:0311]
card=74 RemoteVision MX (RV605)
card=75 Powercolor MTV878/ MTV878R/ MTV878F
card=76 Canopus WinDVR PCI (COMPAQ Presario 3524JP, 5112JP) [0e11:0079]
card=77 GrandTec Multi Capture Card (Bt878)
card=78 Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF   [0a01:17de]
card=79 DSP Design TCVIDEO
card=80 Hauppauge WinTV PVR                                 [0070:4500]
card=81 IODATA GV-BCTV5/PCI                                 [10fc:4070,10fc:d018]
card=82 Osprey 100/150 (878)                                [0070:ff00]
card=83 Osprey 100/150 (848)
card=84 Osprey 101 (848)
card=85 Osprey 101/151
card=86 Osprey 101/151 w/ svid
card=87 Osprey 200/201/250/251
card=88 Osprey 200/250                                      [0070:ff01]
card=89 Osprey 210/220/230
card=90 Osprey 500                                          [0070:ff02]
card=91 Osprey 540                                          [0070:ff04]
card=92 Osprey 2000                                         [0070:ff03]
card=93 IDS Eagle
card=94 Pinnacle PCTV Sat                                   [11bd:001c]
card=95 Formac ProTV II (bt878)
card=96 MachTV
card=97 Euresys Picolo
card=98 ProVideo PV150                                      [aa00:1460,aa01:1461,aa02:1462,aa03:1463,aa04:1464,aa05:1465,aa06:1466,aa07:1467]
card=99 AD-TVK503
card=100 Hercules Smart TV Stereo
card=101 Pace TV & Radio Card
card=102 IVC-200                                             [0000:a155,0001:a155,0002:a155,0003:a155,0100:a155,0101:a155,0102:a155,0103:a155]
card=103 Grand X-Guard / Trust 814PCI                        [0304:0102]
card=104 Nebula Electronics DigiTV                           [0071:0101]
card=105 ProVideo PV143                                      [aa00:1430,aa00:1431,aa00:1432,aa00:1433,aa03:1433]
card=106 PHYTEC VD-009-X1 MiniDIN (bt878)
card=107 PHYTEC VD-009-X1 Combi (bt878)
card=108 PHYTEC VD-009 MiniDIN (bt878)
card=109 PHYTEC VD-009 Combi (bt878)
card=110 IVC-100                                             [ff00:a132]
card=111 IVC-120G                                            [ff00:a182,ff01:a182,ff02:a182,ff03:a182,ff04:a182,ff05:a182,ff06:a182,ff07:a182,ff08:a182,ff09:a182,ff0a:a182,ff0b:a182,ff0c:a182,ff0d:a182,ff0e:a182,ff0f:a182]
card=112 pcHDTV HD-2000 TV                                   [7063:2000]
card=113 Twinhan DST + clones                                [11bd:0026,1822:0001,270f:fc00,1822:0026]
card=114 Winfast VC100                                       [107d:6607]
card=115 Teppro TEV-560/InterVision IV-560
card=116 SIMUS GVC1100                                       [aa6a:82b2]
card=117 NGS NGSTV+
card=118 LMLBT4
card=119 Tekram M205 PRO
card=120 Conceptronic CONTVFMi
card=121 Euresys Picolo Tetra                                [1805:0105,1805:0106,1805:0107,1805:0108]
card=122 Spirit TV Tuner
card=123 AVerMedia AVerTV DVB-T 771                          [1461:0771]
card=124 AverMedia AverTV DVB-T 761                          [1461:0761]
card=125 MATRIX Vision Sigma-SQ
card=126 MATRIX Vision Sigma-SLC
card=127 APAC Viewcomp 878(AMAX)
card=128 DViCO FusionHDTV DVB-T Lite                         [18ac:db10,18ac:db11]
card=129 V-Gear MyVCD
card=130 Super TV Tuner
card=131 Tibet Systems Progress DVR CS16
card=132 Kodicom 4400R (master)
card=133 Kodicom 4400R (slave)
card=134 Adlink RTV24
card=135 DViCO FusionHDTV 5 Lite                             [18ac:d500]
card=136 Acorp Y878F                                         [9511:1540]
card=137 Conceptronic CTVFMi v2
card=138 Prolink Pixelview PV-BT878P+ (Rev.2E)
card=139 Prolink PixelView PlayTV MPEG2 PV-M4900
card=140 Osprey 440                                          [0070:ff07]
card=141 Asound Skyeye PCTV
card=142 Sabrent TV-FM (bttv version)
card=143 Hauppauge ImpactVCB (bt878)                         [0070:13eb]
card=144 MagicTV
card=145 SSAI Security Video Interface                       [4149:5353]
card=146 SSAI Ultrasound Video Interface                     [414a:5353]
card=147 VoodooTV 200 (USA)                                  [121a:3000]
card=148 DViCO FusionHDTV 2                                  [dbc0:d200]

Sintonizadores soportados por v4l -video for linux-

tuner=0 - Temic PAL (4002 FH5)
tuner=1 - Philips PAL_I (FI1246 and compatibles)
tuner=2 - Philips NTSC (FI1236,FM1236 and compatibles)
tuner=3 - Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF)
tuner=4 - NoTuner
tuner=5 - Philips PAL_BG (FI1216 and compatibles)
tuner=6 - Temic NTSC (4032 FY5)
tuner=7 - Temic PAL_I (4062 FY5)
tuner=8 - Temic NTSC (4036 FY5)
tuner=9 - Alps HSBH1
tuner=10 - Alps TSBE1
tuner=11 - Alps TSBB5
tuner=12 - Alps TSBE5
tuner=13 - Alps TSBC5
tuner=14 - Temic PAL_BG (4006FH5)
tuner=15 - Alps TSCH6
tuner=16 - Temic PAL_DK (4016 FY5)
tuner=17 - Philips NTSC_M (MK2)
tuner=18 - Temic PAL_I (4066 FY5)
tuner=19 - Temic PAL* auto (4006 FN5)
tuner=20 - Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5)
tuner=21 - Temic NTSC (4039 FR5)
tuner=22 - Temic PAL/SECAM multi (4046 FM5)
tuner=23 - Philips PAL_DK (FI1256 and compatibles)
tuner=24 - Philips PAL/SECAM multi (FQ1216ME)
tuner=25 - LG PAL_I+FM (TAPC-I001D)
tuner=26 - LG PAL_I (TAPC-I701D)
tuner=27 - LG NTSC+FM (TPI8NSR01F)
tuner=28 - LG PAL_BG+FM (TPI8PSB01D)
tuner=29 - LG PAL_BG (TPI8PSB11D)
tuner=30 - Temic PAL* auto + FM (4009 FN5)
tuner=31 - SHARP NTSC_JP (2U5JF5540)
tuner=32 - Samsung PAL TCPM9091PD27
tuner=33 - MT20xx universal
tuner=34 - Temic PAL_BG (4106 FH5)
tuner=35 - Temic PAL_DK/SECAM_L (4012 FY5)
tuner=36 - Temic NTSC (4136 FY5)
tuner=37 - LG PAL (newer TAPC series)
tuner=38 - Philips PAL/SECAM multi (FM1216ME MK3)
tuner=39 - LG NTSC (newer TAPC series)
tuner=40 - HITACHI V7-J180AT
tuner=41 - Philips PAL_MK (FI1216 MK)
tuner=42 - Philips FCV1236D ATSC/NTSC dual in
tuner=43 - Philips NTSC MK3 (FM1236MK3 or FM1236/F)
tuner=44 - Philips 4 in 1 (ATI TV Wonder Pro/Conexant)
tuner=45 - Microtune 4049 FM5
tuner=46 - Panasonic VP27s/ENGE4324D
tuner=47 - LG NTSC (TAPE series)
tuner=48 - Tenna TNF 8831 BGFF)
tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in
tuner=50 - TCL 2002N
tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
tuner=52 - Thomson DTT 7610 (ATSC/NTSC)
tuner=53 - Philips FQ1286
tuner=54 - tda8290+75
tuner=55 - TCL 2002MB
tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
tuner=57 - Philips FQ1236A MK4
tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
tuner=59 - Ymec TVision TVF-5533MF
tuner=60 - Thomson DTT 761X (ATSC/NTSC)
tuner=61 - Tena TNF9533-D/IF/TNF9533-B/DF
tuner=62 - Philips TEA5767HN FM Radio
tuner=63 - Philips FMD1216ME MK3 Hybrid Tuner
tuner=64 - LG TDVS-H06xF
tuner=65 - Ymec TVF66T5-B/DFF
tuner=66 - LG TALN series
tuner=67 - Philips TD1316 Hybrid Tuner
tuner=68 - Philips TUV1236D ATSC/NTSC dual in
tuner=69 - Tena TNF 5335 and similar models
tuner=70 - Samsung TCPN 2121P30A
tuner=71 - Xceive xc3028
tuner=72 - Thomson FE6600
tuner=73 - Samsung TCPG 6121P30A
tuner=75 - Philips TEA5761 FM Radio

**Notas finales**

Con esto terminamos amigos, ojalá les sea útil y que puedan disfrutar al máximo de Ubuntu GNU/Linux.

Un gran abrazo a todos!

Fuentes:
[http://tldp.org/HOWTO/BTTV/]("http://tldp.org/HOWTO/BTTV/")
[http://www.linuxtv.org/v4lwiki/index.php/Main_Page]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page")
[http://www.wlug.org.nz/TvTunerCards]("http://www.wlug.org.nz/TvTunerCards")

Miguel Angel Ríos ::: LikeVinyl 2007 :::

Este documento es copyleft, Miguel Angel Ríos, 2007
Tienes la Libertad de copiar, modificar y distribuír esta documentación.

---

