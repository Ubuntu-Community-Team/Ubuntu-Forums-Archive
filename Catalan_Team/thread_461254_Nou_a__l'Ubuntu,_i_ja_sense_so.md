---
title: "Nou a  l'Ubuntu, i ja sense so"
date: 2007-06-01
forum: Catalan Team
---

### Post by Urfe on 2007-06-01
Hola.

Fa uns dies que m'he instal·lat l'Ubuntu compartit amb el Windows XP. Començo l'aventura del linux!!

Però ja tinc problemes. El primer dia em funcionava el so de les cançons i películes, però ara ja no.

A l'entorn Windows si em funciona.

Alguna suggerència?

Gràcies.

---

### Post by papapep on 2007-06-01
Doncs si: que vagis a Aplicacions > So i vídeo >  Mesclador Alsa de Gnome i comprovis que tens tots els volums, com a mínim, a mitja alçada i que no tens res marcat com a "Silencia".
Si així tampoc et funcionés, pots provar-ho al mesclador en consola, ja que temps enrera hi havia un bug que feia que el mesclador gràfic no acabés de fer el fet:

A un terminal, com a usuari normal, executa "alsamixer", i t'apareixerà un mesclador de text (curiós, oi?) on amb les fletxes esquerra-dreta pots anar canviant de control, i amb amunt-avall podràs pujar o baixar el volum.

A veure què tal.

---

### Post by Urfe on 2007-06-02
Gràcies pel consell.

Però és que a Aplicacions - So i video - no apareix aquest opció de Mesclador Alsa de Gnome. El que apareix és Creador de CDs Serpentine, Extractor de musica de CDs Sound Juicer, Gravador de sons, Reproductor de musica Rhythmbox i Reproductor de películes Totem.

¿?

La veritat és que tampoc sé com s'exectuta Alsamixer.

---

### Post by papapep on 2007-06-02
1.- Doncs obres un terminal: Aplicacions > Accessoris > terminal, i hi poses "alsamixer" (sense les cometes, clar), prems intro i, voilà!! l'alsamixer funcionant.

2.- Si no t'apareix, serà que no el tens instal·lat, cosa no gaire normal. Aleshores, al mateix terminal, teclejes "sudo aptitude update", i quan acabin d'aparèixer coses rares i tornis a tenir el cursor esperant-te teclejes "aptitude install alsamixer" i ja el tindràs instal·lat. Ja pots tornar a fer el pas 1.

---

