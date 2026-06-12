---
title: "Pregunta de administrador novato (aunque veterano)"
date: 2007-08-03
forum: Argentina Team
---

### Post by ccp on 2007-08-03
Hola amables foristas. Como comenté en un anterior post instalé una pc por primera vez con Linux. Ahí funciona Ubuntu Feisty- Apache2 - Mysql /phpmyadmin y finalmente Joomla 1.5. Registré un dominio en Dyndns y todo marcha ok.
Estaba remozando mi proyecto de sitio mediante el admin de Joomla y en un descanso me moví hasta otra pc (que está en otra parte) y le mostré a mi mujer lo que estaba haciendo vía web.( Esta 2da pc es muucho más moderna, rápida, etc., pero vino con Vista, que hasta ahora no me ha dado problemas.)
Se me ocurrió probar de loguearme como Admin de mi Joomla desde esa 2da pc, y lo hice fssssssss! hiper fast!.
Modifiqué algunas cosas del sitio, y también, ultra rápido.
Como era tarde me fui a dormir pensando: Mañana trabajo desde la 2da pc y mi trabajo de "tuneo" de mi sitio irá a 1000 por hora!!!.
La cosa fue que al otro día no podía entrar, en vez de abrir las páginas PHP me decía de guardarlas, etc. Un problema que motivó mi anterior post y que con la ayuda de este foro logré solucionar.
Ahora bien... mi pregunta es:
eso que trataba hacer (de acceder a Admin de Joomla, en un server LAMP) desde mi pc Vista, no es posible???
Si me dicen "NO", listo, no hace falta más. Si por el contrario es posible, no pido me expliquen todo sino las coordenadas de lo que debería hacer (o es que mi problema no se debió a ese acceso que hice sino a otra cosa? y simplemente puedo intentarlo del mismo modo nuevamente).
La cosa es que como soy nuevo en Linux, aun no me animo a "matar" al Vista de la 2da pc y saltar al vacío (pero ya lo haré, jaja) pero trabajar desde esa 2da pc sería fantástico ya que es muy superior a mi viejo ahora server-LAMP.
Gracias mil.
CCP

---

### Post by gepatino on 2007-08-03
mm...eso me suena a apache mal configurado... ¿seguro que no cambiaste la configuracion del apache antes de reiniciar el server?

cuando pasa eso es porque el apache no interpreta que las paginas php tienen que ser 'ejecutadas' en vez de 'servidas'

aca no tengo a mano un apache configurado, pero supongo que reinstalando (o reconfigurando con dpkg-reconfigure) el paquete de los modulos de php deberia volver a funcionar.

---

### Post by marianom on 2007-08-03
Me parece, ccp, que tanta claridad, oscureció. :) 
Si el site sigue funcionando ok, de la misma forma que entraste la última vez desde tu máquina nueva, deberías poder acceder para trabajar sin inconvenientes. Un acceso al sitio -por más Windows Vista que uses- no puede desconfigurar un apache así nomás. Entiendo que algo pasó la otra vez pero debe haber sido un error inadvertido cuando trabajabas en el server directamente.

Si existe algún problema puntual, hacelo saber y entre todos lo vamos viendo.

---

### Post by ccp on 2007-08-04
Thks again!!
Pruebo y cualquier cosa, aviso.
Saludos
CCP

---

