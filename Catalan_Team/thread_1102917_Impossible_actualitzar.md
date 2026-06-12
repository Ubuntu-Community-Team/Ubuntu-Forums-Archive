---
title: "Impossible actualitzar"
date: 2009-03-22
forum: Catalan Team
---

### Post by metoli on 2009-03-22
Quant actualitzo el sistema m sur el següent missatge:

W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 58403026387EE263

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 60D11217247D1CFF

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 43C0AFF0D7FAE680

W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 2C392DFEEFD17969
W: No s'ha pogut obtenir [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)  

W: No s'ha pogut obtenir [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release)  

W: No s'ha pogut obtenir [http://wine.budgetdedicated.com/apt/dists/intrepid/Release](http://wine.budgetdedicated.com/apt/dists/intrepid/Release)  

W: No s'ha pogut obtenir [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: No es poden descarregar alguns fitxers índex, s'han ignorat o en el seu lloc s'han emprat els antics.

com puc fer per tal de solucionar-ho i actualitzar el sistema
Gràcies

---

### Post by oriolsbd on 2009-03-22
Sembla que has perdut (o no has tingut mai) les claus d'encriptació de tots aquests repositoris que comentes.

La de Google, te la pots baixar així:
```
wget https://dl-ssl.google.com/linux/linux_signing_key.pub
sudo apt-key add linux_signing_key.pub
```

Per les de Launchpad, em sona que hi ha una shell que te les busca automàticament. Segurament algú et podrà dir on trobar-la.

La del Wine, jo no la utilitzo, però [aquí]("http://www.winehq.org/download/deb") he vist que has d'executar això:
```
wget http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg
sudo apt-key add Scott%20Ritchie.gpg
```

Salut!

---

