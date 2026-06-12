---
title: "Problemes al carregar l'escriptori"
date: 2009-06-04
forum: Catalan Team
---

### Post by akyra on 2009-06-04
Bon dia,

Fa un parell de dies que vaig observant que engego l'ordinador sense problemes, però una vegada introduit el login i el password, quan està a punt de veures l'escriptori la pantalla es queda en negre o amb barres grises verticals (el tema de fons es gris, i no l'he canviat des de fa un mes) i no puc veure res.
Si faig ctrl + alb +bcksp no fa res i de reiniciar-lo amb el botó d'engegar.

Aquest matí, el primer cop que l'engegat s'ha quedat la pantalla en negre, l'he reiniciat i s'ha quedat amb barres grises veticals, l'he tornat a reiniciar i s'ha reiniciat bé, però no s'ha connectat a la xarxa wifi, em demana tornar a entrar la contrasenya de la xarxa i encara que li doni no es connecta fins que no torno a inificar l'ordinador. He copiat el dirctori /var/log/ per si he de treure algun fitxer i l'he tornat a reiniciar i tot a funcionat bé.
Faig saber que tinc carregats els efectes de compiz.

El problema del wifi em pasa sovint i tornant a reiniciar em va bé, però tot està passant a l'iniciar l'ordinador.

Pot ser algun problema amb els screenlets que càrrega a l'inici?
En quin fitxer log ho puc mirar el que pasa?
Té alguna cosa que veure amb la calitat del color (24 bits)?

Per cert ahir vaig pasar la partició /home de ext3 a ext4 sense problemes, vaig seguir el que va dir papapep en el seu blog [http://extralinux.net/?q=node/209]("http://extralinux.net/?q=node/209")
i m'ha anat perfecte, amb la diferencia que no m'ha donat errors quan he fet:
 **tune2fs -O extents,uninit_bg,dir_index /dev/sda4**
i després em deia que executes
**e2fsck -pDf /dev/sda4**

en lloc de 
**fsck -pDf /dev/sda4**
aquí si que ha correcte errors.

Salutacions

---

### Post by oriolsbd on 2009-06-04
Hola,

Pots veure els missatges que ha donat el sistema a l'arranc executant la següent comanda:
```
dmesg
```
Salut!

---

### Post by akyra on 2009-06-04
Sí, pero em sembla que el "dmesg" dóna tots els valors quan arrencas i es reseteja quan tornes a apagar, i com jo no el puc veure quan se'm queda la pantalla en negre, em sembla que no em serveix de gaire.

El que sí que he trobat és en el fitxer **"wpa_supplicant.log"** el següent per la connexió Wifi:
> Trying to associate with 00:1c:df:c6:1c:f8 (SSID='Jordi_Belkin_N1' freq=2472 MHz)
Authentication with 00:1c:df:c6:1c:f8 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:df:c6:1c:f8 (SSID='Jordi_Belkin_N1' freq=2472 MHz)
Authentication with 00:1c:df:c6:1c:f8 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:df:c6:1c:f8 (SSID='Jordi_Belkin_N1' freq=2472 MHz)
Authentication with 00:1c:df:c6:1c:f8 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:df:c6:1c:f8 (SSID='Jordi_Belkin_N1' freq=2472 MHz)
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:00:00:00:00:00 timed out.
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 


i he trobat això en el "debug"
> Jun  4 07:00:57 jordi-laptop kernel: [    1.240942] pci 0000:01:05.0: Boot video device
Jun  4 07:00:57 jordi-laptop kernel: [    1.241068] pcieport-driver 0000:00:04.0: setting latency timer to 64
Jun  4 07:00:57 jordi-laptop kernel: [    1.241140] pci_express 0000:00:04.0:pcie00: allocate port service
Jun  4 07:00:57 jordi-laptop kernel: [    1.241154] pci_express 0000:00:04.0:pcie02: allocate port service
Jun  4 07:00:57 jordi-laptop kernel: [    1.295229] sata_sil 0000:00:12.0: version 2.3
Jun  4 07:00:57 jordi-laptop kernel: [    2.008545] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  4 07:00:57 jordi-laptop kernel: [    2.008816] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  4 07:00:57 jordi-laptop kernel: [    2.137304] pata_atiixp 0000:00:14.1: setting latency timer to 64
Jun  4 07:00:57 jordi-laptop kernel: [    2.487641] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jun  4 07:00:57 jordi-laptop kernel: [    3.081230] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jun  4 07:00:57 jordi-laptop kernel: [    3.738905] PM: Resume from partition 8:3
Jun  4 07:00:57 jordi-laptop kernel: [    3.738907] PM: Checking hibernation image.
Jun  4 07:00:57 jordi-laptop kernel: [    3.739095] PM: Resume from disk failed.
Jun  4 07:00:57 jordi-laptop kernel: [    4.348324] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d0000001234]
Jun  4 07:00:57 jordi-laptop kernel: [   11.607144] phy0: Selected rate control algorithm 'pid'
Jun  4 07:00:57 jordi-laptop kernel: [   12.056103] /dev/vmmon[1712]: Module vmmon: registered with major=10 minor=165
Jun  4 07:00:57 jordi-laptop kernel: [   12.056122] /dev/vmmon[1712]: Initial HV check: anyNotCapable=0 anyUnlocked=1 anyEnabled=1 anyDisabled=0
Jun  4 07:00:57 jordi-laptop kernel: [   12.056128] /dev/vmmon[1712]: HV check: anyNotCapable=0 anyUnlocked=1 anyEnabled=1 anyDisabled=0
Jun  4 07:00:57 jordi-laptop kernel: [   12.056130] /dev/vmmon[1712]: Module vmmon: initialized
Jun  4 07:01:08 jordi-laptop kernel: [   25.329641] wlan0: direct probe to AP 00:23:54:a7:91:19 try 1
Jun  4 07:01:08 jordi-laptop kernel: [   25.532053] wlan0: direct probe to AP 00:23:54:a7:91:19 try 2
Jun  4 07:01:08 jordi-laptop kernel: [   25.728059] wlan0: direct probe to AP 00:23:54:a7:91:19 try 3


no sé si té alguna cosa que indiqui res.

Gracies

---

### Post by akyra on 2009-06-05
Bé em sembla que el problema del wifi el tinc solucionat (espero), he tingut que habilitar els controlador alternatiu Atheros Madwifi, a veure si va bé.

El tema de la pantalla pel moment no m'ha tornat a pasar. poder és un problema del compiz, però no sé com trobar-ho, si algú té alguna idea.

Salutacions

---

### Post by akyra on 2009-06-05
Sembla que encara no anem del tot bé.

Veig que quan la cobertura del wifi està en un 50%, comença a anar molt lenta la velocitat de connexió i les pàgines en molts casos no s'arriben a carregar.

De que pot ser? Si pot fer alguna cosa.

Gracies.

---

### Post by oriolsbd on 2009-06-05
Tens engegat algun programa de compartició de fitxers p2p? Amule, mldonkey, ...? Prova d'aturar-lo, i a veure si és això.

Salut!

---

### Post by akyra on 2009-06-05
No, res de res.

Poder és un problema del controlador de la wifi que sigui menys potent. Poder ho provaré des de windows a veure si la potencia del senyal és el mateix i la navegació funciona.

Gracies.

---

### Post by akyra on 2009-06-07
Bé, la connexió wifi és connecta a la primera i sembla que el problema de no connexió ja està solventat.

Per altre banda he comprobat la diferència de potència de senyal wifi rebuda en l'ordinador. Amb ubuntu (52%) i en el mateix lloc però amb windows xp (excelente, o pràcticament el 100%). Això crec que significa que els controladors del wifi d'Ubuntu donen menys voltatge a la tarja wifi i fa que la recepció sigui més baixa que el controlador utilitzat per windows, ja que el senyal que envia el router sempre és el mateix.

El problema de l'escriptori no m'ha tornat a passar, així que no tinc ni idea que ha pogut pasar.

Si algú té alguna idea de com augmentar la potència del senyal de wifi de recepció de l'ordinador, que ho escrigui.

Poder té que veure amb la gestió d'energia...

Moltes gracies.

---

### Post by akyra on 2009-06-08
He probat una altre cosa i és treure les dades del syslog, bé en concret del syslog.0, i em dóna com a resultat just abans de que surtin les barres verticals grises (sí, aquest matí han tornat) tot de coses relacionades amb la conexió wifi.
El que surt és el següent:

> Jun  8 07:00:01 jordi-laptop /USR/SBIN/CRON[3928]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  8 07:00:01 jordi-laptop /USR/SBIN/CRON[3930]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jun  8 07:00:11 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  inactive -> scanning 
Jun  8 07:00:17 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> inactive 
Jun  8 07:00:31 jordi-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 6 -> 9 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) failed for access point (WebSTAR) 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Marking connection 'Auto WebSTAR' invalid. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) failed. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 9 -> 3 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): deactivating device (reason: 0). 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) starting connection 'Jordi_Belkin_ip_estatica' 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 3 -> 4 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'Jordi_Belkin_ip_estatica' has security, but secrets are required. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 5 -> 6 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 6 -> 4 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0/wireless): connection 'Jordi_Belkin_ip_estatica' has security, and secrets exist.  No new secrets needed. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Config: added 'ssid' value 'Jordi_Belkin_N1' 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jun  8 07:00:31 jordi-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  8 07:00:31 jordi-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Jun  8 07:00:31 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  inactive -> scanning 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> associating 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  associating -> associated 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  associated -> 4-way handshake 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  4-way handshake -> group handshake 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  (ath0): supplicant connection state:  group handshake -> completed 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Jordi_Belkin_N1'. 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  (ath0): device state change: 5 -> 7 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
Jun  8 07:00:33 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
Jun  8 07:00:33 jordi-laptop avahi-daemon[2800]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.2.2.
Jun  8 07:00:33 jordi-laptop avahi-daemon[2800]: New relevant interface ath0.IPv4 for mDNS.
Jun  8 07:00:33 jordi-laptop avahi-daemon[2800]: Registering new address record for 192.168.2.2 on ath0.IPv4.
Jun  8 07:00:34 jordi-laptop NetworkManager: <info>  (ath0): writing resolv.conf to /sbin/resolvconf 
Jun  8 07:00:34 jordi-laptop NetworkManager: <info>  (ath0): device state change: 7 -> 8 
Jun  8 07:00:34 jordi-laptop NetworkManager: <info>  (ath0): writing resolv.conf to /sbin/resolvconf 
Jun  8 07:00:34 jordi-laptop NetworkManager: <info>  Policy set 'Jordi_Belkin_ip_estatica' (ath0) as default for routing and DNS. 
Jun  8 07:00:34 jordi-laptop NetworkManager: <info>  Activation (ath0) successful, device activated. 
Jun  8 07:00:34 jordi-laptop NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  8 07:00:35 jordi-laptop ntpdate[4701]: adjust time server 91.189.94.4 offset 0.194225 sec


Tinc un ordinador Fujitsu Siemens AMD Turion DualCore con 2GB de RAM i una tarja gráfica ATI Radeon Xpress 1100, per si serveix d'alguna cosa.

Per la tarja gráfica utilitzu els controladors lliures, ja que no hi ha de privatius amb jaunt, y per la tarja wifi el "madwifi alternatiu", ja que amb el que venia per defecte vaig començar a tenir aquest problemes.

Si algú veu alguna cosa, li estaré molt agraït.

---

### Post by PatrickVogeli on 2009-06-09
podries provar a instal·lar el paquet linux-backports-modules-jaunty, deshabilitar el madwifi alternatiu i reiniciar, a veure si així et soluciona el problema.

Segurament el driver de la teva tarjeta encara esta bastant verd i per això té aquest rendiment tan dolent.

salut!

---

