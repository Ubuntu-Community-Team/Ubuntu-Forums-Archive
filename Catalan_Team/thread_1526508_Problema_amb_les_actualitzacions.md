---
title: "Problema amb les actualitzacions"
date: 2010-07-08
forum: Catalan Team
---

### Post by albertdelleida on 2010-07-08
Hola a tothom!

Com prova l'estiu? Espero que molt bé.

Us escric (ja fa temps que no ho faig) perquè he tingut el següent problema. Avui, mentre actualitzava el programari l'ordinador s'ha penjat. He tingut alguns problemes en tornar a poder engegar l'Ubuntu però després de reiniciar el sistema operatiu unes quantes vegades i fer servir el "recovery mode" he aconseguit tornar a la última versió del Lucid Liynx. Durant el "recovery mode" s'han reparat els paquets que s'havien "trencat", és a dir, els paquets que estava actualitzant. 

Ara bé, quan torno a gestors d'actualitzacions em surt el següent missatge d'error:
[I]
No s'ha pogut obtenir [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
No es poden baixar alguns fitxers índex, s'han ignorat o en el seu lloc s'han emprat els antics.[/I]

Algú sap el que ha pogut passar? Espero la vostra resposta.

Salut i gràcies

---

### Post by Joan A. on 2010-07-08
No entenc el que t'ha passat. Prova a obrir el **Gestor de paquets Synaptic** i pitja a **recarregar**. Després, prova a actualitzar una altra vegada.

---

### Post by albertdelleida on 2010-07-08
Em continua sortint el mateix error. Quan clico a comprovar em torna a sortir el mateix error :confused:

---

### Post by Joan A. on 2010-07-08
Prova a anar a *Sistema/Administració/Orígens del Software*. A la pestanya **Software d'Ubuntu** canvia **Descarregar des de**. Jo tenc seleccionat **Servidor principal** perquè el d'Espanya me dona problemes. Prova-ho tu. ;)

---

### Post by wgarcia on 2010-07-08
També es pot mirar al menú Sistema -> Administració -> Fonts de programari, pestanya "Altre programari" si tens marcat algun repositori "ppa". 

Si continua donant aquest error pots adjuntar (no engantxar) el teu arxiu /etc/apt/sources.list i potser algú pot veure alguna cosa malament aquí.

---

### Post by albertdelleida on 2010-07-08
He canviat l'Origen del Programari com has comentat Joan A. i a l'hora de refrescar em surt el següent error:

[I]No s'han pogut baixar tots els índexs dels dipòsits

Pot ser que el dipòsit ja no estigui disponible, o bé que no s'hi hagi pogut contactar degut a problemes de xarxa. Si està disponible, s'utilitzarà una versió antiga de l'índex que ha fallat. En cas contrari, s'ignorarà el dipòsit. Comproveu la vostra connexió de xarxa i assegureu-vos que l'adreça del dipòsit a les preferències és correcta.

Error del GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: Les signatures següents són invàlides: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>No s'ha pogut obtenir [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
No es poden baixar alguns fitxers índex, s'han ignorat o en el seu lloc s'han emprat els antics.[/I]

Per altra banda, fent el que em comentes wgarcia, he desactivat els ppa següents:

[http://ppa.launchpad.net/user/ppa-name/ubuntu](http://ppa.launchpad.net/user/ppa-name/ubuntu) lucid main

[http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main

i no em dona cap error. Ara bé, les actualitzacions que abans tenia disponibles no m'apareixen. Què us sembla? Quina creieu que és la millor solució?

Moltes gràcies :)

---

### Post by wgarcia on 2010-07-08
Aquests repositoris "ppa" són per accedir a paquets que encara no són oficials però que algun desenvolupador posa a disposició de la comunitat, per solucionar coses o per posar-los a disposció abans que siguin oficials. 

Tu te'n recordes quins són aquest paquets? Els has d'haver habilitat tu mateix per alguna raó. Si ja no els necessites no farà res deshabilitar-los.

Quines eren aquestes actualitzacions que menciones? Això et donarà una indicació dels paquets relacionats amb aquests repositoris "ppa".

---

