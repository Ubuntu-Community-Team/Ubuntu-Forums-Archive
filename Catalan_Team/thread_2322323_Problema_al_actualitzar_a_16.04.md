---
title: "Problema al actualitzar a 16.04"
date: 2016-04-27
forum: Catalan Team
---

### Post by josep7 on 2016-04-27
Hola, he actualitzat a 16.04 com sempre i semblava que anava bé fins que he reinicialitzat al acabar i ara el ratolí no funciona i no hem surten les barres superior i lateral.
Algú té hem pot donar un cop de mà ?
Es pot tornar a fer un altre cop la actualització?

---

### Post by wgarcia on 2016-04-27
Quin escriptori fas servir? L'escriptori per defecte de l'Ubuntu (Unity)?

---

### Post by josep7 on 2016-04-27
Correcte faig servir el Unity.

---

### Post by wgarcia on 2016-04-28
Sembla un problema de la targeta gràfica, que no està iniciant l'escriptori correctament. Caldria esbrinar quina targeta gràfica tens i quin controlador està fent servir. 

Si pots obrir una terminal (tot i que si no tens els panells suposo que no podràs), primer jo asseguraria que el sistema ha quedat totalment actualitzat amb les comandes: 

```
sudo apt-get update
sudo apt-get upgrade
```

Si s'actualitzen coses tornaria a provar si s'ha arreglat, i si no s'ha arreglat, ara sí miraria quina targeta gràfica hi ha:
```
sudo lshw -c video
```
Si et diu que no troba "lshw" fes "sudo apt-get install lshw" abans d'entrar aquesta ordre.

Si no tens accés a una terminal perquè no pots entrar a l'escriptori, al menú d'entrada al sistema (el menú de "grub") pots escollir "Opcions avançades" i aquí a la segona línia veuràs "Mode de recuperació". Al menú que s'obre primer esculls "Iniciar la xarxa", i aquí no recordo si ja se t'obre una consola per entrar les ordres de dalt o si has d'escollir després "Consola de root" per tenir la terminal. En tot cas la idea es tenir la terminal per esbrinar la targeta gràfica i veure si es pot canviar el controlador perquè funcioni correctament el tema gràfic.

---

### Post by josep7 on 2016-04-28
He pogut entrar al terminal a través del grub, a Unity impossible . He fet que actualitces com has dit i res.
He decidit tirar pel dret i provar desde un llapis i collonut.
He tornat a instalar la distribució i ara sí que tinc les barres del Unity, però el cursor segueix bloquejat. En la pantalla de inici, on poses la contrasenya si que va pero al entrar a dins de sobte es queda parat.
He mirat el controlador de la gràfica i es el que m'ha funcionat sempre, es el propi de Nvidia i mai havia donat problemes. De moment puc anar fent amb el tabulado, fletxes i demés però  aniria millor si el ratolí funcionés . I no és problema del animaló que fins i tot l'he provat en un altre màquina.
Cal aclarir que funcionava perfectament amb el llapis.

---

### Post by wgarcia on 2016-04-29
A vegades els controladors no estan actualitzats, el controlador de NVIDIA és privatiu, és a dir, depèn que NVIDIA li surti dels c....... actualitzar-lo, els desenvolupadors de Linux no poden fer res perquè no proveeixen el codi font. També hi ha el controlador "nouveau" que sí que és obert i desenvolupat per la comunitat Linux. El que pots fer, si vols, és a "Paràmetres de sistema -> Programari i actualitzacions -> Controladors addicionals", canviar del controlador Nvidia privatiu al "X.Org X server - Nouveau" i veure què tal et va. Si et va bé sempre és molt millor utilitzar aquest controlador, 1) per ser programari lliure, 2) perquè és molt menys probable que et passin aquestes coses en actualitzar el sistema.

Si tens problemes de fer aquest canvi perquè no et va el cursor hi ha maneres de fer-lo també des de la consola.

---

### Post by josep7 on 2016-04-29
A base de teclat he anat a "programari i actualitzacions "
Efectivament tenia el de propietat funcionant , val a dir que posa "recomenat i comprovat". De totes maneres  he seleccionant el que surt com a alternatiu i posa:
"S'està utilitzant X.Org X Server- Noveau display Driver des de xserver-xorg-video-noveau (programari lliure)".

He reiniciat i no hi trobo cap canvi , el cursor es queda parat....
Al menys no anem enrere :-)

---

### Post by wgarcia on 2016-04-29
Obre una terminal amb "Ctrl-Alt-T" (Crtl: tecla Control, Alt: tecla Alt, T: la tecla T, totes 3 a l'hora). Entra la següent ordre:
```
xsetpointer -l | grep Pointer
```
Et mostrarà els dispositius tipus ratolí que veu el sistema i al costat d'almenys un hauria de dir "[XExtensionPointer]". Almenys així se sabrà si el sistema veu algun dispositiu tipus ratolí.

---

### Post by josep7 on 2016-04-29
Diu això :

2: "Virtual core pointer".             [XPointer]

4: " Virtual core XTEST pointer"[XExtensionPointer]

10: "HID 0a5c:4503"    [XEtensionPointer]

8: " USB OPTICAL MOUSE". [XExtensionPointer]

---

### Post by wgarcia on 2016-04-30
D'acord, el sistema sembla veure bé el ratolí, a l'última línia, per tant em segueix semblant un problema gràfic.

Hi ha un parell d'informes d'error semblants, molt recents i per tant encara pendents. Sembla succeir en un parell de sistemes. Algunes solucions que he vist que s'han suggerit, mentre no s'arregli mitjançant alguna actualització, són les següents:

1) Obrir una terminal i donar les següents ordres:
```
sudo rmmod usbhid
sudo modprobe usbhid
```

2) Obrir i tancar una consola virtual, amb CTRL-ALT-F6 (surt dels sistema gràfic cap a una consola), CRTL-ALT-F7 torna al sistema gràfic.

Una altra cosa que pots fer és anar a l'informe d'error, i al costat de "Does this bug affect you?", clicar sobre el petit cercle groc i escollir que també t'afecta a tu (si no tens compte al Launchpad, la plataforma d'informes d'error d'Ubuntu, t'has de crear primer una). També et pots subscriure a l'informe perquè t'arribin correus quan hi ha comentaris o novetats, a vegades la gent proposa solucions fins que s'arregli l'error.

L'informe d'error el pots trobar a:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1575872](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1575872)

---

### Post by josep7 on 2016-04-30
He començat pel punt 1 i res.
Paso al punt 2 ctrl+alt+F6 introdueixo sudo rmmod usbhid
sudo modprobe usbhid
I el ratolí comença a funcionar , beee!!

Reiniciat del ordinador i torna a quedà immòbil , me..a!!

Provaré el punt 3 i ja et diré.

De totes maneres gràcies

---

### Post by josep7 on 2016-05-01
Ja he fet el punt tres. A veure si ens faciliten un pedaç...

De totes maneres hi ha una cosa a la que li dono voltes. Com es que amb el Ubuntu treballant des de un llapis no hi ha cap problema i si el poses al disc dur si?.
A veure tant en un lloc com en l'altre fan servir la resta de maquinària i de controladors de la mateixa manera , no ho entenc .
Hi ha alguna cosa que s'escapa del meu raonament ...

---

### Post by wgarcia on 2016-05-02
Possiblement la sessió autònoma (la d'iniciar amb l'USB) està fent servir un altre controlador gràfic que la versió instal·lada. Prova de fer això que et deia de:
```
sudo lshw -c video
```
i compara el que es veu a "Driver" a les últimes línies. 

Potser a la sessió autònoma hagis d'instal·lar "lshw":
```
sudo apt-get install lshw
```
si et diu que no troba aquesta ordre.

---

### Post by josep7 on 2016-05-02
Posa exactament el mateix :

description: VGA compatible controller
product: G86 [GeForce 8400 GS]
vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: a1
width; 64 bits
clock: 33MHz
capabilities: pm msi pciexpres vga-controler bus-master cap-list rom
configuració: driver=noveau latency=0
resources: irq:26 memory:fd000000-fdffffff...

---

### Post by wgarcia on 2016-05-03
Pots enganxar el que hi ha al fitxer de configuració de dispositius?:
```
cat /etc/modprobe.d/blacklist.conf
```
El més pràctic és que enganxis la sortida a "http://paste.ubuntu.com/" i aquí sols enganxis l'enllaç que et dóna.

---

### Post by josep7 on 2016-05-04
Hem dona aquesta llista

paste.ubuntu.com/162121180/

Es greu doctor ?

---

### Post by wgarcia on 2016-05-04
Molt bona! Però aquí t'has de curar tu sol...

L'enllaç que poses no em funciona, [http://paste.ubuntu.com/162121180/](http://paste.ubuntu.com/162121180/) diu que no existeix. Està bé el número?

---

### Post by josep7 on 2016-05-04
Crec que no he copiat bé l'enllaç
Prova aquest

paste.ubuntu.com/16212301/

---

### Post by wgarcia on 2016-05-04
Ara sí.

Segons alguns informes de sistemes que el passa el mateix que a tu, es pot provar de usar un controlador diferent per al ratolí usb. Per tant primer has d'editar el fitxer aquest (que posa en la "llista negra" alguns controladors):

```
sudo nano /etc/modprobe.d/blacklist.conf
```

A la línia que posa:

```
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
```
afegeix-li una línia perque no es faci servir usbhid i es faci servir un dels dos que estan cancel·lats aquí, o els dos, per tant hauria de quedar ara com:
```
# these drivers are very simple, the HID drivers are usually preferred
# blacklist usbmouse
blacklist usbkbd
blacklist usbhid
```
on "#" davant de la línia la converteix en comentari i per tant deixa de tenir efecte, o sigui que ara "blacklist usbmouse" no s'executa i per tant usbmouse es pot fer servir. Si encara no et funciona prova de posar un "#" també davant "blacklist usbkbd", tot i que aquest refereix al teclat USB i per tant no crec que tingui a veure amb el ratolí. 

Si això no ho arregla torna a deixar tot com estava (és a dir esborra la línia afegida i treu els "#" que hagis escrit) i s'haurà de provar alguna altra cosa.

---

### Post by josep7 on 2016-05-04
Edito les línies què dius però no sé com guardar-ho. Al tornar a obrir el terminal està sense modificar.
Tinc que teclejar ^0 ?

---

### Post by wgarcia on 2016-05-04
CTRL-X i contestar "Y". A baix a l'última línia tens una ajuda de les ordres.

---

### Post by josep7 on 2016-05-04
He provat la modificació i res, continua igual .
Ho he tornat a deixar com abans

---

### Post by wgarcia on 2016-05-04
Resumint: si fas 
```
 sudo rmmod usbhid
sudo modprobe usbhid
```
comença a funcionar el ratolí però quan reinicies ja no funciona més?

---

### Post by josep7 on 2016-05-04
correcte

---

### Post by wgarcia on 2016-05-04
Una manera de forçar l'execució d'aquestes ordres és afegir-les al fitxer /etc/rc.local. Per tant el pots editar:
```
sudo nano /etc/rc.local
```
i afegir abans a l'última línia que posa "exit 0" les dues ordres en qüestió:

```
sudo rmmod usbhid
sudo modprobe usbhid
```

A veure si hi ha sort, no estic 100% segur que aquest fitxer és com s'executen ara les ordres personalitzades en iniciar el sistema, perquè el sistema d'inici de l'Ubuntu i de moltes distribucions Linux ha canviat recentment (d'un sistema que es diu "upstart" a un que es diu "systemd", i no tot funciona igual). Si ho arregla, tot bé, si no ho arregla s'haurà d'investigar si realment s'estan executant aquestes ordres a l'inici.

Una altra cosa que pots fer és informar d'aquest error, perquè sembla un error del nucli de Linux (és un error que s'havia solucionat en el passat però sembla que torna a aparèixer). 

Per informar de l'error, primer t'has de crear un compte a Launchpad que és on es registren els errors: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Un cop tens el compte, a una terminal has d'entrar
```
ubunbu-bug linux
```
on "linux" vol dir que es vol informar d'un error al nucli. 

Et preguntarà una sèrie de coses i, un cop les contestes, obrirà una pàgina web on entrar l'error, pots entrar com a tema de l'error "Mouse stuck at start-up", i a la descripció: «My mouse is stuck at start-up. A workaround is to enter "sudo rmmod usbhid; modprobe usbhid" and the mouse starts working.»
Enganxa també si vols informar de l'error la sortida que et dóna l'ordre "lsusb" a una terminal.

---

### Post by josep7 on 2016-05-04
[SIZE=2][FONT=arial]he provat el [/FONT][/SIZE]
sudo nano /etc/rc.local

i modificat el que dius però no ha funcionat. Al reinicia torno a quedar sense ratolí, per tant he tornat a deixar-ho tot igual.

He comunicat al launchpad tal com has dit i ja tenim numero de bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1578317]("https://bugs.launchpad.net/")

---

### Post by wgarcia on 2016-05-05
Jo de moment deixaria les ordres en /etc/rc.local, i miraria a veure si s'aconsegueix executar a l'inici. Primer s'hauria de mirar si el fitxer és executable:

```
ls -l /etc/rc.local
```

Hauria de mostrar una cosa semblant a:
```
-rwxr-xr-x 1 root root 333 may 5  2016 /etc/rc.local
```
Les "x" mostren que el fitxer és executable per l'usuari (root: l'administrador), el grup de l'usuari i tothom.

---

### Post by josep7 on 2016-05-05
he deixat les ordres a /etc/rc.local
 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo rmmod usbhid
sudo modprobe usbhid

exit 0


i al reiniciar no va. El terminal diu el següent

-rwxr-xr-x 1 root root 345 mai  5 09:14 /etc/rc.local

---

### Post by wgarcia on 2016-05-05
D'acord, m'ho he mirat i amb "systemd" és una mica més complicat. Et passo les instruccions.

1) S'ha de crear un fitxer nou:
```
sudo nano /etc/systemd/system/rc-local.service
```

2) S'ha d'entrar el següent contingut a aquest fitxer:
```
[Unit]
Description=/etc/rc.local Compatibility

[Service]
Type=oneshot
ExecStart=/etc/rc.local
TimeoutSec=0
StandardInput=tty
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

3) Un cop desat el fitxer, s'ha d'obrir una terminal i s'ha de donar la següent ordre:
```
sudo systemctl enable rc-local.service
```


4) Reiniciar i a veure si ara funciona.

---

### Post by josep7 on 2016-05-05
pitjor, ara no va ni amb
sudo rmmod usbhid
sudo modprobe usbhid

---

### Post by wgarcia on 2016-05-05
Per deixar-lo com estava elimina les línies 
```
sudo rmmod usbhid
sudo modprobe usbhid
```
de /etc/rc.local, però abans prova de deixar-les sense "sudo":
```
rmmod usbhid
modprobe usbhid
```

---

### Post by wgarcia on 2016-05-05
Per cert, he vist que t'han contestat a l'informe d'error. A la primera pregunta comenta'ls que sí que ha començat a passar amb una actualització:
"Yes, this started happening when I updated to 16.04". 

També et suggereix que provis algun altre nucli, no sé si ha quedat algun nucli de la versió anterior instal·lat, pots mirar-ho a l'inici del sistema, al menú del "grub". Si l'ordinador s'inicia directament sense passar per aquesta pantalla, pots forçar que la mostri prement la tecla de majúscula quan s'inicia l'ordinador. A "Opcions avançades" a vegades et dóna opció d'iniciar el sistema amb un nucli més antic. Si et funciona el ratolí amb el nucli més antic, pots comentar a l'informe d'error:
"I tried with an older kernel and it works" (i si veus la versió, posar-la). 

Per últim et suggereix provar un nucli més nou. Això ja és més complicat, però no massa, si t'animes puc donar-te una mà.

Una altra cosa: respecte a això que deies al missatge #12, que el ratolí funciona a una sessió iniciada des de memòria USB, mira d'entrar aquesta sessió i mirar quin nucli de Linux està fent servir, des d'una terminal:
```
uname -a
```
i compara'l amb la versió quan no funciona el ratolí donant la mateixa ordre en la sessió instal·lada.

---

### Post by josep7 on 2016-05-06
acabo de comprovar la versió live i la instal·lada i son les mateixes

instal·lada

josep@josep-GJ306AA-ABE-m8175-es:~$ uname -a
Linux josep-GJ306AA-ABE-m8175-es 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

live

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Al meu entendre, potser vaig errat, no es un problema de nucli ja que les dues tenen el mateix. Crec que la cosa podria vindre de les actualitzacions que rep al instal·lar. 
Per això hem fa cosa canviar el nucli i posar el mes nou (no està rodat), Al disc no hi queda cap antic ja que es va fer un muntatge tot nou, les dades les tinc a un altre disc.

---

### Post by wgarcia on 2016-05-06
Sí, és el mateix. Em sorprèn una mica perquè a la imatge d'instal·lació de la versio 16.04 hi havia una versió anterior del nucli 4.4.0, potser la 17 o la 18.

Quant al nucli més nou, sols es tracta de provar-lo, no d'instal·lar-lo permanentment, perquè el problema pot ser una combinació de coses i el fet que no funcioni a la versió live i no a la instal·lada no permet descartar que sigui un problema de nucli. 

Bé, en tot cas et passo les instruccions per si t'animes, realment pot ser molt útil per a l'informe d'error i descartar que sigui un problema del nucli. De pas queda com a referència per algú/alguna que vulgui provar nuclis més nous i veure si algun problema de maquinari que veu està resolt en versions futures.

T'explico així doncs com provar un nucli més recent a veure si el problema està arreglat. Al final es desinstal·la i tot queda igual que abans.

Mira el nucli que tens ara, obre una terminal i fes:
```
uname -a
```

Anota't la versió per recordar-la.

Des de la terminal crea't una carpeta per fer les proves:

```
mkdir proves
```

Entra a la carpeta:
```
cd proves
```
Baixa't el nucli que provaràs:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb

```

Instal·la el nucli:
```
sudo dpkg -i *.deb
```

Reinicia el sistema, i al menú inicial d'arrencada de l'Ubuntu (el Grub) busca aquest nucli, que el veuràs amb la mateixa informació de versió que hi ha als noms dels fitxers que s'han baixat (4.6.0-040600rc6), i inicia el sistema amb aquest nucli. Si no surt el menú del Grub i el sistema va directament a la pantalla d'inici o a l'escriptori, prem la tecla Majúscules quan s'estigui iniciant el sistema.  

Mira si funciona el ratolí. 

Torna a reiniciar el sistema i arrenca'l en el nucli que tenies, la versió és la que es va anotar al principi, potser al menú del Grub et sorti a "Opcions avançades".  

Desinstal·la el nucli que has provat:
```
sudo apt-get remove linux-headers-4.6.0-040600rc6-generic linux-image-4.6.0-040600rc6-generic
```

Des del navegador de fitxers pots esborrar els fitxers que s'han baixat i la carpeta de proves.

Reinicia el sistema i no es veurà més aquest nucli de prova.

---

### Post by josep7 on 2016-05-06
vaig a intentar-ho

---

### Post by wgarcia on 2016-05-06
Genial que ho hagis volgut provar, al teu informe d'error ja hi ha 4 altres persones afectades i ningú no s'ha atrevit.

El problema ha estat en la segona ordre "wget", li has enganxat la següent ordre al final ("dpkg -i *.deb"), i aquesta segona ordre hauria de donar-se després. És a dir primer prémer intro després de l'ordre "wget ..." i després entrar "dpkg -i *.deb" i prémer intro.

---

### Post by josep7 on 2016-05-06
He vist l'error de copiar i enganxar, per això he rectificat el post.

He tornat a fer-ho i si que ha descarregat els paquets, però segueix igual el ratolí. De fet ara al grub hi tinc els dos i arrenca amb el nou 

Repassa el que diu el terminal si ara es tot correcte o no.

josep@josep-GJ306AA-ABE-m8175-es:~$ mkdir proves
mkdir: no s&#8217;ha pogut crear el directori «proves»: El fitxer ja existeix
josep@josep-GJ306AA-ABE-m8175-es:~$ cd proves
josep@josep-GJ306AA-ABE-m8175-es:~/proves$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb)
--2016-05-06 11:59:02--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb)
S'està resolent kernel.ubuntu.com (kernel.ubuntu.com)&#8230; 91.189.94.216
S'està connectant a kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80&#8230; conectat.
HTTP: s'ha enviat la petició, s'està esperant una resposta&#8230; 200 OK
Mida: 1066858 (1,0M) [application/x-debian-package]
S'està desant a: «linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb.1»

linux-headers-4.6.0 100%[===================>]   1,02M   730KB/s    in 1,4s    

2016-05-06 11:59:04 (730 KB/s) - s'ha desat «linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb.1» [1066858/1066858]

josep@josep-GJ306AA-ABE-m8175-es:~/proves$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb)
--2016-05-06 11:59:33--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc6-wily/linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb)
S'està resolent kernel.ubuntu.com (kernel.ubuntu.com)&#8230; 91.189.94.216
S'està connectant a kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80&#8230; conectat.
HTTP: s'ha enviat la petició, s'està esperant una resposta&#8230; 200 OK
Mida: 57595954 (55M) [application/x-debian-package]
S'està desant a: «linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb»

linux-image-4.6.0-0 100%[===================>]  54,93M   737KB/s    in 2m 34s  

2016-05-06 12:02:08 (365 KB/s) - s'ha desat «linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb» [57595954/57595954]

josep@josep-GJ306AA-ABE-m8175-es:~/proves$ sudo dpkg -i *.deb
[sudo] contrasenaya per a josep: 
S'està seleccionant el paquet linux-headers-4.6.0-040600rc6-generic prèviament no seleccionat.
(S'està llegint la base de dades&#8230; hi ha 181777 fitxers i directoris instal·lats actualment.)
S'està preparant per a desempaquetar linux-headers-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb&#8230;
S'està desempaquetant linux-headers-4.6.0-040600rc6-generic (4.6.0-040600rc6.201605012031)&#8230;
S'està seleccionant el paquet linux-image-4.6.0-040600rc6-generic prèviament no seleccionat.
S'està preparant per a desempaquetar linux-image-4.6.0-040600rc6-generic_4.6.0-040600rc6.201605012031_amd64.deb&#8230;
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
Done.
S'està desempaquetant linux-image-4.6.0-040600rc6-generic (4.6.0-040600rc6.201605012031)&#8230;
dpkg: problemes de dependències impedeixen la configuració de linux-headers-4.6.0-040600rc6-generic:
 linux-headers-4.6.0-040600rc6-generic depèn de linux-headers-4.6.0-040600rc6; tot i així:
  El paquet linux-headers-4.6.0-040600rc6 no està instal·lat.

dpkg: s'ha produït un error en processar el paquet linux-headers-4.6.0-040600rc6-generic (--install):
 problemes de dependències - es deixa sense configurar
S'està configurant linux-image-4.6.0-040600rc6-generic (4.6.0-040600rc6.201605012031)&#8230;
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
Error! Bad return status for module build on kernel: 4.6.0-040600rc6-generic (x86_64)
Consult /var/lib/dkms/bbswitch/0.8/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
update-initramfs: Generating /boot/initrd.img-4.6.0-040600rc6-generic
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/sw_method_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/sw_bundle_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/sw_nonctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/sw_ctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/gpccs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/gpccs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/fecs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/fecs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm206/acr/bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/sw_method_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/sw_bundle_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/sw_nonctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/sw_ctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/gpccs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/gpccs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/fecs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/fecs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm204/acr/bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/sw_method_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/sw_bundle_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/sw_nonctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/sw_ctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/gpccs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/gpccs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/fecs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/fecs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm200/acr/bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/sw_method_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/sw_bundle_init.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/sw_nonctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/sw_ctx.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/gpccs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/gpccs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/fecs_data.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/fecs_inst.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gm20b/acr/bl.bin for module nouveau
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
Generating grub configuration file ...
Avís: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
S'ha trobat una imatge de linux: /boot/vmlinuz-4.6.0-040600rc6-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.6.0-040600rc6-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.4.0-21-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.4.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fet
S'han trobat errors en processar:
 linux-headers-4.6.0-040600rc6-generic

---

### Post by wgarcia on 2016-05-06
Ha donat molts errors, però sembla que s'ha instal·lat. 

Has provat de reiniciar i mirar si es veu ara aquest nou nucli al menú del Grub, i si et deixa iniciar amb ell?

---

### Post by josep7 on 2016-05-06
Si, si he reiniciat. Hem surten els dos al grub i el nou està com ha predeterminat.
El ratolí continua enganyant-se al entrar a dins.

---

### Post by wgarcia on 2016-05-06
D'acord perfecte. Per acabar ara desinstal·la aquests nucli nou, entrant primer a l'antic (que suposo tindràs a "opcions avançades" i seguint després les instruccions de desinstal·lació) i després posa el següent comentari a l'informe d'error:

I installed and tried kernel 4.6.0-040600rc6-generic and the mouse is still stuck when I start my system.

Pensarem ara perquè no s'executen les ordres que activen el ratolí quan s'inicia el sistema, tot i que es posen a /etc/rc.local i s'habilita aquest fitxer d'inici. És un pegat, però de moment pot servir per no haver de donar aquestes ordres cada cop que s'inicia el sistema.

---

### Post by josep7 on 2016-05-06
josep@josep-GJ306AA-ABE-m8175-es:~$ uname -a
Linux josep-GJ306AA-ABE-m8175-es 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
josep@josep-GJ306AA-ABE-m8175-es:~$ sudo apt-get remove linux-headers-4.6.0-040600rc6-generic linux-image-4.6.0-040600rc6-generic
[sudo] contrasenaya per a josep: 
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
El paquet «linux-headers-4.6.0-040600rc6-generic» no està insta&#320;lat, així doncs no es suprimirà
Es SUPRIMIRAN els paquets següents:
  linux-image-4.6.0-040600rc6-generic
0 actualitzats, 0 nous a insta&#320;lar, 1 a suprimir i 0 no actualitzats.
Després d'aquesta operació s'alliberaran 218 MB d'espai en disc.
Voleu continuar? [S/n] s
(S'està llegint la base de dades&#8230; hi ha 187143 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant linux-image-4.6.0-040600rc6-generic (4.6.0-040600rc6.201605012031)&#8230;
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
update-initramfs: Deleting /boot/initrd.img-4.6.0-040600rc6-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.6.0-040600rc6-generic /boot/vmlinuz-4.6.0-040600rc6-generic
Generating grub configuration file ...
Avís: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
S'ha trobat una imatge de linux: /boot/vmlinuz-4.4.0-21-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.4.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fet
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]



El nou nucli ja es fora i ja he fet el comentari al informe d'error, però recorda que com ja he dit al missatge #30 ara ja no funciona

sudo rmmod usbhid
sudo modprobe usbhid


En el informe hi ha un comentari de que potser havia passat algo aixi a Fedora 23











                        



Same issue occurred in Fedora 23.
[https://bugzilla.redhat.com/show_bug.cgi?id=1277837](https://bugzilla.redhat.com/show_bug.cgi?id=1277837)

 Is this a bug of gnome-software or fwupd instead of linux.
If "/etc/xdg/autostart/gnome-software-service.desktop" is removed, then logout and login,
doesn't this problem occurred?

---

### Post by wgarcia on 2016-05-06
Sí, a l'informe suggereixen una cosa a provar:

Fer:
```
sudo mv /etc/xdg/autostart/gnome-software-service.desktop /etc/xdg/autostart/gnome-software-service.desktop.old
```
això el que fa és que evita que el "gnome-software", el programa per instal·lar programari nou, s'iniciï automàticament. S'hauria de donar aquesta ordre, reiniciar, i veure si torna a funcionar el ratolí. Si no funciona, o per deixar-lo com estava per si un cas, s'ha de revertir aquesta ordre:
```
sudo mv /etc/xdg/autostart/gnome-software-service.desktop.old /etc/xdg/autostart/gnome-software-service.desktop
```

Quant a que no funcionen les ordres que abans restablien el ratolí, has esborrat les línies que havies afegit a "/etc/rc.local"?

---

### Post by josep7 on 2016-05-06
=d> Podríem haver començat per aquí no?

Introdueixo en el terminal

josep@josep-GJ306AA-ABE-m8175-es:~$ sudo mv /etc/xdg/autostart/gnome-software-service.desktop /etc/xdg/autostart/gnome-software-service.desktop.old
[sudo] contrasenaya per a josep: 
josep@josep-GJ306AA-ABE-m8175-es:~$ 

reinicio

i el ratolí FUNCIONA NORMAL !!

---

### Post by josep7 on 2016-05-06
Vaig a provar-ho una estona i a engegar i parar uns cops per estar segur i posaré el solved.

Gràcies a tots per la paciència i ajuda.

---

