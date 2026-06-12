---
title: "A l'engegar després d'«Atura temporalment», no es veu res"
date: 2012-10-17
forum: Catalan Team
---

### Post by jinglada on 2012-10-17
Benvolguts ubunteros:

En un portàtil Easy Note TM86 de Packard Bell, Intel Core i3-330M, Intel HD Graphics, 4GB, 15,6" 16:9 HD LED LCD, Windows 7, he instal·lat l'Ubuntu 12.04 LTS (Alternate) i quan engego després de l'«Atura temporalment»  no es veu clar a la pantalla; tot queda en un fons obscur il·legible, com si hagués perdut la llum del tot. Em sembla que no te res a veure amb fn+f6, la brillantor; almenys no canvia res tocant aquestes tecles.

---

### Post by albandy on 2012-10-17
Simplement per provar, sense guardar la configuració, prova arrencant una vegada amb el paràmetre del grub noapic

Es a dir, la linia del grub hauria de quedar del pal .... noapic backlight=vendor ..........

---

### Post by jinglada on 2012-10-17
> **albandy said:**
> Simplement per provar, sense guardar la configuració, prova arrencant una vegada amb el paràmetre del grub noapic

Es a dir, la linia del grub hauria de quedar del pal .... noapic backlight=vendor ..........

Vols dir en el fitxer /etc/default/grub que hauria de quedar així?:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux noapic backlight=vendor"
GRUB_CMDLINE_LINUX=""
```

---

### Post by albandy on 2012-10-17
No, vull dir que l'afegeixis durant l'arrencada, el menú del grub et permet afegir paràmetres.

Més que res, per que si no funciona, no cal modificar cap fitxer.

---

### Post by jinglada on 2012-10-17
> **albandy said:**
> No, vull dir que l'afegeixis durant l'arrencada, el menú del grub et permet afegir paràmetres.

Més que res, per que si no funciona, no cal modificar cap fitxer.

No ho havia fet mai. He premut 'e' per editar, he posat 'noapic' davant de 'backlight=vendor' i he prenmut F10 per arrancar.

Un cop arrancat he triat 'Atura temporalment' i al reactivar es veu el menú en un fons obscur il·legible, com abans :-(

---

### Post by kimet on 2012-10-17
No se si "Atura temporalment" es el mateix que hibernar o suspendre a disc.
Si es així pots mirar a var/log/pm-suspend a veure si et dona alguna idea del que esta passant, de vagades m'ha passat que alguna aplicació no hiberna correctament.


Salut.

---

### Post by albandy on 2012-10-18
Que et retorna això?
ls /sys/class/backlight

---

### Post by jinglada on 2012-10-18
> **albandy said:**
> Que et retorna això?
ls /sys/class/backlight

Gràcies albandy. Em surt això:

joan@ubuntu:~$ ls /sys/class/backlight
acpi_video0  acpi_video1  intel_backlight
joan@ubuntu:~$

---

### Post by jinglada on 2012-10-18
> **kimet said:**
> No se si "Atura temporalment" es el mateix que hibernar o suspendre a disc.
Si es així pots mirar a var/log/pm-suspend a veure si et dona alguna idea del que esta passant, de vagades m'ha passat que alguna aplicació no hiberna correctament.


Salut.

Gràcies kimet. El meu pm-suspend.log té 3895 línies i n'hi ha moltes com ara les següents, que he copiat de les 80 primeres línies:

> Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...**Failed**.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: **No such file or directory**

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: **not applicable.**
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: **Unknown instance**:

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, **not using quirks**.

Hi ha res estrany?

---

### Post by albandy on 2012-10-19
> **jinglada said:**
> Gràcies albandy. Em surt això:

joan@ubuntu:~$ ls /sys/class/backlight
acpi_video0  acpi_video1  intel_backlight
joan@ubuntu:~$

OK, ara hauriem de mirar el contingut de /sys/class/backlight/intel_backlight

Per fer-ho fes:
cat /sys/class/backlight/intel_backlight

Hauria de contenir un número. Aquest número indica el nivell actual de brillantor de la pantalla.

Un cop obtingut el número el guardarem i mirarem de restaurar-lo després de suspendre la màquina.

---

### Post by jinglada on 2012-10-19
> **albandy said:**
> OK, ara hauriem de mirar el contingut de /sys/class/backlight/intel_backlight

Per fer-ho fes:
cat /sys/class/backlight/intel_backlight

Hauria de contenir un número. Aquest número indica el nivell actual de brillantor de la pantalla.

Un cop obtingut el número el guardarem i mirarem de restaurar-lo després de suspendre la màquina.

Com es fa això de  restaurar-lo després de suspendre la màquina? Si m'ho dius, aquesta tarda quan pugui posar-m'hi, ho faria tot de cop. Gràcies.

---

### Post by albandy on 2012-10-19
A lo que t'he dit abans falta afegir-li /brightness, es a dir:
per consultar el número:

cat /sys/class/backlight/intel_backlight/brightness

per restaurar-lo la forma seria:
echo "numero" > /sys/class/backlight/intel_backlight/brightness


Intentaré muntar-te un script que l'hauràs d'executar just abans de suspendre, tindrá un timer que als 60s aproximadament restauri la brillantor per comprovar que funciona.

Edito per ficar el script:

Guarda el fitxer al teu home.
Assigna-li permisos d'execució:
chmod 755 pantalla.sh
després executa'l com a sudo:
sudo ./pantalla.sh

---

### Post by jinglada on 2012-10-19
> **albandy said:**
> A lo que t'he dit abans falta afegir-li /brightness, es a dir:
per consultar el número:

cat /sys/class/backlight/intel_backlight/brightness

per restaurar-lo la forma seria:
echo "numero" > /sys/class/backlight/intel_backlight/brightness


Intentaré muntar-te un script que l'hauràs d'executar just abans de suspendre, tindrá un timer que als 60s aproximadament restauri la brillantor per comprovar que funciona.

Edito per ficar el script:

Guarda el fitxer al teu home.
Assigna-li permisos d'execució:
chmod 755 pantalla.sh
després executa'l com a sudo:
sudo ./pantalla.sh

Ara he pogut agafar el portàtil:

joan@ubuntu:~$ cat /sys/class/backlight/intel_backlight/brightness
976
joan@ubuntu:~$ 

Converteixo 
echo "$BRILLANTOR" > /sys/class/backlight/intel_backlight/brightness

en
echo "976" > /sys/class/backlight/intel_backlight/brightness ?

---

### Post by albandy on 2012-10-19
> **jinglada said:**
> Ara he pogut agafar el portàtil:

joan@ubuntu:~$ cat /sys/class/backlight/intel_backlight/brightness
976
joan@ubuntu:~$ 

Converteixo 
echo "$BRILLANTOR" > /sys/class/backlight/intel_backlight/brightness

en
echo "976" > /sys/class/backlight/intel_backlight/brightness ?

Si seria això pero com que no es veurà la pantalla es millor que facis servir el script que t'he adjuntat.

La diferència es que el script te un timer que restaura la brillantor als 60 segons.

És a dir. Executes el script, ràpidament suspens la màquina i quan estigui suspesa la de-suspens i com a molt en 60 segons, si el script funciona bé serà qüestio d'automatitzar el procés (que això encara he de mirar com fer-ho)

---

### Post by jinglada on 2012-10-19
> **albandy said:**
> Si seria això pero com que no es veurà la pantalla es millor que facis servir el script que t'he adjuntat.

La diferència es que el script te un timer que restaura la brillantor als 60 segons.

És a dir. Executes el script, ràpidament suspens la màquina i quan estigui suspesa la de-suspens i com a molt en 60 segons, si el script funciona bé serà qüestio d'automatitzar el procés (que això encara he de mirar com fer-ho)

FANTÀSTIC, albandy!!! ha funcionat!!! Han estat uns 60 segons molt lents; gairebé estava a punt d'escriure't que no funcionava, quan tot d'una s'ha il·luminat la pantalla.

Quedo a l'espera de l'automatització ;-)

Moltes gràcies!

---

### Post by albandy on 2012-10-20
> **jinglada said:**
> FANTÀSTIC, albandy!!! ha funcionat!!! Han estat uns 60 segons molt lents; gairebé estava a punt d'escriure't que no funcionava, quan tot d'una s'ha il·luminat la pantalla.

Quedo a l'espera de l'automatització ;-)

Moltes gràcies!

Ok, has de fer el següent:

1.- Descarrega el fitxer adjunt i guarda'l al teu home.
2.- Copia el fitxer a /etc/pm/sleep.d/
```

sudo cp backlight.sh /etc/pm/sleep.d/

```
3.- Assigna permisos d'execució al fitxer:
```

sudo chmod 755 /etc/pm/sleep.d/backlight.sh

```
4.- Canvia el propietari de l'arxiu a root:
```

sudo chown root.root /etc/pm/sleep.d/backlight.sh

```

I ja hauria de funcionar

---

### Post by jinglada on 2012-10-20
> **albandy said:**
> Ok, has de fer el següent:

1.- Descarrega el fitxer adjunt i guarda'l al teu home.
2.- Copia el fitxer a /etc/pm/sleep.d/
```

sudo cp backlight.sh /etc/pm/sleep.d/

```
3.- Assigna permisos d'execució al fitxer:
```

sudo chmod 755 /etc/pm/sleep.d/backlight.sh

```
4.- Canvia el propietari de l'arxiu a root:
```

sudo chown root.root /etc/pm/sleep.d/backlight.sh

```

I ja hauria de funcionar

Perfecte! Funciona. Gràcies albandy! Poso SOLVED.

---

