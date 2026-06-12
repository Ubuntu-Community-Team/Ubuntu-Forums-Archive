---
title: "[SOLVED] Sóc nou. Problemes amb wifi..."
date: 2007-07-17
forum: Catalan Team
---

### Post by girotix on 2007-07-17
Salutacions a tothom,

Un company de feina porta temps "donant-me la vara" amb això del LINUX. Ja que fa dues setmanes em vaig comprar un ordinador portàtil HP Pavilion dv t6000, vaig pensar que era un bon moment per a provar això del Linux...

Així que m'he instal·lat la darrera versió de l'UBUNTU. Bé, tot i ser novato total no he tingut gaires problemes ja que només l'utilitzo per escriure i navegar. 

La única cosa que no he aconseguit fer funcionar (a saber) és el wifi. La llumeta que indica que aquesta antena o detector o el-que-sigui està funcionant no s'activa.

Si premo un "Hardware information" em surt que jo tinc això: Dell Wireless 1390 WLAN Mini-PCI Card. 

Algú em pot fer un cop de mà? 

Per acabar, només dues coses. He buscat en aquest forum i no m'ha semblat trobar algun "post" anterior sobre aquest problema. La segona és que jo em plantejo l'ordinador com un instrument d'ús i no m'agrada gaire això d'entretenir-me més del necessari amb la informàtica (recordo que vaig llegir un post comparant l'ordinador amb un rentadora, doncs jo sóc d'aquests). Tot i això, vull introduir-me amb el LINUX per una qüestió de principis i m'ho plantejo com una cosa a llarg termini, d'aprendre pas a pas.

Moltes gràcies per anticipat,
Carles.
Girona.

---

### Post by papapep on 2007-07-17
Té pinta de que aquesta placa wifi que dius no tingui un mòdul propi desenvolupat per Linux. O sigui, que sembla que et caldrà fer servir ndiswrapper per a fer-la funcionar.
Si no tens molt problema amb l'idioma d'en Chekspir, aqui: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) trobaràs un post que parla de com fer-ho tot plegat.

---

### Post by girotix on 2007-07-19
Hola!

He provat de seguir les instruccions del post que vas esmentar i no m'ha anat bé. Tot això dels comandaments en línia és nou per a mi i segur que estic fent quelcom malament.

En fi, quan tingui  temps ho tornaré a repassar.

Gràcies,
Carles.

---

### Post by papapep on 2007-07-19
Tu mateix, ja diràs si et cal alguna cosa. Si ens dius on et quedes o què no entens segur que ho tindràs més fàcil.

---

### Post by girotix on 2007-07-23
Hola!

Segueixo les instruccions del post i és la segona vegada que em quedo encallat al pas 4: 

Literalment el text diu:

[COLOR="Blue"]Now change directories (cd) to the DRIVER directory that was just extracted.

Code:

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l[/COLOR]

Entenc que tinc que cercar el directori DRIVER i aplicar aquestes instruccions, però...

[COLOR="Blue"]girotix@girotix-laptop:~/DRIVER$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
girotix@girotix-laptop:~/DRIVER$ sudo ndiswrapper -l
bcmw15 : invalid driver!
bcmwl5 : invalid driver![/COLOR]


Mmm... Crec que fins aquí ho había fet tot bé (després de diversos prova i error), però no puc assegurar-ho per què d'algunes coses senzillament no he entès el que he fet. 

Això darrer mereix un aclariment. M'hi entenc força amb la llengua anglesa, el que no conec són aquestes instruccions de les línies de comandament. Algunes ja les he esbrinades però d'altres, bé... de mica en mica.

El post que em vares passar té 63 pàgines en aquests moments. Cercant he vist alguna referència a ordinadors semblants al meu però de moment no m'ho he mirat a fons ja que prefereixo assegurar-me que faig aquests primers passos correctament.

Gràcies,
Carles.

---

### Post by girotix on 2007-07-25
Salutacions,

Nois, no m'ensurto. Segueixo encallat al mateix lloc. O sigui, allò del INVALID DRIVER! que us comentava al missatge anterior.

He cercat a altres fòrums, a la web original de UBUNTU i també la de NDISWRAPPER.

Si algú em pot fer un cop de mà...

Gràcies per endavant,
Carles.

---

### Post by papapep on 2007-07-25
Crec que seria bo que ens deixessis veure el resultat de l'ordre "lspci" i de la "dmesg".

Ja que no et funciona el procediment que semblava que havia d'anar bé, haurem de començar de base. :-)

---

### Post by girotix on 2007-07-27
Hola!

Ja tinc connexió!

Abans de mirar això que em comentes, he reinstal·lat l' Ubuntu i he tornat a escriure els comandaments. 

Al post que em vares indicar ja s'advertia que calia netejar bé els intents anteriors d'instal·lar el NDISWRAPPER i fins i tot aconsellava tornar a instal·lar l'Ubuntu. Per això, abans de provar el que em deies he intentat això i m'ha sortit bé :-)

Moltes gràcies pels consells,
Carles.

---

