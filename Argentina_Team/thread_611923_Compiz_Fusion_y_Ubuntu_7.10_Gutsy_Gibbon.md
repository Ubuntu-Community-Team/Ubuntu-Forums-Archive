---
title: "Compiz Fusion y Ubuntu 7.10 Gutsy Gibbon"
date: 2007-11-13
forum: Argentina Team
---

### Post by Skavenger on 2007-11-13
[SIZE="5"]**[CENTER]Compiz Fusion y Ubuntu 7.10 Gutsy Gibbon[/CENTER]**[/SIZE]

Si tu placa de video usa drivers restringidos habras notado que Compiz Fusion no funciona. Esto es porque tenes que instalar esos drivers y activar Compiz


[SIZE="2"]**1 - Instalamos el driver**[/SIZE]

Vamos a **Sistema > Administracion > Gestor de controladores restringidos**

[IMG]http://img204.imageshack.us/img204/1994/01ee7.jpg[/IMG]


Nos aparece esta ventana, ahi marcamos la casilla y cerramos

[IMG]http://img250.imageshack.us/img250/4848/02jm9.jpg[/IMG]


Ahora nos pide que reiniciemos la maquina


[SIZE="2"]**2 - Instalamos la utilidad grafica de Compiz y Emerald**[/SIZE]

Esta utilidad nos va a permitir configurar Compiz y con Emerald la decoracion de las ventanas

Para instalarlas abrimos una terminal: **Aplicaciones > Accesorios > Terminal** y tipeamos lo siguiente:

```
sudo apt-get install compizconfig-settings-manager
sudo apt-get install emerald
```

Una vez completado, vamos a **Sistema > Apariencia > Efectos visuales** y marcamos la casilla **Personalizado**

[IMG]http://img223.imageshack.us/img223/1192/03gx4.jpg[/IMG]


A partir de aca podemos configurar Compiz desde **Sistema > Preferencias > Advance desktop effect settigs**. Recomiendo tocar TODO hasta quedar satisfechos =P [pueden volver al estado default de cada cosa si no les gusto algo], es muuuuuy configurable :)

[IMG]http://img131.imageshack.us/img131/1659/04yp0.jpg[/IMG]


[SIZE="2"]**3 - Configuracion de Emerald**[/SIZE]

La configuracion de Emerald es mucho mas simple que la de Compiz, pero antes de poder configurar las ventanas tenemos que bajar los temas, para esto podemos ir a alguna de los siguientes sitios y buscar lo que nos guste:

- [http://www.gnome-look.org/](http://www.gnome-look.org/)
- [http://art.gnome.org/](http://art.gnome.org/)
- [http://gnomestyle.blogspot.com/](http://gnomestyle.blogspot.com/)

Una vez que bajamos los temas, vamos a **Sistema > Preferencias > Emerald theme manager**, hacemos click en **Importar** y buscamos el archivo **.emerald** que bajamos y aceptamos, y asi sucesivamente con los temas que hayan bajado. Podemos ver como quedan con solo clickear en cada uno de ellos

[IMG]http://img159.imageshack.us/img159/2974/05rd2.jpg[/IMG]


Y por ultimo, un video demostracion de Compiz Fusion:

[YouTube - Compiz Fusion Development]("http://www.youtube.com/watch?v=_ImW0-MgR8I")

---

### Post by sajnox on 2007-11-13
Muy buen post.

Espero que sea de utilidad para muchos

(ojo los que tienen placas ati todavia no lo usen)

---

### Post by leonardo83 on 2007-11-13
Y con ubuntu 7.04 como lo hago ????? :confused:

---

### Post by Skavenger on 2007-11-13
con 7.04 es mas complicado
aca hay muchas guias
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

---

### Post by majatu on 2007-11-14
Instalé emerald y todo lo que me pedia para q andubiece bien en relación a repositorios, la cosa s que me baja desde el mismo emerald solo temas NO GPL y yo tambien quiero q me baje los que tienen licencia GPL (cuando hago clic en el boton para bajarlos me carga como si los estubiece bajando pero no baja nada) como puedo hacer? a alguien le pasa?

otra duda, yo con ubuntu 7.04 +beryl+emerald podia elegir cual sería mi gestor de temas por defecto, en compiz+emerald en ubuntu 7.10 no encontré esa opcion, como puedo hacer?

todo esto pasa porque si yo quiero volver mi sistema a su estado por defecto, con el tema human, no puedo, porque o en emerald no tengo el paquete gpl "human" porque no me lo baja, o porque tampoco encuentro como deshabilitar emerald, para ir entonces a apariencia y elegir human desde ahi.

un saludo! espero haberme explicado bien, muchas gracias por sus respuestas!

---

### Post by User21 on 2007-11-14
Bajate los temas de emerald que encuentres en [www.gnome-look.org](www.gnome-look.org). y listo, amigazo! los agregas desde el administrador de temas de Emerald. que mas , cumpa ??? xD n_n

---

### Post by majatu on 2007-11-14
y si quiero desactivar emerald, osea, poder elegir los temas por defecto que trae en el menu apariencia?

---

### Post by sajnox on 2007-11-14
Para elegir el decorador de ventanas, en Compiz settings manager / windows decorator (decoracion de ventanas)

incluir la siguiente linea

Emerald = emerald --replace

GTK = gtk-window-decorator --replace

esto lo soluciona

---

### Post by sajnox on 2007-11-14
> **majatu said:**
> Instalé emerald y todo lo que me pedia para q andubiece bien en relación a repositorios, la cosa s que me baja desde el mismo emerald solo temas NO GPL y yo tambien quiero q me baje los que tienen licencia GPL (cuando hago clic en el boton para bajarlos me carga como si los estubiece bajando pero no baja nada) como puedo hacer? a alguien le pasa?

otra duda, yo con ubuntu 7.04 +beryl+emerald podia elegir cual sería mi gestor de temas por defecto, en compiz+emerald en ubuntu 7.10 no encontré esa opcion, como puedo hacer?

todo esto pasa porque si yo quiero volver mi sistema a su estado por defecto, con el tema human, no puedo, porque o en emerald no tengo el paquete gpl "human" porque no me lo baja, o porque tampoco encuentro como deshabilitar emerald, para ir entonces a apariencia y elegir human desde ahi.

un saludo! espero haberme explicado bien, muchas gracias por sus respuestas!

Para que te descargue todos los temas de los repositorios de emerald anda al tab de repositories y segui las instrucciones que estan al pie en la ventana que son para habilitar todos las decoraciones

---

### Post by majatu on 2007-11-14
> **sajnox said:**
> Para elegir el decorador de ventanas, en Compiz settings manager / windows decorator (decoracion de ventanas)

incluir la siguiente linea

Emerald = emerald --replace

GTK = gtk-window-decorator --replace

esto lo soluciona

me podes explicar mejor como hacer eso?:confused: me siento perdido, encontre el decorador de ventanas en compiz pero ahi no se q hacer

---

### Post by majatu on 2007-11-14
> **sajnox said:**
> Para que te descargue todos los temas de los repositorios de emerald anda al tab de repositories y segui las instrucciones que estan al pie en la ventana que son para habilitar todos las decoraciones

mira lo que me dice si hago lo del pie de ventana:

marcelo@Marcelo-desktop:~$ svn ls [http://svn.generation.no/emerald-themes](http://svn.generation.no/emerald-themes)
svn: requerimiento PROPFIND falló en '/emerald-themes'
svn: PROPFIND de '/emerald-themes': 301 Moved Permanently ([http://svn.generation.no](http://svn.generation.no))

---

### Post by leonardo83 on 2008-04-27
mira yo baje los archivos que decis o sea, 

sudo apt-get compiz bla bla y el de install emerald

despues la placa nvia (legacy, viejita) la tengo activada ok

me aparece el emerald manager y la parte de darle efectos a la ventana y demas

PEEEERO cuando voy a efectos de escritorio y elijo la ultima opcion me dice 

```
Desktop effects could not be enabled
```

Falta habilitar algo o que???

Ya instale todo y pense que iba a andar, que paso me falta realizar ??? :confused::confused::confused::confused::confused::confused:

Gracias.

---

