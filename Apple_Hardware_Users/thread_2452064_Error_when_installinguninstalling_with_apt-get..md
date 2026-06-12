---
title: "Error when installing/uninstalling with apt-get."
date: 2020-10-15
forum: Apple Hardware Users
---

### Post by theasdas on 2020-10-15
Hello. I'm having issues when trying to manage software in Ubuntu. I'm not really sure what this error messages mean, but I get them when installing or uninstalling apps using the "sudo apt-get" command. This issue also happens when installing things from the Ubuntu Software Store.

The error message I'm getting is:
```
Error! Bad return status for module build on kernel: 5.4.0-51-generic (x86_64)
Consult /var/lib/dkms/nvidiabl/0.87/build/make.log for more information.
dpkg: error al procesar el paquete nvidiabl-dkms (--configure):
el subproceso instalado paquete nvidiabl-dkms script post-installation devolvió el código de salida de error 10
Se encontraron errores al procesar:
nvidiabl-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's in Spanish, but it basically says an error ocurred when processing the "nvidia-dkms" package, and it outputted an error with code 10. I checked the "make.log" file, and this is what is says:
```
DKMS make.log for nvidiabl-0.87 for kernel 5.4.0-51-generic (x86_64)
jue 15 oct 2020 23:16:53 -03
make: se entra en el directorio '/usr/src/linux-headers-5.4.0-51-generic'
  LEX     scripts/kconfig/lexer.lex.c
/bin/sh: 1: flex: not found
make[2]: *** [scripts/Makefile.host:9: scripts/kconfig/lexer.lex.c] Error 127
make[2]: *** Se espera a que terminen otras tareas....
  YACC    scripts/kconfig/parser.tab.[ch]
/bin/sh: 1: bison: not found
make[2]: *** [scripts/Makefile.host:17: scripts/kconfig/parser.tab.h] Error 127
make[1]: *** [Makefile:617: syncconfig] Error 2
make: *** [Makefile:723: include/config/auto.conf.cmd] Error 2
make: se sale del directorio '/usr/src/linux-headers-5.4.0-51-generic'
```

I believe this has to do with the n-NVIDIA drivers, which I had a really hard time installing in this Mac computer. 
Do you guys have any idea what this error is?

---

### Post by CelticWarrior on 2020-10-15
Welcome.

How exactly did you install the Nvidia drivers?

---

### Post by theasdas on 2020-10-16
Hello. I followed this tutorial: 
[https://medium.com/@nolanmudge/installing-an-nvidia-graphics-driver-with-a-ubuntu-14-04-and-up-efi-boot-52725dd6927c](https://medium.com/@nolanmudge/installing-an-nvidia-graphics-driver-with-a-ubuntu-14-04-and-up-efi-boot-52725dd6927c)
I'm not really sure what was I changing when following it, but it worked.

---

### Post by CelticWarrior on 2020-10-16
The guide is old and some steps may not be applicable today.
Before further troubleshoot please post the Nvidia card model and the driver version you actually installed.

---

### Post by theasdas on 2020-10-17
I have the Nvidia 320M, and I installed the "nvidia-340" and "nvidia-340-updates" packages. I had to follow the configuration steps from that guide, otherwise I would get a black screen when rebooting, and I had to reinstall the OS.
I also have the "nvidia-opencl-icd-340", "nvidia-settings" and "nvidiabl-dkms" packages installed.

---

### Post by CelticWarrior on 2020-10-17
[COLOR=#000000]"nvidia-340" and "nvidia-340-updates" are two different driver versions of the same branch, one is 340.xx and the other 340.yy where, supposedly, yy > xx.

Try using the GUI Additional Drivers to select and apply only what there is mentioned as "recommended". First remove all Nvidia drivers with ```
sudo apt-get remove nvidia*
```
Then use the boot parameter 'nomodeset': [/COLOR]https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu
This will allow booting graphically albeit with lower resolution. Open Additional Drivers then, select and apply the recommended one. Reboot.

---

### Post by theasdas on 2020-10-17
I tried that command and I got the following error:
"E: Invalid operation: nvidiabl-dkms_0.87_all.deb"

---

### Post by CelticWarrior on 2020-10-17
In that case you have other problems with packages that are above my pay grade.

---

### Post by ajgreeny on 2020-10-17
That command omitted the **remove** so run it again.
sudo apt-get remove nvidia*

---

### Post by CelticWarrior on 2020-10-17
I'm so sorry.
Corrected above for future readers.

---

### Post by ajgreeny on 2020-10-17
Thanks CW.

---

### Post by theasdas on 2020-10-18
Ok, so I believe  I know what might be the problem. I tried the corrected command in the console, and I got the following error messages:
```
E: No se ha podido localizar el paquete nvidiabl-dkms_0.87_all.deb
E: No se pudo encontrar ningún paquete usando «*» con «nvidiabl-dkms_0.87_all.deb»
E: No se pudo encontrar ningún paquete con la expresión regular «nvidiabl-dkms_0.87_all.deb»

```
Translating it from spanish, it basically says it cannot find the "nvidiabl-dkms_0.87_all.deb" package. 
That is weird, because when I do "apt list --installed | grep nvidia", I get the following result:
```
nvidia-340-updates/focal,now 340.108-0ubuntu2 amd64 [instalado]
nvidia-340/focal,now 340.108-0ubuntu2 amd64 [instalado]
nvidia-opencl-icd-340/focal,now 340.108-0ubuntu2 amd64 [instalado, automático]
nvidia-settings/focal-updates,now 440.82-0ubuntu0.20.04.1 amd64 [instalado, automático]
nvidiabl-dkms/now 0.87 all [instalado, local]

```
I believe that the system believes that the package is installed, but cannot find it.
Any idea how to solve this?

---

