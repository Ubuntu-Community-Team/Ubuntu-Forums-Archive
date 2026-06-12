---
title: "Firefox no carga imágenes en forma directa"
date: 2008-05-02
forum: Argentina Team
---

### Post by eduf on 2008-05-02
Paso a comentarles, instalé ubuntu 8.04 y al ir a la página del diario clarin me dice que tengo que instalar plugs-in para poder verla en forma correcta, hasta acá todo bien, realizo la descarga y dejo marcado el plug-in que trae por defecto, pero ahora viene el problema, y es que en la anterior versión, firefox 2, las imágenes se veían cuando se cragaba la página ahora me aparece un cadrado gris con un triángulo en el medio, como el play que se ve en youtube, con algunas imágenes no con todas, y al darle click recién muestra la imágen, esto no solo me ocurre con la página de clarín, sino con el resto de las páginas, les dejo las imágenes. Espero por favor alguna ayuda ya que esto me resulta muy molesto.
Aclaro que ya me fijé en preferencias del firefox y en contenido está tildado cargar las imágenes en forma automática.

---

### Post by Mauro22 on 2008-05-02
Hola!

No son las imagenes. Son contenidos flash.


Eso te paso porque no estas usando el reproducto flash adecuado.

Abri al consola y hace:

sudo apt-get purge gnash              * Por las dudas
sudo apt-get purge swfdec-mozilla   * Seguro instalaste este la vez que te preguntó
			 				sudo apt-get install flashplugin-nonfree  			 		* Este es el que va.


:lolflag:

---

### Post by eduf on 2008-05-02
Mauro22 funcionó perfecto, desde ya muchas gracias has sido muy amable.


:):):):)

---

