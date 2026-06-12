---
title: "Insta&#320;lar l'amsn 0.97 SVN + tcl/tk 8.5 + tcltls"
date: 2007-08-26
forum: Catalan Team
---

### Post by patrickfromspain on 2007-08-26
Hola gent!

Avui m'agafeu amb ganes de treballar i fare un petitu tutorial per a insta&#320;lar l'amsn 0.97 (versio no estable) amb el tcl/tk 8.5 (versions pre-beta) i solucionar 4 problemes que hi ha.

Perque ho volem aixo? Perque l'amsn dels repositoris es LLEIG i no ens fiem de repositoris no oficials (:)).

El primer que hem de fer es descarregar les dependencies per compilar l'amsn:

en un terminal:
sudo apt-get install build-essential imagemagick libjpeg62-dev libpng12-dev g++ libxft-dev tcltls

a continuacio, baixe'm les fonts del programari que necessitem:
amsn: [http://amsn.sourceforge.net/amsn_dev.tar.gz](http://amsn.sourceforge.net/amsn_dev.tar.gz)
tcl 8.5: [http://prdownloads.sourceforge.net/tcl/tcl8.5.0-src.tar.gz](http://prdownloads.sourceforge.net/tcl/tcl8.5.0-src.tar.gz)
tk 8.5: [http://prdownloads.sourceforge.net/tcl/tk8.5.0-src.tar.gz](http://prdownloads.sourceforge.net/tcl/tk8.5.0-src.tar.gz)

Per facilitat a l'hora de treballar, descomprimiu tot a l'escriptori. Comencem, en un terminal:

cd ~/Desktop/tcl8.5.0/unix
./configure --prefix=/usr/local
make
sudo make install

cd ~/Desktop/tk8.5.0/unix
./configure --prefix=/usr/local --enable-xft
make
sudo make install

cd ~/Desktop/msn
./configure --prefix=/usr/local --with-tcl=/usr/local/lib --with-tk=/usr/local/lib
make
sudo make install
gksudo gedit /usr/local/share/amsn/amsn i allà, al principi veureu que hi posa wish, ho heu de canviar per wish8.5. Guardeu i tanqueu.


Ara ja tenim l'amsn al menu. Sota Aplicacions -> Internet -> Amsn. Si no hi es, tanquem la sessió i tornar a entrar. L'obrim i:

Compte -> Preferencies -> Avançades i busquem Altres i alla i veurem TLS. Hi posem: /usr/lib/tls1.50 Desar i tancar. Ara ja hauriem de poder entrar al nostre compte. (Fer-ho nomès si no us entra i us demana el tls)

Consell: Compte -> Preferencies -> Aparença -> Canviar la font Seleccioneu Dejavu-Sans a 10.

En fin.. hem sembla que ja esta, no m'oblido res no? Ara ja es cosa vostra fer que quedi be buscant o fent una pell que us agradi.

Salut! i espero que us serveixi. :)

---

### Post by patrickfromspain on 2007-08-26
Us pot quedar aixi de bé (o de malament no? xD)

---

### Post by ChAoS.ct on 2007-08-28
Personalment faig servir el gaim però sempre es pot provar.

Només una cosa:

Déu meu quina quantitat de make install... :shock:

Jo et recomanaria que no embrutessis el sistema tant ja que després quan surten els paquets estables no es deixen instal·lar correctament...
Consell: instal·la el checkinstall, i enlloc de   *sudo make install *  fes   ***sudo checkinstall***  : això farà que tot el que t'instal·la estigui dins d'un **higiènic i asèptic paquet desinstal·lable** a traves del teu gestor de paquets preferit.:KS

---

### Post by patrickfromspain on 2007-08-28
Gracies pel consell. De totes formes el checkinstall hem sembla una xapuça i no m'agrada. Ja hi he tingut problemes de fitxers que vol sobreescriure i de conflictes.

De la manera que ho faig jo, insta&#320;lant a /usr/local no embruto res: els paquets d'ubuntu de tcl, tk i amsn estan tots a /usr. De fet, juraria que /usr/local esta pensat per a aquest tipus d'usos.

Salut

---

### Post by papapep on 2007-08-28
Correcte Patrick.

ChAoS.ct: Això que fa no és embrutar el sistema, sempre que es faci controlat, com en Patrick fa. Sempre saps on queden els fitxers.
Això, per sort, no és com aquell altre S.O. que posa, treu, fa i desfà sense que ningú sàpiga el què. 

Aquí, gairebé, tot està documentat i pamat.

---

### Post by ChAoS.ct on 2007-08-28
Sí, estic d'acord que el checkinstall no és el millor del món, però realment és segur posar les coses a /usr/local/ amb un make install? 

I una altra: per desinstalar i eliminar el programari, s'ha de fer sempre amb un make distclean?

Es que si és així segueixo pensant que és més còmode usar el checkinstall, que per altra banda es pot usar sense que t'instal·li res, k nomes et crei el .deb i aixi no tens problemes quan t'intenta sobreescriure fitxers no?

Ja sé que el procés de debianitzar (Ubuntitzar?) un programari és un concret però pot ser cansat si no estàs massa familiaritzat amb aquest programari.

---

### Post by papapep on 2007-08-28
ChAoS.ct (ostres, quins noms us poseu...per escriure'l correctament estic mitja hora...:-D), és que ÉS el lloc adient:

(Extret d'un meravellós ([http://recepteslinux.homelinux.org/wordpress/?p=3](http://recepteslinux.homelinux.org/wordpress/?p=3)) blog :-) )

> [B] /usr/local
[/B]
Aquí és on s’instal·la les aplicacions i fitxers que s’utilitzen a la màquina local. Si el teu ordinador s’utilitza en una xarxa, el directori /usr pot ser físicament a una altra màquina essent compartit per moltes màquines Linux en xarxa. En aquesta mena de xarxa, al directori /usr/local només conté coses que no es facin servir a moltes màquines sinó que son per a ser usats a la màquina local.

El més probable és que el teu ordinador no estigui en una xarxa d’aquesta mena, però això no significa que el directori /usr/local sigui inútil. Si trobes aplicacions interessants que no formin part oficialment de la teva distribució, el pots instal·lar a /usr/local. Per exemple, si la aplicació normalment hauria d’anar a /usr/bin però no és part de la teva distribució, el podries instal·lar a /usr/local/bin. Quan mantens els teus propis programes separats dels que inclou la distribució de Linux, evites confusió i queda perfectament delimitat el que et proporciona la distro del que instal·les tu per lliure.


És un tema generalment admés i acceptat (no em preguntis d'on ha sortit, perquè no ho sé). Tu pots ficar-ho on et plagui - això és obvi-, però si tinguèssis vàries màquines o si vàries persones haguèssin d'administrar la teva, evidentment caldria convencions per no tornar-vos bojos, i la ubicació d'aplicacions "no estàndar" de la teva distro és a /usr/local.

---

### Post by nickpage on 2007-10-21
Hola,

estic probant d'instal·lar el amsn seguint aquestes instruccions, pero quan executo al terminal la instrucció:

./configure --prefix=/usr/local --with-tcl=/usr/local/lib --with-tk=/usr/local/lib

tinc el següent error:

> checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/local/lib
checking tk build dir... using tk library in /usr/local/lib
./configure: line 3042: /usr/local/lib/tkConfig.sh: No such file or directory


Teniu alguna idea de que pot passar, el sistema es un Gutsy recient instal·lat.

---

### Post by papapep on 2007-10-21
Tens alguna raó especial per a instal·lar l'Amsn compilant-lo en vers de fer servir el paquet oficial del repositori? Ho dic perquè, si ets novell, només és complicar-se la vida.

---

### Post by patrickfromspain on 2007-10-21
papapep, l'amsn dels repos es lletgissim, ja que tk8.4 no soporta antialiasing..

Sobre l'error.. ni idea :S

Has seguit tot pas per pas? Jo ho revisaria tot y ho repetiria, per si acas.

---

### Post by pespin on 2007-10-21
Jo amb lo vago que sóc opto per utilitzar el amsn dels repos del treviño. He posat els del fesity al gutsy acabat d'instal·lar i funciona de perles :)

---

