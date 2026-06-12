---
title: "problemes amb l'instalació de feisty"
date: 2007-06-12
forum: Catalan Team
---

### Post by alpicat on 2007-06-12
Hola, aquest és el meu primer post, a veure si algú em pot ajudar una mica...

la cosa està en que vaig fer un format a saco ficant feisty sobre la dapper que tenia abans i va funcionar bé. Llavors, vaig decidir que també necessitava una partició amb windows, que l'ordinador és una mica vell i el vmware em fa perdre la paciència. Total, que vaig ficar els discs de restauració del portàtil, i ja tenia la windows. Però ... al tornar a ficar el cd de ubuntu em dona errors i no es carrega ni la live. He probat a fer manualment desde windows una partició fat32 i despres una hex2 + swap, i res, el ubuntu no s'engega en live. Algú sap què pot ser? (suposant que no és que el cd és defectuós).

Gràcies!

---

### Post by Ferri on 2007-06-12
No sé si és possible, però se m'acut que potser els discs de recuperació t'han tornat la BIOS a una configuració que no té activada l'inici des del CD.

---

### Post by prostata on 2007-06-12
> **alpicat said:**
> Hola, aquest és el meu primer post, a veure si algú em pot ajudar una mica...

la cosa està en que vaig fer un format a saco ficant feisty sobre la dapper que tenia abans i va funcionar bé. Llavors, vaig decidir que també necessitava una partició amb windows, que l'ordinador és una mica vell i el vmware em fa perdre la paciència. Total, que vaig ficar els discs de restauració del portàtil, i ja tenia la windows. Però ... al tornar a ficar el cd de ubuntu em dona errors i no es carrega ni la live. He probat a fer manualment desde windows una partició fat32 i despres una hex2 + swap, i res, el ubuntu no s'engega en live. Algú sap què pot ser? (suposant que no és que el cd és defectuós).

Gràcies!

si ho he entès bé, vas ficar windows desprès d ubuntu?? doncs si és així el problema es del MBR, del windos que es carrega tot...el procediment és:

primer instal-las windows
segon instal-las ubuntu i que ell faci les particions

al fer-lo com entenc que ho has fet el master boot register de windows prenc posessió i per això no et permet fer res, crec que hauras de formatar el disc, i fer con te he dit.

---

### Post by patrickfromspain on 2007-06-12
be, dones molt poca informacio... on et falla al carregar-se el live cd??

---

### Post by alpicat on 2007-06-13
al posar el live cd comencen a sortir una serie d'errors, línies escrites com si fos en consola, fins que arriba un moment que es queda penjat i ja no abança més. Suposo que no és un fallo del cd, perquè el primer cop que el vaig posar va anar bé, però al intentar ficar ubuntu sobre windows no va. No se si queda més clar ara ...

---

### Post by prostata on 2007-06-13
> **alpicat said:**
> al posar el live cd comencen a sortir una serie d'errors, línies escrites com si fos en consola, fins que arriba un moment que es queda penjat i ja no abança més. Suposo que no és un fallo del cd, perquè el primer cop que el vaig posar va anar bé, però al intentar ficar ubuntu sobre windows no va. No se si queda més clar ara ...

Haveu-re alpicat, dis-me exactament això:

A) Vas instal-lar Windows sobre Ubuntu?
B) Vas instal-lar Ubuntu sobre windows?

si la opció va ser la segona, és a dir instal-lació de Windows a sobre d'Ubuntu, sols i si és així, ja t'ho vaig dir ahir. Tens un problema amb el MBR. si tens insterès en saber el que es el boot master register, busca'l al google i en trovarás  una mica més d'info.

No sé quin nievell d'informàtica tens però sàpigues que el MBR de windows prevaleix per sobre del GRUB, que és l'inici d'Ubuntu, per tant i com et vaig dir, si primer instal-las Ubuntu i a sobre windows, aquest prenc l'arranc del sistema pel MBR i anula o des habilita qualsevol sistema posterior o anterior d'arranc del sistema..
Per tant, fes el que vulguis, però recorda que aquesta és l'unica sol-lució, primer windows, i després els. SO que vulguis, i recorda que els discos dels PC's només poden suportar quatre particions, que quan instal-las qualsevol SO pots definir l'espai que ocuparan en el disc, i que degut a la "física"  dels discos i dels PC, no dels Mac, en igualtat de condicions el MBR que preval es el del Windows, i que si instal-les un SO que requereix, com cal, un sistema d'arranc, avans de windows, cagada pastorets. Ës el que hi ha, i no hi ha cap més sol-lució al teu problema.

salutacions...i fes-me cas, formatea el disc dur, instal-les,  windows, o directament Ubuntu, però si ho fas així ja no podràs instal-lar windows, si vols tenir els dos SO al mateix temps, recorda primer windows, desprès.....el que vulguis.....

---

### Post by prostata on 2007-06-13
alpicat, com pots veure he comes un error, No és la segona opció (B) sino la primera (A) la que et crea el problema, disculpes...


A) Vas instal-lar Windows sobre Ubuntu?
B) Vas instal-lar Ubuntu sobre windows?

si la opció va ser la segona, és a dir instal-lació de Windows a sobre d'Ubuntu,*** [aquí deuria dir la primera]***

---

### Post by alpicat on 2007-06-14
gracies per les respostes, el problema és que m'explico malament. A veure, la cosa està en que al intentar posar ubuntu sobre windows (primer windows) em surten errors i no es carrega el live CD. 
Abans de fer això havia ficat ubuntu (sobre l'ubuntu anterior que tenia) i es va instal·lar sense problemes. Però aquesta primera instal·lació no em serveix, perquè necessito tenir els dos ara, i per això vaig carregar-me l'instalació d'ubuntu sol i vaig començar de nou, primer windows, i despres ubuntu a sobre, però res. Total, que si tinc un windows previ no m'engega el live cd, surten una sèrie d'errors i es penja. He pensat que igual no li mola que el disc dur sigui NTSC, però no tindria perquè.
Bé, espero haver estat més clar ara, i perdó per ser tant pesadet.

---

### Post by prostata on 2007-06-14
> **alpicat said:**
> gracies per les respostes, el problema és que m'explico malament. A veure, la cosa està en que al intentar posar ubuntu sobre windows (primer windows) em surten errors i no es carrega el live CD. 

***quin tipus de erros, què diuen, donan's info, perquè erros aixì en general és molt genèric....***

Abans de fer això havia ficat ubuntu (sobre l'ubuntu anterior que tenia) i es va instal·lar sense problemes. Però aquesta primera instal·lació no em serveix, perquè necessito tenir els dos ara, ** què vol dir els dos, els dos què, dos ubuntus, dos windows, windows i ubuntu????**
i per això vaig carregar-me l'instalació d'ubuntu sol i vaig començar de nou, primer windows, i despres ubuntu a sobre, però res. Total, que si tinc un windows previ no m'engega el live cd, surten una sèrie d'errors i es penja. He pensat que igual no li mola que el disc dur sigui NTSC,** un disc dur NTSC, que jo sàpigue NTSC es un format d'matge, mira't aixó [http://es.wikipedia.org/wiki/NTSC](http://es.wikipedia.org/wiki/NTSC)** però no tindria perquè.
Bé, espero haver estat més clar ara, i perdó per ser tant pesadet.no ets pesadet, pot ser poc clar, que es molt diferent, fes el favor de descriure lo més acurat possible els erros que et surten, descriu el teu equip amb precissió, i ja veurem que es pot fer....salutacions

---

