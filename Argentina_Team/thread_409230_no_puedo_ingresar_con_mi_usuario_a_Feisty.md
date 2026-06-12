---
title: "no puedo ingresar con mi usuario a Feisty"
date: 2007-04-14
forum: Argentina Team
---

### Post by atari130xe on 2007-04-14
Hola Foro, hice la actualizacion de 359 paquetes desde Feisty Beta de los cuales algunos fallaron, luego de 17 horas conectado por dial up bajaron las actualizaciones hasta que cuando las hizo se colgo y reinicie, el tema esta en que cuando inicia sesion y me pide el usuario y la clave, me sale un cartel diciendo lo siguiente:

"GDM: No pudo escribi en su archivo de autorizacion. este puede significar que no tiene espacio en disco o que su directorio personal no se pudo abrir para escritura. En cualquier
caso no es posible iniciar la sesion. contacte con el administrador del sistema".

Soy el único que utiliza esta PC y no puedo entrar a Ubuntu alguien tiene idea de como poder solucionar este problema? gracias de antemano. :confused:

---

### Post by beuno on 2007-04-14
¿Podra ser que no tenes espacio?

Desde la consola ejecute:   

```
df
```

Ahi te va a decir.

En tal caso, tenes que hacer algo de espacio en disco.

Para borrar es:

```
rm tu_archivo
```

---

### Post by atari130xe on 2007-04-14
gracias por responder pero no es un tema de espacio (tengo 17 Gigas libres en esa particion), me dà la sensacion de que cuando se me colgò la actualizacion se corrompieron algunos archivos entre ellos el de mi user y pass o justame esos archivos son los que quedaron truncados cuando se colgò mi pc. El tema es COMO volver a entrar, si alguien lo sabe PASO a PASO (soy nuevo en Linux) se lo agradeceria mucho mientras tanto sigo Googleando en busca de una solucion. Tengo dial up y me mataria tener que instalar y bajar los 350MB de actualizaciones de nuevo :(

---

### Post by kowal on 2007-04-14
No te preocupes que si se bajaron las actualizaciones quedan guardadas en el directorio:

/var/cache/apt/archives/

Asi que no vas a tener que volver a bajar todo.. a menos que haya _nuevas_ actualizaciones que tengan que reemplazar las que ya bajaste. Todo esto que te digo Ubuntu se da cuenta sólo cuando quieras actualizar.

Yo te diría que primero pruebes con otro usuario. No tenés otro usuario?. Creá uno nuevo. Andá a la consola con ALT+CTRL+F1, logueate y pone "sudo adduser xxxxxx" (reemplazá xxxxxx por el nombre nuevo de usuario). Y después proba logueandote con el nuevo.

---

### Post by atari130xe on 2007-04-15
Pude entrar ejecutando "sudo apt-get clean" y una vez adentro dejé la entrada automática, pero de todas maneras cada vez que inicio me sale un cartel que dice:

"Se está ignorando el archivo $HOME/.dmrc del usuario. Esto impide que se guarden la sesión predeterminada y el idioma. El archivo deberia pertenecer al usuario y tener los permisos 644.
El directorio personal del usuario debe pertenecer al usuario y no ser escribible por otros usuarios".

Que significa eso? es algo que pueda arruinarme el sistema en un futuro? Es necesario esperar al
19/04 para bajarme la version final de Feisty y formatear lo que tengo ahora? es un garrón si es
algo asi porque si tuviera banda ancha no hay drama pero con dial up es parir bajar actualizaciones
porque hay un bug o algo asi. En fin si alguien ducho en el tema me tira alguna idea, genial
gracias de nuevo! :)

---

### Post by clasificado on 2007-04-15
probá con esto en una consola (logueado con el usuario en cuestion, no entres con otro que me cachás)

```

touch ~/.dmrc
chmod 644 ~/.dmrc

```

que basicamente es hacer lo que te dice.

Clasificado.

---

### Post by atari130xe on 2007-04-16
Grax clasificado hice hice lo que dijiste pero sigue el bendito cartel al inicio, no sé porque pero me veo instalando la version final el 19/04 :(  algo similar me habia pasado cuando tenia Dapper y actualicé a Edgy (cada vez que se instalaba una actualizacion del kernel sonaba algo). Te comento que intenté hasta con "sudo touch...." y nada, al reiniciar otra vez el cartel. gracias mil! :)

---

