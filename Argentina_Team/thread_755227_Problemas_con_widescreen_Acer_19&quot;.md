---
title: "Problemas con widescreen Acer 19&quot;"
date: 2008-04-14
forum: Argentina Team
---

### Post by om11_99 on 2008-04-14
Problema

Resulta que quiero pasar a GNU/LINUX, nada Gente me canse de windows y quiero experimentar con algun sistema operativo SO real.

Me puse a instalar en un inicio Kubuntu, pero cuando inicio me da problemas, uan vez que empieza a iniciar se me queda la pantalla en negro y me informa el monitor out range frecuency, he arrancado con el disco de ubunti y le he configurado bajar la resolucion , pero automaticamente me la cambia y viene el bateo.

Como puedo cambiar las opciones graficas ya sea frecuencia y pixels para que ubuntu arranque.

Saludos
OMAR

---

### Post by sajnox on 2008-04-14
Yo probaria con lo siguiente, ya que evidentemente no te reconoce el monitor correctamente.

cuando empieza el "bateo" apretas ctrl + alt +f1 y te vas a una consola, te va a pedir que te loguees, para eso el user es: ubuntu y no tenes que usar password. Una vez adentro escribis

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Para que redetecte el monitor y configure, y luego tipeas 

```
sudo /etc/init.d/gdm restart
```

Para que reinicie la grafica.

Si esto no te funciona podes probar la primer linea sin el -phigh y configurar manualmente las opciones que te pide.

Plan B, usa el alternate CD (implica bajarte de nuevo el disco de instalacion)

Proba con eso, igual seguramente algunos mas te tiraran algunas otras ideas

Contanos como fue

---

