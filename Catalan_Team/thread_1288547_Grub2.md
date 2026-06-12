---
title: "Grub2"
date: 2009-10-11
forum: Catalan Team
---

### Post by jdk9 on 2009-10-11
Hola

Bé, ara torno as tenir un problema xD I és que he instal·lat Windows 7 després de l'Ubuntu 9.10 (si, ja ho sé noi es té quer fer) i no aconsegueixo tornar a instal·lar el grub. Què puc fer? He probat des de el Super Grub Disk, el qual se'm queda penjat, i des de el Live CD de Ubuntu 9.10, fent un "sudo grub-install --root-directory=/mnt/linux /dev/sda1" [FONT=Verdana]i no hem funciona, em retorna error.

Gràcies de nou per la vostra ajuda 
[/FONT]

---

### Post by kimet on 2009-10-12
Després d'entrar amb el live cd hasd e crear un directori on nstalar el grub.

```
 mkdir linux
```

Muntar la partició:

```
 sudo mount /dev/sda1 linux/
```

Muntar el proc.

```
 sudo mount -t proc /proc linux/proc
```

Muntar /dev

```
 sudo mount --bind /dev linux/dev
```

Etrar com a root i instalar grub:

```
 sudo chroot linux/
```

```
 grub-install /dev/sda
```

(al disc sda sense especificar la partició)
 
Si no em deixo res hauria de funcionar.

Salut.

---

### Post by jdk9 on 2009-10-12
Després de fer-ho, em detecta la carpeta gurb però li falta un fitxer

Gràcies!

---

