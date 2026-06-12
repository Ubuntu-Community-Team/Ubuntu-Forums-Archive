---
title: "Amule i xarxa KAD"
date: 2007-09-24
forum: Catalan Team
---

### Post by muleta on 2007-09-24
Després d'alguns dies de funcionament força correcte, tot i que descaregava amb lentitud, aquesta nit, l'amule s'ha aturat i m'ha apagat l'ordinador.

Quan l'he tornat a engegar, no aconsegueixo connectar la xarxa KAD.

Perque em funcionés, vaig haver de reinstal·lar l'amule diverses vegades. No hi ha configuració de firewall que valgui, ni canvis de ports ni introducció de nodes. Es veu que és aleatori.

Si ja em baixaven els fitxers lents, ara, sense el KAD, sembla que caminin enrera.

Hauré de tornar a reinstal·lar-lo algunes vegades fins que, per casualitat, torni a connectar-se... o algú sap si depèn d'algun factor control·lable?.

---

### Post by pespin on 2007-09-24
Pel que he sentit ultimament han tancat diversos servidors importants  de la xarxa que utilitza l'amule; potser això i té alguna cosa a veure

---

### Post by muleta on 2007-09-24
Han tancat, precisament, els eDonkey. En aquell moment em va començar a funcionar el KAD.

---

### Post by cortsenc on 2007-09-24
A mi ja fa uns dies que no em funciona la xarxa KAD, i he provat de baixar la llista de servidors de diferents llocs i no hi ha forma de que arrenqui. La xarxa ED2K en canvi, em funciona millor que abans.

---

### Post by muleta on 2007-09-24
> **cortsenc said:**
>  La xarxa ED2K en canvi, em funciona millor que abans.

Perque se't connecta a Razorback, que torna a funcionar. Si revises la llista de Servidors, veuràs que edonkey 1, 2, 3, 4, 5... han desaparegut.

---

### Post by orestesmas on 2007-09-25
> **muleta said:**
> 
Perque em funcionés, vaig haver de reinstal·lar l'amule diverses vegades. No hi ha configuració de firewall que valgui, ni canvis de ports ni introducció de nodes. Es veu que és aleatori.


No és aquesta la meva (limitada) experiència. Si obres els ports del router correctament, obtens una ID alta i baixen tant ràpid com te'ls dónen. Això ho he comprovat en 4 instal·lacions diferents a 4 cases diferents, amb resultats repetibles.

---

### Post by muleta on 2007-09-28
Enhorabona, Orestesmas!. Però això de "repetibles" ho deixaria en suspens.

Ahir, després de molts díes, vaig veure la xarxa Kad ok, sense fer res ni canviar res, com ha passat altres vegades, poc abans de tancar-se l'amule espontàneament.

Com esperava, avui s'ha tancat sol i m'ha costat tornar-lo a engegar perque es tornava a apagar.

Ara porta funcionant unes 3 hores però sense Kad. Em diu que està firewallada.

No espero pas que ningú s'escarrassi a suggerir-me solucions. Sé que és un tema irresoluble. Us ho comento perque en tingueu coneixement i perque serveixi e consol a altres que també s'hi trobin.

---

### Post by lluisanunez on 2007-09-30
Si no vols les solucions no les facis servir, però si vens aquí a dir que un tema és irresoluble, quan resulta que és un tema amb solució (la que diu l'Orestesmas), t'haurem de contestar, justament per a consol d'altres que s'hi trobin ;)

---

### Post by muleta on 2007-09-30
L'Orestesmas no em dona cap sol·lució sino que em respon que a ell sí que li funciona després d'obrir els ports.

Sé que hi ha altres usuaris que també ho han lograt. Si no fos així, ja no existiria el programa.

Quan, després d'obrir els ports en el router, instal·lar Firestarter per assegurar-me d'obrir els ports en el PC i seguir les instruccions al peu de la lletra per a cada port, no em va i ho explico en aquest forum i en molts d'altres més especialitzats però ningú no em dona una solució, no em sembla molt reconfortant que em diguin: "doncs a mi sí". Només me'n puc alegrar, però això no em resol el problema.

No crec que sigui dolent admetre que algunes aplicacions no són del tot estables a Ubuntu ni penso que sigui bó amagar la realitat. 

Crec que els novells necessitem encoratjament i saber que no sempre és culpa nostra que l'Ubuntu no ens respongui satisfactòriament, quan seguim les instruccions donades.

---

### Post by orestesmas on 2007-09-30
Hola, sóc aquell-que-no-dóna-solucions :-)

Sé per experiència la frustració que es pot arribar a sentir quan hom té un problema que no té ningú més. Com pots suposar, són els més complicats de resoldre perquè si els altres no podem reproduir el problema, no tenim ni idea de què pot estar fallant.

Per tant, estem davant d'un problema que només tens tu, i que per lògica ha de tenir l'origen en la teva configuració particular de maquinari i programari. Davant d'això, jo només et puc donar consells genèrics, que encara es compliquen més perquè assumeixo que tu fas servir Gnome, i jo tinc KDE.

Però ho podem intentar. La major part de les vegades donarem pals de cec, però alguna podem encertar entre tots.

La primera cosa que podem atacar és això de que l'ordinador "s'apagui". En un sistema GNU/Linux és moooolt difícil que un ordinador s'apagui "perquè sí". Només pot passar en alguna d'aquestes situacions:

[LIST=1]
[*] Un usuari amb permisos suficients li diu conscientment que s'apagui. No és el cas, oi?

[*] Una errada en el nucli o en un dels mòduls que carrega (pel cas és el mateix). Tampoc no és el cas perquè l'aMule és un programa que corre en espai d'usuari i no afecta al nucli per a res. I si fos així, molts usuaris estarien igual que tu, perquè tots els nuclis que venen de sèrie amb l'ubuntu són iguals, i molts usuaris tindran un maquinari igual que el teu.

[*] Una errada aleatòria en el maquinari, que penja la màquina.
[/LIST]

Jo personalment m'inclino pel punt 3, concretament per un problema relacionat amb l'escalfament excessiu del maquinari, especialment si apareix quan porta hores funcionant. Sigui com sigui, per mirar de diagnosticar la causa del problema és útil donar una ullada als fitxers de bitàcola del sistema (els LOGs, per entendre'ns). Potser diuen quelcom interessant.

Concretament els fitxers a mirar són /var/log/syslog, /var/log/kern.log  /var/log/messages i /var/log/debug (alguns d'aquests tenen info redundant, però és igual). També és útil la sortida de l'ordre "dmesg". Tot això, evidentment, des d'un terminal.

Tots aquests fitxers estan formats per una sèrie de línies que comencen amb una data. Mira de penjar al fòrum els fragments d'aquests fitxers corresponents al dia que hagis sofert una aturada sobtada. Si no apareix el dia, tingues en compte que el sistema es va guardant uns quants fitxers de log de dates anteriors. Per exemple, el penúltim "syslog" es diu "syslog.0", i els anteriors estan comprimits i es diuen "syslog.1.gz", i així successivament.

---

### Post by patrickfromspain on 2007-09-30
jo he treballat en una tenda de pc's i be, quan un pc s'apaga, es per culpa del hardware en el 99,9% dels casos. A vegades sobreescalfament i molts cops per una font d'alimentacio en mal estat. L'amule no hi te res a veure ;)

Sobre la xarxa cad.. no t'hi matis. Jo la tinc quasi sempre en off o bloquejada pel firewall i l'amule hem tira.. no m'amargo ni hi indago. Paso de perdre-hi temps

EDITO: si tens ID Alta, no et preocupis per res mes. Si no la tens, comença a buscar on tens la fallada: router o firestarter, de l'amule no sera. Per cert, canvia el port que et ve per defecte i posa 30000 i 30010, per exemple, i obre aquests dos port al ruter. Ho dic perque he sentit que el 4762 y el 4772 (suposant que son els de l'amule per defecte) venen capats des del proveidor d'internet.

salut!

---

### Post by albert-I on 2007-10-01
Amb persones pel mig, no hi ha mai res segur. ;)

L'amule, el que tenim tots, el 2.1.3 té un problema no resolt i em sembla recordar,que no se sap el pq. Peró es que no es porta gairebé amb el 7.04. i s'apaga sol, ara d'aquí a tancar l'equip. :confused:

Jo solc tenir el Kad en off i tot i això, be em baixa.

Conec de primera ma :), el cas de mes d'una i cinc dones que al tindre la torre al costat i a terra i anant amb sabates de puntera. Els reinicien al tocar el boto. :D :D :D
> **patrickfromspain said:**
> jo he treballat en una tenda de pc's i be, quan un pc s'apaga, es per culpa del hardware en el 99,9% dels casos. A vegades sobreescalfament i molts cops per una font d'alimentacio en mal estat. L'amule no hi te res a veure ;)

Sobre la xarxa cad.. no t'hi matis. Jo la tinc quasi sempre en off o bloquejada pel firewall i l'amule hem tira.. no m'amargo ni hi indago. Paso de perdre-hi temps

EDITO: si tens ID Alta, no et preocupis per res mes. Si no la tens, comença a buscar on tens la fallada: router o firestarter, de l'amule no sera. Per cert, canvia el port que et ve per defecte i posa 30000 i 30010, per exemple, i obre aquests dos port al ruter. Ho dic perque he sentit que el 4762 y el 4772 (suposant que son els de l'amule per defecte) venen capats des del proveidor d'internet.

salut!

---

