---
title: "Problem Installing PACGEN"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by ptosiani on 2006-11-19
I Downloaded pacgen110.tar.gz from sourceforge, i tried to install it using the ./install.sh but it keeps sending me this truoble:

Compiling pacgen.c version 1.10 to binary pacgen using gcc
pacgen.c: En la función ‘main’:
pacgen.c:160: aviso: el puntero que apunta en el paso del argumento 10 de ‘libnet_build_tcp’ difiere en signo
pacgen.c:178: aviso: el puntero que apunta en el paso del argumento 5 de ‘libnet_build_udp’ difiere en signo
pacgen.c: En la función ‘convert_proto’:
pacgen.c:405: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:408: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:411: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:414: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c: En la función ‘convert_toscontrol’:
pacgen.c:421: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:424: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:427: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:430: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:433: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:436: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:439: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:442: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:445: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo
pacgen.c:448: aviso: el puntero que apunta en el paso del argumento 1 de ‘strstr’ difiere en signo


I see that the problem is related with something called libnet, i installed libnet though aptitude. sudo aptitude install libnet-dev.

So.. i dont know waht to do.. any ideas..? :confused: :confused: 

I'm using Ubuntu 6.06 LTS - Dapper Drake

---

