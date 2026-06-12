---
title: "Ocultar kernels vells en Ubuntu 10.04"
date: 2010-05-15
forum: Catalan Team
---

### Post by albertdelleida on 2010-05-15
Hola a tots i totes,

m'acabo d'instal·lar l'Ubuntu 10.04 i m'agradaria ocultar (no eliminar) els kernels vells que apareixen al GRUB. 

Buscant per la xarxa he trobat l'opció següent (que de fet és la que vaig usar en l'Ubuntu 9.10):

[B]1) Obrir terminal i escriure:

*$ sudo gedit /boot/grub/menu.lst*

2) S'obra l'arxiu *menu.lst* i  buscar les línies que comencin per* title, root, kernel *i *intrid* que facin referència als kernels que volem ocultar. Escriure una # davant de cada línia[/B].

Doncs bé, quan faig el primer pas i s'obra l'arxiu *menu.lst *aquest surt en blanc (per tant, intueixo que no l'ha obert, sinó que l'ha creat). :( Que m'aconselleu que faci?

Moltes gràcies.

---

### Post by lluisanunez on 2010-05-15
Assegura't que has escrit bé la comanda. El menu.lst a la 10.4 és al mateix lloc que a les versions anteriors.

---

### Post by albertdelleida on 2010-05-15
Ho acabo de comprovar lluisanunez, un parell de cops, i res. També he entrat a la carpeta * /boot/grub/ i* tampoc, res de res... Què puc fer? Alguna idea?

---

### Post by pserra on 2010-05-15
> **albertdelleida said:**
> Ho acabo de comprovar lluisanunez, un parell de cops, i res. També he entrat a la carpeta * /boot/grub/ i* tampoc, res de res... Què puc fer? Alguna idea?

has mirat que dintre la carpeta grub no tinguis un arxiu que es diu brub.cfg? aquest es el que remplaça a l'anterior grub menu.lst en el  nou GRUB

---

### Post by wgarcia on 2010-05-15
Què et surt a dalt del tot del menú del grub? És possible que hagis actualitzat el grub i per tant els canvis ja no es fan editant el menu.lst.

---

### Post by albertdelleida on 2010-05-15
A dalt del menú del GRUB em surt *GNU GRUB, versió 19.8-1ubuntu6*. 

He buscat l'arxiu *brub.cfg* i res, tot i que he trobat el *grub.cfg* Tot i això, les línies que hauria de modificar no són exactament les mateixes que he trobat per la xarxa. Les meues són aquestes:
[I]
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2ece7135-d5d6-4a7d-8a22-fe1d78b04b3e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###[/I]

Alguna solució? Moltes gràcies a tots :)

---

### Post by kimet on 2010-05-15
A /etc/grub.d hi ha una serie de arxius que serveixen per generar el grub2 

Per fer-te un grub personalitzat has triar les entrades que vulguis tenir al nou grub d'aquestes que et surten al grub.cfg y copiarles al arxiu /etc/gurb.d/40_custom, així apareixeran al final del teu grub després d'executar un ```
# update-grub
```.
Per tal que no apareguin les altres entrades haurás de canviar el nom del arxiu /etc/grub.d/10_linux (per exemple afegint un "~" al darrera, y per evitar que s'actualitzin reanomenar també l'arxiu "30-os-prober".

Salud.

---

### Post by albertdelleida on 2010-05-16
Acabo d'obrir l'arxiu */etc/grub.d *El que no sé és com escriure les entrades en aquest arxiu. Em podries escriure un exemple d'entrada? A part, es m'antindrien les entrades a Windows o també les hauria d'escriure? 

Moltes gràcies! Espero la vostra resposta. :)

---

### Post by kimet on 2010-05-16
Poso un petit manual que vaig fer per una altre pàgina, espero que et serveixi.

_Personalització de les entrades al Grub2_

Possiblement en interessi organitzar millor l'ordre de les entrades que apareixen al Grub, afegir-ne de noves o suprimir-ne d'altres.

Per afegir noves entrades només caldrà escriure-les en els fitxers de configuració localitzats a **/etc/grub.d**, seguint els següent ordre:

00_*: Reservat a les capçaleres
10_*: Entrades natives
20_*: Aplicacions secundaries ( Memtests86, etc)

Per exemple. Es pot afegir una una entrada per a un altre S.O. Creant un arxiu **11_altreSO**, i actualitzar el Grub.

En cas de voler eliminar entrades que considerem innecessàries, per exemple la de Memtests86 o, les entrades errònies que apareixen d'altres sistemes operatius. Haurem d'editar l'arxiu **/etc/grub.d/40_custom **afegint-hi les entrades que ens siguin necessàries obtenint-les de l'arxiu **/boot/grub/grub.cfg**. Per exemple:

[I]menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 06eddf7b-6b5f-4669-b6be-ae18ce977039
	echo	Loading Linux 2.6.32-trunk-686 ...
	linux	/boot/vmlinuz-2.6.32-trunk-686 root=UUID=06eddf7b-6b5f-4669-b6be-ae18ce977039 ro splash vga=773 quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-trunk-686
}
[/I]
En aquest punt s'afegiran al final de Grub2 les  entrades que hagem posat al fitxer /etc/grub.d/40_custom, al darrere de les que ja hi teníem.
Com el que en realitat el que  ens interessa es que només apareixin les que em posat a l'arxiu 40_custom, haurem de suprimir els permisos d'execució als fitxers que s'encarreguen de proporcionar les altres entrades: /etc/grub.d/10_linux, /etc/grub.d/50_Memtest86, etc. I deshabilitar la opció de regenerar el grub del fitxer 30_os.prober. Per que no torni a afegir entrades que no desitgem.

Per tant executem al terminal com a root:
```
chmod -x /etc/grub.d/10_linux
```
```
chmod -x /etc/grub.d/memtest86+
```

I afegim la línia:

**GRUB_DISABLE_OS_PROBER=true**  Al final de l'arxiu /etc/default/grub

Nota: Teniu en compte que en futures actualitzacions del kernel, les entrades noves no apareixeran i les haurem d'afegir manualment.

---

### Post by albertdelleida on 2010-05-16
Moltes gràcies pel manual. Llàstima que les actualitzacions del kernel no apareguin automàticament i s'hagin d'afegir cada vegada. En tot cas, moltes gràcies :)

---

### Post by papapep on 2010-05-16
> Moltes gràcies pel manual. Llàstima que les actualitzacions del kernel no apareguin automàticament i s'hagin d'afegir cada vegada.

Com? qui ho diu això?? el sistema de post-configuració del gestor de paquets s'encarrega d'actualitzar sempre el Grub quan instal·les o desinstal·les nuclis i deixar-ho tot ben sincronitzadet.

---

### Post by albertdelleida on 2010-05-16
Ho ha comentat en kimet, jo encara no ho sé...

> Nota: Teniu en compte que en futures actualitzacions del kernel, les  entrades noves no apareixeran i les haurem d'afegir manualment.

---

### Post by kimet on 2010-05-16
Ho dic jo Papapep

Per tenir les actualitzacions del kernel hauràs de refer els permisos d'execució als fitxers on les hagis denegat, que son els que s'encarreguen d'actualitzar el grub, i repetir el procés.

---

### Post by papapep on 2010-05-16
Ah! :D

És que no havia llegit el post on explicaves el tema aquest :oops:

Aleshores he interpretat que l'Albert ho deia a "nivell general".

Perdó pel malentès. :)

---

### Post by albertdelleida on 2010-05-16
No passa res :) tot solucionat!

---

