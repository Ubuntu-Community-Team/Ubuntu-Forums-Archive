---
title: "[SOLVED] Compressió d'arxius"
date: 2007-08-08
forum: Catalan Team
---

### Post by pablinsfc on 2007-08-08
Hola companys!!

Us volia preguntar si algú sap perquè em surt el següent missatge al intentar descomprimir arxius amb l'Ubuntu, que prèviament havia comprimit amb WinXP (amb Winrar).

"No s'ha pogut obrir 'nom.rar'
Aquest tipus d'arxiu no està implementat".

Gràcies!

---

### Post by RainCT on 2007-08-08
Hola,

per poder descomprimir arxius .rar has te tenir insta&#320;lat el paquet 'unrar' dels repositoris (per exemple, des del Synaptic).

---

### Post by lluisanunez on 2007-08-08
unrar és un programa de línia de comandes (CLI), però si te l'insta&#320;les, podràs comprimir i descomprimir RAR des del mateix File Roller o Nautilus (GUI)

---

### Post by CarlesOriol on 2007-08-09
Pots insta&#320;lar el rar (llicència restrictiva) o unrar amb el synaptic. 

Qualsevol dels dos s'integra perfectament amb el gestor gràfic de paquets comprimits.

(L'unrar -amb llicència lliure- sols descomprimeix)

---

### Post by orestesmas on 2007-08-11
Jo afegiria que hi ha 2 versions del UNRAR: la lliure i la no lliure. La primera no pot descomprimir fitxers comprimits amb la versió 3.X del RAR.

L'ús del RAR en linux només et donarà que problemes. Hi ha altres mètodes de compressió (ZIP, GZIP...) que funcionen perfectament tant en linux com en windows i que no donen maldecaps. Potser la ràtio de compressió és un xic menor (tot i que m'agradaria veure un estudi seriós sobre el tema), però el guany de compressió no compensa els inconvenients.

Evita els RAR sempre que puguis. És tant dolent com el format .DOC però per als arxius comprimits.

---

### Post by pablinsfc on 2007-08-20
Bones! Merci per tot, ja està solucionat, ja ho tinc instal·lat. El problema és que els de la banda Windows ara estan que no caguen amb els .rar... però seguiré les vostres recomanacions, oi tant!

Salut!

Pau.

---

### Post by CarlesOriol on 2007-08-20
Llavors el millor que pots fer és insta&#320;lar el decompresor rar lliure i quan preparis arxius per companys que tinguin el winrar pots fer-ho en format tar.bz2  que el mateix programa llegeix.

---

### Post by Urfe on 2008-09-11
Hola.

Jo també tinc problemes per obrir arxius .rar

He probat a instal·lar programes com ark i rar (aquest no me'l deixa seleccionar per la descarga en "Añadir i quitar".

Ja no se què fer. Vull probar amb això dels repositoris però no sé qué són. Tampoc sé què és el Synaptic.

Gràcies.

---

### Post by papapep on 2008-09-11
Hola urfe,

Els repositoris són els servidors d'on després descarreguem els paquets de programari per instal·lar.

El Synaptic el trobaràs a Sistema > Administració > Gestor de paquets Synaptic. És el programa en mode gràfic per a instal·lar, eliminar o configurar paquets de programari.

Et recomano llegir documentació sobre Linux i Ubuntu per entendre aquests, i altres, conceptes sense els quals no entendràs res. [Aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos") trobaràs uns quants documents interessants, però a internet en trobaràs milers, i si entens l'anglès, milions.

Un dels que t'hauries de mirar primer és [aquest]("https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat"), que t'ajudarà a fer-te una idea global de tot plegat.

Pel tema dels fitxers rar, fes a un terminal (obre el programa: Aplicacions > Accessoris > Terminal):

```
sudo aptitude search rar
```

Quan facis això i premis intro, et demanarà la contrasenya. Quan la posis no la veuràs, no t'estranyis. Quan estiguis, prem intro i, si ho has fet bé, veuràs que pensa uns segons i et torna un llistat. Aquest llistat copia'l i enganxa'l al teu següent missatge aquí. :-)

---

