---
title: "Problemes amb Debian"
date: 2012-09-20
forum: Catalan Team
---

### Post by Polrodoreda on 2012-09-20
Hola,
fa poc he instal·lat l'ubuntu 12 al meu ordinador portatil. Per temes de programació em van aconsellar instal·lar el debian, però després de provar-lo he decidit quedar-me amb l'ubuntu.
El problema és que a la pantalla d'arrencada de l'ordinador, quan haig de triar entre ubuntu o windows em surt al fons de Debian i l'aparença alhora de triar l'usuari és diferent a la que tenia abans.
Com desinstal·lar totalment Debian i quedar-me amb l'ubuntu? 
moltes gràcies.

---

### Post by wgarcia on 2012-09-21
Això segurament és perque tens instal·lada al registre mestre d'arrencada (MBR, Master Boot Recorda) del disc principal la versió de Debian del "grub", la utilitat que permet arrencar diversos sistemes operatius. 

Per reinstal·lar la versió d'Ubuntu del grub primer convé determinar quin és el dispositiu que identifica el disc principal d'arrencada. Normalment és /dev/sda en sistemes actuals. Per saber-ho es pot fer

```
sudo fdisk -l
```

Un cop identificat el disc d'arrencada, per instal·lar el grub aquí es fa

```
sudo grub-install /dev/sda
```

També convé actualitzar els fitxers de configuració del grub perquè reconegui els sistemes operatius que tens instal·lats amb:

```
sudo update-grub
```

Per llegir més sobre el tema:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by wgarcia on 2012-09-21
Per al segon tema que comentes 

> l'aparença alhora de triar l'usuari és diferent a la que tenia abans.

el que deu passar és que tens el gestor "gdm" en comptes del "lightdm" que és el que fa servir Ubuntu. 

Per recuperar aquest últim gestor d'usuaris es pot fer

```
sudo apt-get install --reinstall lightdm
```

i em sembla que et donarà l'opció d'escollir aquest gestor per escollir els usuaris.

---

### Post by CarlesOriol on 2012-09-22
> **wgarcia said:**
> Per al segon tema que comentes 

el que deu passar és que tens el gestor "gdm" en comptes del "lightdm" que és el que fa servir Ubuntu. 

Insta&#320;lant un debian no es canvia el lightdm pel gdm.

Polrodoreda: Exactament com dius que vas insta&#320;lar el debian?

---

### Post by wgarcia on 2012-09-22
Doncs per sortir de dubtes, des d'una terminal

```
ps -ef | grep lightdm
```

mostrarà el procés de lightdm si és que està executant-se. 

Potser el que ha canviat és el tema de lightdm que fa servir l'Ubuntu.

---

