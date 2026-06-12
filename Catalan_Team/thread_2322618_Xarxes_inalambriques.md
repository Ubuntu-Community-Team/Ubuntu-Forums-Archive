---
title: "Xarxes inalambriques"
date: 2016-04-29
forum: Catalan Team
---

### Post by guiobaix on 2016-04-29
Bon dia a tothom!

soc un nou usuari d'ubuntu (i pel poc temps que hi porto, puc dir que molt feliç). L'unic problema que tinc amb el sistema es que no trobo manera de que em connecti via wifi. Tot el que veig ´es que "les xarxes inalambriques no estan habilitades". Per molt que faci clic a habilitar inalambrica, no hi ha manera. Suposo que tinc algun problema amb els drivers del dispositiu pero, tot i que he llegit els dubtes plantejats al forum i que he provat unes quantes solucions no me n'ensurto....

aquesta es la info que tinc

~$ lspci
00:00.0 Host bridge: Intel Corporation Device 2280 (rev 21)
00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)
00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 21)
00:13.0 SATA controller: Intel Corporation Device 22a3 (rev 21)
00:14.0 USB controller: Intel Corporation Device 22b5 (rev 21)
00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 21)
00:1b.0 Audio device: Intel Corporation Device 2284 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 22c8 (rev 21)
00:1c.1 PCI bridge: Intel Corporation Device 22ca (rev 21)
00:1c.2 PCI bridge: Intel Corporation Device 22cc (rev 21)
00:1c.3 PCI bridge: Intel Corporation Device 22ce (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 21)
00:1f.3 SMBus: Intel Corporation Device 2292 (rev 21)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

Moltes gracies per la vostra ajuda!

---

### Post by wgarcia on 2016-04-29
guiobaix,  bona benvinguda a Ubuntu si comences amb problemes de wifi!

Sembla que la targeta gràfica que tens té un problema, el controlador per a Linux no selecciona bé l'antena i per tant el sistema no veu els punts d'accés wifi. Encara no està incorporat al nucli de Linux un nou controlador proveït per la comunitat que ho arregla, l'acaben d'aconseguir, i primer ha d'entrar al nucli més recent de desenvolupament (4.7) i després possiblement anirà arribant als nuclis més estables (el de l'última versió d'Ubuntu és el 4.4). 

Es pot fer servir ja aquest nou controlador, però s'han de seguir una sèrie de passos que si no tens costum de treballar a Linux poden ser difícils. Hi ha un blog on ho explica pas per pas: [http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/](http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/), que transcric en català aquí.

Els passos a seguir són:

1) Obre una terminal (entra "terminal" al tauler o busca terminal als menús, segons quin escriptori tinguis)

2) Instal·la tots els programes necessaris per construir el controlador entrant la següent ordre a la terminal (després de cada ordre prem "Intro"):

```
sudo apt-get install build-essential
```

3) Entra ara la següent ordre a la terminal:

```
iwconfig
```

Mira a la segona línia de la sortida d'aquesta ordre, la primera paraula que comença amb "wlp" i anota't el número que veus, per exemple si fos "wlp13s0" aquest seria el teu número.

4) Baixa't el codi del controlador de: [https://github.com/lwfinger/rtlwifi_new/archive/rock.new_btcoex.zip](https://github.com/lwfinger/rtlwifi_new/archive/rock.new_btcoex.zip), directament a aquesta màquina si tens connexió per cable o a una altra amb connexió Internet i copia-la a una carpeta d'aquesta màquina, la terminal s'obre a la teva carpeta d'inici, per exemple.

5) Descomprimeix el zip amb:
```
unzip rock.new_btcoex.zip
```

6) Entra a la carpeta on està el codi:
```
cd rtlwifi_new-rock.new_btcoex
```

7) Entra l'ordre per construir el controlador:
```
make
```

8) Instal·la el nou controlador
```
sudo make install
```

9) Habilita el controlador perquè l'usi el sistema:
```
sudo modprobe -rv rtl8723be
```

10) Canvia l'antena que utilitza la targeta wifi:
```
sudo modprobe -v rtl8723be ant_sel=2
```

11) Per iniciar la targeta wifi entra ara:
```
sudo ip link set wlp13s0 up
```
on has de substituir "wlp13s0" pel que hagis vist al pas 3). 

12) Per buscar les xarxes sense fil, ara pot entrar l'ordre:
```
sudo iw dev wlp13s0 scan
```
i si tot ha anat bé hauria de veure la teva.

13) Per fer els canvis permanents:
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```

---

### Post by guiobaix on 2016-04-30
Wow! no m'ho puc ni creure! quina eficiència de fòrum! Molt agraït per  la resposta i per les indicacions! Tot molt fàcil i ho he pogut seguir  sense cap problema. Tot i això, el resultat és una mica "incert"... em  segueix passant el mateix que abans. Hi ha hagut un moment d'esperança  que ha trobat les xarxes inalàmbriques però això només ho fa si estic  connectat per cable. Quan li demano activar les xarxes inalàmbriques  desapareixen tot el nom de les xarxes wifi i s'acaba la història.

lspci
00:00.0 Host bridge: Intel Corporation Device 2280 (rev 21)
00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)
00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 21)
00:13.0 SATA controller: Intel Corporation Device 22a3 (rev 21)
00:14.0 USB controller: Intel Corporation Device 22b5 (rev 21)
00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 21)
00:1b.0 Audio device: Intel Corporation Device 2284 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 22c8 (rev 21)
00:1c.1 PCI bridge: Intel Corporation Device 22ca (rev 21)
00:1c.2 PCI bridge: Intel Corporation Device 22cc (rev 21)
00:1c.3 PCI bridge: Intel Corporation Device 22ce (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 21)
00:1f.3 SMBus: Intel Corporation Device 2292 (rev 21)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

aquesta és la situació actual.

Moltes gràcies per l'ajuda i la dedicació! 

@guiobaix

---

### Post by wgarcia on 2016-05-01
Suposo que si en un moment ha vist les xarxes inalàmbriques, vol dir que el controlador ara està bé. També suposo que no hi ha cap tecla de hardware que estigui inhabilitant l'antena wifi. Una altra cosa que es pot provar és mirar si hi ha algun element de programari que estigui bloquejant la connexió inalàmbrica, i per això es pot donar l'ordre:

```
rfkill list all
```

i et mostrarà com veu el sistema l'estat de les connexions de xarxa.

---

### Post by guiobaix on 2016-05-24
Res... no hi ha manera. Avui ho he tornat a intentar seguint tots els passos de @wgarcia i res de res... al final em surt això

rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



m'hauré d'acostumar a viure amb un cable connectat :S

gràcies igualment!

---

### Post by wgarcia on 2016-05-24
Fixa't que posa el wifi (Wireless LAN) està "Soft blocke: yes", vol dir que està bloquejat per programari, normalment un controlador incorrecte. El primer que es pot provar és si es deixa desbloquejar, amb:

```
sudo rfkill unblock wifi
```

---

### Post by guiobaix on 2016-05-24
segueix igual - també he intentat deshabilitar un controlador desconegut i tornar-ho a provar - per si serveix de res i no... mateixes condicions :S

sudo rfkill unblock wifi
[email]enric@guiobaix:~/Baixades/rtlwifi_new-rock.new[/email]_btcoex$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


serà que em té mania? XD

---

### Post by wgarcia on 2016-05-26
Sembla clarament un problema de controlador de la targeta wifi, no està bloquejada per maquinari però si per programari, i això ho diu quan no li agrada el controlador que té. Per veure quin és pots fer:
```
sudo lshw -C network
```
a una terminal.

---

