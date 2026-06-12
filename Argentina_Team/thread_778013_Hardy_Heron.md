---
title: "Hardy Heron"
date: 2008-05-01
forum: Argentina Team
---

### Post by ghertzan on 2008-05-01
Buenas Gente!!
recen termino de ponerlo, 
Tengo 2 Problemas
1. No puedo cambiar la resolucion de la pantalla, en la version anterior lo podia hacer.
Tengo una GForce 7300 GS, ya se instalaron los controladores.
2. Los discos... Me dice que no los puede montar, uno esdonde esta el XP y los otros estan en NTFS vacios.
el error es:
$Logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operacion no soportada Mount is denied because NTFS is mark to be in use ( Esto es lo que no entiendo, que significa "esta marcada para estar en uso2.
Chosse one action: 1 If you have windows then disconnect the external devices by clicking on the 'Safety Remove Hardware' icon in yhe windows taskbar.

Les agradezco cualquier dato que me puedan dar.

Desde Córdoba, Gambit!!

---

### Post by i586 on 2008-05-01
> **ghertzan said:**
> Buenas Gente!!
recen termino de ponerlo, 
Tengo 2 Problemas
1. No puedo cambiar la resolucion de la pantalla, en la version anterior lo podia hacer.
Tengo una GForce 7300 GS, ya se instalaron los controladores.
2. Los discos... Me dice que no los puede montar, uno esdonde esta el XP y los otros estan en NTFS vacios.


1. Con respecto a la resolución: instalar los controladores pocas veces soluciona los problemas. Muchos dicen que corras **dpkg-reconfigure**, pero la verdad es que en esta versión deja configurar sólo hasta el teclado. Hacé lo siguiente:

A. Editá tu **xorg.conf** (como **root**; en** /etc/X11/xorg.conf**); en la sección Monitor añadí **HorizSync** y **VertRefresh** con sus respectivos valores (rangos) dependiendo de tu monitor. 

B. Luego CTRL+ALT+BACKSPACE para reiniciar X11. Deberías tener las resoluciones deseadas en cualquier lista.

2. Con respecto a Windows/NTFS. Intentá hacer esto:
```

sudo mount /dev/<disco> <carpeta>

```En versiones anteriores, **mount**, a veces, no montaba automáticamente la partición y debías *forzarlo*. En Hardy (y con la versión actualizada del programa) yo no tuve inconvenientes.

Recordá que no vas a poder escribir la partición (si podrías si el sistema de archivos fuese FAT o alguna variante), pero sí vas a poder leerla (ejemplo: copiar archivos).

Saludos.

---

### Post by Hei Ku on 2008-05-01
con ntfs-3g sí podes escribir en las particiones ntfs. Y si no me equivoco, es la que viene por defecto.

---

### Post by i586 on 2008-05-01
> **Hei Ku said:**
> con ntfs-3g sí podes escribir en las particiones ntfs. Y si no me equivoco, es la que viene por defecto.

Verdad. Aunque no me acordaba porque no lo probé.

Saludos.

---

### Post by Hei Ku on 2008-05-01
El ntfs-3g anda muy bien. Muchas distros ya lo estan usando por defecto.

Puede ser que para montar esas particiones tengas que correrle un chkdisk desde windows, porque parece que algo se cerro mal la ultima vez que lo usaste.

---

### Post by sajnox on 2008-05-01
> **ghertzan said:**
> 
2. Los discos... Me dice que no los puede montar, uno esdonde esta el XP y los otros estan en NTFS vacios.
el error es:
$Logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operacion no soportada Mount is denied because NTFS is mark to be in use ( Esto es lo que no entiendo, que significa "esta marcada para estar en uso2.
Chosse one action: 1 If you have windows then disconnect the external devices by clicking on the 'Safety Remove Hardware' icon in yhe windows taskbar.

Les agradezco cualquier dato que me puedan dar.

Desde Córdoba, Gambit!!

Te dice que se cerro "mal" en la sesion de windows, lo arreglas facilmente con entrar a windows y apagarlo "normalmente" no fuerzes el apagado. Entra a Ubuntu y los deberia tomar.

---

### Post by faktorqm on 2008-05-02
Para no reiniciar le podes tirar el fsck derecho, y luego montar. Es medio animal, pero funciona :D

---

### Post by rojojuan on 2008-05-02
Tengo la misma placa y funciona bien. Podés hacer lo siguiente:
Si actualizaste a Hardy, tenés que desinstalar los drivers anteriores y eliminar completamente Envy si lo tenías instalado.
Después instalar Envy a través de Sinaptics (está en los repositorios)
Correr envy y te instala los drivers de la placa.
Después, en Sistema vas a tener el programa de seteo de Nvidia de la placa y allí podés cambiar la resolución.
Si todo funciona bien, vas a ver que no podés guardar esa configuración y para solucionarlo corres "nvidia-settings" con sudo desde la consola; así te permite guardar la configuración que quieras.
Si no fui muy claro ampliamos.
Saludos

> **ghertzan said:**
> Buenas Gente!!
recen termino de ponerlo, 
Tengo 2 Problemas
1. No puedo cambiar la resolucion de la pantalla, en la version anterior lo podia hacer.
Tengo una GForce 7300 GS, ya se instalaron los controladores.
2. Los discos... Me dice que no los puede montar, uno esdonde esta el XP y los otros estan en NTFS vacios.
el error es:
$Logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operacion no soportada Mount is denied because NTFS is mark to be in use ( Esto es lo que no entiendo, que significa "esta marcada para estar en uso2.
Chosse one action: 1 If you have windows then disconnect the external devices by clicking on the 'Safety Remove Hardware' icon in yhe windows taskbar.

Les agradezco cualquier dato que me puedan dar.

Desde Córdoba, Gambit!!

---

