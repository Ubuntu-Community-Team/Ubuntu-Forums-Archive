---
title: "No me anda el cubo en ubuntu"
date: 2007-08-03
forum: Argentina Team
---

### Post by aceki on 2007-08-03
Gente me dejo de andar el cubo le dije a un amigo "mira que lindo anda el cubo" y chanfles dejo de andar, estan activados los efecto de escritoro, que puede ser?

---

### Post by gepatino on 2007-08-03
Cuantos más datos nos des más fácil va a ser ayudarte:

que placa de video tenés, si instalaste actualizaciones ultimamente, que versión de ubuntu, que programas estabas usando, etc.

Saludos,

---

### Post by kowal on 2007-08-03
Suena a quilombo con la configuración de Beryl.. probá borrando la carpeta de configuración de Beryl.. 

```
rm ~/.beryl* -r
```

Saludos

---

### Post by valucha on 2007-08-03
> **kowal said:**
> Suena a quilombo con la configuración de Beryl.. probá borrando la carpeta de configuración de Beryl.. 

```
rm ~/.beryl* -r
```

Saludos
[COLOR="DarkOrchid"]
No, está usando los efectos de escritorio. A mi me pasa seguido pero ni le doy bola porque no uso mucho el cubo... Pero todavía no logré descubrir que es lo que hace que se vaya...
[/COLOR]

---

### Post by zspikes on 2007-08-04
te fijaste bien la configuracion del cubo, q este todo en orden?
si te andan los demas efectos, dudo q sea problema de beryl.

por cierto, usas beryl o compiz?

---

### Post by beuno on 2007-08-04
Es posible que lo hayas activado y desactivado, entonces perdiste los escritorios.
Tendras un solo escritorio, con lo cual, no hay cubo  :D

Hace click derecho en el icono de escritorios, abajo a la derecha, y elegi "preferencias".

Ahi, pone para que haya mas escritorios (los que quieras).

Salvo que sea otra cosa, eso lo deberia solucionar.

---

### Post by aceki on 2007-08-04
Miren tampoco anda como me dijieron, no tengo ninguna configuracion de beryl por que es el cubo que viene por defecto en el ubuntu 7.04, entongo 4 escritorios, y no esta  bloqueado, y tengo los dos efectos activados, dejo de andar asi por que si, por que primero lo movi, y despues no andubo mas

---

### Post by zspikes on 2007-08-06
pues es buena excusa para poner alguno de los cubos. Ya sea beryl o compiz.
Te recomiendo beryl, esta en una version mas estable q compiz, y en la [pagina oficial]("www.beryl-project.org") hay unos scripts muy buenos para instalarlo.

---

### Post by fernando_bonnin on 2007-08-08
Hola a todos, estoy dando mis primeros pasos con ubuntu, instalé festy para AMD64, y siguiendo un poco los posts quise activar los efectos de escritorio, y luego de activarlos me queda la pantalla en blanco, veo el cursor pero nada mas. Supongo que debe ser alguna incompatibilidad con la placa de video, es on-board ATI el mother es un ECS RS485M-M.
con CTRL+ALT+F1 puedo abrir un terminal, pero no se que comando utilizar para desactivar los efectos o como volver a la configuración anterior. Espero no haber sido demasiado extenso con la explicación. Y ojalá alguien me tire alguna idea. Desde ya muchas gracias.

---

### Post by aceki on 2007-08-08
Fernando, fijate si estan bien los drivers, suena a que estan mal, otra cosas, tu nombre me suena de algun lado (mi nombre es marcelo fusse), suerte con eso.

PD: te recomiendo instalar la vercion de 32 bit, ya que algunas (por no decir casi todas) cosas tienen problemas de compatibilidad y es engorrosisimo encontrar paquetes para ubuntu 64 Bit suerte!!!

---

### Post by fernando_bonnin on 2007-08-11
Marce, nos conocemos de Clínica Bessone en San Miguel, al final reinstalé el 7.04 para 32 bits. y ahora estoy configurando la placa de video con Envy, espero poder hacer funcionar el cubo y los efectos. Saludos y nos seguiremos encontrando por acá, espero que esto no sea desvirtuar el foro.

---

### Post by aceki on 2007-08-12
Fer si si, me habia acordado de vos,  despues que escribi el post, te dejo mi mail [email]mfusse@simssi.ath.cx[/email] o [email]mfusse@gmail.com[/email], asi seguimos en contacto, un  abrazo.

---

### Post by Mataca on 2007-08-12
Fernando, tenes que instalar los drivers de Nvidia (si es que tenes una Nvidia :P) por que sino se te va a ver blanquito el cubo.

Abrazo

---

### Post by fernando_bonnin on 2007-08-13
Muchas gracias por los consejos, ya lo tengo funcionando al cubo, y ahora voy por los efectos.

---

### Post by Mataca on 2007-08-13
Fernando instalá el beryl manager y usa el gestor de ventanas del beryl. De esta forma tenés los efectos funcionando.

A lo que voy es que no actives el compiz (o sea efectos de escritorio desde el menu preferencias) por que son excluyentes.

A no ser que te instales el compiz-fusion.

Humilde Recomendación: usa beryl y fue, tenés muchos efectos y el cubo a full.

Abrazo de pingüino

---

### Post by fernando_bonnin on 2007-08-15
Mataca, vos me decís que desinstale los efectos de escritorio y después instale el Beryl? Te pregunto si esos son los pasos a seguir porque en otra instalación con una ATI fue donde tratar de hacer eso se me quedó  sin entorno gráfico. Desde ya muchas gracias.

---

### Post by jpmorelli on 2007-08-15
> **fernando_bonnin said:**
> Mataca, vos me decís que desinstale los efectos de escritorio y después instale el Beryl? Te pregunto si esos son los pasos a seguir porque en otra instalación con una ATI fue donde tratar de hacer eso se me quedó  sin entorno gráfico. Desde ya muchas gracias.

No hace falta desinstalar los efectos de escritorio, beryl puede estar instalado a la par sin problemas, arrancas uno u el otro.
Para instalar beryl ademas de tener instalada la placa Nvidia desde los controladores restringidos tenés que instalar los siguientes paquetes:

beryl
beryl-manager
emerald-themes

con eso es suficiente, despues para la nieve por ejemplo seguí el otro post donde hablamos de eso.

---

### Post by fernando_bonnin on 2007-08-17
Gracias por los consejos y quería agregar que instalé desde el Synaptic el compiz y el emerald completos. y funciona todo bien. Todavía no estoy muy canchero con las teclas, pero ya seguiré probando. Un caño el efecto de lluvia y la nieve.

---

