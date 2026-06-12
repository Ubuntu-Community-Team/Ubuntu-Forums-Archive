---
title: "Compartir un directori encriptat amb Samba"
date: 2012-03-08
forum: Catalan Team
---

### Post by guillemtanya on 2012-03-08
Hola,

he estat buscant al fòrum tant el català com a l'anglès i a Internet i no n'he tret l'aigua clara.

Tinc muntat un Ubuntu Server amb un directori home (podria ser qualsevol carpeta) compartit a través de Samba. Actualment, aquest directori no està encriptat i es comparteix perfectament sense problemes.

Ara, m'agradaria tenir aquest directori encriptat. Tenia pensat utilitzar "ecryptfs-migrate-home" perquè m'encripti el directori tal com està. He fet alguna prova creant un nou usuari, encriptar el seu home, i compartir-lo però no funciona. Quan accedeixo a la carpeta compartida des d'un client linux la veig buida.

En conclusió, el que busco és tenir accés a una carpeta encriptada i compartida. És possible amb "ecryptfs" i "samba"? O teniu alguna recomanació d'algun altre sistema?

Moltes gràcies per endavant!

---

### Post by kimet on 2012-03-08
No se si ho he entès, vols compartir una carpeta xifrada entre dos pc's amb linux? Ho he provat amb una carpeta xifrada amb 'encfs' i funciona correctament, tenint el programa en ambdós ordinadors i la contrasenya...no veig perqué hi ha d'haver cap problema.

---

### Post by guillemtanya on 2012-03-09
Hola de nou,

Gràcies per l'interès kimet.

he vist quin és el problema. Si la carpeta home de l'usuari està encriptada, fins que l'usuari no inicia sessió, és a dir, fa "login", la carpeta no és muntada sense encriptació. És lògic ](*,)

Aleshores, al tractar-se d'un servidor on no hi ha usuaris que hi treballin, si es vol accedir a la carpeta compartida, no es pot perquè no està desencriptada. 

Ara la meva pregunta és si hi ha cap sistema, perquè quan vulgui accedir a la compartició amb l'usuari i contrasenya, en aquest moment la desencripti tal i com ho fa en el procés de "login".

Tota l'estona he parlat del home, però crec que hauria de ser per qualsevol carpeta encriptada.

Com ho veieu?

---

