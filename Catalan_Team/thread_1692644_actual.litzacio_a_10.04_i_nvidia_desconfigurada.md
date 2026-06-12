---
title: "actual.litzacio a 10.04 i nvidia desconfigurada"
date: 2011-02-21
forum: Catalan Team
---

### Post by venusfenix on 2011-02-21
buenas,

tinc un notebook Acer and una nvidia Gefor7000M,
m'he actual.litzat al LTS 10.04 i la nvidia no s'ha instal.lat.
no em deixar ni entrar, quan hauria de tenir la pantalla amb el selector d'usuari, no es veu res.
que puc fer?

gracies,

---

### Post by wgarcia on 2011-02-22
El primer que pots provar és entrar en "recovery-mode" des del grub i et donarà un menú per reconfigurar la gràfica, a veure si això ho arregla.

---

### Post by venusfenix on 2011-02-22
fet. pero ara no sé que mes he de fer....

que puc fer per instal.lar el que toca?
El missatge que em dona es:
L'Ubuntu s'està exevutant en mode de baixa resolució.
S'ha trobat el següent erro. Hauríeu d'actualitzar la vostra configuració per a solucionar-lo. (EE)
failed to load module "nvidia" module does not exit, 0
no drivers available.

gracies,

---

### Post by wgarcia on 2011-02-22
Si pots entrar a una terminal, em sembla que és una de les opcions que et dóna quan inicies en "recovery", entra 

sudo apt-get update
sudo apt-get upgrade

sudo dpkg-reconfigure xserver-xorg

a veure si s'acaba de configurar la gràfica.

---

### Post by venusfenix on 2011-02-22
Moltes gracies, pero res!!
no funciona....
en mode recovery, puc entra, en demana entra reiniciant les X's, i tot be.
he fet tot el que m'heu dit, i res.

quant reiniciu, es veuen 4 linies a la part superior i res.
si intento entrar a l'aplicacio de nvidia, en diu que no puc (no root),i  no trova el driver.

estic una mica perdut en aixo!

---

### Post by kimet on 2011-02-22
Hauràs de buscar el driver que correspon a la teva tarja, entrar a la pàgina de descarregues d'nvidia, baixarlo  i instalar-lo manualment.

Em sembla que hi han instruccions a la mateixa pàgina.

---

### Post by wgarcia on 2011-02-23
Quan dius "intento entrar a l'aplicació de nvidia" exactament què és el que fas?

No has dit tampoc si has pogut entrar a la línia de comandes. 

En tercer lloc, si entres en mode de baixa resolució, prova si pots obrir una terminal i en aquesta terminal entrar:

sudo /usr/bin/jockey-gtk

Se t'obrirà l'aplicació que busca mòduls propietaris per la targeta, a veure si des d'aquí et dóna l'opció d'instal·lar el mòdul per a la targeta nvidia.

---

### Post by venusfenix on 2011-02-23
>>Quan dius "intento entrar a l'aplicació de nvidia" exactament què és el que fas?
>Tinc  l'aplicacio NVIDIA X srver settings. I no funciona, diu que no tinc cap driver de Nvidia.

>>No has dit tampoc si has pogut entrar a la línia de comandes. 
> Si que puc!

En tercer lloc, si entres en mode de baixa resolució, prova si pots obrir una terminal i en aquesta terminal entrar:

sudo /usr/bin/jockey-gtk

Se t'obrirà l'aplicació que busca mòduls propietaris per la targeta, a veure si des d'aquí et dóna l'opció d'instal·lar el mòdul per a la targeta nvidia.
> M'obre la finestra de maquinari de propietari pero res, no m'instal.la res.

Continuo igual, res de res!!
alguna idea??

Gracies,

---

### Post by wgarcia on 2011-02-23
Pot ser convindria saber exactament quina targeta gràfica tens instal·lada. Des de la línia de comandes fes

lspci | grep -i vga 

a veure que et mostra.

---

### Post by venusfenix on 2011-02-23
tinc una VGA COMPATIBLE CONTROLLER: NVIDIA CORP. C67 (GeForce 7000M/nForce 610M) Rev A2

---

### Post by wgarcia on 2011-02-24
Sembla que la teva targeta pot funcionar amb el següent mòdul propietari:

sudo apt-get install nvidia-glx-180

---

### Post by venusfenix on 2011-02-24
L'he instal.lat sense problemes, i sembla que comença a funcionar. Pero no puc cambiar resolucions, etc...


unes notes:
lspci |grep -i vga
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
glxgears
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by venusfenix on 2011-02-24
He reiniciat varies vegades, i funciona, ara nomes tinc el missatge d'error de:
undefined video mode: 31b
esta definit com a 795, pero no esta en la llista de la tarja.
L'unic problema es que si defineixo un mode, i no puc triar ningun mode superior de 1024, i hi  torno a tindre el problema d'abans.
sino defineixo res, em surt el missatge, pero entra amb una resolucio de 1440x900.

???
tant l'opcio de monitor com a la Nvidia X server settings continua donant el missatge que no tinc instal.lat cap driver de Nvidia.

Gracias,

---

### Post by wgarcia on 2011-02-25
Pots mostrar el que tens a la carpeta /etc/X11

ls /etc/X11

i si tens un fitxers xorg.conf, adjuntar-lo?

---

### Post by venusfenix on 2011-02-26
contingut del directori /etc/X11

app-defaults             xorg.conf-backup-090424072954        Xreset
cursors                  xorg.conf-backup-110221225311        Xreset.d
default-display-manager  xorg.conf-backup-110222215326        Xresources
fonts                    xorg.conf-backup-110224220351        Xsession
rgb.txt                  xorg.conf.dist-upgrade-200811021159  Xsession.d
X                        xorg.conf.dist-upgrade-201002200931  Xsession.options
xinit                    xorg.conf.dist-upgrade-201102212251  XvMCConfig
xorg.conf.backup         xorg.conf.failsafe                   Xwrapper.config

---

### Post by venusfenix on 2011-02-26
contingut del directori /etc/X11

app-defaults             xorg.conf-backup-090424072954        Xreset
cursors                  xorg.conf-backup-110221225311        Xreset.d
default-display-manager  xorg.conf-backup-110222215326        Xresources
fonts                    xorg.conf-backup-110224220351        Xsession
rgb.txt                  xorg.conf.dist-upgrade-200811021159  Xsession.d
X                        xorg.conf.dist-upgrade-201002200931  Xsession.options
xinit                    xorg.conf.dist-upgrade-201102212251  XvMCConfig
xorg.conf.backup         xorg.conf.failsafe                   Xwrapper.config

(sembla que no tinc xorg.conf

---

### Post by wgarcia on 2011-02-27
Tens alguna opció que digui "vga=..." a les línies d'arrencada del GRUB? Si no estàs segur pots adjuntar el fitxer

/etc/grub/grub.cfg

per veure com tens les línies d'arrencada.

---

### Post by venusfenix on 2011-02-27
malauradament, ni tinc directori grub, ni el fitxer que em dius.

no soc un expert com vosaltres, pero aixo no pinta be (?)

gracies,

---

### Post by wgarcia on 2011-02-27
No et preocupis, aquí tots sóm un usuaris, amb més o menys experiència però tots usuaris, d'experts no n'hi ha. 

I de fet m'he equivocat, el que volia dir és:

/boot/grub/grub.cfg

---

### Post by venusfenix on 2011-02-27
gracies per tot Wgarcia,


/boot/grub$ ls
default        grubenv            menu.lst~          splashimages
device.map     installed-version  menu.lst.backup    stage1
e2fs_stage1_5  jfs_stage1_5       minix_stage1_5     stage2
fat_stage1_5   menu.lst           reiserfs_stage1_5  xfs_stage1_5


hem sembla que no tinc el fitxer que dius.

---

### Post by wgarcia on 2011-02-27
D'acord, el que passa és que tens instal·lat el "Grub legacy", que és la versió de grub que hi havia abans de la versió 9.10 (o potser 9.04, no ho recordo bé). A les últimes versions sempre ve per defecte el Grub 2, que és la nova versió de Grub. Si vols actualitzar-la busca informació al respecte o obre un fil específic per això. 

El que has d'enganxar dons és el fitxer "menu.lst".

---

### Post by venusfenix on 2011-02-27
Aqui tens el contigut de menu.lst

## ## End Default Options ##

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=434587df-a259-447e-a901-222a0dcc1ca1 ro splash vga=795 
initrd		/boot/initrd.img-2.6.32-28-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=434587df-a259-447e-a901-222a0dcc1ca1 ro  single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=434587df-a259-447e-a901-222a0dcc1ca1 ro splash vga=795 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=434587df-a259-447e-a901-222a0dcc1ca1 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.04.2 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by venusfenix on 2011-02-27
buenas,

algunes aportacions, he tingut problemes amb l'instal.lació de programes, ja solventat en un altre fil, i ajudat per Wgarcia.

pero estic veient que puc instal.lar programes pero programes relacionants amb wifi com el ndiswrapper, wifi radar, wicd, network-manager, no funcionan... 
alguna pista?

gracies,

---

### Post by venusfenix on 2011-02-27
TEMA SOLUCIONAT,

finalment, despres d'intentar varies vegades d'entrar en Nvidia S server config, s'ha ences la llum, i he fet en el terminal, sudo nvidia-xconfig, despres un sudo /etc/init.d/gdm restart, "y listos"


sembla que tot funciona be, ara a per la wifi


gracies per la vostra paciencia!!!

---

### Post by wgarcia on 2011-02-28
És estrany que no et demanés autentificar-te quan volies canviar els paràmetres des del menú, però m'alegro que s'hagi solucionat. 

Si tens més problemes pot ser per tenir l'opció "vga=795" al menú d'arrencada del grub.

Per cert: si li poses "Solved" usant "Thread tools" al fil pot ser d'utilitat a altra gent que tingui el mateix problema.

---

### Post by venusfenix on 2011-02-28
he probat amb el que dius (vga= 795) pero no va funcionar, finalmente, he probat amb vga= normal, i tot correcte.

Gracies,

---

### Post by wgarcia on 2011-03-01
Sí, justament el que deia és que vga=795 podia ser el problema, però sembla que ja et funciona.

---

