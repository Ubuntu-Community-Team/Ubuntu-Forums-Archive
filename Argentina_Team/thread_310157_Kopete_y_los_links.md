---
title: "Kopete y los links"
date: 2006-11-30
forum: Argentina Team
---

### Post by felipelerena on 2006-11-30
Tengo el siguiente problema:
cuando abro un link desde Kopete me lo abre con open office... además de que toma muchisimo tiempo abrir no me abre un a"pagina" sino un documento "de word".

Supongo que tendra que ver con el browser por defecto de KDE

Se me ocurrio que el problema se solucionaria sabiendo como se llama el paquete del progama de configuracion de KDE e instalarlo (por que uso Gnome) o desde algun archivo de configuracion... (ya me fije en mi ~ no encontre nada parecido a la conficuracion deseada).

si alguien sabe como solucionarlo please avise.

---

### Post by jpmorelli on 2006-11-30
El tema es que no teniendo KDE instalado no se como podrías solucionarlo, porque desde kcontrol vas a la parte de Componentes de KDE, y alli cambias las opciones de Aplicaciones predeterminadas y Asociaciones de archivos.
En Gnome creo que tambien debe estar por algun lado de la administracion pero no me acuerdo como se llama. CUalquier cosa cuando lo vea chiflo.

---

### Post by felipelerena on 2006-11-30
claro, el problema es que la configuracion de Gnome solo va para las aplicaciones de GTK, las de QT se manejan con la conf de KDE.

Creo que uno de los objetivos de proyecto portland (¿se llama asi?) es solucionar ese tupo de inconvenientes molestos

---

### Post by jpmorelli on 2006-11-30
Me parece que tenes que buscarlo por el lado de como asociar archivos o extensiones con tal o cual programa en Gnome, seguramente hay algo para hacer, aunque sea kopete.

---

### Post by jajajavi on 2007-01-24
> **jmorelli said:**
> Me parece que tenes que buscarlo por el lado de como asociar archivos o extensiones con tal o cual programa en Gnome, seguramente hay algo para hacer, aunque sea kopete.

No encuentro dónde configurar eso en gnome. Quiero hacer que los links de kopete se abran en firefox. Alguien sabe algo?

---

### Post by MeduZa on 2007-01-24
> **jajajavi said:**
> No encuentro dónde configurar eso en gnome. Quiero hacer que los links de kopete se abran en firefox. Alguien sabe algo?

yo tuve un problema parecido en ubuntu, todo se abria por defecto en el FF y yo uso seamonkey asi que tuve que editar varias cosas en el Configuration editor de Gnome y ahi repare eso (donde salia firefox yo ponia seamonkey)

---

### Post by kowal on 2007-01-24
Buenas, actualmente uso KDE, asi que buscando un poquito se me ocurre que podrías probar creando/modificando el archivo **~/.kde/share/config/kdeglobals** y agregarle unas lineas como estas:

[B][General]
BrowserApplication=!firefox[/B]

Saludos!

---

### Post by felipelerena on 2007-01-25
> **kowal said:**
> Buenas, actualmente uso KDE, asi que buscando un poquito se me ocurre que podrías probar creando/modificando el archivo **~/.kde/share/config/kdeglobals** y agregarle unas lineas como estas:

[B][General]
BrowserApplication=!firefox[/B]

Saludos!

copado, ahora en un rato lo pruebo y te digo

---

### Post by felipelerena on 2007-01-25
fantastico!!! funciono!!!

---

### Post by kowal on 2007-01-25
Me alegro que haya servido! Un abrazo.

---

