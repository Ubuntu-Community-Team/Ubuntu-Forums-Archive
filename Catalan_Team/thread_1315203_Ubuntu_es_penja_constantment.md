---
title: "Ubuntu es penja constantment"
date: 2009-11-05
forum: Catalan Team
---

### Post by Omit7 on 2009-11-05
Hola a tots,

Tinc un ordinador amb les següents caracteristiques:

Pentium 4 amb 512 Mb de Ram a 2.8 Ghz
120 Gb de disc dur (100 Gb lliures)
Targeta gràfica Nvidia Gforce Fx 5200 amb 128 Mb

El problema es que es penja constantment(escribint aquest missatge s'ha penjat 3 cops)

Crec que ja ho he probat tot i no aconsegueixo resoldre el problema. Això es tot el que he probat:

-Memtest. Ok en totes les ocasions
-Control de temperatura. Placa mare entre 34º i 45º. Processador entre 36º i 65º. Per si de cas he tret les tapes de la caixa de la CPU per a que refrigeri millor.
-He probat amb tot tipus de distros. Xubuntu,Kubuntu,Debian,Suse,etc...
-He desactivat totes les aplicacions de inici que no necesito (bluetooth, accesibilitat, notificacions Evolution, etc.)
-He probat amb altres navegadors mes lleugers.
-He desactivat del firefox tots els components innecesaris que tenia.


I després de tot això no aconsegueixo resoldre-ho. Es continua penjant.

Si algú em pot ajudar o donar alguna pista de que mes puc probar...

---

### Post by papapep on 2009-11-05
Has provat, si en tens disponibles, a posar una altra tarjeta gràfica a veure què fa? per cutre que sigui. Molts cops els problemes vénen per aquí.

---

### Post by Omit7 on 2009-11-05
No, no acostumo a trastejar la maquinaria de l'ordinador per que no es quelcom que domini, però aquest cop estava tant deseperat que he probat lo de la caixa perque semblava força senzill.

Insinues que pot ser un problema de compatibilitat de la targeta gràfica?

---

### Post by papapep on 2009-11-05
> Insinues que pot ser un problema de compatibilitat de la targeta gràfica? 

Bé, és una de les opcions. Digues-li incompatibilitat, digues-li que potser no està ben inserida al seu slot. Poder ser, pot ser.

> El problema es que es penja constantment

Amb això vols dir que es queda completament inoperatiu i que l'has de reiniciar cada cop amb el botó físic per a poder tornar a arrencar tot l'ordinador i poder treballar?

Quan se't "queda penjat", si fas la combinació de tecles Ctrl+Alt+F1 (o F2, o F3), pots anar a un tty?

---

### Post by Omit7 on 2009-11-05
En referencia a la targeta grafica, ja buscaré si trobo alguna guia per tal de assegurar-me que esta ben inserida.

Sí quan dic penjat, vull dir que haig de reiniciar amb el botó físic perque no respon a absolutament res de res.

---

### Post by papapep on 2009-11-05
> En referencia a la targeta grafica, ja buscaré si trobo alguna guia per tal de assegurar-me que esta ben inserida.

No cal cap manual per això, home. Simplement, desendolles el cable de la corrent, descargoles la placa gràfica (o treus l'anclatge si és dels que no porten cargols), bufes l'slot (intenta no tocar els xips amb les mans, agafa-la per les vores), mira que no tingui quisca pels contactes i torna-la a posar on era ferma i carinyosament (les dues coses :D). A vegades tonteries així porten problemes. També hi ha l'opció de que estigui feta malbé, clar...o potser és alguna altra part del maquinari. Si tant de programari diferent té el mateix simptoma, cal aïllar el problema canviant el ferro a veure què és el que falla.

---

### Post by Omit7 on 2009-11-05
D'acord doncs. Ja ho probaré hi et diré el resultat.

Merci

---

### Post by CarlesOriol on 2009-11-06
Prova també de fer un test de memòria. 

Iniciant l'ordinador al menu GRUB tries memtest

---

### Post by papapep on 2009-11-06
> Prova també de fer un test de memòria.

Iniciant l'ordinador al menu GRUB tries memtest

neeeen: [llegeix bé]("http://ubuntuforums.org/showpost.php?p=8247201&postcount=1").

Estàs perdent la forma... :P

---

### Post by Omit7 on 2009-11-06
Doncs, un cop verificada la conexió de la targeta gràfica, tot segueix igual.

A mi em segueix semblant que ha de ser alguna cosa relacionada amb la memòria, ja que em dona la sensació que es penja mes sovint quant tinc varies tasques obertes, o utilitzo programes que utilitzen mes recursos (jocs flash, transmission, reproduccio de video, etc...). Per aquest motiu he probat de reduir el consum de recursos al màxim. No se si hi ha alguna manera de verificar que l'us de la memoria RAM i Swap es fa de forma correcta.

Si em podeu suggerir alguna altra comprobació..

---

### Post by sordoman on 2009-11-06
Doncs et proposo ke revisis la conexió del ratolí, sembla una xorarda perofa una estona ke m'ha donat un mal de cap increible, es penjava feia coses rares dins ke per casualitat ho he vist.

No se espero ke funcioni

sort
):P

---

### Post by papapep on 2009-11-06
Omit7: com t'he comentat abans, és anar substituit ferro (la RAM per exemple) fins que trobes quina falla. Si el Memtest no et dóna error seria estrany que fos això, però coses més grosses he vist.

Sordoman: està bé fer servir la **K** quan pertoca (poquetes vegades en català) però la resta de cops intenta fer servir la **C** o la **Q** que també hi juguen.
No cal redactar poesia aquí, però estaria bé no escriure en sistema SMS ;)

---

### Post by kimet on 2009-11-06
Bones.

Permetem suggerir-te que provis amb una distribució especialment lleugera, perquè 512mb de ram són força justets per a l'ubuntu, slitaz o alguna d'altre similar.

Una altre cosa que se'm pasa pel cap és el driver que utilitzes per a la gràfica, es el privatiu? prova de camviar al xorg.conf (/etc/X11/xorg.conf) el driver "nvidia" per el "nv".

Salutacions a la comunitat.

PD. Precisament en aquesta mateixa pàgina, una mica mes avall, hi ha un post que en parla de distros lleugeres.

---

### Post by Omit7 on 2009-11-06
Sordoman: Gràcies pel suggeriment, però està correctament conectat.

Papapep: Entessos doncs, si no trobo cap altre solució, visitarem al técnic per a que hi faci una ullada.

Kimet: el xorg.conf no el trobo a la ruta que m'especifiques.El que trobo es -> xorg.conf.5gz a /usr/share/man/man5. Es normal?

---

### Post by kimet on 2009-11-06
Si és normal, a les últimes versions de x.org, aquest pren la configuració de Hal, pero com la teva gràfica es vella hi ha la possibilitat de que no la reconegui.

Pots crear el fitxer xorg.conf la ruta que t'he dit i posar-hi la configuració de la part del driver.

```
#nano /etc/X11/xorg.conf
```

i enganxar-hi:

```
Section "Device"
	Identifier	"Configured Video Device"
        Driver          "nv"
      EndSection

```
control+o per desar
control+x per sortir

Si així és sol.luciona torna a preguntar com instal.lar el driver privatiu.
Tot i aixó és molt probable que sigui un problema de ferralla

Salut

---

### Post by Omit7 on 2009-12-11
Bé, finalment despres de probar-ho tot. He trobat la sol·lució, efctivament com deia en papapep era "FERRO".

Així que com que ja era una mica vellet, he canviat el processador, he augmentat la RAM i he canviat la targeta gràfica. I voilà, tot rutlla.

Gràcies a tots per l'ajuda prestada.

---

