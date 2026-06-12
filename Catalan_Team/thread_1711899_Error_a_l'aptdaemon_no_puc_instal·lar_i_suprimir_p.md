---
title: "Error a l'aptdaemon: no puc instal·lar i suprimir programari"
date: 2011-03-21
forum: Catalan Team
---

### Post by dariusill on 2011-03-21
Hola a tots i totes,

Alguna cosa he fet que no puc insta·lar ni suprimir software. Em surt aquest error quan ho intento: 

[INDENT]**S'ha produit un error que no es pot gestionar**
[/INDENT][INDENT]Sembla que hi ha un error de programació en l'aptdaemon, l'aplicació que us permet instal·lar i suprimir programari, així com realitzar altres tasques relacionades amb la gestió de paquets. Hauríeu d'informar d'aquest error a [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) i tornar-ho a intentar.
[/INDENT]I aquests són els detalls de l'error:

[INDENT]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

[/INDENT]Algú em pot ajudar? estic molt perdut

Gràces

Dàrius ill

---

### Post by wgarcia on 2011-03-22
Sembla que és un error (ja reportat i en vies de solució) amb els programes que gestionen la instal·lació de programari. 

Per intentar arreglar-ho primer prova obrir una terminal (Aplicacions -> Terminal) i un cop oberta escriure

```
sudo apt-get update
```

i després prems la tecla "intro". Comenta el que surt un cop que facis això. Aquesta comanda actualitza la informació del sistema sobre els paquets que fan falta actualitzar. 

També pots provar les següents dues comandes addicionals:

```
sudo apt-get install -f
```

que arregla si pot algun paquet al que li falta alguna dependència i 

```
sudo dpkg --configure -a
```

que intenta arreglar paquets trencats.

---

### Post by dariusill on 2011-03-22
Merci per la resposta, 

De totes maneres encara no ho tinc sol·lucionat. Quan poso ...
sudo apt-get update
Em surt una série de linies d'informacó i finalment això...**"S'està llegint la llista de paquets... Fet" **Després he **teclejat **a la terminal això...

darius@Acer-TravelMate-5335:~$ sudo apt-get install -f
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
S'instal·laran els següents paquets extres:
  ttf-mscorefonts-installer
S'actualitzaran els paquets següents:
  ttf-mscorefonts-installer
1 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.
1 no instal·lats o suprimits completament.
Es necessita obtenir 0B/40,3kB d'arxius.
Després d'aquesta operació s'empraran 221kB d'espai en disc addicional.
Voleu continuar [S/n]?

i li dic que si. **S**

Finlament es transforma la finestra de la terminal i em sut això amb un fons de color blau en comptes de negre

Configuració del paquet «ttf-mscorefonts-installer» &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474;                                  <D'acord>                                  
 &#9474;                                                          


Quan intento tancar el terminal em diu que encara s'ha de fer un procés en aquest terminal i que si la tanca mataria el procés. 

No tinc el problema sol·lucionat, però sha transformat en un altre.

Merci per l'atenció!

---

### Post by wgarcia on 2011-03-22
Sembla que tens mal instal·lat el paquet "ttf-mscorefonts-installer". Potser reinstal·lant-lo s'arregli, des de'una terminal pots provar:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

I si no funciona, desintal·lar-lo i tornar-lo a instal·lar amb:

sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer

---

### Post by dariusill on 2011-03-22
Hola Wgarcia i companyia,


[LIST]
[*]Continua sense funcionar , això és el que passa quan intento:
[/LIST]

sudo apt-get install --reinstall ttf-mscorefonts-installer

[I]darius@Acer-TravelMate-5335:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for darius: 
E: S'ha interromput el dpkg, harieu d'executar manualment 'sudo dpkg --configure -a' per a corregir el problema.
darius@Acer-TravelMate-5335:~$ sudo dpkg --configure -a
darius@Acer-TravelMate-5335:~$ sudo dpkg --configure -a
darius@Acer-TravelMate-5335:~$ [/I]

Com es veu intento posar el sudo dpkg configure a però no funciona.


[LIST]
[*]He intentat aquests comendaments però tampoc funcionen.
[/LIST]

**sudo apt-get remove ttf-mscorefonts-installe**r ----> RESUTAT: 

S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Es SUPRIMIRAN els paquets següents:
  ttf-mscorefonts-installer
0 actualitzats, 0 nous a instal·lar, 1 a suprimir i 0 no actualitzats.
1 no instal·lats o suprimits completament.
Després d'aquesta operació s'empraran 0B d'espai en disc addicional.
Voleu continuar [S/n]? s
dpkg: s'ha produït un error en processar ttf-mscorefonts-installer (--remove):
 El paquet està en un estat molt dolent e inconsistent - el tindreu que
 reinstal·lar abans d'intentar desinstal·lar-lo.
S'han trobat errors en processar:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


** sudo apt-get install ttf-mscorefonts-installer 	**---> RESULTAT: Tipica pantalla amb el fons blau cel:

Configuració del paquet

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuració del paquet «ttf-mscorefonts-installer» &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474;                                  <D'acord>                                  
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               

Intento tancar la terminal blau cel on posa configuració del paquet  passada una bona estona i em diu això....

[I]Voleu tancar aquest terminal?

Encara s'està executant un procés en aquest terminal. Si el tanqueu es matarà aquest procés.

[/I]Quin suplici....

Gràcies per l'ajuda (altre vegada)

---

### Post by wgarcia on 2011-03-22
Una pregunta ximple: Quan estàs a la finestra blava, uses el tabulador perquè el D'acord es posi vermell i prems INTRO?

---

### Post by dariusill on 2011-03-22
wgarcia,


Resposta ximple per una pregunta que no ho era... "Uppppsssss...error de principiant"

He clicat el tabulador, s'ha posat vermell i he apretat l'intro .---> RESULTAT: 

FUNCIONA!!! Ja puc instalar i desinstalar programes!!! GRACIES!

---

