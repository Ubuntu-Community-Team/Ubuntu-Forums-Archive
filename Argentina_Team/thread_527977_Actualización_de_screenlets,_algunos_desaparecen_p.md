---
title: "Actualización de screenlets, algunos desaparecen pero no los puedo instalar"
date: 2007-08-17
forum: Argentina Team
---

### Post by valucha on 2007-08-17
[COLOR="DarkOrchid"]Buenos días.
Hace unos días se actualizaron los screenlets y el tema es que cuando reinicié noté que no estaba ninguno de ellos.
Yo solía iniciarlos con screenletsd start. Pero al parecer no se habían iniciado.
Lo inicio desde el menú, (osea desde screenlets-tray) y me aparece el cuadro de diálogo de siempre para poner nuevos screenlets, pero no aparecen los mios.
Trato de agregarlos y me doy cuenta de que tampoco estaban para elegir en el cuadro de diálogo. En su reemplazo había muchos screenlets nuevos pero casi ninguno de los viejos.

Recurro a la página web [http://hendrik.kaju.pri.ee/screenlets/?q=node/14](http://hendrik.kaju.pri.ee/screenlets/?q=node/14) y dice que los screenlets viejos hay que instalarlos.
Bajo el archivo, leo el readme y dice que se instalan con un make install. Lo hago y siguen sin aparecer en el cuadro de diálogo.
Intento hacerlo manualmente, es decir, copiar todos los archivos en /usr/local/share/screenlets, pero siguen sin aparecer en el cuadro de diálogo.
Nuevamente trato de apretar el botón "INSTALAR" que tiene la misma ventana de  los screenlets y lo selecciono desde la carpeta /usr/local/share/screenlets, pero nuuuunca aparecen.


ALguien logró instalarlo, o podría ayudarme a hacerlo.
Muchas gracias desde ya.

PD: lei que de ahora en más no se inician más con screenletsd start
PPD: tengo instalado compiz fusion, pero tengo deshabilitado el efecto widget... asi que deberían aparecer bien.
Valentina.[/COLOR]

---

### Post by shadowboxer_k on 2007-08-19
hola valentina.

mi espanol no es muy bueno, pero tratare de explicarte como instalar los screenlets de nuevo. ese update si que fue una pesadilla...

desde el screenlets-tray puedes anadir el Control Screenlet y desde ahi (right click) puedes anadir todos los screenlets que quieras. incluso todos los viejos estan ahi y los encontraras. 

buena suerte.

---

### Post by valucha on 2007-08-19
[COLOR="DarkOrchid"]El tema es que me dice "/home/valen/.screenlets/NowPlaying/NowPlayingScreenlet.py installed!"

Y no lo veo en ningún lado, es como si nunca lo hubiese instalado.[/COLOR]

---

### Post by shadowboxer_k on 2007-08-19
intentare explicartelo en ingles porque te confundire mas con mi espanol, jejej...

open 
 applications --> accessories--> screenlets --> then add the screenlet that says Control and looks like a stop sign. once you add that one and right click it, you can add everything. Control screenlet-->right click--> add -- and then you'll see them all hidden there! they won't show in the initial tray in the beginning, but they're there in that list. just select and add.

it worked for me, it should work for you too.

---

### Post by valucha on 2007-08-20
> **shadowboxer_k said:**
> intentare explicartelo en ingles porque te confundire mas con mi espanol, jejej...

open 
 applications --> accessories--> screenlets --> then add the screenlet that says Control and looks like a stop sign. once you add that one and right click it, you can add everything. Control screenlet-->right click--> add -- and then you'll see them all hidden there! they won't show in the initial tray in the beginning, but they're there in that list. just select and add.

it worked for me, it should work for you too.


[COLOR="DarkOrchid"]Ahhh ok ahi entendí, lo traduzco por si aluien lo necesita.

"Abrir aplicaciones>accesorios>screenlets > ahi añadir el screenlet llamado "Control" que se asemeja a una señal de alto (la roja con la raya blanca en el medio). Luego hacer click dereche en él y ahi vamos a poder añadir de todo. Cuando hacemos click derecho sobre ese screenlet vamos a poder ver todos los screenñets, no van a estar en el panel del principio pero sí ahi. Entonces solo hace falta seleccionarlo y añadirlo.

funcionó para mi, deberia funcionarte a vos también"[/COLOR]

---

### Post by valucha on 2007-08-23
[COLOR="DarkOrchid"]Bueno probé lo que me contaste y no funcionó.
Reinstalé los screenlets y ahora se abren desde screenlets-manager. Ahi me aparecen todos los screenlets viejos que instalé tal como me dijo la página. Pero cada vez que quiero agregar uno de los viejos me manda:
FATAL ERROR: This screenlet seems to be written for an older version of the framework. Please download a newer version of the NowPlayingScreenlet.


Alguien sabe como puedo instalar la versión vieja?[/COLOR]

---

### Post by spg76 on 2007-08-23
Podés descargar los screenlets actualizados en [http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/)
Fijate los que dicen "Updated old 3rd party Screenlets"
Para instalarlos, tenes que descomprimirlos y copiar los que quieras a "/usr/local/share/screenlets" para reemplazar las versiones viejas.
Espero que te sirva.
Saludos.

---

