---
title: "Micro extern que no va"
date: 2009-02-21
forum: Catalan Team
---

### Post by lpargemi on 2009-02-21
Hola

A casa tenim un portàtil HP ce la sèrie Compaq nx 7300, amb ubuntu 8.4 (Hardy) instal.lat. Volem fer anar un microfon extern connectat a l'entrada (amb un connector d'aquests tipus jack) i el cas és que no hi ha manera.

He instal.lat alsamixer, l'executo, i el cas és que no hi ha manera d'habilitar el canal que suposo que és l'entrada del micro. Ni amb enter, ni amb tabulador, ni amb control, ni de cap de les maneres que recomanen al programa (us adjunto la pantalla de alsamixer).

Alguna idea?

---

### Post by Diegstroyer on 2009-02-21
Saultacions, mira't aquest [blog]("http://gambasconchocolate.blogspot.com/2009/01/problemas-de-audio-en-hardy.html") a veure si funciona. És per Skype, però la forma d'activar el micro potser t'interessa.

Ja diràs a veure que tal.

---

### Post by lpargemi on 2009-02-21
Agraït per la idea, però he provat amb el pulseaudio com recomanen al blog, i segueix sense anar.

Lluís

---

### Post by Diegstroyer on 2009-02-21
Has clicat sobre la opció Captura i has pujat els nivells?

---

### Post by lpargemi on 2009-02-21
> **Diegstroyer said:**
> Has clicat sobre la opció Captura i has pujat els nivells?

L'opció capture d'on?

Amb el gstreamer-configure he declarat actiu l'origen de pulse audio

Amb gnome-configuration també he fel alguna cosa semblant, però no he vist enlloc per pujar cap volum de captura. 

El de l'altaveu, si que el tinc aixecat des de sempre que ho he provat

lluís

---

### Post by Diegstroyer on 2009-02-21
Boto dret sobre l'altaveu de la barra d'eines-->obre controlador de volum-->Edita-->Preferencies. Aquí marca la opció de captura, ara apareix una nova pestanya al Controlador de Volum que diu Enregistrament. Ho deia en el tutorial del blog on has anat (has d'activar totes les opcions de Micròfon.

En l'apartat de Reproducció has de tenir en Silenci el Micròfon, si no fa sorolls extranys.

---

### Post by lpargemi on 2009-02-21
Hola de nou, i gràcies per la paciència.

Tot això ja ho havia fet, però segueix sense funcionar. Per cert que amb *Botó dret sobre l'altaveu de la barra d'eines-->obre controlador de volum* se m'obre el programa "HDA Itel (Alsa Mixer)" segons diu a la barra d'identificació.
 
No sé si és que els drivers de la placa base no estan suportats,o així... i per això no hi ha manera.

Lluís

---

### Post by Diegstroyer on 2009-02-21
Proba a veure si això et funciona: Sistema-->Preferencies-->So i a la captura posa Servidor de PulseAudio.

Doncs jo he acabat de configurar avui completament el PulseAudio i em funciona tot a la perfecció, si vols, i tens paciència, pots intentar fer [aixó]("http://ubuntuforums.org/showthread.php?t=789578"). A mi m'ha funcionat al 100%.

Ara no tinc problemes d'àudio de cap tipus i puc fer servir totes les aplicacions que utilitzen l'àudio a la vegada (s'escolten tote alhora!).

Això que et surt amb el botó dret es normal, identifica correctament la tarjeta de so, a mi em posa Intel ICH6 (Alsa mixer)

---

### Post by lpargemi on 2009-02-23
Hola Diegstroyer,

Fa estona que no dic res, però és que l'enllaç que em vas passar és abassegador. He fet el què diu al post, i m'he quedat penjat en la hipòtesi B de l'apèndix A, em sembla: sona música, però no aconsegueixo res a la llista del Playback. És un post amb més de 100 pàgines de rèpliques, així que suposo que per algun lloc hi explicarà com em cal seguir... llàstima per no saber més anglès. i ho resolc us ho explico

Lluís

---

### Post by Diegstroyer on 2009-02-25
A veure si ens en sortim, t'envio unes captures de com ho tinc jo.

---

### Post by lpargemi on 2009-02-25
Hola, 

Ho tinc tot com a les teves captures, excepte que tinc menys controladors i suposo que menys harware. A la captura 1 hi ha la mesura del Volume Meter recording, i el cas és que les barres es mouen com el micro (pugen si hi bufo, per exemple) però no ho puc sentir enlloc més.

Tinc seleccionada la captura, i el micròfon.

T'envio les pantalles dem Manager, perquè admeto que no m'hi entenc amb res del què m'hi diuen

lluís

---

### Post by Diegstroyer on 2009-02-26
Pel que veig a la captura 1, tens activada la reproducció del micro, aquí ha d'estar desactivada (ja que si no reprodueix pels altaveus el que enregistra de forma immediata). Has d'activar el micro a la pestanya d'enregistrament.

En Aplicacions-->So i video, hi ha un enregistrador de micròfon per que facis proves.

Estats pel bon camí, només es cosa de configuració. si aconsegueixes que et funcioni però el so sona com trencat (com si trenquessis papers davant del micro), es problema de que tens el volum del dispositiu d'entrada de pulseaudio massa alt.

Vinga, que ja ho tens.

PD: si et fixes en la captura 3, quan algún dispositiu utilitza l'audio (tant en captura con en sortida) apareix un número, si hi cliques a sobre amb el botó dret, pots configurar els paràmetres d'audio per a cada aplicació de forma independent de la resta :) molt útil!

---

### Post by lpargemi on 2009-02-26
Finalment ja funciona i ja puc gravar!

Ha costat, però al final apagant els micros que m'has comentat això ha xutat.

Molt Agraït

Lluís

PD. Veig que no puc penjar el SOLVED. És que ja no es porta això?

---

### Post by lo gambusí on 2009-02-26
Crec que amb la darrera actualització del fòrum va deixar de funcionar.

---

