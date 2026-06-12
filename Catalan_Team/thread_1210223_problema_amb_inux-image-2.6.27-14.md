---
title: "problema amb inux-image-2.6.27-14"
date: 2009-07-11
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-07-11
bon dia.
Cada cop que utilitzo Synaptic o Afegeix/Elimina hem surt aquest error:

E: linux-image-2.6.27-14-generic: el subprocés post-installation script retornà el codi d'eixida d'error 2
E: linux-headers-2.6.27-14-generic: el subprocés post-installation script retornà el codi d'eixida d'error 2

Cap idea sisplau?
Gracies.

---

### Post by Miquel Ubuntero on 2009-07-11
Una mica més d'informació. 
El Virtualbox ha deixat de funcionar-me i tinc la sensació que el xubuntu 8.10 hem va més lent, obrint i tencan finestres, obrin programari, etc.

Pregunta. Estaria be, iniciar amb un kernel anterior i amb synaptic treure aquest 2.6.27-14 que sembla que no hem va be?

O be, aniria be actualitzar-me del Xubuntu 8.10 al 9.04?

No se si dic bestieses? Però el sistema no hem va fi i no tinc clar que fer!

Salut!

---

### Post by pauelmaco on 2009-07-11
Hola

Potser és una solució una mica dràstica, preò podries copiar tots els arxius que tens en un disc dur extern i instalar el xubuntu 9.04 des d'un cd. D'aquesta manera segur que eliminaries qualsevol problema.

Sort

---

### Post by Miquel Ubuntero on 2009-07-11
Hola de nou.
Aquesta última "so&#320;lució" ja la conec, però la deixo com a última opció, que hem sap greu de perdre tot el programari insta&#320;lat.
Gracies, de totes maneres.
Salut!

---

### Post by oriolsbd on 2009-07-11
Des d'un terminal, prova d'executar el següent:
```
sudo dpkg --configure -a
```

Quant al Virtualbox, ara ja no passa, però amb versions antigues, cada cop que canviaves la versió de Kernel, s'havia de recompilar una part. No t'espantis amb això de "recompilar", que en aquest cas és molt senzill. :-)   Només cal executar aquesta comanda:
```
sudo /etc/init.d/vboxdrv setup
```
De tota manera, si és aquest el problema, en el missatge d'error del VirtualBox ja t'indica que és això el que has d'executar.

Salut!

---

### Post by Miquel Ubuntero on 2009-07-11
Hola oriolsdb.
La primera comanda que comentes ja ho havia provat sense ser efectiu.
Per tant he decidit amb synaptic eliminar tot allò que digues linux 2.6.27-14 i m'ha anat be. Ara amb el kernel 2.6.27-7 tot sembla que va be, synaptic, brasero, ect. Hem falta provar VirtualBox que dona error no botable medium, però podria ser del cd. si no fos aixì ja faria un altre post. Un problema un fil. ;)
gracies i salut!

---

### Post by Miquel Ubuntero on 2009-07-14
Finalment he fet el salt. He actualitzat a xubuntu 9.04 i per sor tot be. Mantenint tot el programari en forma.
Salut!

---

