---
title: "actualització fallida"
date: 2020-11-17
forum: Catalan Team
---

### Post by josep-maria on 2020-11-17
He volgut actualitzar l'ubuntu, del 16 al 18.04, però s'ha quedat la pantalla en blanc a mig fer. He reengegat el pc, però ja no s'ha engegat. Fent moltes proves, no sé com però al final ha tornat a sortir la pantalla inicial (la que diu aplicacions-llocs-sistema), i no s'ha esborrat cap arxiu. 

Però no funciona l'accés a internet. No és culpa del hardware, perquè sí que funciona la internet si faig servir el windows que hi ha al mateix pc.

He intentat tornar a començar ficant-hi el disc de l'ubuntu, però no surt el missatge de quan engegues el pc (boot), el que diu que per configurar cal tocar esc o F10.

Curiosament, a aplicacions > eines del sistema > monitor del sistema diu que ara tinc la versió del 2018, però no es va acabar pas de ficar:
 release 18.04.5
 linux 4.4.0-194-generic x86_64
 mate 1.20.1

He pensat comprar un disc de la versió del 2020, però si no puc canviar la configuració del boot, tampoc no em servirà.
No he vist cap post semblant al meu.

---

### Post by jmaspons on 2020-11-18
No acabo d'entendre el problema. L'actualització es va interrompre i pots entrar al sistema. L'únic problema és la connexió a internet? Pot ser que hagi quedat algun paquet a mig actualitzar i que sigui la causa del problema. Per començar, cal mirar que el gestor de paquets quedi en bon estat. Pots provar amb

```

sudo dpkg --configure -a
sudo apt full-upgrade

```

Si cal, repeteix les ordres fins que quedi net després

```

sudo apt autoremove

```

Si surt algun error pel camí, passa'l per aquí i ho mirem.

---

### Post by josep-maria on 2020-11-18
Diu això:


lloll@lloll-HP-Compaq-6200-Pro-SFF-PC:~$ sudo apt dpkg --configure -a
E: No s'admet l'opció de la línia d'ordres --configure en combinació amb altres opcions

lloll@lloll-HP-Compaq-6200-Pro-SFF-PC:~$ sudo apt full-upgrade
E: No s'ha pogut blocar /var/lib/dpkg/lock-frontend - open (11: El recurs no es troba disponible temporalment)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

---

### Post by jmaspons on 2020-11-18
error meu, sobra apt. L'ordre correcte és [FONT=Courier New]sudo dpkg --configure -a[/FONT]

---

### Post by josep-maria on 2020-11-18
Si faig:     sudo dpkg --configure -a
diu:          error: dpkg frontend està blocada per un altre procés


Si faig:     sudo apt full-upgrade
diu:
E: No s'ha pogut blocar /var/lib/dpkg/lock-frontend - open (11: El recurs no es troba disponible temporalment)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

---

### Post by josep-maria on 2020-11-23
Com que no es pot arreglar l'ubuntu perquè no es pot entrar a internet, he intentat tornar a ficar l'ubuntu sencer, treient-lo d'una memòria flash.
Quan engego el pc, i després de molts intents, he pogut entrar al menú de boot, per dir on el processador ha d'anar a copiar el sistema operatiu.
Però ara no sé com li dic que no vagi al disc dur sinó al connector usb.
Em surt això:

EPI boot sources
      ubuntu
      windows boot manager
      ubuntu
Legacy boot sources
      hard drive
      SATA0
IBA GE Slot 00CB v1376
ATAPI CD/DVD Drive
      SATA2

Què li dic?

---

### Post by josep-maria on 2020-11-23
Han desaparegut els espais en blanc. Vegem ara:

EPI boot sources
.......ubuntu
.......windows boot manager
.......ubuntu
Legacy boot sources
.......hard drive
............SATA0
IBA GE Slot 00CB v1376
.......ATAPI CD/DVD Drive
.......SATA2

---

