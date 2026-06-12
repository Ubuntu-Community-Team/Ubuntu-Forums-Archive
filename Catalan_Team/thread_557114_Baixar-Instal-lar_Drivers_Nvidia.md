---
title: "Baixar-Instal-lar Drivers Nvidia"
date: 2007-09-22
forum: Catalan Team
---

### Post by prostata on 2007-09-22
Voldria instal-lar a Kubuntu els drivers de la meva Nvidia GeFroce FX 5200. I primer me'ls hauria de baixar . Em podrieu donar un cop de ma..??
gràcies

---

### Post by Ferri on 2007-09-22
Em sembla que amb això n'hauries de tenir prou (assegura't de tenir les fonts de programari "restricted" habilitades).
```
sudo apt-get install nvidia-glx nvidia-settings
```
I després:
```
sudo nvidia-glx-config enable
```

---

### Post by CarlesOriol on 2007-09-22
Si no uses el gutsy millor canvies:

sudo apt-get install nvidia-glx**-new** nvidia-settings

---

### Post by prostata on 2007-09-23
> **Ferri said:**
> Em sembla que amb això n'hauries de tenir prou (assegura't de tenir les fonts de programari "restricted" habilitades).
```
sudo apt-get install nvidia-glx nvidia-settings
```
I després:
```
sudo nvidia-glx-config enable
```

Gràcies per la teva ajuda, Carles, però dins l'entorn gràfic de kubuntu on es troba les fonts de programari "restricted"...

Gràcies

---

### Post by orestesmas on 2007-09-23
No puc dir-t'ho exactament ara, perquè no tinc una kubuntu a mà (sóc a debian), però més o menys és això:

Has d'obrir l'ADEPT complet (el que hi ha al menú del sistema, l'executable es diu "adept_manager") i, un cop dins, els següents menús:

Adept -> Administra els repositoris

T'ha de sortir un diàleg i per allí trobaràs una caixa de selecció que hauràs de marcar per activar els "restricted".

---

### Post by prostata on 2007-09-23
> **CarlesOriol said:**
> Si no uses el gutsy millor canvies:

sudo apt-get install nvidia-glx**-new** nvidia-settings

El resultat per consola es el següent ;-(

[I]josep@josep-desktop:~$ sudo apt-get install nvidia-glx nvidia-settings
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  nvidia-glx: Entra en conflicto: nvidia-settings pero 1.0+20060516-3ubuntu1 va                   a ser instalado
E: Paquetes rotos
josep@josep-desktop:~$ sudo nvidia-glx-config enable
sudo: nvidia-glx-config: command not found
josep@josep-desktop:~$

[/I]

Alguna alternativa més???

---

### Post by Ferri on 2007-09-23
Intenta instal·lar el nvidia-glx (o nvidiaglx-new), sense el nvidia-settings (pel que sembla no et coincideixen les versions. El nvdia-settings només et permet modificar la configuració, però el driver hauria de funcionar encara que no l'instal·lis.

---

### Post by patrickfromspain on 2007-09-24
nvidia-gl-new no l'insta&#320;lis, no et funcionara en una 5200. Tampoc et fa falta nvidia-settings, s'insta&#320;la el mateix amb el driver, o alguna cosa semblant.

salut

---

### Post by CarlesOriol on 2007-09-24
SI et funcionarà en una 5200 i millor que l'altre. L'anterior va des de la tnt fins a la GForce 4.

---

