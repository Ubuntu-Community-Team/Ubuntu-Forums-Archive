---
title: "Com despertar el PC"
date: 2020-06-28
forum: Catalan Team
---

### Post by josep-maria on 2020-06-28
Després d'haver fet dormir el PC (fent clic a "atura temporalment"), quan el vull despertar, haig de tocat el botó d'engegada que hi ha a la carcassa del PC. Però a uns altres PCs els pots despertar tocant qualsevol tecla. Com es fa?

Tinc l'Ubuntu mate 1.12.1, ubuntu 16.04.6. El processador és Intel Celeron G1620.

---

### Post by wgarcia on 2020-06-30
Per veure si el teclat està habilitat per despertar l'ordinador des de la suspensió, es pot mirar amb l'ordre següent des d'una terminal:

```
cat /proc/acpi/wakeup
```

Per exemple si tens un teclat USB et podria sortir quelcom com ara:

```
USB0      S3    *disabled   pci:0000:00:12.0
```

Per habilitar-lo:

```
sudo su
echo USB0 > /proc/acpi/wakeup
```

Si no pots identificar quina línia representa el teu teclat, enganxa la sortida de la primera ordre a "pastebin.ubuntu.com" i enganxa l'enllaç que et dóna aquí, a veure si ho podem esbrinar.

---

### Post by josep-maria on 2020-07-02
Surt això:

josep@josep:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PS2K	  S4	*disabled
PS2M	  S4	*disabled
P0P1	  S4	*disabled
RP01	  S4	*disabled  pci:0000:00:1c.0
PXSX	  S4	*disabled
RP02	  S4	*disabled
PXSX	  S4	*disabled
RP03	  S4	*disabled
PXSX	  S4	*disabled
RP04	  S4	*disabled
PXSX	  S4	*disabled
RP05	  S4	*disabled
PXSX	  S4	*disabled
RP06	  S4	*disabled  pci:0000:00:1c.5
PXSX	  S4	*disabled  pci:0000:03:00.0
PEG0	  S4	*disabled  pci:0000:00:01.0
PEGP	  S4	*disabled
PEG1	  S4	*disabled
PEG2	  S4	*disabled
PEG3	  S4	*disabled
GLAN	  S4	*disabled
EHC1	  S4	*enabled   pci:0000:00:1d.0
EHC2	  S4	*enabled   pci:0000:00:1a.0
HDEF	  S4	*disabled  pci:0000:00:1b.0

---

### Post by wgarcia on 2020-07-05
D'acord amb la sortida que has enganxat, sembla que pràcticament tot està deshabilitat ("disabled"). Els únics dos "enabled" deuen ser el botó d'arrencada i alguna altra cosa. 

El primer que es pot fer és mirar a la configuració inicial ("Setup") quan engegues l'ordinador, normalment accessible prement la tecla F2, però depèn del model de l'ordinador. Al menú de configuració s'ha de buscar a veure si hi ha alguna opció per fer que el teclat desperti l'ordinador.

---

### Post by josep-maria on 2020-07-09
He tocat molts cops F2 quan engegues el pc, però no fa res. No surt cap menú. Es veu un avís que diu que toquis F2 o del. També he provat tocant del, i tampoc no passa res. Pot ser una altra tecla?

---

### Post by josep-maria on 2020-07-09
Quan engegues, durant un segon es veu "no keyboard detected". Però el teclat sempre ha anat bé.

---

### Post by josep-maria on 2020-07-09
He provat tocant F10, i tampoc no surt res.

---

### Post by wgarcia on 2020-07-09
Has provat F2 i Del a l'hora?

---

### Post by josep-maria on 2020-07-09
Sí, i no fa res. 

No sé com però una de les vegades ha sortit això:

[IMG]Screenshot at 2020-07-09 23:50:54.png[/IMG]

---

### Post by josep-maria on 2020-07-09
Vegem si ara es veu:

[https://blocs.tinet.cat/tokra/files/2020/07/Screenshot-at-2020-07-09-235054.png](https://blocs.tinet.cat/tokra/files/2020/07/Screenshot-at-2020-07-09-235054.png)

---

### Post by wgarcia on 2020-07-10
Això que mostres no sembla el menú de configuració de la BIOS. Quina marca i model exacte és l'ordinador?

---

### Post by josep-maria on 2020-07-16
No és de cap marca. És fet a mida, d'artesania.

---

### Post by wgarcia on 2020-07-21
El que cal és la marca/model de la placa mare, per veure com accedir al menú de configuració de la BIOS.

---

