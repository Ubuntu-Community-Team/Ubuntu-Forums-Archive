---
title: "Problema amb les actualitzacions"
date: 2011-11-25
forum: Catalan Team
---

### Post by U-Joan on 2011-11-25
Aquesta setmana m'ha sorgit un problema amb les actualitzacions. Resulta que en la darrera actualització, crec que amb la baixada va fallar alguna cosa i ara cada dia m'apareix un avís a la barra superior de l'escriptori, un símbol vermell en forma de triangle amb un signe d'admiració (com un senyal de trànsit de perill).

Si faig clic en aquest avís em diu el següent: "la informació d'actualització és obsoleta. Això pot ser degut a algun problema de la xarxa o bé al fet que algun dipòsit ja no sigui disponible. Caldrà que dugueu a terme l'actualització de forma manual fent clic a aquesta icona i seleccionant "comprova si hi ha actualitzacions". Llavors podreu veure si algun dels dipòsits de la llista falla".

Faig clic a "mostra les actualitzacions" que hi ha a sota, se m'obre el gestor d'actualitzacions i faig clic a "comprova". Llavors m'apareix una finestra que diu "actualitzant la memòria cau" i quan acaba finalment em diu que ha fallat la baixada de la informació del dipòsit. A "Detalls" em surt aquesta informació:

W:Failed to fetch [http://ad.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://ad.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'ad.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

Què puc fer?
:?

---

### Post by wgarcia on 2011-11-26
Prova de canviar el servidor des d'on et baixes les actualitzacions. Això ho pots fer des de, per exemple, el Centre de Programari Ubuntu, amb el menú "Edita -> Fons de Programari". 

Et sona haver habilitat aquesta fon "ad.archive.ubuntu.com", a mi no em sona quina font de programari és. Pots provar de deshabilitar-la al mateix lloc, a "programari addicional", per si un cas. 

Un cop fet això pots intentar actualitzar manualment, obrint una terminal i entrant

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by U-Joan on 2011-11-27
Ahir vaig fer el canvi de servidor. A la finestra de Fonts de Programari per defecte em sortia "servidor per a Andorra", i l'he canviat per "servidor principal".
No tenc present d'on surt aquesta adreça de "ad.archive.ubuntu.com", potser té a veure amb el servidor d'Andorra? De totes maneres a la pestanya de "altre programari" no em consta...
Després vaig posar les ordres que em deies al terminal, un cop posada la primera "sudo apt-get update" em va sortir una llista d'adreces i al final em posa el següent:

S'està llegint la llista de paquets... Fet 
W: S'ha produït un error durant la verificació de la firma. El repositori no està actualitzat i serà utilitzat el fitxer d'índex anterior. error GPG: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: Les signatures següents són invàlides: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: S'ha produït un error amb el GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: Les signatures següents són invàlides: BADSIG D6B6DB186A68F637 Launchpad JDownloader PPA
W: S'ha produït un error amb el GPG: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: Les signatures següents són invàlides: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: S'ha produït un error amb el GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release: Les signatures següents són invàlides: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: No s'ha pogut obtenir [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

Després de posar "sudo apt-get upgrade" em va sortir:

S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.

Avui m'ha tornat a aparèixer l'avís amb el triangle vermell...

---

### Post by wgarcia on 2011-11-27
Sembla que a alguna actualització algunes de les claus d'autentificació de paquets han quedat mal baixades. La següent seqüència de comandes (obre una terminal i ves-les entrant una a una) solen arreglar aquest problema:

```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get clean
sudo apt-get update

```

Les dues línies on surt "rm" et poden donar un missatge de directoris o fitxers no trobats, no et preocupis d'això.

El que sí hauria de deixar de sortir és l'error al final de la comanda "update".

---

### Post by U-Joan on 2011-11-27
Fet! Efectivament m'ha sortit la llista d'adreces i al final ja no han sortit els missatges d'error. A veure si els propers dies ja no apareix l'avís i ho donam per resolt.

Gràcies de nou!
:-)

---

