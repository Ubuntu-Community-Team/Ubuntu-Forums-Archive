---
title: "connexió ssh sense contrasenya"
date: 2011-06-14
forum: Catalan Team
---

### Post by Kette on 2011-06-14
Hola,
fa temps que per connectar els netbooks de casa amb l'equip de taula, aprofitant el mòdem wifi, ho fem amb Nautilus via "sftp" i no tinc cap problema. Ara, per simplificar la connexió volia eliminar el pas per autenticar-se per contrasenya i no m'acabo d'en-sortir. Haig de dir que això ja ho he fet en xarxes Debian i no entenc que pot passar, quasi segur que és un problema de configuració al fitxers que pertoca, sshd_config i ssh_config.
Les passes que he fet fins ara son:
- crear un joc de claus rsa des dels clients amb ssh-keygen sense "passphrase" per la clau privada.
- exportar la clau publica al servidor amb "ssh-copy-id usuari@ip_servidor". Després he comprovat que s'havia creat el fitxer "authorized_keys" al directori .ssh/ del usuari al servidor (els permisos que te per defecte son 6 0 0).
- reiniciar el servei ssh. Ho he fet com creia que es fa amb tots els serveis de servidor, des de /etc/init.d : "/etc/init.d ssh restart" i la "bronca" del terminal ha esta impressionant, mes o menys venia a dir: "acepto pop com animal de companyia ;) però fa anys que vivim al segle XXI i ara es fa: service ssh restart".
- comprovar que funcionava: "ssh usuari@ip_servidor -v" per veure tot el proces.
Hores d'ara continua demanant la contrasenya.
Adjunto fitxers amb la sortida del terminal, sshd_conf (del servidor) i ssh_config del client.
Em podreu il·luminar? Gracies

---

### Post by kimet on 2011-06-14
Em sembla que la contrasenya la demana per defecte, prova a descomentar la linia #PasswordAuthentication yes i canviar el valor a no. (al ssh_config i sshd_config).

Salut

---

### Post by wgarcia on 2011-06-15
Penso que el "pasphrase" o el "password" no té res a veure, si els parells de claus estan en el servidor i el client es connectarà sense demanar la clau. 

Jo de la manera que ho faig és la següent.

A la màquina amb el client ssh:

```
ssh-keygen -t dsa
```

Això crea a ~/.ssh dos fitxers: id_dsa (clau privada) i id_dsa.pub (clau pública).

Afegim el contingut d' id_dsa.pub a ~/.ssh/authorized_keys a l'ordinador on s'està corrent el servidor ssh.

No es necessita reiniciar el servidor ssh.

---

### Post by orestesmas on 2011-06-15
De fet, no calia reiniciar el servidor ssh. Les claus són exclusives per cada usuari i el servidor ssh ja s'encarrega de mirar el fitxer authorized_keys que toca.

He donat un cop d'ull als fitxers que adjuntes i sembla que passen les comprovacions usuals:

1) Tens activat l'accés per clau pública al fitxer de configuració del servidor.
PubkeyAuthentication yes

2) El servidor pot utilitzar la versió 2 del protocol a banda i banda
Protocol 2

3) Que realment el servidor ssh tingui accés a la clau pública copiada a /home/usuari/.ssh/ . Això podria no ser així en algun cas, per exemple si utilitzes un directori /home xifrat (que només és accessible en posar la contrasenya)

Per la sortida de terminal que envies sembla que l'opció 3 no és, però confirma-ho si et plau.

Ah, i pots enviar també la sortida del teminal amb més detall encara si uses l'opció -vv en lloc de la -v només. Ho dic perquè l'essència del problema es troba en aquestes línies:

```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/nuria/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
```

Alguna cosa passa allà dins i potser amb l'opció -vv es veurà més clar.

---

### Post by Kette on 2011-06-15
Gràcies per les respostes però encara no me'n surto. Anem a pams:
la contrasenya no hauria de tenir res a veure amb el problema, de fet m'estimo mantenir aquest sistema d'autentificació per poder entrar, com faig ara, des del exterior amb IP pública. La "passphrase" si és important, he decidit deixar-la en blanc per que el sistema no la demani per desbloquejar la clau privada. Tot i això en kimet m'ha donat l'idea de posar-la en "no" l'autenticació per contrasenya  per provar si funcionava exclusivament amb les claus, i el resultat ha estat que no, que no va.
wgarcia, la generació de les claus ha estat tal com tu fas, o gaire bé, jo he fet servir l'encriptació RSA en comptes de la DSA. Per eliminar dubtes he esborrat la .pub de "authorized_keys" antiga al "/home/usuari/.ssh del servidor i del /etc/ssh/ del client juntament amb la privada i he tornat a generar les claus en DSA amb un resultat similar al anterior: em demana la "contrasenya" i això només vol dir que ha fallat l'autenticació amb claus.
Em fa la impressió  que falla quelcom als fitxers de configuració. Desprès de fer diverses provatures, fins i tot a la babalà, els he deixat com estaven quan els he penjat en el primer missatge.
De moment continuem accedint amb la contrasenya com fèiem fins ara però toca els nassos no poder en sortir-me'n 
Se us acut res més per provar? Gràcies

---

### Post by Kette on 2011-06-15
Òndia orestesmas, s'han creuat els missatges. Ara ho comprovo però canviarà el tipus de clau.
Salut

---

### Post by Kette on 2011-06-15
Adjunto fitxers de la sortida de terminal i dels fitxers de configuració.
Edito: no, el netbook no esta encriptat i en teoria ha de tenir accés al fitxer encara que sembla que no ho fa!

---

### Post by wgarcia on 2011-06-15
Sembla que tens algun problema de permisos del directori .ssh, em sembla que del servidor, però podem mirar també del client. 

Què et surt quan entres en una terminal:

```
ls -al | grep ~/.ssh
```

tant al servidor com al client?

---

### Post by Kette on 2011-06-15
Doncs si, wgarcia, sembla ser que hi ha un problema de permisos o de "propietari". Pasos que he fet aquesta vegada:
- esborrar els directoris .ssh/ tan del servidor com del client.
- generar una nova clau DSA
- exportar la clau publica (.pub) al servidor: ssh-copy-id usuari@servidor. Amb aquesta comanda es copia la clau publica al directori .ssh/ del usuari en el servidor, crean si cal, el mateix directori (que jo havia esborrat)i el fitxer "Authorized_keys". En aquesta connexió s'ha generat el "finger print" per que havia desaparegut en esborrar el directori .ssh
- entrar en el servidor des del client amb "ssh usuari@servidor" i la opció -vv per veure en detall el procés.
I... encara continua el problema de reconeixement de claus!
Enganxo les sortides a un "ls -la" als directoris .ssh/ dels dos equips. 

-servidor:
total 12
drwxrwxrwx  2 nenes nenes 4096 2011-06-15 22:40 .
drwxrwxrwx 88 nenes nenes 4096 2011-06-15 17:47 ..
-rw-------  1 nenes nenes  608 2011-06-15 22:40 authorized_keys
-client:
total 20
drwx------  2 nuria nuria 4096 2011-06-15 22:40 .
drwxr-xr-x 47 nuria nuria 4096 2011-06-15 22:38 ..
-rw-------  1 nuria nuria  672 2011-06-15 22:38 id_dsa
-rw-r--r--  1 nuria nuria  608 2011-06-15 22:38 id_dsa.pub
-rw-r--r--  1 nuria nuria  222 2011-06-15 22:40 known_hosts

---

### Post by wgarcia on 2011-06-16
Jo el que et deia és que entressis l'ordre "ls" tal qual te l'he posada perquè es puguin veure els permisos dels directoris ".ssh" mateixos, no els permisos dels fitxers en aquests directoris.

Rellegint, em sembla que el que posa a "." dóna els permisos del directori en qüestió. I veig que al servidor el directori ".ssh" té permisos universals, tothom pot llegir i escriure. Aquest pot ser el problema. 

Intenta entrar:


```
chmod oa-rwx .ssh
```

al servidor, i torna a provar.

---

### Post by Kette on 2011-06-16
Si, he fet el llistat dins del .ssh/ per que veiessis tot el que conté i, tal com dius, el "." fa referència a directori on son els arxius.
La comanda que m'has aconsellat és equivalent a un "chmod 000" sobre el directori. Ho he fet i tot continua igual. Val a dir que aquest directori no l'he creat jo, ho ha fet el sistema en tenir la primera connexió per "ssh".
```
total 12
d---------  2 nenes nenes 4096 2011-06-15 22:40 .
drwxrwxrwx 88 nenes nenes 4096 2011-06-16 10:30 ..
-rw-------  1 nenes nenes  608 2011-06-15 22:40 authorized_keys
```

En els "debug" de la sortida ve a dir que el problema és de permisos o de propietari. Haig de dir que a "nenes" s'entra com l'usuari "nuria" i la seva corresponent contrasenya. Enganxo la sortida de /etc/passwd:
```
eugeni@principal:~$sudo cat /etc/passwd | tail -5
nenes:x:1003:1003:Nuria,,,,:/home/nenes:/bin/bash
marta:x:1001:1001:,,,:/home/marta:/bin/bash
haldaemon:x:114:123:Hardware abstraction layer,,,:/var/run/hald:/bin/false
timidity:x:116:128:TiMidity++ MIDI sequencer service:/etc/timidity:/bin/false
sshd:x:115:65534::/var/run/sshd:/usr/sbin/nologin

```
Per si de cas he trobat curiós com es defineix el propietari del fitxer "authorized_keys" en forma gráfica (ho adjunto). Ves que no vinguin per aquí els problemes!

---

### Post by wgarcia on 2011-06-16
No és equivalent a "chmod 000 .ssh" sinó a "chmod 700 .ssh", jo faig servir l'altre especificació perquè allò dels número mai me'n recordo com va. 

Prova amb aquesta especificació a veure si això ho arregla.

---

### Post by Kette on 2011-06-16
Per provar ho he fet en sentit invers: he instal·lat el servidor en el netbook, he creat les claus en el servidor, les he enviades i.... e voilà  funciona!
Ara només restava copiar permisos i configuracions en sentit invers i... continuava sense funcionar.
wgarcia tens tota la raó del món, em vaig embolicar i l'hi vaig passar malament els permisos. Ara el directori .ssh/ del servidor està a 600. Tornant a filtrar la sortida amb -vv cap a un fitxer, l'he pogut examinar tranquil·lament. Un cop establerta la comunicació no m'he pogut treure del cap aquesta línia: "Remote: Ignored authorized keys: bad ownership or modes for directory /home/nenes/". Tal com deies wgarcia era cosa de permisos. Tinc, no, tenia els permisos del directoris d'usuaris a 766 per poder intercanviar arxius entre usuaris sense problemes. He provat combinacions a la baixa i he trobat que a 750 funcionava. I així l'he deixat!
Gràcies per la vostra ajuda!

---

