---
title: "Cd-rw Udf"
date: 2007-07-11
forum: Catalan Team
---

### Post by Curial on 2007-07-11
Déuvosguard Ubuntaires,

És possible utilitzar amb l'ubuntu els cd-rw en format UDF?

Suposo que em direu que sí però, el cas és que he instal·lat els
udftools des del synaptic i no me'ls reconeix.

Gràcies.

---

### Post by orestesmas on 2007-07-12
Per llegir-los, cap problema. Només has de muntar el cdrw usant aquest sistema de fitxers.

Per escriure no sé si ho fa automàticament o hi ha més feina. Ho hauria de mirar, perquè jo no ho he necessitat mai. Però no crec que sigui complicat. Mira per internet, que trobaràs molta informació.

---

### Post by Curial on 2007-07-12
Me'l munta automèticament quan el carrego a la CDera.

Quan provo de desmuntar-lo me'ls expulsa.

Quan el munto des del terminal em diu que ja està muntat com a /media/cdrom1/

Tot i estar muntat únicament veig els arxius: autorun.inf, udfrdhk.exe i udfrinst.zl.

Renuncio?

M'imagino que s'ha de poder treballar amb CD-RW, no?

Gràcies.

---

### Post by orestesmas on 2007-07-13
> **Curial said:**
> Me'l munta automèticament quan el carrego a la CDera.

Quan provo de desmuntar-lo me'ls expulsa.

No és pas descabellat.

> Quan el munto des del terminal em diu que ja està muntat com a /media/cdrom1/

Amb quin sistema de fitxers? Potser te l'ha muntat com a iso9660 normalet (depèn de l'ordre en què testegi els sistemes de fitxers). Assegura't que està muntat i fes:

mount

així tal qual en un terminal. Et treurà una llista dels sistemes de fitxers muntats amb el tipus de sistema detectat. Llavors només has de mirar si te l'ha muntat com UDF o ISO9660.

Si és aquest el problema, hauràs de posar una línia explicita al /etc/fstab que faci referència al teu cdrom i especificant *per ordre* els sistemes de fitxers que ha de testejar: primer UDF i després ISO9660 (en cas que no trobi UDF)

> Tot i estar muntat únicament veig els arxius: autorun.inf, udfrdhk.exe i udfrinst.zl.

Renuncio?

Aquesta pregunta només te la pots respondre tu mateix.

> M'imagino que s'ha de poder treballar amb CD-RW, no?

Gràcies.

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/translations/es/pdf/udf-como.pdf](http://www.ibiblio.org/pub/Linux/docs/HOWTO/translations/es/pdf/udf-como.pdf) (una mica antic, crec)

---

### Post by Curial on 2007-07-13
Quan faig mount si que em diu que  és de tipus iso9660. No diu pas res d'UDF.

He obert l'fstab amb el gedit i m'apareix això:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda2 :
UUID=5c55fc59-6625-408f-8f35-6b859c6dc189	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=9C88795D8879373C	/media/Magatzem	ntfs-3g	defaults,nosuid,nodev,locale=ca_AD.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=E66C07D86C07A303	/media/disk	ntfs-3g	defaults,nosuid,nodev,locale=ca_AD.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=9e4fb5cb-1f9a-472c-bc5a-3c07f0206975	none	swap	sw	0	0
/dev/scd1	/media/cdrom0	udf,iso9660	user,noauto	0	0
/dev/scd0	/media/cdrom1	udf,iso9660	user,noauto	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto	0	0


Com em comentes, udf esta per ordre abans que iso 9660.
És correcte això?

Gràcies.

---

### Post by orestesmas on 2007-07-13
Ja és estrany. Segons això, les 2 unitats de CD que tens haurien d'explorar primer UDF i després ISO9660, però per algun motiu no ho fan.

Potser no se't carrega automàticament el suport de UDF del nucli??

Proposo la següent via a seguir:

Muntar-lo a mà, forçant UDF

```
sudo mount -t udf /dev/scd0 /media/cdrom0
```
(suposo que és el scd0 el que estas usant, sinó, canvia els zeros per uns)

Si el sistema te l'ha muntat automàticament, desmunta'l primer:

```
sudo umount /dev/scd0
```

Això t'hauria de permetre llegir el disc en UDF. Si NO t'ho permet, serà que no tens carregat el suport UDF del nucli. Per comprovar-ho fes:

```
lsmod | grep udf
```

T'hauria de sortir quelcom del tipus:

```
udf                    86664  0
```

En cas contrari, carrega el driver primer:

```
sudo modprobe udf
```

I aleshores prova de remuntar-lo.

De tota manera, jo penso que el format UDF aquest està bastant en desús, havent-hi avui en dia els pendrives de Gigabytes. Pot semblar interessant però malgasta l'espai del CD en comparació amb el ISO9660 normalet.

---

### Post by CarlesOriol on 2007-07-14
> **orestesmas said:**
> 
Per escriure no sé si ho fa automàticament o hi ha més feina. Ho hauria de mirar, perquè jo no ho he necessitat mai. Però no crec que sigui complicat. Mira per internet, que trobaràs molta informació.

He estat fent proves després de llegir aquest post i per llegir-los no hi ha cap problema però per escriure crec que cal recompilar el nucli canviant un parell d'opcions. 

Mirant les opcions UDF veiem que hi ha escrit: UDF write support (DANGEROUS). Algú sap el per què d'aquests dangerousisme?

---

### Post by Curial on 2007-10-05
> **CarlesOriol said:**
> He estat fent proves després de llegir aquest post i per llegir-los no hi ha cap problema però per escriure crec que cal recompilar el nucli canviant un parell d'opcions. 

Mirant les opcions UDF veiem que hi ha escrit: UDF write support (DANGEROUS). Algú sap el per què d'aquests dangerousisme?


Ja em perdonareu si us trec un post tant antic, però no me n'he sortit ni amb la lectura.

Gràcies .

---

### Post by CarlesOriol on 2007-10-06
Pots llegir-los però per escriure'ls cal refer el sistema... i trobo que això fa més per debianistes que per ubuntaires.

---

### Post by albertg on 2007-10-06
> **Curial said:**
> Ja em perdonareu si us trec un post tant antic, però no me n'he sortit ni amb la lectura.

Gràcies .

El problema deu ser la versió d'UDF que utilitza el disc. Linux només suporta fins la versió 2.0 del format.

---

### Post by Curial on 2007-10-06
[/QUOTE]

Si és aquest el problema, hauràs de posar una línia explicita al /etc/fstab que faci referència al teu cdrom i especificant *per ordre* els sistemes de fitxers que ha de testejar: primer UDF i després ISO9660 (en cas que no trobi UDF)


[/QUOTE]


He trobat la solució únicament per a la lectura:
He fet  sudo gedit  /etc/fstab/  i llavors he canviat l'ordre del tipus, és a dir , he posat primer iso9660 i després UDF (el contrari del que em deies). així:
/dev/scd1	/media/cdrom0	iso9660,udf	user,noauto	0	0
/dev/scd0	/media/cdrom1	iso9660,udf    	user,noauto	0	0

La bombeta se m'ha encès a rel d'entrar a sistema-Administració-Monitor de sistema-sistema de fitxers, em mostrava que el tipus del dispositiu /dev/scd1 era iso9660. Després del canvi ja apareix com a UDF.

No se si teniu algun comentari al respecte: serà agraït.

Salut.:guitar:

---

