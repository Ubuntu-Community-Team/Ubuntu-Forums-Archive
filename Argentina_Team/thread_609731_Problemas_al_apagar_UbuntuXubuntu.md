---
title: "Problemas al apagar Ubuntu/Xubuntu"
date: 2007-11-11
forum: Argentina Team
---

### Post by krebscycle on 2007-11-11
Estoy usando Ubuntu 7.10 y Xubuntu 7.10 en el mismo computador, cada uno en su respectiva partición. En ambos casos luego de indicarle al S.O. que apague el computador aparece lo siguiente en pantalla:

**bogl_init failed: receding screen info: Innapropriate ioctl for device screen init failed**
*Unmounting temporary filesistems... [ok]
*Deactivating swap... [ok]
*Unmounting local filesistems... [ok]
*Will not halt
[10858.685497] System Halted

A partir de ese punto el proceso queda estancado y el computador no se apaga. Tengo que mantener apretado el boton de apagado durante unos segundos para que se apague de manera manual.

En otra partición del disco duro tengo instalado Win XP, el cual se apaga sin problemas.

Espero que alguien pueda ayudarme. De antemano graicas.

---

### Post by krebscycle on 2007-11-12
Logré resolver el problema.

Entré a la **BIOS y la configuré de modo que tuviera abilitada la función ACPI. **En el caso de mi tarjeta madre, esta opción está en la sección llamada "Power Manager".

Una vez hecho ésto, entré a Xubuntu y escribí en la terminal el siguiente código:

**sudo mousepad /boot/grub/menu.lst**

(En el caso de Ubuntu se debe cambiar la palabra "mousepad" por "gedit")

Con esto se abre un editor de texto para modificar el archivo menu.lst. En este archivo modififqué la primera línea que comenzaba con la palabra "kernel", agregando al final de la misma "**acpi=force**" (sin las comillas).

Posteriormente, y luego de reiniciar el sistema, Xubuntu se apaga sin problemas.

---

