---
title: "Còpia de seguretat de Evolution i del Simple BackUp"
date: 2010-01-06
forum: Catalan Team
---

### Post by joaquimrubio on 2010-01-06
Vaig fer una còpia de seguretat del programa Evolution amb l'aplicació que té el propi programa Evolution (Fitxer > Configuració de la còpia de seguretat) i després vaig fer una còpia de seguretat amb el programa Simple BackUp. Vaig ubicar les dues còpies en una carpeta que vaig crear en un HD extern.

Avui he volgut restaurar les dues còpies i fallo en els 2 casos:
En el cas de l'Evolution faig: Firxer > Configuració de la restauració > i trio el camí fins a l'arxiu Evolution-Backup.targ.gz i un cop allí clico a "obre". Em respon:" Seleccioneu un fitxer de còpia de seguretat de l'Evolution vàlid a restaurar".

En el cas de Simple Backup trio "Use custom" i navego fins l'arxiu "data_una xifra.lleida.ful. També fracaso, allí el missatge és "Error. No backups found in the target directory".

Que és el que faig malament? Les còpies, en ambdós casos, semblen correctes.

Ubuntu Karmic Koala 9.10.
AMD de 64 bits.
Usuari absolutament inexpert.

---

### Post by ffp on 2010-01-07
Hola,

Jo ho vaig provar una vegada, i no em va funcionar en un altre disc (en el meu cas intern). En canvi si ho faig dins del mateix disc (al escriptori mateix) si funciona. Després nomes cal copiar el fitxer on vulguis. Per recuperar les dades també tindràs que copiar el fitxer al mateix disc i executar la restauració.
Funciona, per que aprofitant el nou Karmic, vaig instal·lar un nou disc i vaig restaurar amb la còpia de seguretat.

---

### Post by joaquimrubio on 2010-01-07
Moltes gràcies, ffp:

Resolt totalment amb l'Evolution, he fet: Copiar el fitxer des del Disc Dur Extern al meu escriptori i després amb l'eina del propi Evolution he efectuat la restauració i ha funcionat perfecte.

No ha funcionat en el cas del Simple Backup.
He fet: Copiar l'arxiu sencer a l'escriptori i restaurar. No ha funcionat, surt el mateix missatge d'abans:  "Error. No backups found in the target directory".

He provat de copiar només l'arxiu files.tgz  i restaurar. Tampoc ha funcionat i ha sortit el mateix missatge.

Em queda pendent restaurar aquest arxiu.

---

### Post by joaquimrubio on 2010-04-10
Una persona profesional de l'Ubuntu m'ha ensenyat com es fa: 
Calen privilegis d'administrador per a restaurar la còpia de seguretat del Simple BackUp, aleshores la manera més fàcil és fer-hi via consola escrivint el següent manament:

"sudo simple-restore-genome" 


Ho explico amb més detall pels principiants com jo:

En el meu portàtil quan obro la consola veig:
  	 	 	 	 	 	  [SIZE=3]joaquim@joaquim-laptop:~$ 
[/SIZE]


Aleshores haig d'escriure:[SIZE=3]
[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo simple-restore-gnome 
[/SIZE]


El conjunt a mi em queda així (el joaquim@joaquim-laptop variarà en cada portàtil i si és ordinador de taula potser posa desktop enlloc de laptop...)



[SIZE=3]joaquim@joaquim-laptop:~$ [/SIZE][SIZE=3]sudo simple-restore-gnome [/SIZE]


Aleshores, prémer la tecla "Enter". La consola et demanarà la teva contrasenya, la introdueixes, tornes a prémer la tecla Enter i la resta de l'execució és intuitiva i no presenta problemes.

---

