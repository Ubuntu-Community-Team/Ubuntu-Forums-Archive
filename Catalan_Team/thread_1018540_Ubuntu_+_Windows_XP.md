---
title: "Ubuntu + Windows XP"
date: 2008-12-22
forum: Catalan Team
---

### Post by Hecturt on 2008-12-22
Hola a tothom!
Tinc un ordinador portàtil i vull instal·lar-hi l'Ubuntu i el Windows Xp. Voldria saber si...

1- Puc formatar tota la unitat c en una sola partició NTFS?
2- L'Ubuntu es pot instal·lar en una partició NTFS?
3- Es necessari fer dues particions al disc, o l'Ubuntu s'encarrega de fer la seva pròpia partició quan s'instala? (una per cada OS)
4- Es possible crear una partició NTFS i una altra FAT32?
5- Quina es la mida recomanable per l'instal·lació de l'Ubuntu?

Ja he buscat pel posts publicats però de fet cap d'ells contesta aquestes qüestions amb claredat!

Gràcies per endavant!

---

### Post by oriolsbd on 2008-12-22
Hola,

Cada sistema operatiu s'ha d'instal·lar en una partició diferent. Apart, Ubuntu necessita (com a mínim, és altament recomanable) una partició d'intercanvi per a poder treballar en disc quan et quedes sense memòria real. Aquesta partició (que seria l'equivalent al fitxer pagefile.sys de Windows) en principi hauria de ser de 1,5 vegades la memòria que tinguis, encara que jo mai no l'he creada més gran d'1,5Gb. Apart, també és interessant (encara que no imprescindible) tenir en una partició separada el "/home". Les particions "/" i "/home", millor que siguin "ext3".

Quant a la mida de les particions, a la "/", pots assignar-li uns 7Gb. A la "/home" (si al final decideixes tenir-les separades) depèn de l'ús que li vulguis donar. És on hi aniran els fitxers de configuració del teu usuari i on, per defecte, es desaran els fitxers de les aplicacions (encara que això ho podràs canviar).

Si primer instal·les el Windows, el millor és que ho facis sobre una partició que no ocupi tot el disc, i deixis un espai sense particionar al final, que serà el que utilitzaràs en la instal·lació d'Ubuntu (ja hauries de tenir fets els càlculs de quant espai necessitaràs).

Per últim, quan instal·lis Ubuntu, li pots dir que et munti també la teva partició de Windows. Quan jo encara utilitzava Windwos, la muntava a "/windows" o a "/fitxers". Sobretot, si ho fas així, no marquis la opció de "formatar aquesta partició"... :-)

No sé si t'ho he respòs tot, o si m'he explicat prou bé. Demanaves molta cosa. :-)

---

### Post by Hecturt on 2008-12-22
Gracies oriolsbd!
El cas es que a hores d'ara ja tinc el Windows instalat!. T'explico com ho he fet... He formatat l'unic disc dur que tinc en format NTFS i tot en una sola partició. Tot seguit he instal·lat el Windows. 
El cas es que ara que em trobo en aquest punt inicial (no he instal·lat programes ni arxius) i que no m'importaria tornar a formatar, em pregunto si dins la instal·lació de l'Ubuntu tinc la possibilitat de decidir les particions sense carregar-me la instal·lació del Windows (reparticionar vaja!).
De la teva resposta però, em quedo amb la informació de les diferents particions i assignacions d'espai en disc que m'expliques.

Salut!

---

### Post by Kette on 2008-12-22
Hola,
Fes una ollada a aquest enllaç:

[Tutorials del Wiki Catalan Team]("http://wiki.ubuntu.com/CatalanTeam/Tutorials")

Espero que et serveixi d'ajuda.

Salut
Eugeni

---

### Post by oriolsbd on 2008-12-23
Ara no recordo si des de la instal·lació d'Ubuntu pots redimensionar una partició.

Jo el que faria és, abans que res, desfragmentar el disc de Windows. Encara que la instal·lació de Windows sigui nova i segurament no el tens massa fragmentat, segur que anirà bé. Després, redimensionaria la partició, deixant un espai sense particionar al final. Ho pots fer o bé amb el Partition Magic (o algun programa similar de Windows), o bé amb un LiveCD d'Ubuntu, amb el programa GParted. Tots dos programes van molt bé.

Un cop tinguis l'espai lliure sense particionar, executa la instal·lació d'Ubuntu, creant en aquest espai sense particionar les particions pròpies d'Ubuntu que creguis convenient. Quan et demani com vols fer les particions, indica que ho vols fer de manera manual (no automàtica). Sobretot, tingues en compte el que t'he comentat abans d'indicar que et munti on vulguis la partició de Windows, però _que no te la formategi_.

Salut!

---

### Post by RainCT on 2008-12-23
> **oriolsbd said:**
> Ara no recordo si des de la instal·lació d'Ubuntu pots redimensionar una partició.

I tant que pot :).

Te les opcions: esborra tot el disc i fes particions noves per a l'Ubuntu, redimensiona la partició existent (sense esborrar les dades) i fes-ne de noves per a l'Ubuntu en l'espai guanyat, i fer les particions manualment.

---

### Post by Hecturt on 2008-12-24
Us explico el que he fet finalment.
He formatat tota la unitat c (la única que tinc) en format NTFS. He instal·lat el Windows. He instal·lat alguns programes i he desfragmentat la unitat per tal de comprimir tota la informació al principi del disc. Aleshores he iniciat la instal·lació de l'Ubuntu. Quan he arribat a la pantalla que parla de particions, he estirat la partició del windows per redimensionar-la (he deixat un 20% per Ubuntu). He acabat la instal·lació de l'Ubuntu preguntant-me si m'hauria carregat la instal·lació del Windows.
Resultat:
Windows funciona correctament (només m'ha fet un scandisk la primera vegada que l'he iniciat). Ubuntu també funciona. Des de l'Ubuntu puc veure que m'ha muntat una unitat per aquest i una altra per Windows. Agradable sorpresa! Puc obrir arxius de la partició Windows des de l'Ubuntu!. 
Algú m'havia parlat de crear diferents particions per l'Ubuntu. Crec que això no m'ho ha fet. Es necessari fer-ho? Em funcionaria millor l'Ubuntu? De moment tot va com una seda. Es pot millorar?

---

### Post by oriolsbd on 2008-12-24
El fet de tenir el "/" i el "/home" d'Ubuntu en diferents particions no afecta al rendiment (excepte si són particions de discos diferents). L'únic que es millora és que, si algun dia has de reinstal·lar Ubuntu, tens separades les dades dels programes, i només caldria reinstal·lar Ubuntu a la partició "/", i mantindries totes les teves dades personals.

Si ho tens junt, si algun dia has de reinstal·lar Ubuntu hauràs de fer-te còpia de seguretat del "/home" i al final recuperar el que t'interessi. És un tema de comoditat.

Suposo que sí et deu haver creat una partició d'intercanvi (Swap), oi?

---

### Post by Hecturt on 2008-12-24
Doncs la veritat es que no ho sé. Si això es pot veure en el monitor de Sistema/Sistemes de fitxers et diré que aquí puc veure 3 unitats. T'adjunto imatge de la finestra per veure si em pots explicar que vol dir. Ok?

Gracies

---

