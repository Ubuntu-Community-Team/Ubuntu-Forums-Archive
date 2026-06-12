---
title: "com configurar microfons inteterns del portatil"
date: 2009-07-02
forum: Catalan Team
---

### Post by auska1714 on 2009-07-02
Bones gent,

tinc un problema (que raro... xD)

No se com activar els micros del portàtil. Quan vaig al controlador de volum- enregistrament, em diu que estan desactivats. Els activo. Surto i tornen a estar desactivats.t

Per altra banda quan faig Alsamixer al terminal em diu que està activat. I a més té el so al màxim possible avanç de que es posi la barra vermella.

Aviam que mi podeu fer,

Moltes gracies

Salut!

---

### Post by lpargemi on 2009-07-05
Hola

No dones masses pistes, ni versió d'Ubuntu, ni ordinador ni res. Així és difícil que se't pugui donar un cop de mà.

Jo vaig tenir problemes amb un portàtil i l'Alsa Mixer fent anar Hardy. Es va resoldre fent-lo anar amb pulseaudio

A aquest fil hi ha les meves cuites en aquell cas:

[http://ubuntuforums.org/showthread.php?t=1076338]("http://ubuntuforums.org/showthread.php?t=1076338")

A veure si et serveix d'alguna cosa

Salut

Lluís

---

### Post by akyra on 2009-07-06
Hola auska1714

A mi em pasa el mateix des de varies versions d'ubuntu, en la 8.04 ho vaig poder solucionar compilant els drivers d'alsa, però després en la 8.10 i en la 9.04 no he trobar la solució, totes les distribucions són de 64 bits.

Crec que és molt important que diguis quin chipcard tens.

Prova de fer això:
**aplay -l**
o també pots probar:
**cat /proc/asound/card0/codec#* | grep Codec **

La sortida d'aquests comandos hauria de donar-te el tipus de chip card que tens, i a les hores trobar més informació

Jo encara no he pogut solucionar-ho.

Ja diràs con et va.

Salutacions.

---

### Post by auska1714 on 2009-07-06
aviam anem per parts, l'ubuntu es el 9.04. I l'ordinador es un Acer aspire 5920. 

Quan executo al terminal la comanda aplay -l, em surt:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

En fer, cat /proc/asound/card0/codec#* | grep Codec, em posa:

Codec: Realtek ALC1200
Codec: Conexant ID 2c06

I per acabar, adjunto una imatge dels controladors que crec que s'haurien d'activar però que em porten el problema. Segurament per tema de drivers. 

[IMG]http://img210.imageshack.us/img210/3872/16191006.jpg[/IMG]

Aviam que podem fer, moltes gràcies

Joel

---

### Post by akyra on 2009-07-06
Prova a fer això:
sudo gedit /etc/modprobe.d/hda_intel.conf

i després li poses aquesta opció dins del fitxer:
options snd-hda-intel model=auto probe_mask=1

Reinicies, i a veure si tens sort.

Tens els linux-backports instalats? Podrien ser una solució.

Salutacions.
 (ho he tret d'aquí [http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149"))

---

### Post by auska1714 on 2009-07-07
Fent això que deies de sudo gedit /etc/modprobe.d/hda_intel.conf .......
no funciona. I per altre banda això del linux-backports no en tenia instel·lat cap. I com que no sabia quin era, he instal·lat tots els que hi havia als respositoris... Que he de fer ara... O hauria d'haver funcionat "automaticament"??

Moltes gràcies,

Salut!

---

### Post by akyra on 2009-07-09
Crec que ja t'hauria d'haver funcionat.

Jo tinc un altre model d'ordinador i de chipset i també he intentat fer els pasos i tampoc em funciona. Em pasa com a tu que surten sempre desactivats els micros, i encara que els torni a activar tornen a sortir desactivats.

Aquesta solucio que et vaig donar funcionava bé a moltisima gent, excepte a nosaltres dos, jo la veritat, no sé que més fer, però segueixo buscant posibles solucions.

El cas es que els drivers deuen estar ben instal·lats, ja que si parlo pel microfon em sento pels auriculars o pels altaveus, però no hi ha manera de grabar. També puc escoltar perfectament música i pelicules.

Si trobés alguna altra opció prova.

Et paso l'ultima cosa que he provat, mira si a tu et va bé:
[http://ubuntuforums.org/showthread.php?t=943791]("http://ubuntuforums.org/showthread.php?t=943791")

Salutacions.

---

