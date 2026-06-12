---
title: "[SOLVED] Problemes amb dependencies"
date: 2007-10-29
forum: Catalan Team
---

### Post by lluisanunez on 2007-10-29
Hola,
he fet l'upgrade a la 7.10 al PC que em quedava, però a mig camí s'ha penjat el PC, l'he rebotat i he pogut engegar els processos del update-manager que s'havien quedat a mitges. Però queda alguna cosa pendent, perquè ara, després de qualsevol procés amb apt o synaptic, m'apareix un missatge dient que per errors de  dependències aquests  4 programes es queden sense configurar: 
acpid
acpi-support
ubuntu-desktop
powermanagement-interface

Intento un pdkg --configure -a, i em torna a sortir l'error:
```
lluisa@ub236115:~$ sudo dpkg --configure -a
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 ubuntu-desktop
 acpi-support
 powermanagement-interface

```
Com puc saber quines dependències són, i mirar d'arreglar-ho?

---

### Post by Ferri on 2007-10-29
Podries intentar:
```
sudo aptitude reinstall acpid ubuntu-desktop acpi-support powermanagement-interface
```

---

### Post by lluisanunez on 2007-11-06
Gràcies. Ho he fet, però em continuen sortint els missatges, al final de cada insta&#320;lació:
```
E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
```
Com que tot funciona bé, diria que simplement és un fitxer que es va quedar sense modificar durant l'actualització a Gutsy, la qüestió és, quin fitxer?

---

### Post by papapep on 2007-11-06
i què tal amb?:

```
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
```

---

### Post by lluisanunez on 2007-11-07
OK moltes gràcies i  ja l'hi pots posar el [COLOR="Red"]RESOLT[/COLOR]! 
A les dues comandes hi he afegit 
```
sudo dpkg --configure -a
```
i s'han acabat els errors!

---

### Post by papapep on 2007-11-07
El configure -a quan l'has fet, al final?

---

### Post by lluisanunez on 2007-11-07
Si, al final, aleshores ha acabat de configurar el power-management i el ubuntu-desktop

---

