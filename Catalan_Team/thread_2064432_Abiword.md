---
title: "Abiword"
date: 2012-09-29
forum: Catalan Team
---

### Post by skywalk on 2012-09-29
Bon dia:
He instal·lat a un portàtil vellet de fa 5 o 6 anys el 12.04 alternate amb un escriptori LXDE. De moment va com una seda i fa servir poca  memòria. M'hi vaig instal·lant els  programes que necessito de mica en mica.
Em vaig instal·lar l'Abiword  però en els repositoris  hi ha la versió 2.9.2, que és una versió de desenvolupament i que no funciona bé.
Ara vull instal·lar-me la versió estable 2.8.6 a partir del paquet tar que he baixat des de la pàgina de l' Abiword. Després de patir per instal·lar tot el que faltava de dependències  i aconseguir fer el configure,  al fer make em dóna errors. Adjunto el final:
> ribidi -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 -lexpat -ljpeg -lpng -lgsf-1 -lxml2 -lenchant -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 -lfreetype -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 -lcairo -lgobject-2.0 -lglib-2.0   -ljpeg 
libtool: link: g++ -g -O2 --no-undefined -o .libs/abiword abiword-UnixMain.o -pthread -Wl,--export-dynamic  ./.libs/libabiword-2.8.so /usr/lib/libfribidi.so -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 /usr/lib/i386-linux-gnu/libexpat.so -lpng -lgsf-1 /usr/lib/i386-linux-gnu/libxml2.so /usr/lib/libenchant.so -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 /usr/lib/i386-linux-gnu/libfreetype.so -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 /usr/lib/i386-linux-gnu/libcairo.so -lgobject-2.0 -lglib-2.0 -ljpeg -pthread
g++: error: unrecognized option '--no-undefined'
make[3]: *** [abiword] Error 1
make[3]: Leaving directory `/home/jordi/Downloads/abiword-2.8.6/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jordi/Downloads/abiword-2.8.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jordi/Downloads/abiword-2.8.6'
make: *** [all] Error 2
jordi@ubuntu:~/Downloads/abiword-2.8.6$ 


He buscat informació fins allà on sé però ja em perdo.
Si algú en sap i em pot ajudar li agrairé.
Salutacions.

---

### Post by CarlesOriol on 2012-09-29
Saps que l'11.04 acaba el seu període de vida el 28 d'octubre?

Per què no insta&#320;les una versió més moderna? (12.04?)

---

### Post by skywalk on 2012-09-29
Perdó. Es el 12.04

---

### Post by wgarcia on 2012-09-30
Fixa't en aquesta pàgina:

[https://launchpad.net/ubuntu/precise/+package/abiword](https://launchpad.net/ubuntu/precise/+package/abiword)

Hi ha paquets "deb" de diferents versions.

---

### Post by skywalk on 2012-09-30
En el Ubuntu Forums "mare" vaig exposar aquest problema i m'han contestat donant-me referències d'un bug en la versió de l'Abiword que es baixa des de la seva pròpia pàgina:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628267](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628267)

Gràcies i marco com a "solved"

---

