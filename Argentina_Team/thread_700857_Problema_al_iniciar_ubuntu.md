---
title: "Problema al iniciar ubuntu"
date: 2008-02-18
forum: Argentina Team
---

### Post by nemodot on 2008-02-18
Buenas, tengo un problema desde hace tiempo al inicio de ubuntu.

Se los describo así: Cuando esta cargando la barra de Ubuntu se sale y me muestra el listado de procesos que se van cargando. En eso se ve que el fsck comprueba el disco donde tengo ubuntu bien y lo hace muy rápido (sda6):

```
fsck 1.40.2 (12-Jul-2007)
/dev/sda6: clean, 134792/3933120 files, 940273/7865817 blocks
```

Pero luego hace lo mismo con un disco FAT32 que tengo y se tarda mucho, más de un minuto! y muestra esto durante la espera y luego:

```
* Checking file systems...
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32 LFN
There are differences between boot sector and its buckup.
Differences: (offset:original/backup)
  28:3f/ef, 29:00/40, 30:00/08, 31:00:07
  Not automatically fixing this.
/dev/sda5:  208524 files, 2470461/4798998 clusters 
```

No sé de que se trata y tampoco sé como corregirlo, pero es muy molesto. Hoy reinstalé ubuntu y cuando analizaba los discos estuvo 10 minutos colgado con el HDD al palo. Esto sucedía antes de que hoy decidiera reinstalar ubuntu, pensé que haciendolo se iba a coregir, pero no.

Alguna idea?

---

### Post by faktorqm on 2008-02-18
Yo lo solucionaba pasandole un scandisk si es vfat o un chkdsk si es ntfs.... sé que mi solucion es lamentable, pero funciona. salu2!

---

### Post by nemodot on 2008-02-18
> **faktorqm said:**
> Yo lo solucionaba pasandole un scandisk si es vfat o un chkdsk si es ntfs.... sé que mi solucion es lamentable, pero funciona. salu2!

Y cómo es el comando en cuestión que debo realizar para hacer el scandisk?

---

### Post by faktorqm on 2008-02-19
eehhhh estoy hablando en windows eh! 

```
scandisk c:
```

o si estas en xp creo que era 

```
chkdsk -f c:
```

---

### Post by nemodot on 2008-02-19
> **faktorqm said:**
> eehhhh estoy hablando en windows eh! 

```
scandisk c:
```

o si estas en xp creo que era 

```
chkdsk -f c:
```

Va a ser scandisk E o scansdisk GORDO. Asi le llamo a mi particion FAT de 150 GB. :)

---

### Post by pol666 on 2008-02-19
a mi eso me sale dura 1 minuto ¬¬ pero si no uso win no sale

---

### Post by nemodot on 2008-02-19
Hice correr el Scandisk sobre windows y puse para que corrigiera errores si es que encuentra.

Me pidio que reinicie para eso, pero al terminar todo e iniciar en ubuntu descubri que el problema seguia estando.

---

### Post by faktorqm on 2008-02-19
eemm otra cosa que podes probar es agarrar y hacer una copia del mbr sobre la copia ya existente. es decir, si el disco tiene una sola particion, agarra cualquier herramienta para discos y copia el mbr actual al de backup y listo, ahi deberia solucionarte el problema. sino no se :S salu2!

---

