---
title: "Hola de nou, ubuntaries !!!"
date: 2009-09-28
forum: Catalan Team
---

### Post by lluisalguero on 2009-09-28
Hola nois,

primer que res demanar disculpes a tots els que vau donar-me solucions als meus problemes amb el meu anterior portàtil. Us ho agraeixo de tot cor, poca gent hi ha disposada a perdre el seu temps lliure ajudant als demés.

Al fil del meu anterior portàtil (escalfament de la CPU, problemes amb la 8.04, etc), ara mateix el tinc aquí al costat tot "destripat". Quan tingui una estona l'haig de tornar a muntar i veure si encara funciona.

Vaig estar un temps tirant d'un vell PC que tenia, fins que vaig acabar també fart, pel que al final m'he decidit per un portàtil nou amb aquestes característiques:

- HP Pavilion dv6-1250ss Entertainment Notebook PC
- Processador Intel® Core™ 2 Duo P7350 • 2 GHz, 3 MB de memòria cau de nivell 2 
- 4 GB RAM
- 500 Gb de disc dur SATA
- ATI Mobility Radeon HD 4530 amb 512 MB DDR3 de dedicació exclusiva

Què us sembla? Prou potent no?

Ara bé el "quid" de la qüestió...instal·lar Ubuntu. Pel que he pogut llegir, aquests portàtils que ja venen amb el Vista pre-instal·lat, donen bastant guerra si vols instal·lar un altre sistema operatiu. He llegit algun fil al respecte, però de portàtils d'altres marques.
La pregunta és: el procediment és si fa no fa el mateix per a tots? Quins problemes em puc trobar? He llegit un fil, on cada cop que volia entrar al Vista tenia que restaurar i per a entrar a l'Ubuntu es tenia que fer des de un live-CD.

Tant aviat com ho tingui mig clar, em ficaré fil a l'agulla. Si alguna anima caritativa, em vol donar un cop de mà i sap d'algun fil on s'explique la instal·lació en aquests tipus de portàtils, jo li estaré agraït. De totes formes, per la meva banda, aniré llegint fils existents.

Una salutació a tots i totes

:lolflag:

---

### Post by orestesmas on 2009-09-29
Penso que la instal·lació no et donarà cap problema. Una vegada instal·lat, pots tenir dificultats amb coses relacionades amb la gestió de l'energia (suspensió a la RAM, "resume", etc.). Jo tinc un pavilion dv7 i n'he tingut. No és el mateix model que el teu, però pels fòrums he vist que la gent té aquesta mena de problemes amb dv5, dv6 i dv7.

L'origen dels problemes es veu que està en unes BIOS amb alguns errors, que fa que no respectin els estàndards ACPI i que, per tant, el kernel Linux no sap com tractar. En windows el fabricant ho soluciona subministrant un controlador que de fet és un pegat per tal que el sistema pugui reconèixer i corregir aquest comportament defectuós de la BIOS, però rarament el fabricant dóna un controlador semblant per Linux.

A vegades hi ha disponibles al web de HP unes actualitzacions de la BIOS que, poc a poc, van arreglant aquests problemes. Malauradament jo m'he trobat que aquestes actualitzacions de la BIOS venen en forma d'uns programes executables només per windows (i, a sobre, només per windows vista; ni XP serveix). Aleshores si has d'esborrar completament el windows del teu sistema jo et recomanaria que, prèviament, l'utilitzis per actualitzar la BIOS del teu portàtil a la darrera versió.

A banda d'això, si el portàtil ha de contenir dades personals teves que consideris sensibles (sempre n'hi ha alguna o altra), jo et recomanano que xifris la totalitat del disc. Així si mai et roben el portàtil no podràn accedir a les teves dades.

Per xifrar-lo has d'usar la versió "alternate" del disc d'instal·lació, perquè em sembla que des del normal no es pot fer (corregiu-me si vaig errat). El procés de xifrat i desxifrat és transparent, l'única cosa és que en arrencar el sistema cada vegada et demanarà una contrasenya per desxifrar el disc i poder continuar el procés de "boot".

Apali, que vagi bé.

---

### Post by PatrickVogeli on 2009-09-29
ostia, una ATI. Ets valent oi? :D

---

### Post by jaume69 on 2009-09-29
Jo tinc un dv7-(NVIDIA gs9200)i quant vaig instal·lar **Ubuntu Jaunty**,em va anar força bé.
Només vaig tenir problema amb el só,però editant l´arxiu (ara no recordo exactament)..modprobe.d..,em va funcionar bé.

Ara no el tinc instal.lat,de moment..

Passa que,per tenir dos S.O.s i o varis portàtils,per mantenir-los actualitzats completament,costa una mica..,al menys a mi.
I per aixó prefereixo,de moment,tenir **Ubuntu** en un portàtil i **Windows** a l´altre.
Salut.

---

### Post by akyra on 2009-10-01
Jo tinc un Toshiba A500, i té la mateixa tarja gràfica que el teu. L'únic que no faria seria instal·lar uns nous controladors que hi ha a la pàgina de AMD, aquest em varen petar, però si agafes el que venen en els "Drivers restringits" no tindràs cap problema (amb l'Ati que tenia abans una Radeon 1300, va ser una mica un drama).

També té el vista instal·lat i no he tingut cap problema per fer la instal·lació de l'Ubuntu, la he fet com sempre amb el live CD.

Et paso un enllaç que et pot ser útili pels que teniu HP.
[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#webcam]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#webcam")

Salut

---

