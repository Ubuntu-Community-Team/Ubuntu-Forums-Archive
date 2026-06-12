---
title: "Midi i Jack (Rosegarden)"
date: 2011-06-16
forum: Catalan Team
---

### Post by bellera on 2011-06-16
Hola!

Estic barallant-me amb la 10.04 LTS (Lucid Lynx) per fer anar Rosegarden i altres aplicacions musicals que facin servir Jack.

Si no ho tinc mal entés la configuració per defecte és:

Tarja de so -> ALSA -> PulseAudio

Tot i trobar moltes planes que en parlen no he aconseguit, per cap via, fer treballar PulseAudio i Jack junts:

Tarja de so -> ALSA -> PulseAudio -> Jack

He de "matar" Pulseaudio perquè em funcioni Jack. En el control de Jack poso **pulseaudio -k** abans d'arrancar Jack i **pulseaudio -D** després de tancar Jack. Llavors el que tinc és:

Tarja de so -> ALSA -> Jack

Una mica incòmode però fa que Rosegarden funcioni. Però no sento res, en reproduir un Midi.

Alguna idea?

Hi ha algú fent informàtica musical amb 10.04 LTS ? O hauré de muntar una 10.04 Studio?

El meu problema és que són 300 miniportàtils!

Gràcies!

Josep Pujadas i Jubany
Coordinador TIC/TAC de [www.bellera.cat](www.bellera.cat)

---

### Post by bellera on 2011-06-17
Bé,

Em contesto a mi mateix...

He tingut una resposta de la llista [http://llistes.cpl.upc.edu/listinfo/ubuntucat-info](http://llistes.cpl.upc.edu/listinfo/ubuntucat-info) i estic treballant en tot el que m'han dit.

He descobert, però, gràcies als companys de LinKat que Rosegarden pot funcionar sense Jack:

[http://linkat.xtec.cat/portal_linkat/wikilinkat/index.php/M%C3%BAsica_i_configuraci%C3%B3_midi_a_la_Linkat_3#Configuraci.C3.B3_del_Rosegarden](http://linkat.xtec.cat/portal_linkat/wikilinkat/index.php/M%C3%BAsica_i_configuraci%C3%B3_midi_a_la_Linkat_3#Configuraci.C3.B3_del_Rosegarden)

O sia que de moment he aconseguit funcionar simplement seleccionant el dispositiu MIDI correcte a Rosegarden:

[http://www.bellera.cat/josep/musica/rosegarden_gestiona_dispositius_midi.png](http://www.bellera.cat/josep/musica/rosegarden_gestiona_dispositius_midi.png)

Segueixo tenint molts dubtes i/o problemes amb tota aquesta parifernàlia de servidors de so i connectors. Si hi ha algun especialista...

A reveure,

Josep Pujadas i Jubany
Coordinador TIC/TAC de [www.bellera.cat]("http://www.bellera.cat/")

---

