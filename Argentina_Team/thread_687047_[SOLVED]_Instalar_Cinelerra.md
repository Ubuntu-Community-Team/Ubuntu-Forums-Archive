---
title: "[SOLVED] Instalar Cinelerra"
date: 2008-02-03
forum: Argentina Team
---

### Post by h9005 on 2008-02-03
Hola chicos necesito un poco de ayuda para instalar correctamente cinelerra: tengo estos links: [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3) , [http://cv.cinelerra.org/getting_cinelerra.php#ubuntu](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu) . Alguien que me guie!

---

### Post by User21 on 2008-02-04
Pues esta claramente explicado como instalarlo! En resumen es asi:
**NOTA: este modo de instalacion es para x86 - Ubuntu en 32 y 64 Bits.**

1) Agregar el origen de software a tus repositorios:
```
sudo gedit /etc/apt/sources.list
```Se te abrira la edicion de sources.list. Abajo de todo agregas esto:
[B]deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main
[/B]Guardas y cierras el archivo.

2) Añades la clave de autenticacion del servidor, tipeando en una terminal:
```
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add -
```3) Actualizas tus repositorios, en la misma terminal:
```
sudo apt-get update
```4) Instalas CINELERRA desde la consola, en cualquiera de sus 5 variantes conforme tus necesidades [ cinelerra (no opengl) - cinelerra-generic (with opengl) - cinelerra-k8 (with opengl) - cinelerra-k7 (no opengl)] - Diria que uses la cinelerra-generic o alguna que sea acorde a tu procesador, como K7 o K8. (ESO QUEDA A TU CRITERIO, verifica mas info en el sitio acerca de cada version)

```
sudo aptitude install cinelerra-generic
```Con eso deberia empezar a descargar el programa e instalarlo.
Si sale un error acerca de que no tienes la version correcta de la libreria libfaac, prueba instalando libfaac0!
```
 sudo apt-get install libfaac0
```Al menos, eso es lo que dice el sitio que enviaste!

---

### Post by h9005 on 2008-02-04
OK gracias anduvo de 10. Había intentado una vez y habia fallado.

---

### Post by User21 on 2008-02-05
**Damos este POST como resuelto?  (SOLVED) **
En el menu Thread Tools, de este foro, puedes asignarle la etiqueta SOLVED al post, de modo que otros con el mismo problema, sepan que pueden encontrar una solución aquí, y aquellos a los cuales no les interesa el tema, directamente ni entran, o no aportan ya que el mismo fue resuelto.

Saludos!

---

