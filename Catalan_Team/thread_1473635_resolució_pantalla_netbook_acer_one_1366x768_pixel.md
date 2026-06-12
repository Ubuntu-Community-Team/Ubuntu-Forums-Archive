---
title: "resolució pantalla netbook acer one 1366x768 pixel 11.6&quot;"
date: 2010-05-05
forum: Catalan Team
---

### Post by pserra on 2010-05-05
TINC EL PROBLEMA DE RESOLUCIÓ DE PANTALLA: LA MEVA ES 16:9 DE 1366X768   i em surt 1036 x 768
al seu dia el vaig arreglar amb les 4 comandes de l'enllaç:
> [http://www.ubuntu-es.org/?q=node/115702](http://www.ubuntu-es.org/?q=node/115702)
que son:
wget [http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz](http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz)
tar -zxvf poulsbo1.tar.gz
cd poulsbo1
sudo ./install.pl
em surten aquests errors:
> 
    carles@carles-laptop:~/poulsbo1$ sudo ./install.pl
    [sudo] password for carles:
    Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys C6598A30
    gpg: requesting key C6598A30 from hkp server keyserver.ubuntu.com
    gpg: key C6598A30: "Launchpad PPA for Ubuntu Mobile Team" not changed
    gpg: Nombre total processat: 1
    gpg: no modificades: 1
    Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 99C0198F
    gpg: requesting key 99C0198F from hkp server keyserver.ubuntu.com


    2 pagines de codi i..

    Deleting module version: 4.41.2
    completely from the DKMS tree.
    ------------------------------
    Done.
    S'està desempaquetant el reemplaçament de psb-kernel-source ...
    Removing old module source...
    S'està configurant psb-kernel-headers (4.41.2-0ubuntu1~910um1) ...
    S'està configurant psb-kernel-source (4.41.2-0ubuntu1~910um1) ...
    Loading new psb-kernel-source-4.41.2 DKMS files...

    Error! Could not find module source directory.
    Directory: /usr/src/psb-kernel-source-4.41.2 does not exist.
    dpkg: s'ha produït un error en processar psb-kernel-source (--install):
    el subprocés installed post-installation script retornà el codi d'eixida d'error 2
    S'han trobat errors en processar:
    psb-kernel-source
    update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic
    carles@carles-laptop:~/poulsbo1$


també en aquest enllaç se'n parla, però ahir ho vaig provar i va quedar igual:
> [https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

i provoca que al carregar un cop m'han sortit els altres errors em surten:
1-l'ubuntu s'està executant a baixa resolució...
2-shan trobat els seguents errors.....
EE-Faillet to load module 'psb'(module does not exist,0)
EE-No driver avaible
MERCI I PERDÓ PER SER TANT 'PROFUS'...

---

### Post by PatrickVogeli on 2010-05-05
tens molt mala solució... realment el millor que pots fer es vendre aquesta maquina i comprar-ne alguna amb grafica suportada.

Et comento, el driver que hi ha per la GMA 500 (la teva grafica) es un desastre absolut: mal disenyat, mal fet i mal mantenit. A més, em sembla haver llegit que el driver que hi ha no es compatible amb l'xorg 1.7 que porta la 10.04.. de moment no sembla que tinguis una bona solucio.

Si saps angles, aqui tens mes informacio: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1453445](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1453445)

Jo tinc la opinio que aquesta situació, lluny de millorar, empitjorara amb el temps... aquesta grafica no la fabrica intel i els drivers tampoc els fan ells.

salut

---

### Post by pserra on 2010-05-05
Ondia,
doncs si que estem bé...
No se com arreglar-ho dons... em va petar 2 dies abans de instal·lar el lucid, quan vaig actualitzar kernel.... hi ha la posibilitat de fer marxa enrera??
amb el karmic i el escritori se'm veia molt bé...
MERCI

---

### Post by pserra on 2010-05-06
en vista de que el problema es que el kernel de la lucid no suporta la grafica del acer one... com ho puc fer per tornar a isntal3lar un  kernel que suporti la gràfica??
Merci

---

### Post by PatrickVogeli on 2010-05-06
no es sols el kernel, si no tambe el servidor grafic. Jo de moment tornaria a la 9.10

---

### Post by pserra on 2010-05-06
> **PatrickVogeli said:**
> no es sols el kernel, si no tambe el servidor grafic. Jo de moment tornaria a la 9.10

per no reinstalar la 9.10 des de el pen drive.. que es més farregós, hi ha alguna manera de fer-ho a través del gestor d'actualitzacions/sinaptic?
llavors puc triar el kernel?? quan estava al 9.10 i va sortir el lucid (fa una semana) a través del gestor vaig canviar el kernel i la grafica  va fer 'figa'  amb el 9.10...
Bé m'agrada tornar enrera... per el que he vist en l'altre ordinador.. el lucid va aparèixer com que seria més ràpit al arrancar... però em sembla que ha estat al ravès...

Si decideixo mantenir-me a 9.10 com faig els updates sense  que em surti actualitzar kernels ni histories que em facin falta?

Merci...

---

