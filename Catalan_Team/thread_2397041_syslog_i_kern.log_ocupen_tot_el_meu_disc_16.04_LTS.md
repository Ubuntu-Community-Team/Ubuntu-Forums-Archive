---
title: "syslog* i kern.log* ocupen tot el meu disc 16.04 LTS"
date: 2018-07-24
forum: Catalan Team
---

### Post by adriarv on 2018-07-24
Hola,

ja m'ha passat dues vegades (de sobte) que els archius syslog* i kern.log* ubicats a /var/log de sobte tenen un tamany de centenars de GB i ocupen el 100% del disc dur. He vist que es poden eliminar (ho he fet doncs sino no podia fer res més) però no les tinc totes.

Voldria saber com es configura el meu Ubuntu 16.04 LTS perquè no torni a passar.

Gràcies

---

### Post by wgarcia on 2018-07-25
Això son els missatges que genera el sistema "journal" del systemd. Aquest gestor d'arrancada genera registres molt detallats i que es poden gestionar de diverses maneres. Normalment la mida dels registres no es dispara, però si el nucli (kernel) alguna altra cosa no està funcionant bé, els registres es poden disparar.

Per tant el primer que faria seria investigar quins missatges estan omplint els registres, especialment el "kern.log". Mira les últimes línies del "kern.log" i el "syslog" amb

```
tail /var/log/syslog
tail /var/log/kern.log
```

a veure si hi ha alguna part del sistema que s'està queixant d'alguna cosa. 

Per netejar els registres i deixar sols, diguem-ne, els últims registres amb una mida de 500 Mb, es pot donar l'ordre següent:

```
sudo journalctl --vacuum-size=500M
```

això alliberarà una mica d'espai, perquè si has d'arreglar alguna cosa que estigui causant els missatges, sense espai a la partició del sistema poca cosa podràs fer.

Un cop arreglat això, perquè no et torni a passar que els registres se t'omplin si hi ha algun problema com el que ha causat això que estàs veient, es pot limitar la mida dels registres del journal de systemd. Això s'ha de fer editant el següent fitxer de configuració, per exemple amb l'editor "nano":

```
sudo nano /etc/systemd/journald.conf
```

En aquest fitxer canvia una línia que posa "#SystemMaxUse=" per

```
SystemMaxUse=500M
```

si vols limitar els registres a 500 Mb. Jo els tinc a 16 Mb, però potser és massa reduït.

---

### Post by adriarv on 2018-07-25
Hola, 

aquestes són les últimes línies. No sé si hi pots veure res en especial:

```
adria@adria-X541UV:~$ tail /var/log/syslog
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409475] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409480] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409491] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409496] pcieport 0000:00:1c.5:    [ 0] Receiver Error         (First)
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409504] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409515] pcieport 0000:00:1c.5: can't find device of ID00e5
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409520] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409527] pcieport 0000:00:1c.5: can't find device of ID00e5
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409541] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jul 25 15:11:16 adria-X541UV kernel: [ 2379.409546] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physicaladria@adria-X541UV:~$
```
```
adria@adria-X541UV:~$ tail /var/log/kern.log
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689839] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689842] pcieport 0000:00:1c.5:    [ 0] Receiver Error         (First)
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689862] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689868] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689871] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689874] pcieport 0000:00:1c.5:    [ 0] Receiver Error         (First)
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689895] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689901] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689905] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Jul 25 15:11:59 adria-X541UV kernel: [ 2422.689909] pcieport 0000:00:1c.5:    [ 0] Receiver Error         (First)
```

---

### Post by wgarcia on 2018-07-25
Sí, és un error conegut. Si obres una consola amb "Control + Alt + F1" per exemple, veuràs que el sistema està enviant constantment aquest error. Pots fer dues coses:

1) Primer prova:

```
sudo apt dist-upgrade
```

mira si el sistema s'actualitza, i si en tornar a engegar el sistema l'error ha desaparegut. 

2) Si continua l'error, s'ha de afegir un paràmetre a l'arrancada. Primer es pot provar per una arrancada puntual per veure si ho arregla. Per això en engegar el sistema, quan surt la pantalla del grub (si no surt perquè l'Ubuntu és l'únic sistema que tens, la pots fer visible prement "Shift", majúscula, quan el sistema està arrancant), quan ja vegis la pantalla del grub prem "e". Això et deixarà editar les línies del grub per a aquesta arrancada concreta. Amb les fletxes del teclat ves a la línia que comença amb "linux" i al final d'aquesta línia has d'afegir "pci=noaer". Un cop hagis fet això, engega el sistema amb "Control-X", ves a la consola un altre cop i mira si el sistema ja no escup aquest missatge. 

Per fer permanent l'arrancada amb aquest paràmetre, edita el fitxer de configuració del grub amb:

```
sudo nano /etc/default/grub
```

mira la línia que posa "GRUB_CMDLINE_LINUX=" i afegeix-le aquest paràmetre:

```
GRUB_CMDLINE_LINUX="pci=noaer"
```

desa, i executa:

```
sudo update-grub
```

en arrencar sempre es farà servir aquest paràmetre.

No sé exactament què fa aquest paràmetre, ja he vist aplicar aquesta solució diversos cops, i cap usuari m'ha comentat que notés res estrany, així que (sembla) que no te gaires conseqüències. Suposo que en actualitzacions futures l'error desapareixerà, així que podràs eliminar el paràmetre desfent aquests passos (editant /etc/default/grub i deixant la línia com estava, sense res, és a dir GRUB_CMDLINE_LINUX="".)

---

### Post by adriarv on 2018-07-25
Hola,

amb la primera prova no s'ha resolts però amb la segona si. A més, sembla que l'ordinador va més ràpid en general. 

Moltes gràcies! :)

---

### Post by wgarcia on 2018-07-25
Segur que ha d'anar més ràpid, l'enviament de milions de missatges cada segon ha d'alentir tot segur.

---

