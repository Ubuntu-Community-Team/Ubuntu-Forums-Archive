---
title: "engegada lenta"
date: 2007-10-23
forum: Catalan Team
---

### Post by muleta on 2007-10-23
El Gutsy Gibbon em triga 3-4 minuts en engegar-se. La pantalla es manté negra durant aquesta estona fins que apareix l'anagrama d'ubuntu i se'm fa molt llarg.

El Feisty Fawn em semblava molt més ràpid. 

Us passa a tots?.

---

### Post by RainCT on 2007-10-23
Jo no he notat cap canvi.

Per cert, ara m'has fet enrecordar de que encara no he desactivat els serveis que no em calen des de l'última insta&#320;lació... Ara vaig a fer-ho :P.

Potser fent el mateix, si no ho has fet ja, guanyaràs uns quants milisegons. Pots desactivar allò que es carrega al encendre el PC però que no et calgui (com per ex. el bluetooth, si no l'utilitzes) des de Sistema -> Administració -> Serveis, però vigila de no treure res que necessitis.

---

### Post by muleta on 2007-10-23
Gràcies, m'ho he mirat però no sé què és important. He activat l'afinament de disc. Moltes altres coses no sé què son.

---

### Post by Kosimo on 2007-10-23
Jo tinc exactament el mateix problema que tu.
Nem per parts:
Pel fet de que vegis la pantalla negra, és simplement per una mala configuració de l'usplash. Probablement tu tens una pantalla panoràmica oi que sí? I segurament no suportarà la resol·lució de 1280x1024. D'això ja se n'ha parlat, està comprobat que és un bug i ja està al launchpad pendent de ser corregit.
Ara, si tu no vols esperar a una update i prefereixes arreglar-t'ho per tu sol, hauras d'editar l'usplash:

Per fer això obre el terminal (Aplicacions > Accessoris > Terminal)

I escriu això: > sudo gedit /etc/usplash.conf

Allà trobaras l'arxiu de configuració (ves amb compte amb el que toques aquí)  Busca xres i yres i digues quina veus, i quin monitor tens, així podriem ajudar-te a posar una que provablment el teu monitor sigui capaç de mostrar: Com per exemple 1024 x 768.
Recorda de desar l'arxiu abans de tancar-lo 

Un cop fet això reconfigurarem l'usplah: 
Nem altra volta al terminal i escrivim això: > sudo dpkg-reconfigure usplash

Fet.



Pel que fa a la lentitut, t'he de dir que a mi també em passa. He estat buscant un bug al launchpad i no n'he trobat cap. El que pots tenir per cert és que és un problema generalitzat a molts usuaris, i per tant tard o d'hora trobaran la sol·lució que ens arribarà de manera automàtica i transparent.

Espero haver-te pogut ajudar.

Salut!

---

### Post by muleta on 2007-10-23
> **Kosimo said:**
>  Busca xres i yres i digues quina veus, i quin monitor tens, així podriem ajudar-te a posar una que provablment el teu monitor sigui capaç de mostrar

Em surt:

xres=1280
yres=1024

És un portàtil amb pantalla de 17" (HP Pavilion)

---

### Post by Kosimo on 2007-10-23
> **muleta said:**
> Em surt:

xres=1280
yres=1024

És un portàtil amb pantalla de 17" (HP Pavilion)

Canvia aquestes dades per aquestes altres:

xres=1024
yres=768


Reinicia i fes-nos saber, no t'oblidis de l'última comanda també:


sudo dpkg-reconfigure usplash

---

### Post by muleta on 2007-10-23
Oh, sí... quina diferència!. Ara triga dos segons. RESOLT.

Gràcies.

---

### Post by muleta on 2007-11-03
Algú sap què vol dir això?:

```
9.215115 ACPI: Resource is not an IRQ entry
9.215407 ACPI: Resource is not an IRQ entry
9.215693 ACPI: Resource is not an IRQ entry
9.872112 kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block (0,0) 
```

M'ha sortit després de reiniciar l'ordinador quan he intentat canviar la resolució de pantalla perque no trigués 4 minuts a engegar-se.

---

### Post by muleta on 2007-11-07
Veig que ningú no em sap respondre. 

L'ordinador és un portàtil Compaq Evo N610c amb un disc dur de 60 Gb i una RAM de 500 Mb.

Dedueixo que es nega a executar l'Edubuntu per manca de recursos, perque és massa gran per a ell.

No crec que l'Ubuntu millori la situació, haurem de tornar a Windows.

---

### Post by papapep on 2007-11-07
Si fas un:

```
uname -a
```

què et mostra?

> Dedueixo que es nega a executar l'Edubuntu per manca de recursos, perque és massa gran per a ell.

D'on ho treus això?

EDICIÓ: El missatge te'l dóna en intentar instal·lar, o un cop arrenca el sistema quan ja has acabat la instal·lació de l'Edubuntu?

---

### Post by muleta on 2007-11-07
Em surt quan intento engegar l'ordinador on vaig instal·lar l'Edubuntu.

Ara no el tinc a mà però, suposo que, per donar-li l'ordre, l'hauré d'engegar.

Vaig instal·lar-hi l'Edubuntu, vaig explorar els menus, actualitzar, etc., el vaig apagar i, com que trigava 4 minuts a engegar-se, quan vaig voler-ho fer, vaig aplicar el consell que m'havieu donat per al meu ordinador (quan vaig actualitzar a l'ubuntu 7.10).

En reiniciar, és quan em va sortir això i ja no s'engega l'Edubuntu.

---

