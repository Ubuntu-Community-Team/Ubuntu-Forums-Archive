---
title: "Drivers per a  CanoScan 5600F"
date: 2012-02-07
forum: Catalan Team
---

### Post by prostata on 2012-02-07
He comprat aquest Scàner per digitalitzar diapos i negatius i només porta drivers per a Windows, per variar, i vull fer-lo anar am Ubuntu....he mirat per Google però de moment res de res...algú coneix una sol-lució per fer-lo anar amb Ubuntu Maverick?? 64 bits..

Gràcies

---

### Post by Linux Dutchman on 2012-02-07
Check here on how to install Canon drivers: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers)

---

### Post by prostata on 2012-02-07
> **Linux Dutchman said:**
> Check here on how to install Canon drivers: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers)


aquesta pàgina no em serveis de res, ja la conec i només hi han drivers per a windows, Mac, o sigui que...

Salut

---

### Post by Linux Dutchman on 2012-02-07
> **prostata said:**
> aquesta pàgina no em serveis de res, ja la conec i només hi han drivers per a windows, Mac, o sigui que...

Salut

??? English please.

---

### Post by wgarcia on 2012-02-08
@Linux Dutchman, you  are posting in the Catalan forum so it is natural that people use Catalan here, please use Gooogle translator if you want to intervene.

---

### Post by Linux Dutchman on 2012-02-08
> **wgarcia said:**
> @Linux Dutchman, you  are posting in the Catalan forum so it is natural that people use Catalan here, please use Gooogle translator if you want to intervene.

No offence, but Google Translator is not the most best translator!

---

### Post by eselma on 2012-02-11
@ Linux Dutchman: Thanks for your help. OP said that the page you pointed is useless, as there are only MS & Mac drivers. I agree, Google translator sometimes is a mess.

@ prostata: He visitat la pàgina que Linux Dutchman recomanava i he vist que hi ha recomanacions per a controladors Canon, tot i que potser algun sigui "CUPS-wrapper". Diu això (traducció lliure meva):

```
També es pot instal·lar un controlador Canon tot usant un dipòsit
PPA amb Ubuntu el que permetrà als usuaris trobar el controlador 
adequat per a la seva *impressora* Canon.  
Cal executar això:

    Obriu un terminal
    Marqueu la següent ordre: sudo add-apt-repository ppa:michael-gruz/canon
    Llavors actualitzeu els dipòsits: sudo apt-get update

Per a instal·lar el controlador Canon adient cal saber per a quina
*impressora* es necessita. Per exemple: Si la impressora és una
Canon Pixma iP100, llavors cal instal·lar aquest controlador: 
cnijfilter-ip100series. Per a trobar la llista de controladors,
vegeu la llista adjunta [COLOR="Navy"]Canon printer driver list.txt[/COLOR]. 
Per a instal·lar el controlador adequat:

    Obriu un terminal
    Marqueu l'ordre següent: sudo apt-get install {...} 
    (on {...} vol dir el nom del controlador adequat, segons la llista)

    Si cal, torneu a engegar l'ordinador
```
Tot i que aquí parla d'impressores, potser també hi ha controladors per a escàners. Tinc una multifunció Canon i he trobat al seu lloc web els controladors adequats per a SANE (escàner), que em funciona perfectament.

Actualment uso Debian *Squeeze* i no tinc *ubuntu, però els controladors han de ser els mateixos per a SANE. Si no hi és possible trobar els controladors de Canon, potser et funcionin bé els de *VueScan*, que són propietaris (de pagament) però de qualitat professional.

---

### Post by prostata on 2012-02-11
> **eselma said:**
> @ Linux Dutchman: Thanks for your help. OP said that the page you pointed is useless, as there are only MS & Mac drivers. I agree, Google translator sometimes is a mess.

@ prostata: He visitat la pàgina que Linux Dutchman recomanava i he vist que hi ha recomanacions per a controladors Canon, tot i que potser algun sigui "CUPS-wrapper". Diu això (traducció lliure meva):

```
També es pot instal·lar un controlador Canon tot usant un dipòsit
PPA amb Ubuntu el que permetrà als usuaris trobar el controlador 
adequat per a la seva *impressora* Canon.  
Cal executar això:

    Obriu un terminal
    Marqueu la següent ordre: sudo add-apt-repository ppa:michael-gruz/canon
    Llavors actualitzeu els dipòsits: sudo apt-get update

Per a instal·lar el controlador Canon adient cal saber per a quina
*impressora* es necessita. Per exemple: Si la impressora és una
Canon Pixma iP100, llavors cal instal·lar aquest controlador: 
cnijfilter-ip100series. Per a trobar la llista de controladors,
vegeu la llista adjunta [COLOR="Navy"]Canon printer driver list.txt[/COLOR]. 
Per a instal·lar el controlador adequat:

    Obriu un terminal
    Marqueu l'ordre següent: sudo apt-get install {...} 
    (on {...} vol dir el nom del controlador adequat, segons la llista)

    Si cal, torneu a engegar l'ordinador
```
Tot i que aquí parla d'impressores, potser també hi ha controladors per a escàners. Tinc una multifunció Canon i he trobat al seu lloc web els controladors adequats per a SANE (escàner), que em funciona perfectament.

Actualment uso Debian *Squeeze* i no tinc *ubuntu, però els controladors han de ser els mateixos per a SANE. Si no hi és possible trobar els controladors de Canon, potser et funcionin bé els de *VueScan*, que són propietaris (de pagament) però de qualitat professional.


si, això ja ho vaig veure, i va ser el fet que parlessin d'impressores el que em va tirar darrera, de totes ho tornaré a intentar, però...el que he vist a la pàgina tot es per windows i mac provaré SANE.

Salut

---

