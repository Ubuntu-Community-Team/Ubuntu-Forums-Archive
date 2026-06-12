---
title: "Actualització a 12.10 m'he quedat sense el menu superior i la barar lateral"
date: 2012-11-11
forum: Catalan Team
---

### Post by MorlanXaos on 2012-11-11
Per la meva sorpresa, després d'instal·lar l'ultima actualització, em trobo que nomes tinc l'escriptori; sense la barra superior i la barra lateral, per tant l'únic que puc per es un CTROL+ALT+SUPR, però jugant amb la opció de amagar o no la barra lateral, no aconsegueixo veure res.

Algú s'ha trobat amb el mateix problema?
De moment no puc fer res mes, que no sigui amb els programes que tinc a l'escriptori...:confused:

---

### Post by wgarcia on 2012-11-11
Possiblement es tracta d'un problema relacionat amb el controlador de la targeta gràfica. Tens una terminal? Si la tens entra:

```
lspci | grep -i vga
```

per veure quina targeta gràfica tens. 

Si no tens terminal i no la pots obrir, pots accedir a treballar en consola amb CONTROL - ALT - F1. Et demanarà usuari i clau i un cop validat podràs entrar la instrucció de més a dalt. 

Un cop acabat si vols tornar a la sessió gràfica entres

```
sudo service lightdm restart
```

i et donarà accés a la pantalla d'inici un altre cop.

---

### Post by MorlanXaos on 2012-11-11
> **k1932k said:**
> :guitar:spam

No, no tinc el terminal, però gracies, crec que si que pot ser la targeta perquè, el que veig es que no tinc els controladors...
Vaig a probar-ho

---

### Post by MorlanXaos on 2012-11-12
Seguint las teves instruccions dona:

*01:00.0 VGA Compatible Controller: Advanced Micro Devices [AMP] nee ATI RV360 [Radeon HD 2600XT]*

Si, sembla que es correcte, perquè la targeta que tinc es la ATI Radeon HD 2600XT

---

### Post by wgarcia on 2012-11-13
Sí, correcte, és la targeta ATI que dius. A veure si hi ha algú altre que tingui aquest tipus de targeta que pugui donar una mà. Si no hi ha resposta des de la terminal es pot mirar si està usant el controlador lliure i propietari, i a veure què es pot fer.

---

### Post by wgarcia on 2012-11-13
De totes maneres mira si les instruccions que donen aquí et serveixen:

[http://ubuntuforums.org/showpost.php?p=12307070&postcount=10](http://ubuntuforums.org/showpost.php?p=12307070&postcount=10)

---

### Post by MorlanXaos on 2012-11-14
Be, sembla que seguint les instruccions ho he fet funcionar. Eliminant els controladors VESA i instal·lant el AMD.

Aquestes coses son les que em porten a la frustració dels sistemes Linux. En cap moment, he fet cap manipulació del sistema, es mes, quant vaig fer la primera instal·lació d'Ubuntu, ell mateix va posar els drivers corresponents i que han funcionat fins ara, al passar a 12.10. 

Ubuntu millora dia a dia, pero crec que encara falta temps per poder anar mes enllà, al menys pels usuaris menys versats a treballar amb la consola. Fa por i tenir que enfrentar-me en tot aquest galimaties d'ordres no te sentit per a mi, com usuari. Ep! que tinc els meus anys, i en el seu moment ja vaig jugar prou amb el BASIC en la consola Amstrad y després amb el DOS dels primers PCs fins i tota vaig fer alguns petits programes amb Turbo Pascal, però ara creia que tot aixo ja estava enrere i que es podria fer tot des de una interfície mínimament gràfica.

Be que hi farem.
De totes maneres gracies per la teva ajuda.

---

### Post by wgarcia on 2012-11-15
El problema principal és que els fabricants de components, com per exemple ATI, es preocupen de mantenir actualitzats els controladors per a sistemes Windows perquè ve preinstal·lat als ordinadors, i si deixen d'actualitzar aquests controladors òbviament els perjudica molt les vendes. Com Linux no ve preinstal·lat als ordinadors no hi ha tanta presa en actualitzar els controladors i a vegades el que ens funcionava en una versió ens deixa de funcionar en una altra. Amb sistemes ATI (i NVIDIA, tot i que són més ràpids aquests últims en la meva experiència en actualitzar controladors) jo intento sempre fer una prova primer amb un USB o CD autònom (live) abans d'actualitzar. 

Fins que Linux no aconsegueixi ser un sistema preinstal·lat als ordinadors i que la gent trobi a les botigues, ho tenim cru. Canonical crec que està fent un intent seriós d'aconseguir això, tot i que no sé si se'n sortirà (ells diuen que ja estan venent uns 5 milions de Dell amb Ubuntu preinstal·lat a la Xina cada any i que va creixent). Un altre intent molt prometedor és el Chromebook de Google. De fet Linux d'alguna manera ja és el sistema dominant a mòbils, i properament ho serà també de tauletes, si no ho és ja. També ho és en sistemes integrats que ni notem a diversos electrodomèstics, sense parlar de servidors on domina des de fa molts anys. 

Sols falten els ordinadors personals, que es resisteixen per les escandaloses pràctiques monopolistes de Microsoft, que en aquest àmbit sempre s'han tolerat tant a Europa com en la resta del món.

---

### Post by MorlanXaos on 2012-11-15
Gracies per la teva resposta.
Esta clar el problema. Ja ho h viscut amb la targeta wi-fi, fins que finalment la vaig canviar per una SMC, i que va como oli en un llum. I també l'impressora, un HP 4500 Wireless, i que Ubuntu la va reconèixer enseguida i va instal·lar el programari necessari perquè funciones. (I millor que en Windows)

Però aquestes petites coses donen una mica (bastant) de mal de cap.
):P

---

