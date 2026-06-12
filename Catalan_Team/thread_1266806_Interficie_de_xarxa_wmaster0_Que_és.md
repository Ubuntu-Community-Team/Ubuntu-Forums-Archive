---
title: "Interficie de xarxa wmaster0 Que és?"
date: 2009-09-15
forum: Catalan Team
---

### Post by akyra on 2009-09-15
Bon dia a tothom

A resulta dels meus problemes amb la connexió wifi, vaig donant voltes i mirant configuracions a veure que pot ser que trigui molt a fer el ping inicial, he trobat fent un ip config, la interficie wmaster0.

Què es això? Pot ser que s'intenti connectar a aquesta interficie abans de la wlan0?
Jo només tinc una xarxa inahlambrica i una cablejada.

Salutacions.

---

### Post by akyra on 2009-09-15
Bé he continuat fent proves, i he fet un:
> sudo ifconfig wmaster0 down 
i el wifi ha deixat d'anar i no és conectava, i després un:
> sudo ifconfig wmaster0 up

i he tornat a connectar a la xarxa inhalambrica.

Segons he llegit per internet és com una connexió generica que el propi ubuntu crea i no ha d'haver cap problema.

El problema el segueixo tenint quan faig la primera connexió amb la xarxa ja que el ping tarda a respondre molt:
> jordi@jordi-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.3 icmp_seq=28 Destination Host Unreachable
From 192.168.2.3 icmp_seq=29 Destination Host Unreachable
From 192.168.2.3 icmp_seq=30 Destination Host Unreachable
From 192.168.2.3 icmp_seq=31 Destination Host Unreachable
From 192.168.2.3 icmp_seq=32 Destination Host Unreachable
From 192.168.2.3 icmp_seq=33 Destination Host Unreachable
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=46189 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=45188 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=44188 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=43188 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=42189 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=41187 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=40188 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=39188 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=38188 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=37189 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=36188 ms
64 bytes from 192.168.2.1: icmp_seq=12 ttl=64 time=35188 ms
64 bytes from 192.168.2.1: icmp_seq=13 ttl=64 time=34189 ms
64 bytes from 192.168.2.1: icmp_seq=14 ttl=64 time=33188 ms
64 bytes from 192.168.2.1: icmp_seq=15 ttl=64 time=32188 ms
64 bytes from 192.168.2.1: icmp_seq=48 ttl=64 time=2.44 ms
64 bytes from 192.168.2.1: icmp_seq=49 ttl=64 time=2.47 ms
64 bytes from 192.168.2.1: icmp_seq=50 ttl=64 time=2.79 ms


Ho he probat amb windows vista i fa la el ping a l'instant, així que puc descartar configuració del router.

És possible que el router es quedi esperant alguna cosa d'ubuntu?
En el router apareix com conexió inhalambrica establerta.

Espero els vostres comentaris.
Moltes gracies.

---

### Post by PatrickVogeli on 2009-09-15
pots enganxar el resultat de fer lspci -nn | grep Network ?

---

### Post by akyra on 2009-09-16
Ho podré fer aquesta nit.

També he observat que cada cert temps, aproximadament 30 minuts, se'm desconnecta del router i es torna a connectar.

Salutacions.

---

### Post by akyra on 2009-09-16
Hola, aquest es el resultat

> jordi@jordi-laptop:~$ lspci -nn | grep Network
14:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

Salutacions

---

### Post by PatrickVogeli on 2009-09-16
Doncs ho sento, no en tinc ni idea de que pot ser. Tens una Intel 5100, que en principi hauria de funcionar be. La meva novia té la mateixa tarjeta i funciona molt bé.

Podries provar a instal·lar un kernel d'aqui [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/)

A veure si amb aquest funciona.

Salut

---

### Post by akyra on 2009-09-17
Bé, avui ho he probar a l'oficina amb una xarxa inhalambrica i s'ha conectat a l'instant, igual que a casa, però ha fet el ping també a l'instant.

Cada vegada em sembla més que és culpa del router.
Els hi he enviat un e-mail a Belkin, a veure si consegueixo aclarir alguna cosa.

Salutacions.

---

### Post by akyra on 2009-09-18
Una pregunta Patrick.
Ahir em vaig connectar a dues xarxes inhalambricas amb wifi "b", i a casa tinc wifi "n".

Ho has probat tu amb wifi "n"?

D'altre banda Belkin m'ha dit que em canvia el router.

Salutacions.

---

### Post by akyra on 2009-09-22
Hola de nou.

Continuant amb els meus problems de wifi, segueixo tenint problemes amb la conexió amb el router de casa que funcina amb la banda "n" de wifi. Connectant-me a xarxes "b" no tinc cap problema i el ping es fa inmediatament i no tinc interrupcions.

Vaig probar amb el windows vista que porta l'ordinador per defecte, i també funciona bé.
Amb aquestes dades sembla que el problema el tinc amb el driver de la tarja de xarxa, una "Intel Corporation Wireless WiFi Link 5100".

He buscat per la xarxa i he arribat a l'enllaç de intel per actualitzar els drivers
[http://www.intellinuxwireless.org/?n=Downloads]("http://www.intellinuxwireless.org/?n=Downloads")
però abans de fer-ho volia saber si jo ja tenia instal·lat el driver que em diuen. 
Com puc mirar quin driver tinc instal·lat (Poder ja és el que tinc isntal·lat)?

D'altre banda les instruccions per actualitzar el driver, per mi no són gaire entenedores:
> 2. INSTALLATION

The iwlagn driver will look for the file iwlwifi-5000-2.ucode using the kernel's firmware_loader infrastructure.  In order to function correctly, you need to have this support enabled in your kernel.  When you configure the kernel, you can find this option in the following location:

        Device Drivers ->
                Generic Driver Options ->
                        Hotplug firmware loading support


You can determine if your kernel currently has firmware loader support by looking for the CONFIG_FW_LOADER definition on your kernel's
.config.

In addition to having the firmware_loader support in your kernel, you must also have a working hotplug and udev infrastructure configured.
The steps for installing and configuring hotplug and udev are very distribution specific.

Once you have the firmware loader in place (or if you aren't sure and you just want to try things to see if it works), you need to install  the microcode file into the appropriate location.

Where that appropriate location is depends (again) on your system
distribution.  You can typically find this location by looking in the hotplug configuration file for your distro:

	% grep \"^FIRMWARE_DIR\" /etc/hotplug/firmware.agent

This should give you output like:

	FIRMWARE_DIR=/lib/firmware

If it lists more than one directory, you only need to put the
microcode in one of them.  In the above example, installation is
simply:

	% cp iwlwifi-5000-2.ucode /lib/firmware

You can now load the driver (see the INSTALL and README.iwlwifi provided with the iwlwifi package for information on building and using that driver.)


Algú em pot orientar una mica més de com fer la instal·lació del driver? No tinc ni idea de com configurar el kernel i la veritat no sé ni per on començar a mirar per poder fer el que diuen.

Moltes gracies.

---

### Post by papapep on 2009-09-22
Akyra,  ja que està considerablement madura, jo provaria l'alpha 6 de la Karmic (9.10) en un live CD, a veure si funciona correctament la placa 5100 aquesta i t'estalvies fer invents.

---

### Post by akyra on 2009-09-22
Hola Papapep

Seria el mateix instal·lar els linux-backports que instal·lar el driver?


Provaré la Karmic també.

Gracies

---

### Post by akyra on 2009-09-22
Hola,

Amb el linux-backports no he notat cap diferencia.

El que he fet es copiar el driver de intel dins de /lib/firmware. En aquesta carpeta estava el mateix driver però la versió 1.

La meva pregunta és que haig de fer ara perquè utilitzi aquest driver en lloc dels altres? O poder ho fa ell solet?

Nota.- Confirmat, funciona malament amb una xarxa wifi "n". Amb una xarxa wifi "b" funciona a la primera.

Moltes gracies.

---

### Post by akyra on 2009-09-24
He provat l'alpha 6 de karmic, i fa com  un bucle quan estar a punt d'iniciar sessió, així que no ho he pogut probar.

Adeu

---

### Post by akyra on 2009-09-25
Hola.

He seguit investigant i he copiat els nou firmware d'intel (sudo cp iwlwifi-5000-ucode-8.24.2.12 (2)/iwlwifi-5000-2.ucode /lib/firmware"), però, quin és el següent pas per què utilitzi els nous drivers?.

He tret aquet resultats de la consola per si pot ajudar. Veig que encara està utilitzant els drivers antics "iwlwifi-5000-1.ucode" (em sembla...)

jordi@jordi-ubuntu:~$ uname -r
2.6.28-15-generic
jordi@jordi-ubuntu:~$ dmesg | grep iwl
[ 11.269247] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 11.269250] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 11.269335] iwlagn 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 11.269343] iwlagn 0000:14:00.0: setting latency timer to 64
[ 11.269375] iwlagn 0000:14:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 11.291255] iwlagn 0000:14:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 11.291325] iwlagn 0000:14:00.0: irq 2296 for MSI/MSI-X
[ 11.294866] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 23.622760] iwlagn 0000:14:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[ 23.710974] iwlagn 0000:14:00.0: loaded firmware version 5.4.1.16
[ 23.866506] Registered led device: iwl-phy0::radio
[ 23.866524] Registered led device: iwl-phy0::assoc
[ 23.866538] Registered led device: iwl-phy0::RX
[ 23.866551] Registered led device: iwl-phy0::TX
[ 54.361843] iwlagn 0000:14:00.0: index 0 not used in uCode key table.
[ 293.541276] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff88013e5ae740 tid = 0
[ 293.541332] iwlagn 0000:14:00.0: HW queue is empty
[14096.921265] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff88012c079740 tid = 0
[14096.921325] iwlagn 0000:14:00.0: HW queue is empty

Moltes gracies.

---

### Post by PatrickVogeli on 2009-09-29
Bones,

ara que tinc una mica de temps, comentar-te unes quantes coses.

1.- El fitxer de firmware no es un driver nou ni res per l'estil. Es només el firmware. Cada versió del driver pot requerir una versió o una altra del firmware. Es possible que una versio més antiga del driver no funcioni amb el firmware més nou i, a l'inversa, que un driver nou no vagi fi amb un firmware vell. Si el tens copiat a /lib/firmware, només has de trobar un driver que el demani, si existeix.

2.- El driver nou: has instal·lat el paquet linux-backports-modules-jaunty-generic?? Alla sembla que si hi ha uns drivers actualitzats. Un cop instal·lat aquest packet, nomes et cal reiniciar l'equip per utilitzar el driver nou. Aquest paquet també inclou un fitxer de firmware, no se la versió que sera, pero al reiniciar i fer un dmesg t'ho dira.

3.- Driver nou: una altra opcio que tens que es compilar-lo. El pots baixar d'aqui [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) que sembla ser que son drivers wifi de kernels meus nous que es poden compilar en kernels vells.

4.- Últim: prova amb un altre punt d'acces 'n' si tens la opcio. A belkin no li tinc massa confiança.

Per cert, un últim apunt. Suposo que quan fas les proves i tot això, estas connectat només tu sol no? Pensa que en les xarxes wifi, la connexió més lenta mana. Es a dir, si algu es conecta amb velocitat 'b', tothom va a 'b'. Si algu esta molt lluny i el punt d'acces ha de baixar la velocitat a 2Mb/s, tothom anira a 2Mb/s.

Salut i ja diras

---

### Post by akyra on 2009-09-30
Hola Patrick, ens trobem per forums del mon, collunut! :P

> 
1.- El fitxer de firmware no es un driver nou ni res per l'estil. Es només el firmware. Cada versió del driver pot requerir una versió o una altra del firmware. Es possible que una versio més antiga del driver no funcioni amb el firmware més nou i, a l'inversa, que un driver nou no vagi fi amb un firmware vell. Si el tens copiat a /lib/firmware, només has de trobar un driver que el demani, si existeix.
Moltes gracies per l'aclaració, però es que ja no sabia que fer per fer-lo funcionar i al final no m'aclaro.


> 2.- El driver nou: has instal·lat el paquet linux-backports-modules-jaunty-generic?? Alla sembla que si hi ha uns drivers actualitzats. Un cop instal·lat aquest packet, nomes et cal reiniciar l'equip per utilitzar el driver nou. Aquest paquet també inclou un fitxer de firmware, no se la versió que sera, pero al reiniciar i fer un dmesg t'ho dira.
Ja tinc instal·lat el inux-backports-modules-jaunty-generic, i també tinc activades les actualitzacions del jaunty-backports (suposo que s'ha de tindre). Des de que ho tinc instal·lat no m'ha actualitzat cap driver, com a minim que jo m'hagi donat compte.
> 
3.- Driver nou: una altra opcio que tens que es compilar-lo. El pots baixar d'aqui [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) que sembla ser que son drivers wifi de kernels meus nous que es poden compilar en kernels vells.

Si has llegit la meva resposta en l'altre forum hauràs vist que sembla que ja funciona des d'ahir a la nit.

> 4.- Últim: prova amb un altre punt d'acces 'n' si tens la opcio. A belkin no li tinc massa confiança.

> Per cert, un últim apunt. Suposo que quan fas les proves i tot això, estas connectat només tu sol no? Pensa que en les xarxes wifi, la connexió més lenta mana. Es a dir, si algu es conecta amb velocitat 'b', tothom va a 'b'. Si algu esta molt lluny i el punt d'acces ha de baixar la velocitat a 2Mb/s, tothom anira a 2Mb/s.
Això que si no ho sabia!!. Doncs és per això que ahir anava tant lent, ja que tenia connectada la impressora que va per wifi, pràcticament segur. Però pensava que la velocitat només baixava si et volies comunicar amb l'equip que anés més lent, però si no, funcionaria tant ràpid com pogués.

Ara mateix estic al costat del router i estic funcionant a 60Mbps, i d'aquí no he passat.

> jordi@jordi-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Jordi_Belkin_N1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:C6:1C:F8   
          Bit Rate=60 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/70  Signal level=-7 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.


Moltes gracies
En el següent post escriure la solució que he trobat, per si hi ha algun altre que tingui problemes semblants.

Salut.

---

### Post by akyra on 2009-09-30
Hola a tots,

Bé, sembla que ja funciona l'ordinador connectat a un router de banda "n", i volia explicar el que finalment he fet,

Bé fa dues setmanes que vaig parlar amb el servei tècnic de Belkin per si el problema podia ser cosa del router, i ahir em van respondre que actualitzes el firmware del router des d'una pàgina seva.
Així ho vaig fer i automàticament em va començar a funcionar el ping i pel moment no es talla la comunicació amb el router.

L'únic tema que em queda pendent és que la velocitat de conexió no em pasa de 60Mbps estan al costat del router, o com ara a 10m i amb dos parets al mig (per cert, amb la mateixa velocitat que a windows vista) i m'agradaria saber el perquè. També m'he posat en contacte amb Belkin, no sigui que sigui cosa seva.

Salut.

Nota.- Podria-ho posar l'etiqueta de SOLVED

---

### Post by CrIlat on 2010-10-10
Hola nois, després d'estar llegint com unes 3 hores i no treure res clar o exposo aqui per que tens la mateixa Intel Wireless WiFi Link 5100, a veure si em ser explicar per que m'enteneu lo millor possible.

Fa un parell de setmanes em funcionaba correctament la Intel Wireless WiFi Link 5100 amb lucid 10.04 i amb wifi "N" nomes tinc posat al router que vagi amb wifi N. La cosa es que des de que vaig posar la Alpha3 de maverick ja no em funciona el wifi N, avui e fet una instal·lació nova, des de 0 i tampoc la trova, en canvi tinc un usb amb wifi N i aquest funciona correctament.    

No se que pot esta passant e mirat al /lib/firmware i allà i son el drivers que indica akyra.

sergi@Sergi-U400:~$ uname -r 
2.6.35-22-generic
sergi@Sergi-U400:~$ dmesg | grep iwl
[   10.137060] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.137063] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.137128] iwlagn 0000:08:00.0: enabling device (0000 -> 0002)
[   10.137137] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.137148] iwlagn 0000:08:00.0: setting latency timer to 64
[   10.137203] iwlagn 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.159837] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.159919] iwlagn 0000:08:00.0: irq 45 for MSI/MSI-X
[   10.196993] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12
[   10.210480] phy0: Selected rate control algorithm 'iwl-agn-rs'
sergi@Sergi-U400:~$ 

  Tambée de dir que no tinc instal·lat el **linux-backports-modules-wirelees-maverick-generic**  ni el** linux-backports-modules-net-maverick-generic **per que no se quin e de posar o que tinc que fer. Gracies espero les vostres respostes.Si necessiteu mes dades o dieu, un salut.

Hola de nou i estat provant amb el router i e posat 11g only i funciona correctament , també e posat 11b only i també funciona correctament , poso 11bgn mixed i funciona correctament , però ara be la mare dels ous poso 11n only com ho tenia abans i no connecta , te de ser un problema del driver wifi n del intel ?.

Quedaria aixi la cosa:

1- 11g Only connecta correctament.
2- 11b Only connecta correctament.
3- 11bgn Only connecta correctament.
**4- 11n Only No connecta ( Amb Lucid 10.04 funcionava correctament).**


P.D. Ja se que el post te un any però es el que e trobat per no obrir un altre de nou.

---

