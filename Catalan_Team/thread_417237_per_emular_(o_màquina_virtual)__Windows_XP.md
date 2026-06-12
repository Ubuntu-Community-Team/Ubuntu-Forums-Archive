---
title: "per emular (o màquina virtual)  Windows XP"
date: 2007-04-21
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-04-21
Bones, voldria emular o tenir a través d'una màquina virtual l'XP. No sé si és el mateix una cosa que l'altra.

Vaja, que obri l'Ubuntu, i llavors des d'allà, "com si fos un programa" podés obrir l'XP i fer anar les quatre coses que encara no puc fer amb Linux.

Llavors quin em recomaneu?

I el tema de particions i compatibilitat de quan estigui a l'XP per llegir i escriure als discs durs,etc... què?

Gràcies per endavant!

---

### Post by CarlesOriol on 2007-04-21
el vmware va molt bé però no és  lliure.

---

### Post by maleses on 2007-04-21
Jo utilitzo el virtual box i funciona perfecte, el pots instal·lar des de el automatix mateix. [Aqui ]("http://www.kriptopolis.org/virtualbox-ii-windows-fundamentals-bajo-linux")trobaras un tutorial que t'explica mes o menys com fer-lo anar.

---

### Post by orestesmas on 2007-04-22
Com t'han dit, tens un ampli ventall: vmware, virtual box, qemu... per comunicar-te entre windows i ubuntu jo et suggereixo que ho facis via xarxa

---

### Post by bikerbaixcamp on 2007-04-22
Doncs de moment he anat mirant per damunt, i veig que es difícil d'instal·lar, i després que vagi...

No ho sé,... a veure...

---

### Post by eselma on 2007-04-23
Hi ha diverses maneres de fer funcionar programes *.exe (si és que *realment* els necessites) sobre GNU/Linux:

**Amb una utilitat (no un emulador) com Wine:** 

Avantatges: És lliure. Els fitxers usen l'espai normal del teu disc. Bona connexió a perifèrics. No necessites res de Microsoft. No és necessari cap mòdul per al kernel.
Punts febles: No tots els programes funcionen, especialment els jocs.

**Amb un derivat comercial de Wine, com CrossOffice:**
Avantatges: Funcionen més programes, especialment els d'empresa. Jo he fet funcionar perfectament programes especials no llistats en la seva base de dades de compatibilitat. tampoc necessites cap llicència de Microsoft.No usa mòduls de kernel. Suport comercial.
Punts febles: És comercial; tot i que econòmic, no és lliure. Tanmateix, dóna suport al desenvolupament de Wine, i la comunitat se'n beneficia.

**Amb un derivat comercial de Wine, com Cedega:**
Avantatges: Diuen que molts jocs per Windows hi funcionen prou bé. Com que no uso jocs, ni tan sols el Penguin Racer, no t'ho puc confirmar.
Punts febles: És comercial, no lliure i a més no col·labora amb Wine ni afavoreix en res la comunitat.

**Amb un emulador com QEMU:**
Avantatges: Pots crear una màquina virtual tipus intel dins del teu Linux. Funcionen més coses que sobre Wine. És lliure, ara també incloent-hi l'accelerador KQEMU.
Punts febles: L'execució de codi és una mica més lenta, i sense l'accelerador molt més lenta. A vegades pot resultar més difícil de configurar. Naturalment, necessites una llicència de Windows i un CD arrencable.

**Amb un emulador propietari com Win4Lin:**
Avantatges: Crea màquines virtuals Windows dins del teu entorn. Abans anava molt ràpid, però necessitava un pedaç de kernel i només anava amb Win95-98, no amb 2000 ni XP. Ara usa una variació de QEMU, però també té alguna mancança. A canvi, funciona bé amb Win 2000 i XP (preferible usar Win 2000, especialment si no tens una màquina molt ràpida). Bona comunicació amb els perifèrics i fitxers. Usa el sistema de fitxers ext3. Bon suport comercial.
Punts febles: És comercial i no lliure. També necessites una llicència de Windows i un CD d'arrencada. Encara presenta algunes pegues.

**Amb un emulador com VirtualBox:**
Avantatges: És gratuït, i hi ha una versió lliure (amb menys prestacions). Darrerament han alliberat el codi. _Instal·lació senzillíssima_. És prou ràpid. No cal apedaçar el kernel. Bona comunicació amb els fitxers i bastants perifèrics. Tan ràpid o més que VMware, i més lleuger.
Punts febles: Encara conserva una part de codi propietari. Com els anteriors, necessita llicència Windows i CD arrencable. A partir de la versió 1.5.2 reconeix perfectament els ports sèrie.

**Amb una màquina virtual VMWare:**
Avantatges: Ara és gratuït, tant el motor VMPlayer (disponible als repositoris de *ubuntu) com el servidor (VMServer) i la utilitat que permet "transplantar" una instal·lació Windows a una màquina virtual. Experiència i solidesa provada. Ara és molt més ràpid que abans. També té bona comunicació amb els ports sèrie. Comunicació mitjançant la xarxa (més segura).
Punts febles: Que ara sigui gratuït no vol dir que sigui lliure. El VMware server és voluminós. La instal·lació és prolixa, però si segueixes un dels molts tutorials que hi ha a la xarxa, és bufar i fer ampolles. Comunicació mitjançant la xarxa (més lenta). Per descomptat, cal llicència i CD d'arrencada.

**Amb una màquina virtual Parallels:**
Avantatges: Instal·lació senzilla. Bona comunicació amb perifèrics, inclòs el port sèrie. Compacte. Semblant (fins i tot massa) al VMware. Versions per a Mac. 
Punts febles: No és lliure. Té un cost (reduït) econòmic. De moment no dóna suport a les tecles amb accents (à, è, ü...), la qual cosa l'inhabilita per la major part de propòsits. Com els anteriors, llicència i CD.

**Altres virtualisadors (Xen, Bochs, etc.):**

Hi ha encara moltíssimes possibilitats de fer funcionar programari MS-Windows sobre una màquina amb GNU/Linux. Algunes, com Xen, molt prometedores. Com que no les he provat, és millor que no comenti res. Per avui ja n'hi deu haver prou, no?

                 Espero haver-te ajudat. 


*P.S: Cada vegada hi ha més aplicacions lliures en GNU/Linux. Com veus, hi ha moltes possibilitats per usar programari per MS-Windows... però sovint no és necessari. Jo tinc un emulador per a fer funcionar UNA SOLA aplicació, i perquè no depèn de mi. Si tothom uses virtualitzadors, el programari lliure mai no seria autònom, i ara està a un pas de ser-ho. Val la pena pensar-s'ho dues vegades abans d'agafar el camí (sense sortida) de les aplicacions MS dins de GNU/Linux.*

---

### Post by boriffus on 2007-04-24
Aprofitant que parleu d' aquest tema, m' agradaria preguntar si algú de vosaltres ha fet servir algun d' aquests programes que comenteu per a carregar jocs windows des de l' ubuntu. Ho dic perquè els jocs de windows són l' únic que trobo a faltar de quan feia servir windows. 
Ja he vist que hi ha diverses possibilitats, però em pregunto si n' hi ha alguna millor que les altres a l' hora de poder carregar jocs amb alts requeriments en quant a efectes 3D i aquestes coses que tenen els jocs moderns.
Vaja, que si ho heu probat i quines conclusions n' heu extret.
Gràcies!

---

### Post by CarlesOriol on 2007-04-24
cedega... 

Et pot costar el mateix que un joc actual però et permet jugar amb els actuals i molts dels que ja tens.

Et recomano que visitis transgaming.com per tal d'informarte.

Tingues en compte però que no és software lliure i que tampoc no et funcionarà en màquines basades en 64 bits.

---

### Post by bikerbaixcamp on 2007-04-24
Moltes gràcies eselma!

El que també tinc el dubte que si estàs dins d'una màquina virtual llavors l'XP llegeix les particions ext3 o bé també ha d'haver una fat32 per poder ser llegida?

---

### Post by CarlesOriol on 2007-04-25
Tot i que dins d'una màquina virtual podries accedir físicament als discs del host (tinguin el format que tinguin) , això a la practica no és realitzable directament ja que l'accés concurrent al sistema d'arxius faria que aquest es trenques. Llavors hauries de desmuntar-lo del host cada cop que entressis en un client per tornar-lo a muntar allà.

El cedega que et comentava no és una màquina virtual.

En vmware que és el que conec simplement muntant una xarxa virtual entre el client i el host et permet una comunicació prou fluida d'arxius i compartint les carpetes del primer el seu us és força transparent.

D'aquest tema se n'ha parlat bastant fa uns dies a la llista de correu. Si vols mirar els logs pots fer-ho a : [https://lists.lafarga.cpl.upc.edu/pipermail/ubuntucat-info/](https://lists.lafarga.cpl.upc.edu/pipermail/ubuntucat-info/)

---

### Post by eselma on 2007-04-25
> **bikerbaixcamp said:**
>  El que també tinc el dubte que si estàs dins d'una màquina virtual llavors l'XP llegeix les particions ext3 o bé també ha d'haver una fat32 per poder ser llegida?

Ja t'ha contestat molt bé en Carles Oriol. 

Cal tenir en compte que una "màquina virtual" (VM), com el seu nom indica, és una "capsa" que emula un ordinador físic (amb el seu disc dur, memòria RAM, pantalla, tarja de xarxa...) DINS d'un altre (normalment l'ordinador real, tangible). De la interfície entre els dos se n'encarrega el programari de virtualització (VMWare, QEMU, Bochs). Tens un disc dur virtual amb el seu sector d'arrencada i sistema de fitxers -per exemple, VFAT de MS-Windows- encastat en un o més fitxers que poden ser d'un altre sistema: per exemple, ext3 de GNU/Linux. Així, si hi ha un problema a la màquina virtual, el pitjor que et podria passar és la corrupció del contingut d'aquest fitxer, sense que el teu sistema principal quedi afectat.

Pots usar aquest mètode per a provar, si tens prou espai de disc dur un S.O. o una distribució "dins" d'una altra: per exemple, Feisty dins d'Edgy, Mepis dins de Dapper, BSD dins de Fedora i també *ubuntu dins de MS-Windows...

Per tant, si vols treballar amb un fitxer dins de la màquina virtual, primer cal que l'importis a l'interior d'aquesta (pots tenir dos fitxers, l'original i la còpia dins de la VM). Un cop acabada l'edició, si vols pots tornar a exportar-lo a l'exterior i substituir l'original amb el que acabes d'editar.

Com t'ha dit l'Orestes abans, el més segur és fer-ho mitjançant una connexió interna de xarxa (virtual, es clar, no necessites cap cable).

Per cert, si vols instal·lar el VMware Server a una *ubuntu 7.04 (Feisty) cal fer, per ara, unes petites adaptacions.  Sobre Dapper i Edgy han funcionat les que esmentava abans. Quant a Cedega, no tinc temps per jugar i no et puc dir res.

És molt interessant tenir una màquina virtual MS-Windows dins del teu GNU/Linux per a exemple d'incrèduls i comprovar que cada vegada la fas servir menys. Jo, per ara, un cop cada any. 

*O.T.: L'altre dia vaig sentir dir: "Windows manxa, Linux enganxa". Et sona?*

---

### Post by lpargemi on 2007-11-10
Una avís per a navegants despistats (com jo mateix):

vmware des de linux no pot crear pc's virtuals. Per a crear-los s'ha de fer des de programes que només corren en entorn windows (encara que siguin simulats). 

O això és el què m'ha semblat entendre a mi, que un cop instal.lat no he estat capaç de crear cap ordinador virtual.

Salut

---

### Post by papapep on 2007-11-10
Si et refereixes a crear la màquina virtual, hi ha un esplèndid lloc web on ho pots fer i descarregar-te el fitxer al teu ordinador en 1 minut:

[www.easyvmx.com](www.easyvmx.com)

---

### Post by CarlesOriol on 2007-11-10
> **lpargemi said:**
> 
vmware des de linux no pot crear pc's virtuals. Per a crear-los s'ha de fer des de programes que només corren en entorn windows (encara que siguin simulats). 

Salut

Malgrat que la versió privativa si que ho permet et recomano el virtualbox  on ho pots fer en la versió lliure que hi ha als repositoris.

---

### Post by PellRoja on 2007-11-10
> **eselma said:**
> Hi ha diverses maneres de fer funcionar programes *.exe (si és que *realment* els necessites) sobre GNU/Linux:

**Amb una utilitat (no un emulador) com Wine:** 

Avantatges: És lliure. Els fitxers usen l'espai normal del teu disc. Bona connexió a perifèrics. No necessites res de Microsoft. No és necessari cap mòdul per al kernel.
Punts febles: No tots els programes funcionen, especialment els jocs.

**Amb un derivat comercial de Wine, com CrossOffice:**
Avantatges: Funcionen més programes, especialment els d'empresa. Jo he fet funcionar perfectament programes especials no llistats en la seva base de dades de compatibilitat. tampoc necessites cap llicència de Microsoft.No usa mòduls de kernel. Suport comercial.
Punts febles: És comercial; tot i que econòmic, no és lliure. tanmateix, dóna suport al desenvolupament de Wine, i la comunitat s'en beneficia.

**Amb un derivat comercial de Wine, com Cedega:**
Avantatges: Diuen que molts jocs per Windows hi funcionen prou bé. Com que no uso jocs, ni tan sols el Penguin Racer, no t'ho puc confirmar.
Punts febles: És comercial, no lliure i a més no col·labora amb Wine ni afavoreix en res la comunitat.

**Amb un emulador com QEMU:**
Avantatges: Pots crear una màquina virtual tipus intel dins del teu Linux. Funcionen més coses que sobre Wine. És lliure, ara incloent-hi l'accelerador KQEMU.
Punts febles: L'execució de codi és una mica més lenta, sense l'accelerador molt més lenta. A vegades pot resultar més difícil de configurar. Naturalment, necessites una llicència de Windows i un CD arrencable.

**Amb un emulador propietari com Win4Lin:**
Avantatges: Crea màquines virtuals Windows dins del teu entorn. Abans anava molt ràpid, però necessitava un pedaç de kernel i només anava amb Win95-98, no amb 2000 ni XP. Ara usa una variació de QEMU, però també té alguna mancança. A canvi, funciona bé amb Win 2000 i XP (preferible usar Win 2000, especialment si no tens una màquina molt ràpida). Bona comunicació amb els perifèrics i fitxers. Usa el sistema de fitxers ext3. Bon suport comercial.
Punts febles: És comercial i no lliure. També necessites una llicència de Windows i un CD d'arrencada. Encara presenta algunes pegues.

**Amb un emulador com VirtualBox:**
Avantatges: És gratuït, i hi ha una versió lliure (amb menys prestacions). darrerament han alliberat el codi. _Instal·lació senzillíssima_. És prou ràpid. No cal apedaçar el kernel. Bona comunicació amb els fitxers i bastants perifèrics.
Punts febles: Encara conserva una part de codi propietari. Com els anteriors, necessita llicència Windows i CD arrencable. No reconeix (de moment) els ports sèrie.

**Amb una màquina virtual VMWare:**
Avantatges: Ara és gratuït, tant el motor VMPlayer (disponible als repositoris de *ubuntu) com el servidor (VMServer) i la utilitat que permet "transplantar" una instal·lació Windows a una màquina virtual. Experiència i solidesa provada. Ara és molt més ràpid que abans. Bona comunicació amb els ports sèrie. Comunicació mitjançant la xarxa (més segura).
Punts febles: Que ara sigui gratuït no vol dir que sigui lliure. El VMware server és voluminós. La instal·lació és prolixa, però si segueixes un dels molts tutorials que hi ha a la xarxa, és bufar i fer ampolles. Comunicació mitjançant la xarxa (més lenta). Per descomptat, cal llicència i CD d'arrencada.

**Amb una màquina virtual Parallels:**
Avantatges: Instal·lació senzilla. Bona comunicació amb perifèrics, inclòs el port sèrie. Compacte. Semblant (fins i tot massa) al VMware. Versions per a Mac. 
Punts febles: No és lliure. Té un cost (reduït) econòmic. De moment no dóna suport a les tecles amb accents (à, è, ü...), la qual cosa l'inhabilita per la major part de propòsits. Com els anteriors, llicència i CD.

**Altres virtualisadors (Xen, Bochs, etc.):**

Hi ha encara moltíssimes possibilitats de fer funcionar programari MS-Windows sobre una màquina amb GNU/Linux. Algunes, com Xen, molt prometedores. Com que no les he provat, és millor que no comenti res. Per avui ja n'hi deu haver prou, no?

                 Espero haver-te ajudat. 


*P.S: Cada vegada hi ha més aplicacions lliures en GNU/Linux. Com veus, hi ha moltes possibilitats per usar programari per MS-Windows... però sovint no és necessari. Jo tinc un emulador per a fer funcionar UNA SOLA aplicació, i perquè no depèn de mi. Si tothom uses virtualisadors, el programari lliure mai no seria autònom, i ara està a un pas de ser-ho. val la pena pensar-s'ho dues vegades abans d'agafar el camí (sense sortida) de les aplicacions MS dins de GNU/Linux.*

Bon resum, si no et fa res, el poso en un article al meu bloc :P

---

### Post by jodufi on 2007-11-11
Molt bon resum de l'eselma

Jo tinc instal·lat el VirtualBox i és molt senzill d'utilitzar i d'instal·lar. A més, hi ha tres maneres molt fàcils d'instal·lar-lo, mitjançant l'"Afegeix/Elimina aplicacions", Automatix o baixant-lo de la pàgina web [www.virtualbox.org](www.virtualbox.org). Et recomano utilitzar  l'últim mètode.

Salut

---

### Post by oriolsbd on 2007-11-13
Jo no havia muntat mai cap màquina virtual, i fent una consulta a algú que havia utilitzat VMWare, Qemu i VirtualBox, em va recomanar aquest últim. La veritat és que l'he trobat molt senzill i, de moment, em va molt bé.

En quant a com veure els discos de la màquina "principal", VirtualBox ho soluciona considerant-les com a carpetes compartides. És a dir, tu primer indiques que, per a una màquina virtual concreta, el teu directori /home (per exemple) serà el recurs "sistema". Llavors, dins la màquina virtual, has d'anar a un interpret de comandes (MS-DOS) i escriure:

net use  x: \\vboxsvr\sistema

A partir d'aquest moment, a x: hi tindràs el /home del teu sistema principal. Ja he provat de modificar algun document compartit d'aquesta manera, i no he tingut cap problema.

Per poder utilitzar aquesta utilitat, has d'instal·lar en el sistema virtual les "VirtualBox Guest Additions". Això es fa de la següent manera: Un cop tens obert el sistema Windows en el VirtualBox, ves a l'opció de menú _del VirtualBox_ (no del Windows) "Dispositivos -> Instalar Guest Additions", i ja podràs fer el que he explicat abans.

---

