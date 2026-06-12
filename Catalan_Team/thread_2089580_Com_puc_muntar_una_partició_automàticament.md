---
title: "Com puc muntar una partició automàticament?"
date: 2012-11-29
forum: Catalan Team
---

### Post by Satboy on 2012-11-29
Hola,
 Vaig fer una partició anomenada "Disc seguretat" per poder formatar el disc dur i guardar els arxius importants i no tenir de perdre'ls.
 Com ho puc fer perquè aquesta partició es munti automàticament quan engegui l'ordinador?
 Adjunto una captura del Gparted per deixar-vos-ho més clar.

 [IMG]http://i47.tinypic.com/1h71bn.jpg[/IMG]

 La partició en qüestió, és la **/dev/sda7**
 Què és la partició "No assignat" i d'on ha sortit??

 Gràcies! :wink:

---

### Post by wgarcia on 2012-11-30
Primer obté el codi del disc que vols muntar, per exemple des d'una terminal:

```
sudo blkid
```

Per a un disc que tinc muntat a mi em surt per exemple una línia que posa:

```
/dev/sdc1: LABEL="Backup" UUID="a9094f24-41ce-45ee-bb57-875682f263b5" TYPE="ext4" 
```

I ara amb "gksudo gedit /etc/fstab", s'ha d'agregar una línia a aquest fitxer, per exemple en el meu cas la línia és:

```
UUID=a9094f24-41ce-45ee-bb57-875682f263b5 /mnt/Backup     ext4    auto,user,rw,exec 0 0

```

Compte amb fer un error en editar aquest fitxer /etc/fstab, si entres alguna cosa incorrecta pot ser que després no puguis entrar al sistema. En aquest cas hauràs d'arrencar el sistema amb un USB o CD autònom ("live"), muntar el disc on tens la instal·lació d'Ubuntu, buscar /etc/fstab i desfer l'error.

---

### Post by wgarcia on 2012-11-30
M'oblidava dir que has de tenir creat el directori /mnt/Backup .

---

### Post by Satboy on 2012-11-30
> **wgarcia said:**
> Primer obté el codi del disc que vols muntar, per exemple des d'una terminal:

```
sudo blkid
```


 Hola,
 A mi m'ha sortit això:
[B]/dev/sda7: LABEL="Disc seguretat" UUID="126b033a-cde6-47c8-a435-5b797f779496" TYPE="ext4" 
[/B]
 Dew! :wink:

---

### Post by Satboy on 2012-11-30
> **wgarcia said:**
> M'oblidava dir que has de tenir creat el directori /mnt/Backup .

 Hola,
 Perdona per la ignorància, com ho tinc de fer, això?

 Dew! :wink:

---

### Post by wgarcia on 2012-12-01
Primer has de crear el directori on vols muntar el teu disc:

```
sudo mkdir /mnt/Disc
```

Ara has d'editar el fitxer /etc/fstab:

```
gksudo gedir /etc/fstab
```

i a sota de tot agregar la següent línia (usant el que has obtingut amb "blkid":

```
UUID=126b033a-cde6-47c8-a435-5b797f779496 /mnt/Disc    ext4    auto,user,rw,exec 0 0
```

El disc ara es muntarà a "/mnt/Disc" cada cop que iniciïs el sistema 

Torno a dir que compte de saber com desfer el canvi a "/etc/fstab" si s'entra alguna cosa malament i després el sistema no es pot iniciar. Amb les instruccions de dalt no hauria de passar, però com sempre s'ha d'estar preparat quan es fan canvis al sistema, i de més està dir que es fan sota la responsabilitat de cadascú.

---

### Post by Satboy on 2012-12-01
Hola,
 Fet, moltes gràcies!!

 Dew!:wink:

---

