---
title: "Actualizar de Edgy a Feisty"
date: 2007-05-22
forum: Argentina Team
---

### Post by daz! on 2007-05-22
Hola a todos! tengo un cd con Feisty y quiero actualizar mi SO. Al inserta el cd yo esperaba algún actualizador automático (soy nuevo) pero no aparece nada. Oficialmente aconsejan hacer

 gksu "sh /cdrom/cdromupgrade" 

Lo ejecuto y no pasa nada.  (con y sin comillas) 

¿Cómo puedo actualizar desde el cd? 

Les hago otra pregunta buscando en los foros encuentro que algunos prefieren instalar desde cero y no actualizar. 

¿Qué recomiendan? 

Muchas gracias.

---

### Post by hernan blau on 2007-05-22
Te cuento lo que yo hice: con el disco live probé que Feisty anduviera en mi pc. No quise instalar desde cero porque ya tenía configuradas varias cosas a mi gusto. 
Quité el cd y desde terminal: sudo update-manager -c -d. Me fue bien. Suerte.

---

### Post by hernan blau on 2007-05-22
P.D: Me olvidé de decirte que me llevó aproximadamente tres horas el proceso.

---

### Post by undiaperfecto on 2007-05-22
No te fijaste si desde el Gestor de Actualizaciones tenes la opcion?
Fijate en Sistema>Administracion>Gestor de Actualizaciones, te deberia salir algo asi:

[img]https://help.ubuntu.com/community/FeistyUpgrades?action=AttachFile&do=get&target=update-manager-upgrade.png[/img]

---

### Post by fetova on 2007-05-22
Se supone que te debe de dar el update-manager la opcion: 

```
sudo update-manager -c -d
```

Pero si no te recomendaria que bajes el Alternate CD de Feisty y lo montes:

[LIST]
[*]Abre una terminal
[*]ejecuta sudo mount -o iso9660 -t loop (ruta del .iso ej. /home/usuario/Desktop/ubuntu-7.04-alternate-i386.iso) /media/cdrom
[/LIST]

y si no te aparece la actualizacion, abre cdrom y hay un archivo que dice (algo)upgrade y lo ejecutas.

Suerte!!

---

### Post by daz! on 2007-05-23
Muchísimas gracias a todos por su respuesta, creo que este tipo de cosas (la ayuda de la comunidad) hace la diferencia mas importante con windows!. 

Al final actualizé como lo suguirió undiaperfecto, pero me descargó +o- 1000 paquetes de internet y solo al final me pidió el cd. Yo lo dejé actulizando toda la noche no sé cuánto tardó. 
Lo que me llamó la atención fue que cuando reinicié respetó la configuración del temido modem de arnet.  Yo creía que iba a tener que configurar todo de nuevo. Grata sorpresa!. Ya estaba conectado.


Gracias de nuevo!

---

### Post by sebas.rhcp on 2007-05-23
A mi me paso lo mismo, el modem seguia funcionando como antes luego del upgrade.

---

### Post by fetova on 2007-05-23
> **daz! said:**
> Muchísimas gracias a todos por su respuesta, creo que este tipo de cosas (la ayuda de la comunidad) hace la diferencia mas importante con windows!. 



Yo por eso uso linux, se respira un ambiente de comunidad y eso me encanta :D
Gracias a todos por hacer esto posible ;)

---

