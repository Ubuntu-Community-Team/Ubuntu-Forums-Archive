---
title: "Sobre particions i sistemes de fitxers"
date: 2007-02-22
forum: Catalan Team
---

### Post by _61_ on 2007-02-22
Hola a tothom,

Fa uns mesos que vaig decidir posar-me un Ubuntu al portàtil i el que és més important... Entrar per defecte en Ubuntu i aprendre a fer les coses en Ubuntu, encara que al principi em costi una mica. La veritat és que estic satisfet i ho recomano a tothom. Ara m'he atrevit a registrar-me al fòrum i escric la primera de motes preguntes que vindran... ;)

Al principi, amb la timidesa i la ignorancia d'un principiant, vaig decidir que les particions que faria serien: 
[LIST]
[*]una per al vell Windows (per si de cas...)
[*]una per al Ubuntu (+ una per al Swap)
[*]una per als documents
[/LIST]

Després de llegir [això]("http://www.psychocats.net/ubuntu/partitioning") he decidit que potser seria bo crear una partició més per al /home...

Què us sembla això? I com ho farieu això?

I una segona cosa... Abans de posar l'Ubuntu, la partició del Windows tenia sistema de fitxers FAT32 i la dels Documents tenia NTFS. (L'Ubuntu el vaig posar sobre EXT3)

Quan vaig començar, no em deixava grabar documents i vaig canviar (en un moment de bogeria, no recordo com) la partició dels documents a FAT32.

Ara, voldria canviar aquesta partició de FAT32 a EXT3, perquè des del Windows podria accedir-hi gràcies al programa [Fs-driver]("http://www.fs-driver.org/") i crec que així el Linux anirà més fi.

Podrieu explicar-me com ho podria fer això? (Tinc un disc dur extern molt gros per poder fer còpies de seguretat, per si de cas...)

Ja ho veieu, dues preguntes de principiant, però ningú no neix ensenyat, no?

Gràcies,

61

---

### Post by RainCT on 2007-02-22
Hola _61_,

Per tal de posar l'home a una altre partició primer de tot crea aquesta. Llavors només has de copiar-hi tot el contingut de la carpeta 'home' i per acabar editar l'arxiu /etc/fstab afegint-hi la nova partició amb /home com a punt de muntatge. Pots trobar informació més detallada a la conversa anomenada "Dubtes: transferir /home a una partició" que hi ha hagut a la llista de distribució, consultable des d'[aquest arxiu]("https://lists.lafarga.cpl.upc.edu/pipermail/ubuntucat-info/2007-January/thread.html").

Per canviar la partició de FAT32 a EXT3 diria que has de copiar tot el seu contingut a un altre disc o partició i llavors formatejar-la (mitjançant el GParted o algun altre programa). Finalment torna a copiar-hi tot el que hi havia.

No se si tens algun motiu per utilitzar dos particions, però jo de tu utilitzaria la mateixa com a /home i per les dades.

---

### Post by chalimac on 2007-02-22
Aquí tens una guia per transferir el /home a una partició:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by _61_ on 2007-02-22
Ostres!

M'estic mirant aquesta pàgina ([http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")) però encara no havia llegit tant avall...

Moltes gràcies RainCT i chalimac, aquest cap de setmana m'hi poso.

---

