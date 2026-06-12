---
title: "compiz en ubuntu 7.10"
date: 2007-10-19
forum: Argentina Team
---

### Post by joseluis on 2007-10-19
Hola...al fin instalé el 7.10. Lo hice "limpio" porque el tema de actualizacion me largaba errores. Bueno, la cuestion es la siguiente, yo en 7.06 tenia unos efectos muuuy lindos y que me habia acostumbrado mucho del beryl y ahora no los encuentro. Paso a "describirlos_".

1. Ls ventanas, cuando se minimizaban lo hacian de una forma que iba como flotando y haciendose chiquita la ventana hasta el escritorio.
2. cuando hacia doble click sobre la banda superior de una ventana abierta, ésta se plegaba, como una persiana.
3. cuando pasaba el mouse por las ventanas minimizadas aparecia sobre la pantalla una miniatura de la ventana..esto me era muy practico..

¿siguen estando esos efectos...??' no los encuentro.

Por lo demás, me encanta esta versión...está muy bien

---

### Post by Hernán-Amaya on 2007-10-19
instalá el paquete que dice compizconfig-settings-manager y ahi vas a poder elegir los efectos que quieras, otra cosa fijate si tenes instalado el compiz-fusion plugins

espero haber sido de ayuda, suerte!

---

### Post by joseluis on 2007-10-19
si...ya tenía instalado todo . Entro al configurador y no encuentro esos efectos. Solo encontré el que muestra la ventana en miniatura..los otros que te decía no los encuentro...estan?

---

### Post by spg76 on 2007-10-19
Fijate si tenes todos los paquetes de plugins instalados.
Hace:

```
sudo apt-get install compiz-compcomm-plugins-main compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins
```

Con eso debería habilitarte todos los plugins que hay en los repositorios de Gutsy.

---

### Post by joseluis on 2007-10-19
me larga esto:


Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
compiz-fusion-plugins-extra ya está en su versión más reciente.
compiz-fusion-plugins-main ya está en su versión más reciente.
compiz-plugins ya está en su versión más reciente.
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  compiz-fusion-plugins-main: Entra en conflicto: compiz-compcomm-plugins-main (< 0.0.0+git20070622-0ubuntu1) pero 0.0.0+git20070612-0ubuntu1 va a ser instalado
E: Paquetes rotos

---

### Post by joseluis on 2007-10-20
Les cuento...selecciono todos los efectos que me gustan...¡¡y no los hace!! ¿cómo se habilitan? tengo todo instalado..gracias

---

