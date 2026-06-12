---
title: "¿Para cuando estiman que estara disponible Thunderbird 2 en Ubuntu?"
date: 2007-08-17
forum: Argentina Team
---

### Post by djthree on 2007-08-17
Hola,

Estoy usando Thunderbird 2.0 , antes de eso, probe la version 1.5 que esta en los repositorios de ubuntu y a mi entender esta bastante lejos de esta nueva version que tiene muchas de las funciones que necesito en un cliente de correo, el manejo de SPAM es realmente muy bueno!

Alguno sabe para cuendo puede llegar a estar la version 2.0 de thunderbird en los repositorios de ubuntu?

Saludos!

---

### Post by faktorqm on 2007-08-17
Yo no tengo idea, pero esta en el automatix, o la podes compilar a mano. ¿cual es el problema? En realidad los repositorios de ubuntu te seguran que los programas son estables, que son 100% compatibles y están "tocados" para que todo funcione excelentemente. Ahora bien, todo lo que compile siempre me anduvo, salvo los drivers del modem huawei en la casa de un amigo xD
salu2!

---

### Post by spg76 on 2007-08-17
> **djthree said:**
> Hola,
Alguno sabe para cuendo puede llegar a estar la version 2.0 de thunderbird en los repositorios de ubuntu?


Lamentablemente no creo que la versión 2 se vaya actualizar en los repositorios de Feisty. Tendrían que a hacer un backport y a dos meses de la salida de Gutsy lo veo poco probable.

---

### Post by por100pre1 on 2007-08-17
[Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") es un script en Python que te sirve para instalar Thunderbird 2, Firefox 2, y hasta SeaMonkey facilmente. Si tanta lectura te molesta descargalo directamente:

```
wget http://umn.dl.sourceforge.net/sourceforge/ubuntuzilla/ubuntuzilla_4.1.1.py
```

renombralo a "ubuntuzilla.py":

```
mv ubuntuzilla_4.1.1.py ubuntuzilla.py
```

y ejecutalo:

```
python ~/ubuntuzilla.py -a install -p thunderbird
```

sigue las instrucciones y listo. :)

---

### Post by nanotube on 2007-08-18
hola
una coreccion: la mas nueva version de ubuntuzilla es ubuntuzilla 4.3.0. por eso, usa la homepage de ubuntuzilla para escoger la mas nueva version.

---

### Post by por100pre1 on 2007-08-19
> **nanotube said:**
> hola
una coreccion: la mas nueva version de ubuntuzilla es ubuntuzilla 4.3.0. por eso, usa la homepage de ubuntuzilla para escoger la mas nueva version.

Si, pero la nueva version viene como un packete .deb, y requiere instalarse. Ademas, la nueva version puede ser un fastidio para algunos buscando actualizaciones. Por eso usé intencionalmente la otra version que es mas viejita pero funciona bien, y no requiere instalación. :)

---

### Post by nanotube on 2007-08-19
> **por100pre1 said:**
> Si, pero la nueva version viene como un packete .deb, y requiere instalarse. Ademas, la nueva version puede ser un fastidio para algunos buscando actualizaciones. Por eso usé intencionalmente la otra version que es mas viejita pero funciona bien, y no requiere instalación. :)

si no quiere instalar el .deb, es posible abrir el .deb con "archive manager" y extraer ubuntuzilla.py manualmente. asi, puede usar la mas nueva version (con algunos bug fixes), y no instalar .deb. 

pero porque to instalar? el .deb viene con una pagina man, y con un "self updater"... tambien, es posible deinstalar despues de usarlo. :)

ahora no es muy importante, porque ambos funcionan bien. pero en el futuro, mozilla puede cambiar su pagina y file mirrors, y versiones viejos ya no seran utiles...

---

### Post by por100pre1 on 2007-08-19
> **nanotube said:**
> si no quiere instalar el .deb, es posible abrir el .deb con "archive manager" y extraer ubuntuzilla.py manualmente. asi, puede usar la mas nueva version (con algunos bug fixes), y no instalar .deb. 

pero porque to instalar? el .deb viene con una pagina man, y con un "self updater"... tambien, es posible deinstalar despues de usarlo. :)

ahora no es muy importante, porque ambos funcionan bien. pero en el futuro, mozilla puede cambiar su pagina y file mirrors, y versiones viejos ya no seran utiles...

Vamos a ejecutar la version mas reciente como nos sugiere Nanotube:

Primero lo descargamos:

```
wget http://easynews.dl.sourceforge.net/sourceforge/ubuntuzilla/ubuntuzilla-4.3.0-0ubuntu1.deb
```

...lo instalamos:

```
sudo gdebi -i ubuntuzilla-4.3.0-0ubuntu1.deb
```

removemos el instalador (opcionalmente):

```
rm ubuntuzilla-4.3.0-0ubuntu1.deb
```

finalmente ejecutamos ubuntuzilla asi:

```
ubuntuzilla.py -a install -p thunderbird
```

Gracias a Nanotube por este excelente script y por orientarnos siempre.
:popcorn:

---

### Post by nanotube on 2007-08-19
gracias, por100pre1 :)
pero una pequena coreccion. para instalar, es mas facil utilizar "gdebi" en vez de "dpkg", porque gdebi va a cuidar de todos dependencies automaticamente.
asi,
```
sudo gdebi -i ubuntuzilla-4.3.0-0ubuntu1.deb
```

y el "apt get -f" no es necesario. :)

---

### Post by por100pre1 on 2007-08-19
Gracias Nanotube, correción hecha. :)

---

### Post by nanotube on 2007-08-19
> **por100pre1 said:**
> Gracias Nanotube, correción hecha. :)

:guitar: ;)

---

