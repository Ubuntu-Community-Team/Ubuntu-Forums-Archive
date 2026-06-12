---
title: "Instalacio clauer IDCAT a ubuntu"
date: 2010-06-08
forum: Catalan Team
---

### Post by pserra on 2010-06-08
Hola, estava seguint els passos al manual i alguna cosa em falla al MAKE, m'explico:
seguint el manual, quan faig el ./congigure a les darreres linies em surt.```

hecking for pthread_create in -lpthread... yes
checking for RSA_sign in -lcrypto... no
configure: WARNING: We can't links against the ssl library
configure: error: Perhaps you need to use the --with-ssl-libraries directive
```

miro de instal·lar la llibreria en questió:
```

pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ sudo apt-get install libnss-dev libssl-dev
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
E: No s'ha pogut trobar el paquet libnss-dev
```

i si faig el MAKE tinc:
```
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ make
make: *** No targets specified and no makefile found.  Stop.
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$

```
 

	


pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ make
make: *** No targets specified and no makefile found.  Stop.
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$
[/CODE]

 
que em falla??  merci

---

### Post by kimet on 2010-06-08
No es una llibreria.
Prova:
```
./configure --with-ssl-libraries
``` 

Salut.

---

### Post by pserra on 2010-06-09
> **kimet said:**
> No es una llibreria.
Prova:
```
./configure --with-ssl-libraries
``` 

Salut.

em surt el mateix... al final del teu configure em genera error (el mateix):
```

pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ ./configure --with-ssl-libraries
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/tmp/ClauerLinux-3.0.4/missing: Unknown `--run' option
Try `/tmp/ClauerLinux-3.0.4/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
..........................................moltes linies i al final...................
checking for pthread_create in -lpthread... yes
checking for RSA_sign in -lcrypto... no
configure: WARNING: We can't links against the ssl library
configure: error: Perhaps you need to use the --with-ssl-libraries directive
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ make
make: *** No targets specified and no makefile found.  Stop.
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ 

```

---

### Post by papapep on 2010-06-09
Pserra,

és que, com tu ja has posat abans, et falta, com a mínim, una llibreria per instal·lar.

> pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ sudo apt-get install libnss-dev libssl-dev
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
**E: No s'ha pogut trobar el paquet libnss-dev**

Prova instal·lant la [http://packages.ubuntu.com/lucid/libnss3-dev](http://packages.ubuntu.com/lucid/libnss3-dev).

```
sudo apt-get install libnss3-dev libssl-dev
```

i repetint el procés a partir d'aquí.

---

### Post by kimet on 2010-06-09
Pot ser et falti alguna llibreria donç, busca a Synaptic libssl i openssl.
 
Aquí ha ha algú que sembla que ho ha aconseguit:
[http://xiquetam.blogspot.com/2010/04/installacio-clauer-linux-idcat-en_8593.html](http://xiquetam.blogspot.com/2010/04/installacio-clauer-linux-idcat-en_8593.html)

---

### Post by telejet on 2010-06-09
Hola, jo ho acabo de fer a un ubuntu 10.04 i com que ha ho havia fet a uns quants he apuntat els passos, a veure si et serveixen:

1- instal.lar prèviament el paquets per a compilar
    sudo apt-get install g++ open-ssl libssl libssl-dev
2- seguir la guia del clauer idcat - descarregar clauer.zip, descomprimir, .configure, make, make install
(pensa que a la guia del clauer diu "su" però es pot fer amb sudo:
sudo ./configure
sudo make
sudo make install
3- no cal iniciar el clos, ni afegir el firefox-pk11.sh (no em funciona a mi)
4- per afegir al firefox anar a preferències-xifratge-dispositius de seguretat-carrega- pk11 clauer - escollir /usr/local/lib/libclauerpkc11.so

I ja ho tindrem tot a punt. A veure si us funciona, fins ara,

Ivan

---

### Post by pserra on 2010-06-09
> **telejet said:**
> Hola, jo ho acabo de fer a un ubuntu 10.04 i com que ha ho havia fet a uns quants he apuntat els passos, a veure si et serveixen:

1- instal.lar prèviament el paquets per a compilar
    sudo apt-get install g++ open-ssl libssl libssl-dev
2- seguir la guia del clauer idcat - descarregar clauer.zip, descomprimir, .configure, make, make install
(pensa que a la guia del clauer diu "su" però es pot fer amb sudo:
sudo ./configure
sudo make
sudo make install
3- no cal iniciar el clos, ni afegir el firefox-pk11.sh (no em funciona a mi)
4- per afegir al firefox anar a preferències-xifratge-dispositius de seguretat-carrega- pk11 clauer - escollir /usr/local/lib/libclauerpkc11.so

I ja ho tindrem tot a punt. A veure si us funciona, fins ara,

Ivan

MERCI IVAN...UN MANUAL MOLT COMPLET...
sobretot m'ha anat molt bé el saber l'adreça de on anar a carregar el pk11...
Un darrer problema que m'extranya.... la instal·lacio ha anat bé... inclus ja he canviat la contrasenya.... però no passo el test... em surt error que fa referencia a TOMCAT... no sé m'estranya.... 
lo del java ho tinc correctament instal·lat... ja que he fet alguna cosa amb java i eclipse i m'ha anat bé...
que em falta instal·lar?

Merci

---

