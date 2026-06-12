---
title: "CUPSYS Error returned"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2008-01-09
After performing suggested upgrade today, I received the following error message:  E: CUPSYS: subprocess post-installation script returned error exit Status 1.  I looked at what appeared to be related posts, but did not find a solution I understood.  I uninstalled CUPSYS and re-installed it only to get the same message.  Obviously, I can no longer print.  How do I fix?
Thanks
CB

---

### Post by Deadmode on 2008-01-10
can you post your logs from /var/log/cups then nano or gedit error_log

---

### Post by FGambaro on 2008-01-11
Hi, this is my firts post in this forum, 

I`m from Uruguay and speack spanish.

I've same problem here wath I recive:


Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
cupsys ya está en su versión más reciente.
cupsys-client ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
2 no instalados del todo o eliminados.
Necesito descargar 0B de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando cupsys (1.3.2-1ubuntu7.5) ...
$Loading AppArmor module: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error al procesar cupsys (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depende de cupsys (>= 1.2.5) | cups (>= 1.2.5); sin embargo:
 El paquete `cupsys' no está configurado todavía.
  El paquete `cups' no está instalado.
dpkg: error al procesar cupsys-driver-gutenprint (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 cupsys
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

thanks

---

### Post by FGambaro on 2008-01-11
I`m usin Kubuntu Gutsy Up to Date, and with some tunning (compizGT, KBFX)
on  
Celeron 1,7Ghz, 512Mb RAM 2 HD 40Gb (primary) 120Gb (secondary)
Nvidia Gforce MX440 64Mb

My problem with cupsys happend before trying to clean up unused files, using 
prugars.sh

for i in `deborphan --guess-all`
do
sudo aptitude remove $i
done


At last I found uno solution for "Reloading AppArmor profiles : done" 
using synaptic download linux-headers-2.6.22-14-server, linux-386, linux-generic

but now oder problems still without solution, 

Configurando cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error al procesar cupsys (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any Idea?

thank's

---

### Post by Imsdal on 2008-01-21
> **Deadmode said:**
> can you post your logs from /var/log/cups then nano or gedit error_log

I had the same problem as OP. I checked the contents of the /var/logs/cups directory as suggested. It turned out that I didn't have such a directory and the installer failed because of it. The installer noted that he directory was missing, but it wasn't obvious (to me) that this was the reason the installer failed. I think this is a bug that should be reported somewhere. How do I do that?

Anyway, sudo mkdir /var/log/cups and rerunning the installer worked for me.

---

