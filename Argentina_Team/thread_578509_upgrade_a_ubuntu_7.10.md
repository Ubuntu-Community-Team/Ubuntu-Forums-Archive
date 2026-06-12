---
title: "upgrade a ubuntu 7.10"
date: 2007-10-17
forum: Argentina Team
---

### Post by joseluis on 2007-10-17
Hola amigos ....¿¿podrían hacer un tutorial EN CASTELLANO sobre cómo pasar de Ubuntu 7.04 a 7.10? Los leo en inglés y no quiero tener problemas. Por favor. Gracias

---

### Post by Mataca on 2007-10-17
Por lo que tengo entendido es solamente abrir una consola y escribir

```
update-manager
```

este comando es para cuando ya este la version final en el servidor, o sea el 18/10/07, si la queres hacer antes de esa fecha usá

```
update-manager -d
```

yo instalé de esta forma y ya tengo la 7.10 rc instalada en casa :)

---

### Post by Mauro22 on 2007-10-17
Hoy se hizo un update de casi 200 mb, parece que esta listo!!

:popcorn::lolflag:

---

### Post by sharkg on 2007-10-17
yo por las dudas espero a mañana.... pero creo q ya por estas horas deberia de estar listo todo no??

---

### Post by niko_3100 on 2007-10-17
Solo con escribir en la consola update-manager te actualiza a gutsy?

---

### Post by Mataca on 2007-10-17
> **niko_3100 said:**
> Solo con escribir en la consola update-manager te actualiza a gutsy?

Tengo entendido que si, por favor si alguno sabe algo mas, q postee. Pero estoy muy seguro que funciona así

---

### Post by Hernán-Amaya on 2007-10-18
entren acá [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) ahí explica varias formas de pasar de feisty a gutsy

a disfrutar que ya es 18!!!!!

---

### Post by niko_3100 on 2007-10-18
Me parece que tengo que tener las actualizaciones de feisty al dia para pasar a 7.10 nunca actualice nada de las actualizaciones correspondientes a la version 7.04 tendria que actualizar todo y despues me va a aparecer actualizar a 7.10???

Es decir nunca hize updates de feisty por eso no me deja hacer un upgrade a gutsy??

---

### Post by spg76 on 2007-10-18
niko_3100, para actualizar a Gutsy, primero tenes que tener instaladas todas las actualizaciones de Feisty.
Después vas a poder hacer el upgrade.

---

### Post by niko_3100 on 2007-10-18
Sacreblouuu!!!! Me tengo que bajar 220 megas de feisty para poder actualizar a gutsy me parece que me pido el live CD y mientras me bajo uno asi lo ahgo todo de cero jeje!!!

---

### Post by steve_ignorant on 2007-10-18
> **niko_3100 said:**
> Sacreblouuu!!!! Me tengo que bajar 220 megas de feisty para poder actualizar a gutsy me parece que me pido el live CD y mientras me bajo uno asi lo ahgo todo de cero jeje!!!

me parece que no es tan fatal... si el gestor lo hace todo solo... ademas asi no configuras todo de nuevo... no se me parece ami... es una opinion, pero ami tambien me pidio bajar todo, la diferencia es que apenas la pude conectar a internet desde el ubuntu le actualize todo... 

pero bueno, miralo de este lado si bajas peliculas de 1 giga, bajar 220 megas, no es tanto, salvo que tengas dial-up, lo contrario al wi-fi(jajaja broma :))

---

### Post by niko_3100 on 2007-10-18
Jajaja tengo conexion banda ancha pero de... 128 kbps :( por eso

---

### Post by steve_ignorant on 2007-10-18
> **niko_3100 said:**
> Jajaja tengo conexion banda ancha pero de... 128 kbps :( por eso



es banda ancha al fin, en todo caso a la noche, ponelo  a actualizar asi cuando te levantas tenes que reiniciar el sistema y listo...

---

### Post by jorgito on 2007-10-18
Hola!

Yo tengo el 7.04 al dia, pero no veo que vaya a actualizar a Gusty solito desde el update-manager. Sera por los servidores recargados o hay que tocar algo en los repositorios?

Saludos!

---

### Post by jorgito on 2007-10-19
Hola de nuevo, 

Intente que se haga la actualizacion automatica tal como indicaron en el link (con todas las actualizaciones de feisty el update manager deberia avisar que hay una version nueva) pero sigue diciendo que el sistema esta al dia sin dar la oportunidad de hacer el update.

Ya toque los servidores y todos los tildes razonables en "Agregar-Quitar" y sigue sin pasar nada.
Alguien tiene alguna idea?

Desde ya muchas gracias!

---

### Post by jorgito on 2007-10-19
Bueno, como me canse de intentar con el primer metodo recomendado baje el alternate CD, pero al querer instalar elegi que levantara actualizaciones de intenet, lo que parece que fue un error, porque al rato aborto la instalacion y tuve que ejecutar el cdromupgrade del CD porque automaticamente no corria mas.

En el segundo intento (sin pedir actualizacion a traves de internet) me dijo que una linda cantidad de paquetes no estan soportados por Cannonical por lo que iban a ser eliminados en el proceso de upgrade.

Alguien tiene idea que es eso??

Desde ya muchas gracias y saludos!

---

### Post by WanderingKnight on 2007-10-19
> En el segundo intento (sin pedir actualizacion a traves de internet) me dijo que una linda cantidad de paquetes no estan soportados por Cannonical por lo que iban a ser eliminados en el proceso de upgrade.


Me parece que se referia a repositorios third-party. Son los repositorios que agregas para instalar cosas como Wine o Skype. Simplemente lo que hace el programa es comentar las lineas de esos repositorios en tu /etc/apt/sources.list, para no tener ningun tipo de conflicto con paquetes third-party. Simplemente edita tu sources.list despues del upgrade y vas a tener todos tus repositorios de nuevo.

No te preocupes que no significa que te va a sacar esos paquetes, eh.

---

