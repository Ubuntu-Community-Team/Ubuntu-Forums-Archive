---
title: "Problemes a l'arrencada"
date: 2009-01-18
forum: Catalan Team
---

### Post by SnowTDM on 2009-01-18
Després de reinstal·lar l'Ubuntu 8.10 per problemes amb el disc dur em trobo que de vegades no arrenca. Es queda amb la pantalla negra després de que aparegui el logo d'Ubuntu i la barra taronja arribi al final. No apareix la pantalla de login, no funcionen les consoles amb Alt+F1 o ni les X amb Alt+F7, ni es reinicien les X amb Ctrl+Alt+Del. Tampoc el puc rebotar amb Ctrl+Alt+Supr.

L'he de rebotar amb el boto de reset i arrencar en "recovery mode" i triar arrencada normal.

Els fallos d'arrencada són aleatoris.

On puc trobar els logs de l'arrencada?

Gràcies.

---

### Post by papapep on 2009-01-18
Si els tens habilitats, seran a /var/log/boot.

Si no hi tens res, que seria el normal si no ho has habilitat després de l'instal·lació, cal que modifiquis el contingut de /etc/default/bootlogd i el modifiquis per que passi de:

```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No
```

a

```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
```

un cop desis el fitxer i tornis a engegar l'ordinador ja podràs consultar el registre.

Tot i això, pel que dius, igual seria més profitós treure el "quiet" i "splash" de la línia del /boot/grub/menu.lst que t'arrenca el nucli i veuràs el que passa "en viu".

---

### Post by jerec on 2009-01-20
Precisament tinc la maquina d'un amic que li passa el mateix.

Encara m'ho haig d'acabar de mirar.
Per mirar-ho amb els logs, apart de posar la variable BOOTLOGD_ENABLE=Yes s'ha d'iniciar el dimoni bootlogd que almenys amb les maquines que remeno no s'inicia a l'arrancada del Linux.

Pots fer servir el BootUp Manager per administrar aquest dimoni 
(comanda bum des de la consola)

De totes maneres no se si va gaire be al 8.10 aquest dimoni.

---

### Post by SnowTDM on 2009-01-21
Gracies. Ja he editat els fitxers de configuració, però no em troba la comanda bum.

A veure que puc veure quan torni a fallar.

Salutacions

---

### Post by jerec on 2009-01-25
Després de renegar, buscar y maleir els de Ubuntu per aquest ultim regal de la versio 8.10 (la veritat que sembla mes una beta que no pas una versio oficial) he vist que el bootlogd l'han deixat obsolet a les ultimes versions, la causa es que portava problemes i han decidit deixar-lo desactivat.

El que si que hi es el fitxer d'arrencada a /etc/init.d el de configuració /etc/defaults/bootlogd, però el programa no que no hi es a /sbin/
(això ho fan per fer-ho una mica mes complicat i que les neurones no s'ens adormin)

Si vols tornar a activar el bootlogd:

1º Instala el paquet Sysvinit, aquest porta el bootlogd
2º Posa be la prioritat a l'arrencada del sistema
    # update-rc.d -f bootlogd remove
    # update-rc.d bootlogd defaults 08
3º Modifica el fitxer /etc/defaults/bootlogd 
   BOOTLOGD_ENABLE=Yes

a dins de /var/log hi tindràs el fitxer boot on hi haurà l'arrencada del sistema.
Tal i com he dit sembla ésser que portava problemes, per alguna cosa l'han desactivat, ja veuràs que no mata pas llops el contingut del fitxer.

Per cert si engeges el dimoni desde les X, et surtira un error:
   # bootlogd: cannot find console device 136:1 in /dev

vol dir que no s'executa des de la consola de les X, si el vols arrencar CTRL+F1 per exemple i l'engegues des de la tty1

---

### Post by SnowTDM on 2009-01-26
Per això tinc buit el fitxer /var/log/boot.

Provaré el que em dieu a veure si començo a endevinar el que passa.

Gràcies

---

### Post by SnowTDM on 2009-02-04
Hola de nou!
Ja tinc el /var/log/boot, però pels temps que indica només em guarda les dades de la darrera arrencada, que , lògicamet, és correcta.

Com puc veure el log de les arrencades anteriors?

Una altre dada: quan no m'arrenca el led del teclat de les majúscules fa pampallugues aproximadament 1 cop per segon.

Salutacions

---

