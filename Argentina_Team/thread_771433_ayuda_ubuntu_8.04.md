---
title: "ayuda ubuntu 8.04"
date: 2008-04-27
forum: Argentina Team
---

### Post by raxodemon on 2008-04-27
instale ubuntu 8.04 anteriormente tenia el 7.10 y windows xp en el mismo disco duro ahora tengo los tres pero quiero quitar el 7.10 como hago gracias

---

### Post by i586 on 2008-04-27
Intentá (usando, por ejemplo, **gparted**) borrar las particiones asociadas con aquella versión.

```

sudo apt-get install -y gparted

```

Saludo.

---

### Post by raxodemon on 2008-04-27
digite el codigo  sudo fdisk -lu

y me dio esto
yo se que el 7.10 esta en el sda2  su swap es el sda5 como los quito 
gracias
Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros, 160836480 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x00540054

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    62492849    31246393+   7  HPFS/NTFS
/dev/sda2        62492850    94237289    15872220   83  Linux
/dev/sda3        94237290   160826714    33294712+   5  Extendida
/dev/sda5       157806558   160826714     1510078+  82  Linux swap / Solaris
/dev/sda6        94237416   155091509    30427047   83  Linux
/dev/sda7       155091573   157806494     1357461   82  Linux swap / Solaris

---

### Post by raxodemon on 2008-04-27
gracias y luego de hacer eso?

sudo apt-get install -y gparted

---

### Post by raxodemon on 2008-04-27
es que soy nuevo en esto de ubuntu gracias

---

### Post by i586 on 2008-04-27
Abrí el **gparted**: Administración > GParted (te va a pedir que insertes la contraseña ya que debés ejecutarlo como **root**). Luego, buscá las particiones **sda2** y borralas. Luego, si querés, podés volver a formatearlas (con FAT para que sean, también, compatibles con M$ Window$ o bien en algún sistema de archivos compatible con Linux, por ejemplo: ext2 ó ext3).

Saludos.

PD: Es importante que consideres dónde instalaste el **GRUB**. Si no pusiste ninguna opción o no la viste al instalar el sistema, entonces es altamente probable que la tengas en **hd0**.

---

### Post by slimx3m on 2008-04-27
primero checkea en donde esta el GRUB como dice i586, porque si borras en el hd donde esta el GRUB no creo que vaya a poder boot y seleccionar el hd que vas a querer bootear

---

### Post by raxodemon on 2008-04-28
muchas gracias por la ayuda creo que ya esta saludos

---

