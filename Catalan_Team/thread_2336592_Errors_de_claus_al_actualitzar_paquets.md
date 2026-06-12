---
title: "Errors de claus al actualitzar paquets"
date: 2016-09-09
forum: Catalan Team
---

### Post by Original Flo on 2016-09-09
Buenas, ja fa uns dies que cuan intento actualitzar la llista de paquets en un servidor ubuntu server 16.04lts. Al fer:

```
sudo apt-get update
```

hem torna errades amb les claus dels repositoris.

He buscat informació i les respostes que trobo sempre diuen que s'ha de posar manualment la clau que et torna al fer l'update, i el problema es que a mi no en torna cap clau i les claus estan perque me las torna al fer

```
sudo apt-key list
```


Poso aquí tot el que hem torna al fer l'update

[URL="https://ubuntuforums.org/misc.php?do=bbcode#code"]```
serveradmin@ElMeuServer:~$ sudo apt-get update
Des:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94,5 kB]
Des:2 http://es.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Ign:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Des:3 http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease [95,7 kB]
Des:4 http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease [92,2 kB]
Ign:2 http://es.archive.ubuntu.com/ubuntu xenial InRelease    
Ign:3 http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease
Ign:4 http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease
Descargados 529 kB en 0s (815 kB/s)
Leyendo lista de paquetes... Hecho
W: Error de GPG: http://security.ubuntu.com/ubuntu xenial-security InRelease: Se encontró al menos una firma inválida.
W: El repositorio «http://security.ubuntu.com/ubuntu xenial-security InRelease» no está firmado.
N: Los datos de un repositorio como este no se pueden autenticar y por tanto su uso es potencialmente peligroso.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
W: Error de GPG: http://es.archive.ubuntu.com/ubuntu xenial InRelease: Se encontró al menos una firma inválida.
W: El repositorio «http://es.archive.ubuntu.com/ubuntu xenial InRelease» no está firmado.
N: Los datos de un repositorio como este no se pueden autenticar y por tanto su uso es potencialmente peligroso.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
W: Error de GPG: http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease: Se encontró al menos una firma inválida.
W: El repositorio «http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease» no está firmado.
N: Los datos de un repositorio como este no se pueden autenticar y por tanto su uso es potencialmente peligroso.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
W: Error de GPG: http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease: Se encontró al menos una firma inválida.
W: El repositorio «http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease» no está firmado.
N: Los datos de un repositorio como este no se pueden autenticar y por tanto su uso es potencialmente peligroso.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.

```[/URL][URL="https://ubuntuforums.org/misc.php?do=bbcode#code"]
[/URL]

Espero que hem podeu ajudar, perque no acabo de trobar resposta.

Salut. ;)

---

### Post by Original Flo on 2016-09-09
Actualitzo per comentar que l'error de claus el dona a tots els repositoris, i aixo fa pensar que potser l'error no es que les claus estiguin malament.

Potser es un problema d'alguna configuració, per aixo al tornar l'error no indica les claus.

Salut. ;)

---

### Post by wgarcia on 2016-09-12
Sembla que s'han corromput les claus que autentifiquen els dipòsits que estàs usant. 

La manera més senzilla d'arreglar-ho s'explica a missatge 5 d'aquest enllaç:
[http://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys](http://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys)

Prova a veure si te'n surts, si no hi ha sort es pot mirar alguna altra alternativa.

---

### Post by Original Flo on 2016-09-20
Gracies per la resposta!

He provat el que m'has comentat, canviant la linea de l'arxiu **gpg.conf, **i l'error persisteix.

També comentar que l'error es intermitent, falla tots el dies, i de tant en tant no dona cap error.

Si sabeu d'alguna altre solució, m'agradaria solucionar això.

Salut ;)

---

### Post by wgarcia on 2016-09-22
Aquí hi ha una altra solució. Consisteix en fer una còpia de les signatures existents, i baixar-les totes un altre cop. Es pot fer amb les següents ordres, des d'una terminal:

```

sudo mv /etc/apt/trusted.gpg.d/ /etc/apt/trusted.gpg.d.backup
sudo mkdir /etc/apt/trusted.gpg.d
sudo chmod 755 /etc/apt/trusted.gpg.d

```

i després
```

sudo apt-get update 2> /tmp/keymissing; for key in $(grep "NO_PUBKEY" /tmp/keymissing |sed "s/.*NO_PUBKEY //"); do echo -e "\nProcessing key: $key"; sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $key ; done

```
Aquesta última ordre ha d'anar tota en la mateixa línia.

Si no funcionés es pot retornar a l'estat anterior (les següents ordres sols s'han de donar si la solució proposada no funcionés):
```

sudo rm /etc/apt/trusted.gpg.d/*
sudo rmdir /etc/apt/trusted.gpg.d
sudo mv /etc/apt/trusted.gpg.d.backup /etc/apt/trusted.gpg.d

```

---

### Post by Original Flo on 2016-09-27
Buenas, está solucionat.

Era per un problema amb el mod-security d'apache, al desactivarlo san acabat uns cuants errors a part d'aquest.

Toca configurar mod-security.

Salut y gracies ;)

---

### Post by wgarcia on 2016-09-27
D'acord, gràcies, si li post posar "Solved" al fil, pot ser d'utilitat per a consultes futures.

---

