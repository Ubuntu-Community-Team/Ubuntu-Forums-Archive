---
title: "Problema instal·lació canon MG3550"
date: 2014-08-25
forum: Catalan Team
---

### Post by pserra on 2014-08-25
Hola,
ja em dono compte que aquesta marca no és la millor per instal·lar-la amb ubuntu...he mirat força informació d'altres models hi donen forces problemes..
porto un parell estones cercant informació i fent proves però no me'n surto...
A veure si algun expert em pot ajudar.
El meu cas és que he baixat el arxiu .deb del fabricant: [http://www.canon.nl/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3550.aspx?type=download&softwaredetailid=tcm:16-1096181&os=&language=]("http://www.canon.nl/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3550.aspx?type=download&softwaredetailid=tcm:16-1096181&os=&language=")


i des de el terminal al intentar-lo instal·lar em surt:

pere@pere-aspireoneAO751h ~/Baixades $ sudo dpkg --install cnijfilter-mg3500series-4.00-1-deb
dpkg-split: error: s'ha produït un error al llegir cnijfilter-mg3500series-4.00-1-deb: Is a directory
dpkg: error processing cnijfilter-mg3500series-4.00-1-deb (--install):
 el subprocés dpkg-split retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 cnijfilter-mg3500series-4.00-1-deb





Gràcies per avançat.

---

### Post by pdc on 2014-08-27
this is an english language forum;

aquest és un fòrum Anglès

so you want to install the driver for the MG3500 series device;

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100550402.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550402.html) and click to download and SAVE the file, which is [COLOR="#008000"]cnijfilter-mg3500series-4.00-1-deb.tar.gz
[/COLOR]
open a terminal and copy and paste each command below; line by line; and hit the ENTER key after each paste

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg3500series-4.00-1-deb.tar.gz
cd cnijfilter-mg3500series-4.00-1-deb
./install.sh[/COLOR]

__________________________________

that will get the printer driver installed; '

Canon provide **[COLOR="#0000FF"]ScanGearMP[/COLOR]** if you want to use it for scanning; get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html?r=s&q=)

and install in the format listed above; 

run it with the command > [COLOR="#FF0000"]scangearmp[/COLOR]

els millors desitjos

---

### Post by pserra on 2014-08-27
Gràcies pdc,
aquest arxiu ja l'havia provat i em vaig rendir... no entenc perquè em genera errors.. m'explico:

faig el que em dius:(verifico que el tinc descàrregat)


pere@pere-aspireoneAO751h ~/Baixades $ ls -l
total 4
drwxrwxr-x 4 pere pere 4096 ago 22 23:52 cnijfilter-mg3500series-4.00-1-deb

i executo la primera comanda:

pere@pere-aspireoneAO751h ~/Baixades $ tar -zxvf cnijfilter-mg3500series-4.00-1-deb.tar.gz
tar (child): cnijfilter-mg3500series-4.00-1-deb.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

No entenc que em passa...
com ho puc solventar? merci.

---

### Post by pdc on 2014-08-27
in Catalan

> necessita utilitzar Google Translate; 

Vaig donar instruccions al meu segon lloc; treballen; 

si us plau, seguiu exactament; Vaig a utilitzar traductor Google per convertir això en català, que Google em diu que és el seu idioma

in English > you need to use Google translate; 

I gave instructions in my second post; they work; 

please follow them exactly; I will use Google translate to convert this to Catalan, which Google tells me is your language

best wishes

els millors desitjos

---

### Post by wgarcia on 2014-08-28
El que et diu el pdc (gràcies) és que donis les següents instruccions, després d'obrir una terminal:

```
cd Baixades
cd cnijfilter-mg3500series-4.00-1-deb
./install.sh
```

El problema que tens és que "cnijfilter-mg3500series-4.00-1-deb" és un directori, no un fitxer deb (per això no funciona "sudo dpkg --install ..."), i sembla que el directori conté tot el necessari per instal·lar el controlador de la impressora (cosa que es fa amb la instrucció "./install.sh").

---

### Post by pdc on 2014-08-28
En el meu primer post els havia aconsellat que vagi al lloc web de Cànon Àsia; La seva descàrrega i el paquet, i seguiu les instruccions que li van donar per instal · lar des d'allà 

Crec que-té en comptes enganxat amb el paquet de Cànon Europa; no-té la seqüència de comandaments de instal · lació; 

així que per instal · lar, (Assumint que-tenir un sistema de 64 bits) em sembla les ordres són

Assumeixo que van descarregar anys-té l'alliberament del programari Cànon Anglès 

de manera que les ordres de reflectir que

> [COLOR="#FF0000"]cd Baixades/cnijfilter-mg3500series-4.00-1-deb/packages[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-common_4.00-1_amd64.deb[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-mg3500series_4.00-1_amd64.deb[/COLOR]

---

### Post by pserra on 2014-08-28
Merci  pdc  i  wgarcia per les clares explicacions i resolutiu ajut.
Era ben senzill... però  no  'entenia' prou be l'error...
JA FUNCIONA!!

---

### Post by pdc on 2014-08-28
Això és genial; Ben fet; gaudir 

pots editar el títol per dir el s'intitule resolen usant Eines a la part superior de la pàgina

---

