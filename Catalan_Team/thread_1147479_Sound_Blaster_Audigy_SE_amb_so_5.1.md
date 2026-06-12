---
title: "Sound Blaster Audigy SE amb so 5.1"
date: 2009-05-03
forum: Catalan Team
---

### Post by Turtun on 2009-05-03
Hola a tots! 

Tinc l'Ubuntu 8.10 i la targeta de so Sound Blaster Audigy SL (ca0106)

Després de moltes proves amb la configuració d'Alsa he arribat a un punt força correcte. Però aquí ve el problema:
Si deixo buits els arxius asound.conf i .asoundrc tinc so a 2 altaveus però puc obrir múltiples sons alhora (Rhythmbox i VLC per exemple).

Després de trastejar aquests arxius he aconseguit so als 6 i poder graduar el so per cada canal, per fer-ho vaig seguir aquests passos:
1.- Instalar GNOME Alsa Mixer
2.-Modificar/crear els arxius asound.conf (carpeta /etc) i .asoundrc i editar-los amb aquestes línies:

[I]pcm.ca0106 {
type hw
card 1
}

ctl.ca0106 {
type hw
card 1
}
pcm.!default {
slave.pcm surround51
slave.channels 6
type route
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}
[/I]

3.- He afegit aquesta línia a /etc/pulse/default.pa

*load-module module-alsa-sink device=”surround51? channels=6 sink_name=sur51*

4.- Comprovar amb la línia d'ordres: "*speaker-test -c6 -l1 -twav -D surround51*" si m'acostava i efectivament em canta els 6 canals correctament i puc graduar el volum per separat de cada altaveu (cosa que m'interessava molt perquè els de darrere els tinc molt lluny).


El problema és que amb aquesta configuració no tinc so al Firefox, a l'únic joc que tinc (WoW a través de Wine) i torno a perdre els múltiples sons (només puc sentir un programa).

El que encara és més curiós es que si substitueixo la línea "*pcm.!default {*" per aquesta altre "*pcm.ch51dup {*" torno a tenir so a tot i múltiples sons però altre cop en estèreo només, inclús amb arxius de so 5.1 que són els que utilitzo per fer les probes. Amb aquesta última configuració l'ordre: "*speaker-test -c6 -l1 -twav -D surround51*" segueix cantant correctament els 6 altaveus tot i que després no sonin amb re.

Soc novell en Ubuntu però porto prou temps capficat en deixar el tema de so completament adobat com per començar-me a desesperar (i més tenint en compte que vaig comprar la tarja de so especialment, perquè se suposa que està completament suportada per aquesta distribució i en canvi la integrada a la meva placa no tenia suport). Crec que estic força aprop de la solució però ara ja, per més que busco i llegeixo... no se trobar la solució final.

Si algú sap com donar-me un cop de mà, de cor que ho agrairé.

Anticipadament, moltes gràcies a tots.

---

### Post by marteljorge on 2009-05-03
Saps anglès? Potser algú hagi solucionat un problema semblant al fórum en anglès.

---

### Post by marteljorge on 2009-05-03
He trobat en ubuntu-es un problema amb una targeta que té el mateix chip:
[http://www.ubuntu-es.org/?q=node/84798](http://www.ubuntu-es.org/?q=node/84798)

---

### Post by Turtun on 2009-05-03
Gràcies per respondre Jorge,

La veritat és que el meu anglès és força justet així que, tot i que si no m'escurcen paraules ni usen argot si que caço força coses, la veritat és que m'he limitat molt més a buscar coses en idiomes de major comprensió per mi ;P

De totes maneres, gràcies a l'enllaç que m'has marcat, he descobert un altre fet curiós i és que en els desplegables de Sistema/Preferències/So, depenent del "*Audigy SE [SB0570] CA0106 (ALSA)*" que marco (en tinc 4 ) em sonen el canal de debant, el central, el de darrere o el subwofer. Així que te tota la pinta de deixar-me els canals separats en aquesta selecció. Si ho deixo en "*Detecta Automàticament*" o en "*ALSA- Avanced Linux...*" m'agafa els 2 de debant (o deixa en un estèreo normal.
Amb això la veritat que no m'hi havia fixat.

La veritat és que d'informació n'hi ha força ja que es una targeta de so que usa un chip força corrent, però no hi ha manera, hauré enganxat la punyetera...

Seguirem buscant i de nou gràcies per l'ajud.

---

### Post by marteljorge on 2009-05-03
> **Turtun said:**
> Gràcies per respondre Jorge,

La veritat és que el meu anglès és força justet així que, tot i que si no m'escurcen paraules ni usen argot si que caço força coses, la veritat és que m'he limitat molt més a buscar coses en idiomes de major comprensió per mi ;P

De totes maneres, gràcies a l'enllaç que m'has marcat, he descobert un altre fet curiós i és que en els desplegables de Sistema/Preferències/So, depenent del "*Audigy SE [SB0570] CA0106 (ALSA)*" que marco (en tinc 4 ) em sonen el canal de debant, el central, el de darrere o el subwofer. Així que te tota la pinta de deixar-me els canals separats en aquesta selecció. Si ho deixo en "*Detecta Automàticament*" o en "*ALSA- Avanced Linux...*" m'agafa els 2 de debant (o deixa en un estèreo normal.
Amb això la veritat que no m'hi havia fixat.

La veritat és que d'informació n'hi ha força ja que es una targeta de so que usa un chip força corrent, però no hi ha manera, hauré enganxat la punyetera...

Seguirem buscant i de nou gràcies per l'ajud.

Et recomano que cerquis pel chip i no pel model de la targeta, cercant la targeta els resultats no són gaire bons.

---

### Post by quitus on 2009-05-03
No crec que afecti gaire, però jo vaig instal·lar una tarja de so i fins que no vaig desactivar la de la placa base (des de la bios) no vaig obtenir bons resultats.

salut

---

### Post by Turtun on 2009-06-29
Bé ja ho he solucionat i per aconseguir-ho he fet el següent:

**1r.** Descarregar alsa-driver-xxx, alsa-lib-xxx i alsa-utils-xxx desde **[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)**

**2n.** Amb la ordre "gksudo nautilus" obrim un nautilus amb tots els permisos i copiem els arxius baixats a la carpeta "alsa" que crearem a /usr/src

**3r.** Tanquem el nautilus o obrim un altre terminal.

**4t.** Comencem la instal·lació:

       cd /usr/src/alsa
       bunzip2 alsa-driver-xxx
       tar -xf alsa-driver-xxx (aqui sense l'extensió bz2)
       cd alsa-driver-xxx
       ./configure --with-cards=ca0106 --with-sequencer=yes ; make ; make install

       cd ..
       bunzip2 alsa-lib-xxx
       tar -xf alsa-lib-xxx (aqui sense l'extensió bz2)
       cd alsa-lib-xxx
       ./configure ; make ; make install

       cd ..
       bunzip2 alsa-utils-xxx
       tar -xf alsa-utils-xxx
       cd alsa-utils-xxx
       ./configure ; make ; make install


**5è.** Creem un fitxer de nom "conf.modules" i l'editem amb:

       # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-ca0106
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

**snd-card-0 en el cas que sigui la tarja de so primària, si en tenim més d'una, mirem quin és el numero que toca i l'editem si cal.*


**6è.** Copiem aquest arxiu a "/etc" amb el terminal o amb "gksudo nautilus" i actualitzem amb "update-modules"


**7è.** Creem un arxiu de nom ".asoundrc" que guardarem a "root" o a "home" i l'editem amb:

	pcm.ca0106 {
	   type hw
	   card 0
	}
       
	ctl.ca0106 {
	   type hw
	   card 0
	}

	pcm.ch51dup {
	slave.pcm surround51
	slave.channels 6
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
	ttable.0.4 0.5
	ttable.1.4 0.5
	ttable.0.5 0.5
	ttable.1.5 0.5               route_policy duplicate
	}


**8è.** Comprovem al "Sistema/Preferències/So" que tinguem seleccionat per a tot excepte per al mesclador, "ALSA - Advanced Linux sound Architecture"
També cal comprovar al mesclador (icona de l'altaveu a la dreta de la barra) que no estiguin seleccionats cap dels "IEC" però **_SI_** tots els Analog que toquin i alçar el volum dels que estiguin baixats.

**9è.** Al VLC (només ho he configurat en aquest reproductor), anem a "Tools/Prefereces/Audio" i on posa "Output" a "Type" seleccionem "ALSA audio output"
Un cop fet tot, si estem reproduint un arxiu que sabem segur que és 5.1 però no funciona com a tal, només anant al menú "Audio/Device" i seleccionant el 5.1, ja tenim el problema resolt.


Espero que li serveixi d'ajuda a algun novell, tant gran com jo, per solucionar aquest molest problema.

P.D.: Voldria canviar el títol del post a Sound Blaster Audigy SE amb so 5.1 i marcar-lo com a SOLUCIONAT però no se com fer-ho, disculpeu les molèsties.

Gràcies per l'ajud.

---

### Post by papapep on 2009-06-29
Canviat. I gràcies pel teu apunt tant detallat ;)

---

