---
title: "ubuntu karmic: controlar ventiladors"
date: 2009-12-02
forum: Catalan Team
---

### Post by grenyut on 2009-12-02
Hola,

he buscat molt, he instal·lat el lm-sensors, he corregut amb èxit el sensors-detect i l'ordre sensors em dona el resultat adequat. Pero quan intento activar el fancontrol no funciona, l'arxiu /etc/fancontrol està buit (bueno, només hi ha els encapçalaments, però sense dades), i el pwmconfig m'accelera el ventilador de la CPU a tope i després el deixa sempre així.
Me n'he adonat que la carpeta thermal_zone està buida. És normal?

L'ordinador té 4 ventiladors, el de la CPU, el del darrera gros i dos laterals. Voldria veure si es pot reduir la velocitat dels ventiladors per que faci menys soroll (el de la CPU és l'únic que varia, ara per ara, de forma automàtica)

Algun consell?

---

### Post by guillemsola on 2009-12-04
Hola

pwmconfig t'ha d'accelerar el ventilador a tope i després el va executant a 90%, 80%... si no pots fer això potser no pots controlar la velocitat dels ventiladors. No totes les plaques o suporten o tenen drivers per linux.

Has mirat que a la bios no tinguis algun comportament definit que anul·li el control per software?

Jo recordo que al final vaig acabar editant l'arxiu /etc/fancontrol a mà ja que m'era més senzill per aconseguir-ho al meu gust. Ho vaig deixar així

> 
INTERVAL=10
FCTEMPS=hwmon1/device/pwm1=hwmon0/device/temp2_input
FCFANS= hwmon1/device/pwm1=hwmon1/device/fan1_input
MINTEMP=hwmon1/device/pwm1=40
MAXTEMP=hwmon1/device/pwm1=65
MINSTART=hwmon1/device/pwm1=0
MINSTOP=hwmon1/device/pwm1=80
MAXPWM=hwmon1/device/pwm1=150

bàsicament el que hi diu és que en funció de temp2_input es controlarà la velocitat de fan1_input, després defineix la temp min i max i la velocitat min i max.

Suposo que has vist que el pwmconfig s'ha d'executar com a root per tenir permisos per escriure a /etc/fancontrol.

---

