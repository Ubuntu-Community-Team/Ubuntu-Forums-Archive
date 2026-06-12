---
title: "[RESOLT] Novell, novell... syntax error &quot;(&quot; unexpected"
date: 2007-05-24
forum: Catalan Team
---

### Post by ncatdesigner on 2007-05-24
Hola Bones,

M'acabu d'instal·lar l'Ubuntu i tinc alguns problemes alhora de compilar els programes amb el gcc

Em surt aquest error:

syntax error "(" unexpected

Fins i tot amb el visca el Barça!

#include<stdio.h>

int main()
{
    printf("Visca el Barça!");


}

Que vindria a ser el Hello World xD


Alguna idea?

---

### Post by CarlesOriol on 2007-05-24
El que dius és correcte i ha de funcionar. Mirem que no sigui alguna collonada:

prova de fer 

sudo apt-get install build-essential

i comprova que l'extensió del fitxer és .c

---

### Post by ncatdesigner on 2007-05-24
Si ja ho he fet...

En principi i segons tinc entés això lúnic que fa és instal·lar-me els paquets bàsics no?

Suposo que no s'ha de reiniciar com el vindous? xD

---

### Post by ncatdesigner on 2007-05-24
Per cert la comanda que he utilitzat és:

gcc -o Hello Hello.c

---

### Post by ncatdesigner on 2007-05-24
Ok, i això va per a tots/es

Els programes compilats en c no s'executen MAI **sh *nom_programa***

sinó ** ./*nom_programa***

Que masell que sóc...

---

### Post by orestesmas on 2007-05-25
Veig que ja ho has resolt, però la propera vegada sigues més precís: tenies problemes EXECUTANT el programa, i no pas COMPILANT-LO. Jo em creia que no tenies el paquet libc6-dev instal·lat.

Ah, i millor posar un "\n" al final de la cadena :-)

---

