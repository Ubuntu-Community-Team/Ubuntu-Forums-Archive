---
title: "problema al engegar"
date: 2010-08-27
forum: Catalan Team
---

### Post by gunyoles on 2010-08-27
Soc nou i potser m'he equivocat en alguna cosa.
tinc instalació dual, Ubuntu10.4 i Windows7  i com que hem faltava espai per l'ubuntu decideixo treura-li un troç de disc dur al windows7, que en tenia de sobres. quan torno a arrencar l'ubuntu diu el seguent missatge: "la configuració per defecte del gestor d'energia del GNOME no ha estat instalada correctament"
Es pot reparar? no he tingut temps de fer copies de seguetat i tinc informacio que no vull perdre.
algú hem pot ajudar?:(
gracies per endevant:)

---

### Post by kukat on 2010-08-28
Unes preguntes....
La insta&#320;lació de l'Ubuntu és nova, o ja la tenies abans???

Pots entrar a la consola prenent CTRL + ALT + F1 ??? 

Gràcies

---

### Post by gunyoles on 2010-08-28
hola kukat
la instalacio del Ubuntu es nova, uns quinze dies, es va intalar un cd que vaig rebre de Canonical. El windows es el amfitrio que ja tenia. tot anava be, actualitzacions, instalacio de programes per cubrir les meves necesitats, etc.., fins fa dos dies que hem quedo sensa memoria per l'ubuntu i intento pasar-ne desde windows. quan engego arriva la pantalla de identificacio amb el missatge que he dit, a dalt a la dreta de la pantalla que despres s'apaga, m'identefico, es posa uns segons en pantalla negre i totna a sortir la de identificacio amb el mateix missatge fent un bucle. L'unic que hem permet es sortir i treballar amb l'altre SO.
pregunto, pot ser que m'hagi carregat l'escriptori? es pot reinstalar sensa fer una instalacio sencera nova? tinc molts dubtes i estic buscant informacio per a tot arreu perque no vull perdre la informacio que tinc a dins i de moment no trobo res.
espero que l'explicacio et serveixi per alguna cosa i hem donis un cop de ma.
fins aviat  
  :confused::confused::confused:

---

### Post by gunyoles on 2010-08-28
per cert la resposta a la segona pregunta es [SIZE=4]SI[/SIZE]
 
potser per aqui podrem fer alguna cosa, o aixo espero.  [-o<
gracies per l'interes.

---

### Post by kukat on 2010-08-28
pot ser hages espatllat alguna cosa de les X (el que s'encarrega de l'apartat gràfic....)

pots provar a ficar-te a **CTRl + ALT + F1**

i fer el següent:

**sudo dpkg-reconfigure xserver-xorg**

i seguir els passos per a re-insta&#320;lar el servidor de les X. 

De totes formes, si la insta&#320;lació és nova...no hi ha problema supose. Pots recuperar les dades importants que tingues a dins de la partició de l'Ubuntu mitjançant qualsevol LIVE CD, i en el cas que no funcione el de dalt, re-insta&#320;&#320;ar el sistema operatiu Ubuntu.

---

### Post by gunyoles on 2010-08-28
gracies per les ideies
primer intentare acedir a les dades amb el Live CD per copiar-les a un lloc segur, per si de cas. Despres provare la reconfiguracio que hem dius i si no, com que el que tinc que salvar ja estara segur, puc fer una instalacio nova que es el que hem feia mes por. dema ho provo amb tranquilitat i ja dire quelcom de com ha anat
 
:-\":-\"

---

### Post by wgarcia on 2010-08-29
Quan dius que has incrementat l'espai per a l'Ubuntu, com ho vas fer? Des del Windows 7?

---

### Post by gunyoles on 2010-08-29
Va ser una acció equivocada perquè la intenció era alliberar espai utilitzat per Windows i el que aquest va fer aquest en reduir el volum assignat es carregar-se tot el que va trobar pel mig i no reconeixia com a propi.#-o

La solució final ha sigut extreure els fitxers importants manualment a traves
 [B]CTRL + ALT + F1
[/B]llavors a base de obrir directoris i entrar en ells 

 [B]usuari@ubuntu:~$cd nom_arxiu
 usuari@ubuntu:~/nom_arxiu$ dir[/B]

i així anar fent fins arribar a cada element que m'interessava salvar i que no estava malmès pel finestres dels collons, per poder-lo copiar a un altre disc exterior.

Al final he tingut que fer una reinstal·alció nova perquè amb Live cd no podia obrir cap fitxer perquè en nom d'usuari no coincidia, i es que en l'aplicació en Live no he estat capaç de canviar-li el nom, venia per defecte
 **ubuntu@ubuntu:~$**
i jo tenia un altre posat.

Res tot nou, torna a actualitzar-ho i configurar-ho tot, torna a posar-hi la documentació que no tenia a les copies de seguretat, ara si que hi son, que nomes son unes horetes davant la maquina.

De totes maneres gracies a KUKAT que ha fet que vegi la possibilitat de fer alguna a traves del panell de control =D>

Ara també tinc una cosa encara mes clara, el senyor de les finestres no te cap ètica i no tolera la instal·alció dual, vol ser ell sol, i ho aconseguira. Al final tots li direm adéu):P

---

### Post by kukat on 2010-08-30
Ep!
Com diu wgarcia, si ho vas fer des de Win7...
win7 no sabrà que és "ext4", el sistema de fitxers de l'Ubuntu.....
:D

Tants diners que val el Win, i no detecta sistemes de fitxers que no siguen el seu! :D

Per cert, si fas CTRL + ALT + F1 fins a F6, tens les "tty" que vulgues! 
XD

Salut!

---

### Post by gunyoles on 2010-08-30
ja vaig avisar que soc nou i moltes coses encara les desconec. Ara el win7 si que diuen que val uns diners, però es el que et ve quan compres un equip, no pots triar de moment.
Ja aniré aprenent, ensopegant, suposo que com tots, però ens en sortirem.
\\:D/

---

### Post by wgarcia on 2010-08-31
El win7 sí que val diners, te'l fan pagar en comprar l'ordinador, i com tu dius en pràcticament tots els llocs "no pots triar" no pagar-lo perquè es basa en un acord entre el fabricant i Microsoft que obliga al fabricant a vendre l'equip amb aquest sistema operatiu. 

Quant a la solució del teu problema potser ha estat més dràstica del necessari. Com deia kukat, el win7 no veu el sistema de fitxers de linux (ext4) i per tant no el pot esborrar. El que fa es esborrar l'arrencada (grub) que és el de dirigeix el sistema a un sistema operatiu o un altre, però el linux continua estant allà. En conseqüència per arreglar-ho simplement es tracta de reinstal·lar el sistema d'arrencada que s'ha carregat el win7 (el "grub", un programeta molt senzill i que no ocupa pràcticament lloc), cosa que no és massa complicada i en la qual molts participants d'aquest fòrum et poden guiar. 

Una de les coses bones del linux es que es poden arreglar pràcticament totes les coses sense necessitat de reinstal·lar, perquè l'usuari té un control molt més gran de tot el sistema operatiu.

---

### Post by gunyoles on 2010-08-31
Hi ha un petit detall que cal tenir en compte, cap sistema operatiu esborra dades del disc dur, a tot cas sobreescriuen sobre allò que no necessiten quan aquest es ple. Els fitxers que creiem que esborrem nomes els hi posem una etiqueta de sobreescriure. Per això la científica el primer que fa en un escorcoll es revisar els discos durs, per treure la informació que la gent es pensa que esta esborrada i allà està tot des de el dia que es va muntar.
El problema es que windows normalment no reconeix els fitxers d'altres SO i els sobreescriu, fins hi tot en una desfracmentació feta a Windows he perdut informació de l'altre quan a començat a moure fragments propis de un lloc a un altre.

Si alguna vegada et desfàs d'algun equip perquè ja no et fa servei, extreu el disquet del HDD i trinxa'l que ni que el formateu queda una pila d'informació que ni t'ho imagines.

---

### Post by wgarcia on 2010-08-31
D'acord, però a més quan està en format "ext4" el windows ni tan sols el toca ( a no ser que li demanis que formategi tot el disc) perquè ni el "veu"...

---

### Post by gunyoles on 2010-09-01
Si no ho veu sobreescriu a sobre sense remei, de fet que uns fitxers siguin transparents per un altre sistema es gairebé d'esperar que els trepitgin. Hauria d'haver algun mètode que no permetes que windows trepitges el que troba per davant. La sort es que quan fas una instal·lació dual, progressivament deixes de banda Windows, que així requereix menys quota de disc i augmentes la de Ubuntu que si que respecta els fitxers que troba, que no son seus i no tenen etiqueta de sobreescriure.

---

### Post by wgarcia on 2010-09-01
No sobreescriu res a no ser que formategi el disc. El que sí sobrescriu és el MBR (master boot record) del disc, però no una partició formatejada amb "ext4". Sols sap escriure, sobreescriure, etc., a particions "fat32", "ntfs", ...

---

