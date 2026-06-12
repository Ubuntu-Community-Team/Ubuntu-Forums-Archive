---
title: "ffmpeg --enable xvid"
date: 2007-04-24
forum: Catalan Team
---

### Post by hackarre on 2007-04-24
Hola a tothom!

La veritat es que ja vaig fer aquesta pregunta a absolute beginner talk però no vaig obtenir resposta. La qüestió és que tinc un ipod video i m'agradaria poder passar-li els meus videos.

Sé que es necessita el programa ffmpeg que fàcilment he instal·lat amb apt-get seguint aquesta guia [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding) el problema recau a l'hora de donar-li suport xvid i tota la pesca l'hora de compilar vaja. Quan faig make aquest missatge d'error m'apareix:
[email]hackarre@hackarre-desktop:~/ffmpeg-0.cvs[/email]20060823$ make
/home/hackarre/ffmpeg-0.cvs20060823/version.sh "/home/hackarre/ffmpeg-0.cvs20060823"
make -C libavutil   all
make[1]: Entering directory `/home/hackarre/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/hackarre/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/hackarre/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/hackarre/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving di

Estic fent servir Festy Fawn i el que es curiós és que amb edgy, abans que no entenia res amb funcionava perfectament amb thinliquidfilm:lolflag: 

S'ha de fer alguna cosa especial a Festy?

Sisplau necesito ajuda? Si no hi ha alguna altra solució per passar els videos al ipod?

---

