---
title: "Problemes al actualitzar de la 7.04 a la 7.10"
date: 2007-11-14
forum: Catalan Team
---

### Post by Minotaure on 2007-11-14
Hola,

En un missatge de fa uns dies vaig preguntar si a la versió 7.10 ja detectava el lector de targetes al portàtil Acer Aspire 5633. Segons el què em vareu contestar sí que havia de funcionar però de totes maneres em vareu donar la idea de provar-ho prèviament amb un LiveCD. Això vaig fer. Vaig poder comprovar que des del LiveCd de l'Ubuntu 7.10 detectava el lector de targetes 5 en 1 i funcionava perfectament.

Això em va fer decidir a actualitzar-me a la versió 7.10 des del propi gestor d'actualitzacions de l'Ubuntu. Vaig seguir el passos i després de descarregar-se via wifi tots les fitxers, la qual cosa va tardar moltíssimes hores (això vol dir tranquil·lament 10 hores) tot i tenir una ADSL de 6 Mb (en els test de velocitat dona 4 Mb de descarrega).

El fet és que un cop va començar a instal·lar el paquets em va sortir un error que no podia instal·lar o actualitzar un paquet d'alguna cosa de la cups, i cada vegada que hi havia un paquet relacionat amb la cups em donava el mateix error, però els altres els instal·lava bé. Ara bé, la meva sorpresa va ser que quan encara no havia ni arribat a 3/4 parts de l'actualització va sortir un error general dient que s'havia de cancel·lar l'actualització i així va ser, no es va completar i va reiniciar el sistema. En un primer moment no em va aparèixer l'escriptori, però al tornar a iniciar sí que em va aparèixer.

El fet és que ara la majoria de cops que inicio l'Ubuntu es mostra correctament l'escriptori, però hi ha cops que se'm queda només amb la imatge de fons (sense els menús) i haig d'apagar directament l'ordinador perquè no puc fer res. D'altra banda al engegar l'ordinador, i abans de sortir el logo d'Ubuntu em surten 3 errors (lletra blanca amb fons negra) de "not allocated resource memory" o alguna cosa semblant.
Quan vaig a Sistema > Quant a Ubuntu em surt com si tingués instal·lada la versió 7.10.

M'agradaria que algú em pogués ajudar a tornar el sistema operatiu estable i poder completar correctament la instal·lació del 7.10.

Moltes gràcies.

---

### Post by papapep on 2007-11-14
Minotaure, has de posar exactament els missatges d'error per a que et poguem ajudar.

No estaria de més, si no ho has fet ja, que et llegissis el post que hi ha remarcat a la pàgina principal del fòrum ;-)

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

---

### Post by Minotaure on 2007-11-14
El problema és que no me dona temps de llegir-los i encar menys d'apuntar-los o memoritzar-los.

Com puc fer perquè es quedi parat a la pantalla del errors abans que surti el logo d'Ubuntu amb la barra de progrés??

---

### Post by papapep on 2007-11-14
Podries fer-li una foto al monitor. Hi ha gent que ho ha solucionat així.
Tot i això, el missatge que esmentes, apunta a un problema amb la RAM.
Potser seria bó executar el MEMTEST que t'ofereix el live-cd en arrencar, a veure si detecta algun error als mòduls de memòria.

---

### Post by Minotaure on 2007-11-15
Gràcies per l'ajuda, aquest cap de setmana (avui i demà no tinc temps) provaré el que em dius del memtest i també provaré si puc enganxar els missatges fent un foto.

---

### Post by Minotaure on 2008-01-25
Com podeu veure lamentablament ho he deixat anar a passant i fins avui no puc escriure aquest missatge amb els errors que em surten.

Els errors a l'inici es poden veure a les següents imatges:
[[IMG]http://img168.imageshack.us/img168/4435/errorsinicilt4.th.jpg[/IMG]](http://img168.imageshack.us/my.php?image=errorsinicilt4.jpg)
[[IMG]http://img252.imageshack.us/img252/644/imgp7181cy6.th.jpg[/IMG]](http://img252.imageshack.us/my.php?image=imgp7181cy6.jpg)


Vaig executar el memtest i em va detectar 2 errors:
Tst: 5 Pass: 2 Failing Adress: 00079e20c38-1950,OM
Tst: 5 Pass: 3 Faling Adress: 00079e20c3u-1950,OM

Good: 20000000
Bad: 20000100
Err. Bits: 00000100
Count: 1


M'agradaria poder solucionar aquest problema i tenir l'Ubuntu instal·lat de froma fiable el més abiat possible, ja que per culpa d'això no em funciona el servidor d'impressores cup's i ara m'està portant molts molèsties, ja que haig de copiar els fitxers a altres PC's per poder imprimir els documents.
Igualment no fa gaire gràcia treballar amb un s.o. inestable, amb errors importants durant la instal·lació.

Què em suggeriu fer per solucionar aquest problema?

Moltes gràcies.

---

### Post by patrickfromspain on 2008-01-25
canviant el modul de ram que et falli xD

---

### Post by Minotaure on 2008-01-25
> **patrickfromspain said:**
> canviant el modul de ram que et falli xD

Com, m'estàs dient que és un problema de hardware?
Que amb el Windows amb funcionava de conya, que amb l'Ubuntu 7.04 també (a excepció de que no funcionava el lector de targetes), que vaig fer un memtest i no va donar cap error, i que resulta que per "casualitat" en el moment d'actualitzar a la 7.10 falla la RAM?

Si és problema de la RAM, és possible que fos l'actualització a la 7.10 que espatllés algun mòdul?

---

### Post by papapep on 2008-01-25
> Com, m'estàs dient que és un problema de hardware?

Jo també crec que sigui hard, però no tinc clar que sigui la ram.

A la fotografia no distingeixo el que hi ha a la dreta de tot. On diu:

> PCI failed to allocate mem resource error

ha d'acabar posant:

```
for 0000:XX:YY.Z 
```

Els número que no tinc clar quins són i he posat amb X's, poden ser la pista per saber quin dispositiu et dóna problemes.

Si fas:

```
lspci | grep XX:YY
```

pot indicar quin és el ferro que has de mirar.

> Si és problema de la RAM, és possible que fos l'actualització a la 7.10 que espatllés algun mòdul?

El que es possible es que s'espatlles durant o després, però no "per causa" de la actualització.

---

### Post by Minotaure on 2008-01-25
Moltes gràcies papapep per les explicacions.

Els números que no veies clar són:
0000:01:00.0

I executant la comanda que m'has dit:
comunitari@portatil-acer:~$ lspci | grep 01:00
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

És ad ir, que segons això el problema està en al targeta gràfica?
Això li veig sentit per una banda, ja que des de que em vaig instal·lar l'actualització de l'Ubuntu la pantalla és una mica més fosca del normal, però cap per a l'altra no vieg que pot tenir a veure la targeta gràfica amb el servidor cups d'impressores qeu no funcioni i precissament fos el que dongués l'error durant al instal·lació.

---

### Post by papapep on 2008-01-25
Ara el que jo provaria és a ficar qualsevol altre gràfica a veure què passa, per intentar delimitar si realment el problema ve de la GeForce Go 7300 o no.

---

### Post by patrickfromspain on 2008-01-25
> **Minotaure said:**
> 
Vaig executar el memtest i em va detectar 2 errors:
Tst: 5 Pass: 2 Failing Adress: 00079e20c38-1950,OM
Tst: 5 Pass: 3 Faling Adress: 00079e20c3u-1950,OM

Good: 20000000
Bad: 20000100
Err. Bits: 00000100
Count: 1

Be, abans has dit que el memtest et dona errors... i per tant jo juraria que es algun modul de memoria RAM no? O al menys, hi ha un probabilitat molt gran de que ho sigui.

EDITO: no, l'actualitzacio no t'ha petat cap modul de RAM.

salut!

---

### Post by torracastanyes on 2008-01-26
A més d'actualitzar el sistema, has tocat res de "dintre" de la màqina?
Has mogut o canviat l'ordinador de lloc?
Ho pregunto perquè, avans de canviar res (no sé si encara s'és a temps), convindría que comprovessis que totes les connexions (connectors i targes) estan ben ferms i al seu lloc, encara que tot sigui aparentment correcte
M'he trobat amb cassos així alguna vegada.

---

