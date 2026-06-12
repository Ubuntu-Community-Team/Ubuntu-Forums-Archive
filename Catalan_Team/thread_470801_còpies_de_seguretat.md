---
title: "còpies de seguretat"
date: 2007-06-11
forum: Catalan Team
---

### Post by CanTimba on 2007-06-11
Bones a tothom!

He perdut les dades d'un disc dur que ,segons sembla, s'ha fet malbé físicament.
No voldria tornar a passar el disgust que això ocasiona.
Per això pregunto, com puc fer còpies de seguretat amb l'ubuntu? és una tasca programable?

jordi

---

### Post by PellRoja on 2007-06-11
has mirat de recuperar-lo? o ja esta mort del tot? hi han eines per recuperar dades de disc durs.

per fer copies de seguretat jo o faig manualment gravant a DVD les dades. Pero algun programa i deu haver.

---

### Post by papapep on 2007-06-11
Depen molt de quin suport vulguis fer servir per a fer les còpies. Per a fer-les a un altre disc dur, per exemple, extern, hi ha un programa, que es diu Unison, que va molt i molt bé, i a més és multiplataforma i senzill d'utilitzar.

Pots veure'n informació, i descarregar-lo, a:

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

### Post by epileg on 2007-06-12
Si el que vols és un programa simple, fàcil de configurar i per a gnome, 'sbackup' és una bona opció.

salut,
Epíleg.

---

### Post by CanTimba on 2007-06-12
Vaig provar de reinstal·lar el windows i no hi va haver manera d'entrar amb l'opció de la consola de recuperació.
Tampoc el vaig poder formatejar des de la instal·lació de Windows.
Està mort?
Quines són aquestes eines de recuperació de dades, Pellroja?

jordi

---

### Post by PellRoja on 2007-06-12
és possible que el disc dur s' hagi mort. Pero per intentar-ho que no quedi.

Les que he provat jo son pagan, no se si existeixen de lliures

mira cercan a softonic pots trobar això [http://www.softonic.com/s/recuperacion-de-datos](http://www.softonic.com/s/recuperacion-de-datos)

no et poso el programa que faig servir per que no el trobo, es diu file recovery, algun cop m' ha anat be, pero d' altres no si ha pogut fer res.

Sort!

---

### Post by lpargemi on 2008-01-22
> **epileg said:**
> Si el que vols és un programa simple, fàcil de configurar i per a gnome, 'sbackup' és una bona opció.

salut,
Epíleg.

Hola

No sé si és del cas reobrir un fil penjat des de fa temps, però com que no té el "Solved"....

M'interessa fer unes còpies del sistema que funciona, per fer proves, o per canviar de versió (encara estic a la feisty) o per precaució per si rebenta tot per sorpresa. 

Suposo que amb el programa aquest es fa la còpia que es guarda, per exemple, a un DVD. 

La pregunta que faig és: suposant que tot rebenti, com es restaura la darrera còpia que tinc en un DVD?

Agraït

Lluís

---

### Post by papapep on 2008-01-22
Tot depèn del que vulguis fer. Si el que vols és fer una instantània de l'ordinador, sistema operatiu inclós, doncs el [partimage]("http://www.partimage.org/Main_Page") (a lo bèstia la ordre **[dd]("http://manpages.debian.net/cgi-bin/man.cgi?query=dd&apropos=0&sektion=0&manpath=Debian+Sid&format=html&locale=en")** també fa una copia bit a bit) te la pot gravar a disc dur o a algun suport òptic. Si només vols fer una còpia de les dades per a reinstal·lar el sistema operatiu per altra banda, doncs [Unison]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unison&searchon=names&subword=1&version=gutsy&release=all"), [Sbackup]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sbackup&searchon=names&subword=1&version=gutsy&release=all") i multitud d'altres aplicacions (que solen fer servir els mateixos protocols per sota) et poden fer la feina.

---

### Post by lpargemi on 2008-01-25
Hola

Jo el què vull fer és una còpia de seguretat de tot el sistema, operatiu inclòs, per poder-lo restaurar en cas de què una prova no surti gaire bé.

Per tant he provat amb partimage. Funciona, ja he descobert que s'arrenca des de la cònsola, però hi ha un problema: Em diu que no pot copiar-me el sistema perquè el disc està muntat. 
Puc fer umount dev/hda1? Ho he provat arrencant en mode segur [amb l'intenció de  tenir menys coses arrencades] i la instrucció cola (no es queixa ni res)
Però després engego el partimage, i em diu que la partició encara està muntada (lògic, perquè l'ordinador està en servei). Si li dic que endavant crea la còpia, però hi ha un moment on peta donant uns errors de I/O. Per tant no sé si em puc refiar de la còpia que ha creat per restaurar el sistema.
Com hauria de sortir d'aquest peix que es mossega la cua?  Em sembla recordar que arrencant amb un live-cd no tenia accés a escriure als discs, per tant cal pensar que tampoc aniria.

---

### Post by PellRoja on 2008-01-26
> **lpargemi said:**
> Hola

Jo el què vull fer és una còpia de seguretat de tot el sistema, operatiu inclòs, per poder-lo restaurar en cas de què una prova no surti gaire bé.

Per tant he provat amb partimage. Funciona, ja he descobert que s'arrenca des de la cònsola, però hi ha un problema: Em diu que no pot copiar-me el sistema perquè el disc està muntat. 
Puc fer umount dev/hda1? Ho he provat arrencant en mode segur [amb l'intenció de  tenir menys coses arrencades] i la instrucció cola (no es queixa ni res)
Però després engego el partimage, i em diu que la partició encara està muntada (lògic, perquè l'ordinador està en servei). Si li dic que endavant crea la còpia, però hi ha un moment on peta donant uns errors de I/O. Per tant no sé si em puc refiar de la còpia que ha creat per restaurar el sistema.
Com hauria de sortir d'aquest peix que es mossega la cua?  Em sembla recordar que arrencant amb un live-cd no tenia accés a escriure als discs, per tant cal pensar que tampoc aniria.

doncs jo crec que o vaig fer amb l' opció de live-cd. Almenys amb el windows de casa ho vaig fer així. prova amb la distro Helix, crec que és la que vaig fer servir, que porta molts programes de sistema, entre ells partimage, i crec que si que deixa monta amb permisos les particions :)

---

### Post by papapep on 2008-01-27
Quan una partició està muntada no s'ha d'efectuar la còpia, ja que hi ha fitxers i directoris que canvien durant la mateixa i podria portar problemes posteriors.
Aleshores, cal fer-ho des d'un sistema que no munti la partició que vols copiar. Un cd live que ja porta el partimage és el [rescuecd]("http://www.sysresccd.org/Main_Page"), que és una petita imatge iso que conté diverses eines per a recuperar o efectuar tasques de manteniment de sistemes operatius. És d'aquelles coses que és bo tenir sempre a mà com a salvavides. :-)

---

