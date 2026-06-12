---
title: "He fet algun un disabarat?"
date: 2010-09-17
forum: Catalan Team
---

### Post by Satboy on 2010-09-17
Bona tarda,
 L'Ubuntu m'ha dit que hi ha paquets per actualitzar, però quan intento actualitzar-los em passa el següent:

 [IMG]http://img832.imageshack.us/img832/4199/capturads.jpg[/IMG]

 Només recordo que vaig intentar instal·lar el ClamAV però un cop instal·lat no el vaig poder fer funcionar i, acte seguit, el vaig desinstal·lar.

 Moltes gràcies!

 Dew!;)

---

### Post by oriolsbd on 2010-09-17
Se't deu haver quedat instal·lat alguna llibreria que necesista el clamav. Obre el Synaptic, i busca els paquets que comencin per «clamav». Si en tens algun d'instal·lat, selecciona'l i fes «Paquet>Marca per a eliminar completament». Fes-ho també per al paquet «clamtk». Aplica els canvis, i mira de tornar a fer una actualització.

Salut!

---

### Post by Satboy on 2010-09-17
Hola,
 Ja ho he mirat i tot està net com una patena, res de res instal·lat (del clamAV, vull dir)

 Dew!

---

### Post by Satboy on 2010-09-17
Hola de 9,
 Hi ha una carpeta anomenada "clamav" a "/home/etc/".

 Dew!

---

### Post by Satboy on 2010-09-17
Hola,
 he fet una recerca hi he trobat aquests arxius de ClamAv:

 > amavisd-new - Interface between MTA and virus scanner/content filters
amavisd-new-milter - Interface between sendmail-milter and amavisd-new
c-icap - ICAP server coded in C
clamassassin - email virus filter wrapper for ClamAV
clamav-data - clamav data files
clamav-getfiles - Update script for clamav
clamav-unofficial-sigs - update script for 3rd-party clamav signatures
clamfs - user-space anti-virus protected file system
clamsmtp - virus-scanning SMTP proxy
clamtk - graphical front-end for ClamAV
courier-filter-perl - purely Perl-based mail filter framework for the Courier MTA
havp - HTTP Anti Virus Proxy
klamav - KDE frontend for ClamAV
libclamav-client-perl - A client for the ClamAV virus scanner daemon
mailscanner - email gateway for virus scanning, spam and phishing detection
python-clamav - Python bindings to ClamAV
python-pyclamd - Python interface to the ClamAV daemon
libclamunrar6 - anti-virus utility for Unix - unrar support
clamav - anti-virus utility for Unix - command-line interface
clamav-base - anti-virus utility for Unix - base package
clamav-daemon - anti-virus utility for Unix - scanner daemon
clamav-dbg - debug symbols for ClamAV
clamav-docs - anti-virus utility for Unix - documentation
clamav-freshclam - anti-virus utility for Unix - virus database update utility
libclamav-dev - anti-virus utility for Unix - development files
libclamav6 - anti-virus utility for Unix - library
clamav-milter - anti-virus utility for Unix - sendmail integration
clamav-testfiles - anti-virus utility for Unix - test files


 Dew!

---

### Post by Satboy on 2010-09-17
Hola,
 Més info:

 > La informació següent pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
  clamav: Depèn: libclamav6 (>= 0.96.1+dfsg) però no serà instal·lat
E: Paquets trencats


 Dew!

---

### Post by tanreb20 on 2010-09-17
Una opció que pots provar és:

```
sudo apt-ge tinstall -f
```

Sinó obre el synaptic y alla ves a filtres / trencats (a la part inferior esquerra) selecciona els que allí surtin i marcals per eliminar COMPLETAMENT.

---

### Post by Satboy on 2010-09-18
Hola,
 Desprès de fer el què tu m'has dit aquest és el resultat:

 > administrador@administrador-desktop:~$ sudo sudo apt-get install -f
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Els paquets següents s'instal·laren automàticament i ja no són necessaris:
  libtext-glob-perl libdate-calc-perl liberror-perl libcarp-clan-perl
  libfile-find-rule-perl libdebian-package-make-perl libtommath0
  libipc-run3-perl libnumber-compare-perl libbit-vector-perl
Empreu «apt-get autoremove» per a suprimir-los.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 32 no actualitzats.

administrador@administrador-desktop:~$ sudo apt-get autoremove
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Es SUPRIMIRAN els paquets següents:
  libbit-vector-perl libcarp-clan-perl libdate-calc-perl
  libdebian-package-make-perl liberror-perl libfile-find-rule-perl
  libipc-run3-perl libnumber-compare-perl libtext-glob-perl libtommath0
0 actualitzats, 0 nous a instal·lar, 10 a suprimir i 32 no actualitzats.
Després d'aquesta operació s'alliberaran 2429kB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 289770 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant libdate-calc-perl ...
S'està desinstal·lant libbit-vector-perl ...
S'està desinstal·lant libcarp-clan-perl ...
S'està desinstal·lant libdebian-package-make-perl ...
S'està desinstal·lant liberror-perl ...
S'està desinstal·lant libfile-find-rule-perl ...
S'està desinstal·lant libipc-run3-perl ...
S'està desinstal·lant libnumber-compare-perl ...
S'està desinstal·lant libtext-glob-perl ...
S'està desinstal·lant libtommath0 ...
S'estan processant els activadors per a man-db ...
S'estan processant els activadors per a libc-bin ...
ldconfig deferred processing now taking place



 Dew!

---

### Post by Satboy on 2010-09-18
Hola,
 No hi ha res a fer, torno a estar com al començament.La dec haver fet molt grossa!

 [IMG]http://img831.imageshack.us/img831/2662/capturafv.jpg[/IMG]

 Dew!

---

### Post by oriolsbd on 2010-09-18
Hola de nou.

Sembla que hi tens alguna línia incorrecta al fitxer "statoverride". Abans que res, feste'n una còpia de seguretat:
```
cp /var/lib/dpkg/statoverride /home/el_teu_usuari/statoverride.cop
```

Després, obre el fitxer amb el gedit, executant el següent des d'un terminal:
```
sudo gedit /var/lib/dpkg/statoverride
```

Segur que hi ha alguna línia on faci referència a aquest usuari «clamav». Elimina la línia en qüestió, desa els canvis i torna a actualitzar.

Salut!

Oriol.

---

### Post by Satboy on 2010-09-18
Hola,
 El fitxer "statoverride" té aquest contingut:
> 
clamav clamav 755 /var/cache/clamav-unofficial-sigs/add-dbs
root mlocate 2755 /usr/bin/mlocate
clamav clamav 755 /var/cache/clamav-unofficial-sigs/si-dbs
clamav clamav 755 /var/cache/clamav-unofficial-sigs/mbl-dbs
clamav clamav 755 /var/cache/clamav-unofficial-sigs/msrbl-dbs
clamav clamav 700 /var/lib/clamav-unofficial-sigs/gpg-key
hplip root 755 /var/run/hplip
clamav clamav 755 /var/cache/clamav-unofficial-sigs/ss-dbs
clamav clamav 755 /var/lib/clamav-unofficial-sigs/configs


 Què tinc de fer?

Dew!

---

### Post by oriolsbd on 2010-09-18
D'aquest fitxer, eliminla les línies que comencen per "clamav".

Salut!

---

### Post by Satboy on 2010-09-18
Hola,
 Ja ho he fet, només hi queda:
 > root mlocate 2755 /usr/bin/mlocate
hplip root 755 /var/run/hplip

 Però estem igual:

 [IMG]http://img824.imageshack.us/img824/2042/capturagh.jpg[/IMG]

 Dew!:(

---

### Post by oriolsbd on 2010-09-18
Mira que no hagis deixat cap línia buida en el fitxer statoverride. Potser al final de tot?

Salut!

---

### Post by Satboy on 2010-09-20
Hola,
 Moltíssimes gràcies Oriol, finalment ho he pogut solventar.He instal·lat les actualitzacions, he reiniciat el sistema, però m'ha sortit això:

 [IMG]http://img185.imageshack.us/img185/7295/capturaab.jpg[/IMG]

 És gaire preocupant? En tinc de fer gaire cas?

 Dew i moltes gràcies!;)

---

### Post by wgarcia on 2010-09-20
Mira si aquest fil et serveix, diu que tenien aquest mateix missatge:

[http://ubuntuforums.org/showthread.php?t=1286538](http://ubuntuforums.org/showthread.php?t=1286538)

---

### Post by oriolsbd on 2010-09-21
Apart del que comenta el wgarcia, has eliminat la línia on hi posava «hplip» del fitxer «statoverride»? En principi, aquesta no s'havia de treure. O sigui, el fitxer «statoverride» hauria de contenir aquestes dues línies (únicament aquestes dues línies):

> root mlocate 2755 /usr/bin/mlocate
hplip root 755 /var/run/hplip

Salut!

---

### Post by Satboy on 2010-09-22
> **oriolsbd said:**
> Apart del que comenta el wgarcia, has eliminat la línia on hi posava «hplip» del fitxer «statoverride»? En principi, aquesta no s'havia de treure. O sigui, el fitxer «statoverride» hauria de contenir aquestes dues línies (únicament aquestes dues línies):



Salut!

 Hola,
 Gràcies Oriol, això que tu dius és exactament el què hi ha, no hi ha res més.
 Ara provaré de reiniciar-lo.
 Gràcies, de 9!!

---

### Post by Satboy on 2010-09-22
Hola companys,
 Ara tot va de meravella, l'he reiniciat dos cops i m'ha funcionat de conya!

  Si mai veniu a Manresa teniu dues birres (com a mínim) pagades!

 Moltes gràcies, de 9!!

---

### Post by wgarcia on 2010-09-22
Les dues per l'Oriol? O una per a cada u? O dues per a cada u? :confused:

---

### Post by Satboy on 2010-09-22
> **wgarcia said:**
> Les dues per l'Oriol? O una per a cada u? O dues per a cada u? :confused:

 Hola,
 Una per cada un, com a mínim! :):):)

 Dew! ;)

---

