---
title: "Sense so al Maverick"
date: 2010-10-17
forum: Catalan Team
---

### Post by Quepotser on 2010-10-17
Hola tothom.

En un disc dur que tinc gairebé exclusivament per a fer proves fa uns dies que hi vaig instal·lar el Maverick. Va tot bé, excepte el so. No hi ha manera de que deixi anar ni el més mínim dels sorollets. He seguit tota mena de tutorials i consell que he anat trobant per google: treure el Pulseaudio, instal.lar drivers de l'Alsa i configuracions més o menys exòtiques, però no hi ha manera.

El lspci:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
lespedretes@lespedretes:~$ 

He de dir que amb aquest mateix ordinador funciono molt bé amb el Lucid i anava perfecte amb el Jaunty i el Karmic.

---

### Post by guillemsola on 2010-10-18
potser podries executar l'script de alsaper detectar falles

[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

i compartir el resultat

---

### Post by wgarcia on 2010-10-18
Has provat alguna de les coses que suggereixen al següent enllaç?:

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by Quepotser on 2010-10-18
Això es per Angrychai. He fet correr el script però no hi ha manera de treure'n l'entrellat ja que es queda en una mena de cercle i hi ha una mena de scroll que no para mai.

Potser és que hi ha alguna cosa que no faig bé:
-clico l'enllaç i em surt el programa. Com que no em dona cap més opció el copio al terminal i el faig còrrer. Si m'he errar en alguna cosa digue'm ho.

Gràcies per endevant.

---

### Post by Quepotser on 2010-10-19
Per a Wgarcia. Provar, ja havia provat alguna de les coses que diuen en aquest enllaç que m'has enviat (actualitzar el driver ALSA, les configuracions, etc)i he seguit totes les pases que s'anaven recomenant fer al llarg dels diferents enllaços als que et porten; i tot continua igual. La veritat és que estic una mica sorprès ja que en aquest mateix ordinador mai havia tingut cap problema d'importancia amb Ubuntu ni amb Gnu/linux en general (provant diferents distros i actualitzacions diverses). Una sol·lució que he trobat a google es canviar el kernel i retocedir al 2.6.32.25, però al Synaptic ja no es troben els kernels més antics que el que pertoca a la distribució (Maverick).

De totes formes continuaré buscant quin pot ser el problema i si és possible, la sol·lució. Així que si a algú se li acudeix alguna cosa que no dubti en fer-m'ho arribar. Gràcies a tothom.

---

### Post by Quepotser on 2010-10-19
Be, ja he aconseguit que funciones el ditxos script (bé, en realitat no sé què passava). El resultat:

---

### Post by Quepotser on 2010-10-19
Em pareix que no s'ha adjuntat el fitxer amb el resultat del script. A veure si ara ho aconsegueixo.

Passa que el fitxer pesa massa i no m'admet adjuntar-lo amb el format amb que s'ha generat. El canvio i el passo a ".odt":

---

### Post by wgarcia on 2010-10-19
Un suggeriment molt tonto, però millor descartar-lo. Has obert una terminal, entrat "alsamixer" i mirat si tots els volums estan donats?

---

### Post by Quepotser on 2010-10-19
Es una de les primeres coses que vaig fer. Això i comprovar totes les connexions, la integritat de CD, etc. He reinstal·lat varies vegades per allò de que no s'hagi gravat malament algún fitxer. De totes maneres penso que aquest és el camí, mirar les coses "tontes"; perquè se'm fa molt extrany que les tres versions anteriors hagin funcionat de conya i la més nova, la última, sigui la que peti. 
Seguiré investigant a veure que pot ser.

Moltes gràcies.

---

### Post by wgarcia on 2010-10-20
Segons els resultats que has penjat tens dues targetes de so, una d'Intel i l'altra de NVIDIA. Suposo que hauràs provat amb les dues (pots escollir quina usar des de l'indicador de so del panell de dalt) i tampoc t'has sortit. 

Una altra possibilitat és entrar a la configuració del BIOS abans d'arrencar el sistema i veure si pots deshabilitat una d'aquestes targetes a veure si entrant amb una sola el sistema acaba fent algun so.

---

### Post by Quepotser on 2010-10-20
Bona tarda. Sí, ja ho havia provat, però no canvia res. Hi ha però una cosa, si més no, curiosa: amb el Lucid tan sols me n'apareix una, de la Nvidia ni rastre.

Tocar la BIOS em fa una mica de respecte i prefereixo esgotar altres possibilitats abans que aquesta.

De totes maneres, haig de confessar que estic una mica perdut (molt, vaja).
Estic pensant de baixar-me la versio de 32 i provar a veure com va.

Si fos el cas, miraré de veure què puc fer amb la BIOS.

De totes maneres, gràcies.

---

### Post by Quepotser on 2010-10-20
Rectifico la última entrada: en el Lucid **SÏ[B] que apareixen les [B]dues**targetes. Perdoneu l'error.

---

### Post by wgarcia on 2010-10-20
A la BIOS no has de fer res més que mirar en el programeta de configuració que pots obrir quan està arrencant l'ordinador a veure si et deixa deshabilitar per la sessió alguna de les dues targetes de so.

---

### Post by Quepotser on 2010-10-21
Bon dia.

He descobert que per inactivar una targeta de so no cal tocar la BIOS, n'hi ha prou anant a SO-->PREFERENCIES DEL SO-->MAQUINARI i, seleccionada la targeta que es vol anular, clicant el botó "Perfil" es desplega un menú en el qual la primera opció és "Inactiu". Si s'escull aquesta opció la tarja queda inhabilitada.

La veritat és que mai havia remenat tant l'ubuntu, tampoc n'havia tingut necessitat.

---

### Post by wgarcia on 2010-10-21
Pel que dius dedueixo que segueixes igual, tot i que has provat de cancel·lar les targetes de so per torn a veure si amb una sola et retornava el so, no ha passat res. 

Si vols remenar una mica més, instal·la "padevchooser" que et permetrà mirar una mica més les configuracions de pulseaudio. Si obres aquesta aplicació et sortirà una icona al panell de dalt, i aquí tens un altre "control de volum" on pots mirar si els volums rellevants estan actius. Té altres coses per configurar el pulseaudio a veure si hi ha alguna cosa que no estigui habilitada i que t'estigui causant aquest problema.

---

### Post by Quepotser on 2010-10-21
Bona nit.

   Efectivament, segueix tot igual després d'haver activat i desactivat les targetes. També m'he baixat la versió de 32 bits i tot continua igual. Hi ha, però alguna informació nova: fent servir el control de volum a  "padevchooser" i, intentant reproduir un fitxer de música, sí que les barres de volum reflecteixen l'activitat, o sia, es com si el pulseaudio estigués treballant, però com si el so no arribés als altaveus (espero que s'entengui l'explicació).
   No sé què deu ser, però sembla que és quelcom que ve amb el Maverick, perquè el so tampoc funciona amb els CD. M'estic plantejant d'enviar un bug al Launchpad però m'agradaria ser una mica més concret i no limitar-me a dir "no funciona el so".

---

### Post by wgarcia on 2010-10-22
I no serà algun problema de cableig cap als altaveus? Ho dic perquè a mi em va passar un cop que pensava que m'havia quedat sense so i era un problema de la connexió amb els altaveus. Has provat amb auriculars? Són tots coses idees molt simples com veus, però qui sap...

---

### Post by kimet on 2010-10-22
Així ho vaig aconseguir jo en portàtils amb targeta intel_HDA.

```
lsmod | grep snd 
```
Si apareix carregat el mòdul snd_hda_intel


Pots provar aquest procediment:

instal·lar alsa:
```
# apt-get install alsa-base alsa-oss alsa-source apmd alsa-utils linux-sound-base apmd oss-compat xapm
```
instal·lar pulseaudio:
```
# apt-get install pulseaudio gstreamer0.10-pulseaudio libasound2-plugins 
```
recarregar alsa:
```
# /usr/sbin/alsa reload
```

I comprova que els controls siguin master hda_intel


Salut

---

### Post by Quepotser on 2010-10-22
Bon dia.

No ho crec, perquè amb el Lucid va de conya. De fet, el Maverick, l'he instal·lat tan sols per veure com va, per "tafanejar", però en el meu dia a dia faig servir el Lucid i, en principi, no penso canviar-lo fins l'abril del 2012 quan surti la propera LTS.
En quant a lo de coses simples estic d'acord amb tú: segur que és una "pocasoltada", però noi, fa la guitza d'allò més. Seguiré investigant totes les estones, en les que tingui temps per fer-ho.
Pel que fa al tema del fil dir-te que en algún lloc (no em vaig apuntar on) he llegit que pot ser cosa del kernel i que una solució transitoria seria fer servir el 2.6.32. El problema es que al synaptic no hi és.

---

### Post by Quepotser on 2010-10-22
Bon dia.

Kimet he provat de fer això que m'indiques però a l'última ordre em respon que no troba ni el directori ni el fitxer. He intentat trobar-lo amb el Nautilus i tampoc ho he aconseguit.

---

### Post by kimet on 2010-10-22
> **Quepotser said:**
> Bon dia.

Kimet he provat de fer això que m'indiques però a l'última ordre em respon que no troba ni el directori ni el fitxer. He intentat trobar-lo amb el Nautilus i tampoc ho he aconseguit.

Em sembla que l'has de tenir a no ser que Maverick hagi canviat molt, que no ho crec.
```
locate /usr/sbin/alsa
```
Has instal.lat alsa-base?
Ho has fet com a root?

Salut.

---

### Post by Quepotser on 2010-10-22
Bona tarda. 

Sí, he instal·lat l'alsa-base i ho he fet com a root (si no, no m'ho deixa fer). Es més, si provo de instal·lar-ho, em diu que ja està instal·lat en la seva versió més nova:

sudo apt-get install alsa-base alsa-oss alsa-source apmd alsa-utils linux-sound-base apmd oss-compat xapm
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
alsa-base ja es troba en la versió més recent.
alsa-utils ja es troba en la versió més recent.
apmd ja es troba en la versió més recent.
linux-sound-base ja es troba en la versió més recent.
alsa-oss ja es troba en la versió més recent.
alsa-source ja es troba en la versió més recent.
oss-compat ja es troba en la versió més recent.
xapm ja es troba en la versió més recent.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.


En quant a "locate /usr/sbin/alsa" no em retorna res.

---

### Post by Quepotser on 2010-10-26
Bon dia a tothom.

Continuant amb el tema del Maverick, he aconseguit que recarregués l'ALSA tal com em deia en Kimet, però suprimint de la ruta el **/usr** i el resultat que em dona és aquest:


 sudo /sbin/alsa reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lespedretes/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1721(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-nvhdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release

Per la meva part no acabo d'entendre, ben bé, que significa l'avís.

---

### Post by wgarcia on 2010-10-26
Un altre suggeriment que no sé si has provat. Entra al Gestor de Paquests Synaptic, i habilita el dipòsit dels "backports" (al menú Configuració -> Fonts de programari -> altres fonts de programari). 

Un cop fet això instal·la "linux-backports-modules-alsa-maverick-generic" a veure si això soluciona el teu problema de so.

---

### Post by Quepotser on 2010-10-26
Bona nit. 

Ja he fet el que m'has dit, més ben dit: he vist que ja tenia instal·lat aquest paquet i per tant no canvia res.

Si a algú se li acudeix alguna cosa que pugui fer no dubteu en fer-m'ho saber, mentestant moltes gràcies a tots els que us preneu la molèstia d'intentar sol·lucionar aquest problema. Repeteixo, moltes gràcies.

---

### Post by kimet on 2010-10-26
El metode amb pulseaudio m'ha funcionat be últimament, en cas de que no et funcioni pots provar a desinstal.lar pulseaudio i seguir un altre sistema editant el fitxer /etc/modprobe.d/alsa-base.
Mirat aquests enllaços:
[http://www.ubuntu-es.org/node/100243](http://www.ubuntu-es.org/node/100243)
[http://www.esdebian.org/wiki/sin-sonido-tarjetas-hdaintel](http://www.esdebian.org/wiki/sin-sonido-tarjetas-hdaintel)
Revisa si tens carregat el mòdul snd_hda_intel.

---

### Post by Quepotser on 2010-11-28
Bona nit a tothom.

Bé, sembla ser que ja he trobat una sol·lució per al problema del so a l'ubuntu maverick. Després de provar moltes coses (algunes molt enrevessades) el problema es resol (per a mi) fent el que diu en aquest post:
[URL=http://www.ubuntu-es.org/node/144405#comment-408844[/URL] que, ves per on, es bastant senzill. La questió, però, no ha quedat resolta perquè a linuxmint 10 i ha fedora 14 passa exactament el mateix i, curiosament ambdues porten el mateix kernel. No sé si deu anar per aquí la cosa però no costa res dir-ho. Jo, per la meva part, intentaré esbrinar-ho. Marco aquest fil com a SOLVED

EDITO: Abans de que m'ho deixi: gràcies a tothom per la paciència ,l'esforç i el temps que heu dedicat a aquest problema

---

