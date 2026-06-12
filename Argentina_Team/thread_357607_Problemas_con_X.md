---
title: "Problemas con X"
date: 2007-02-09
forum: Argentina Team
---

### Post by Mafber on 2007-02-09
Hola. tengo un problema!!! Después de instalar Internet Explorer en Ubuntu (sí, ya se que ese es el error) cuando reinicio me tira un error de X y no me deja entrar al modo grafico. No tengo ni idea como solucionarlo :( 
Les dejo el log del error así lo pueden ver y plantearme alguna solución.
Gracias desde ya!!! :)


NO quiero reinstalar... me niego!!! (además eso seria una solución windistica)

---

### Post by beuno on 2007-02-10
Como comienzo te diria que ejecutes:
```
sudo dpkg-reconfigure xserver-xorg
```

Eso te va a reconfigurar las X.
Por lo que dice el log, al driver de nvidia no le gusta tu placa de video, asi que sospecho que algo se te debe haber desinstalado.
Resetea a defaults con ese comando (creo que corresponde el driver "nv"), y reinstala los drivers de nvidia.
Podes usar esto: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Mafber on 2007-02-10
beuno: muchas gracias, funcionó. 
lo malo es que voy a tener que instalar de nuevo la placa de vídeo. La ultima vez que lo hice fue un calvario, me costó muchísimo.
Ahora voy a ver como me va!! 
gracias de nuevo

---

