---
title: "Desocupar particion!"
date: 2008-04-19
forum: Argentina Team
---

### Post by h9005 on 2008-04-19
Hola tengo la particion a full y no se que borrar! AYUDA!

Olvide mencionar que es la particion del so.

---

### Post by pol666 on 2008-04-19
Cuanto tiene? le pusiste juegos..

Con 5gb tendrias que tener la particion mas que fluida.

---

### Post by sajnox on 2008-04-20
Podrias ser un poco mas especifico?

Tamaño de la particion?

Descargaste muchas cosas?

Tenes el /home separado ?

Tenes mas espacio en el disco ?

en una consola escribi lo siguiente y postea el resultado.

```
sudo fdisk -l
```

---

### Post by h9005 on 2008-04-24
Tengo aparte el home. Descargue algunos juegos pero dos o tres nada más. es de 10 gb y tengo ocupados ocho y algo!

---

### Post by SLA_leandrin on 2008-04-24
Probá con 

 sudo apt-get autoclean

Algo de espacio te va a liberar. Esto lo que hace es borrar los instaladores que van quedando de lo q le instalaste o actualizaste.

---

### Post by h9005 on 2008-04-24
Ya usé ese comando. Ni se movio sigue lleno.

---

### Post by Hei Ku on 2008-04-25
podes fijarte en /var/log si tenes mucho. esos son logs, asi que podes copiarlos a un backup y borrar lo q esta ahi.

---

### Post by h9005 on 2008-04-30
No se porque se me han amontonado tantos gigas. Tantas actualizaciones va a descargar?

---

### Post by Mister X on 2008-04-30
podes usar el baobab para rastrear en que estas usando tanto espacio, es una herramienta grafica muy util en estos casos.

yo tengo 4.6 Gb usados con bastantes cosas instaladas, 8Gb es mucho

---

### Post by spg76 on 2008-04-30
También podés hacer en una terminal:
```
sudo apt-get clean
```
Con eso borras todo el cache de APT, a diferencia de autoclean que deja algunos paquetes. Si nunca lo hiciste e instalaste varios programas te puede ocupar bastante espacio.

---

### Post by h9005 on 2008-05-05
Ya descubrí que es una de las cosas que ocupa tanto espacio:

---

### Post by h9005 on 2008-05-06
Qué es esto? Ayuda! Parece el registro de windows.

---

### Post by atatiducken on 2008-05-06
clamav es un antivirus? si es asi fijate desinstalandolo con **purge**, yo no uso antivirus y ando sin problemas

---

### Post by Hei Ku on 2008-05-06
desinstalalo con purge, y volvelo a instalar. el antivirus no esta de mas tenerlo, para no contagiar a otros usuarios de virus que si bien a vos no te afectan, a otros quizas si. una cosa de buen ciudadano, vio?

---

### Post by h9005 on 2008-05-10
Y como desinstalo con purge? Lo hice desde añadir/quitar programas.

---

### Post by h9005 on 2008-05-10
No puedo borrar la carpeta clamav!

---

### Post by Hei Ku on 2008-05-10
salvo que intentes con sudo, no la vas a poder borrar.

proba con: sudo apt-get remove --purge clamav

---

### Post by h9005 on 2008-05-10
Ya lo use pero el espacio sigue ocupado. Como hago parar borrar la carpeta del archivo raíz.

---

### Post by WanderingKnight on 2008-05-11
/var/ es donde se almacenan los logs, pero estos no son muy necesarios que digamos, mucho menos los de clamav.

Simplemente hacé:

```
sudo rm -rf /var/lib/clamav
```

...y eso se deshará de la carpeta.

De todas formas, como son logs periódicas de clamav, lo más probable es que te vuelva a ocurrir. La verdad te recomendaría que quitaras a clamav de tu sistema, no vale mucho la pena, más allá de evitar que otros se infecten (que se ***! :p).

---

### Post by h9005 on 2008-05-11
OK gracias! Lo desinstale pero no lo use nunca. No se ni para que sirve! Se puede conf para que no haga eso?

---

