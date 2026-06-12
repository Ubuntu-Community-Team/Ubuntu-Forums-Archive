---
title: "Partición Raíz / se ha quedado sin espacio"
date: 2018-05-16
forum: Argentina Team
---

### Post by aussith9nt on 2018-05-16
Hola, hace poco traté de instalar el RemixOS en mi Xubuntu, pero no revisé el espacio disponible y se quedó mi partición root (de 19GB y algo) con 30MB de espacio libre aproximadamente. No tengo el GParted instalado, pero me descargué el Live y le traté de quitar 20GB a la partición /home que tenía aproximadamente 67GB y lo logré, pero se lo pude añadir a /. Ahora mi computadora no puede apagar ni abre el Chromium. Mi Xubuntu es 16.04.1 LTS Xenial Xerus de 32 bits, no puedo instalar ni eliminar ninguna aplicación. Si mal no recuerdo, mis particiones están organizadas así:

100MB Reservado para el Sistema (Creo que es de Windows). Libre: Creo que 78,7MB.
60GB (aprox.) Windows. Libre: 13GB y algo.
2MB Sin asignar.
Extendida:
(/dev/sda5) 19GB / (root). Libre: 30MB (aprox.).
(/dev/sda6(creo)) Creo que 3GB swap. Libre: No me acuerdo.
(/dev/sda7) 48GB (antes 67GB) /home. Libre: 21GB.
20GB (aprox.) Sin asignar.

df -h:

S.ficheros                Tamaño             Usados                Disp                  Uso%                Montado en
udev                                           984M                           0                                        984M            0%                        /dev
tmpfs                                    201M                         6,4M                         195M              4%                     /run
/dev/sda5       19G                               19G                                 0                        100%         / 
tmpfs                                     1003M           16M                              987M              2%                  /dev/shm
tmpfs                                       5,0M                           8,0K                          5,0M               1%                  /run/lock
tmpfs            1003M                        0                                       1003M           0%                  /sys/fs/cgroup
/dev/sda7                48G                                 25G                              21G                55%                /home
tmpfs                                    201M                        40K                               201M                1%                  /run/user/1000
/dev/sda2                59G                               46G                             14G           78%               /media/judith/60500F84500F6060               (Windows)
/dev/sda1                100M                     25M                   76M                 25%                /media/judith/Reservado para el sistema    (Sistema de Windows)

Si necesitan más información solo avisen, muchas gracias.

PD: ¿No parece extraño que tenga 5 "tmpfs"?
PDD: Disculpen por lo desordenado de la lista, no sabía cómo ordenarla XD.

---

