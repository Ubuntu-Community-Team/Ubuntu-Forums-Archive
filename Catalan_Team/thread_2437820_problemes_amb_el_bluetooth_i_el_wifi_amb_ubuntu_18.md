---
title: "problemes amb el bluetooth i el wifi amb ubuntu 18.04 LTS"
date: 2020-03-01
forum: Catalan Team
---

### Post by negu on 2020-03-01
Hola a tots, 
m'he canviat l'ordinador i m'hi he posat l'ubuntu 18.04, el fet és que el bluetooth no m'el detecta per enlloc, ni em deixa desbloquejar-lo ni es fan visibles els aparells... em dona la impressió que ha de ser alguna cosa de drivers de l'ordinador, ja que em sembla motl estrany. 
Si li dono a la consola la ordre 

[COLOR=#686868][FONT=&amp]
sudo rfkill list

[/FONT][/COLOR]
No m'apareix el bluetooth, per això crec ha de ser cosa de drivers, l'ordinador en qüestió és un HP 250 I7-8565U

i l'altte problema, és que percebo que la wifi em va més lenta amb l'ubuntu que amb el windows... és normal això? com es pot solucionar???

moltes gràcies

---

### Post by CelticWarrior on 2020-03-01
cal identificar el mòdul Wi-Fi:

```
lspci -knn | grep Net -A3

```

---

### Post by negu on 2020-03-01
el que m'apareix és això:


[COLOR=#000000]joan@joan-HP-250-G7-Notebook-PC:~$ lspci -knn | grep Net -A3
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
	Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
	Kernel driver in use: rtl8821ce
	Kernel modules: 8821ce
03:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd Device [144d:a809]
[/COLOR]

---

### Post by CelticWarrior on 2020-03-01
Intenta reinstal·lar el driver disponible en els repositoris oficials:

```
sudo apt install --reinstall rftl8821ce-dkms
```

Hi ha una versió més actual, però requereix compilació des del source code.

---

### Post by negu on 2020-03-02
doncs no em deixa... m'apareix això:

[COLOR=#000000]Code:
[FONT=Verdana]joan@joan-HP-250-G7-Notebook-PC:~$ sudo apt install --reinstall rftl8821ce-dkms[/FONT]
[FONT=Verdana][sudo] contraseña para joan: [/FONT]
[FONT=Verdana]Leyendo lista de paquetes... Hecho[/FONT]
[FONT=Verdana]Creando árbol de dependencias       [/FONT]
[FONT=Verdana]Leyendo la información de estado... Hecho[/FONT]
E: No se ha podido localizar el paquete rftl8821ce-dkms[FONT=Verdana]Hi [/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-03-02
He provat en Ubuntu 19.10 i és el mateix driver que tinc jo. El mateix paquet està disponible a "bionic-updates" (per al 18.04): [https://packages.ubuntu.com/bionic-updates/rtl8821ce-dkms](https://packages.ubuntu.com/bionic-updates/rtl8821ce-dkms) 
Cal tenir aquest repositori habilitat. 

Però el teu cas és que el Bluetooth no va i relativament a aquest problema ja hi ha un error (bug) reportat: [https://bugs.launchpad.net/ubuntu/+source/rtl8821ce/+bug/1853665](https://bugs.launchpad.net/ubuntu/+source/rtl8821ce/+bug/1853665)

Sembla ser que el problema té alguna cosa a veure amb un kernel específic Ho has intentat arrencar amb un kernel de versió anterior?

Jo de moment tinc el 5.3.0-40-generic i em va bé la WiFi i el Bluetooth. Tampoc he tingut problemes amb versions anteriors.

En el teu cas jo provaria amb un altre nucli per en tot cas.

---

### Post by negu on 2020-03-02
Moltes gràcies per la resposta (i per la paciència) CelticWarrior 

[B][I]He provat en Ubuntu 19.10 i és el mateix driver que tinc jo. El mateix paquet està disponible a "bionic-updates" (per al 18.04): [https://packages.ubuntu.com/bionic-updates/rtl8821ce-dkms](https://packages.ubuntu.com/bionic-updates/rtl8821ce-dkms) 
Cal tenir aquest repositori habilitat.[/I][/B]
He instalat el paquet i he actualitzat la consola... amb això n'hi ha prou?? disculpa però aquests protocols em costen una mica....

[I][B]Però el teu cas és que el Bluetooth no va i relativament a aquest problema ja hi ha un error (bug) reportat: [https://bugs.launchpad.net/ubuntu/+source/rtl8821ce/+bug/1853665](https://bugs.launchpad.net/ubuntu/+source/rtl8821ce/+bug/1853665)
Sembla ser que el problema té alguna cosa a veure amb un kernel específic Ho has intentat arrencar amb un kernel de versió anterior?[/B][/I]

El fet és que tinc l'ordinador des de fa 1 setmana i vaig demanar que m'instalessin l'ubuntu a la botiga on el vaig comprar, perquè les darreres vegades que ho havia fet jo havia tingut problemes, he estat mirant-me el la pàgina que m'has passat i la veritar és que em costa una mica entendre els passos a seguir... em va una mica gran, perquè no ho entenc gaire... potser tinc que investigar una mica més, però de moment no em detecta el bluetooth, a veure si ho puc solucionar d'alguna manera

***En el teu cas jo provaria amb un altre nucli per en tot cas.*** a que et refereixes amb això??

Disculpa tanta ignorància però em costa una mica el tema ubuntu... fa anys que vaig amb ell i ara feia un parell d'anys que no l'utilitzava i m'en adono que realment és un xic complicat per a mi... però no vull passar per windows ni de conya..

---

