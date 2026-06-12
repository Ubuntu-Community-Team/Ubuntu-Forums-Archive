---
title: "[SOLVED] Correo- no puede resolver el servidor"
date: 2007-08-27
forum: Argentina Team
---

### Post by Vero1 on 2007-08-27
Hola,

Despues de mucha lucha por fin he podido conectarme a Internet.

Ahora, al querer configurar Nautilus, me encuentro que sistemáticamente me dice que no puede resolver al servidor.

Tengo speedy como servidor y al rellenar los campos que me pide y luego tratar de recibir o enviar, me sale lo que comento mas arriba.

Debo estar haciendo algo mal.

Alguien me puede orientar por favor?


gracias y saludos:)

---

### Post by Hei Ku on 2007-08-27
postea toda la configuracion que pusiste en el nautilus. Pareciera ser algo en el nombre del dominio que pusiste.

---

### Post by Vero1 on 2007-08-27
> **Hei Ku said:**
> postea toda la configuracion que pusiste en el nautilus. Pareciera ser algo en el nombre del dominio que pusiste.

Hola Hei Ku,
Puse la misma configuración que tengo en Windows, pero el problema está con Speedy.com.ar que no puede reconocer.
Cuando trato de recibir o enviar me contesta que no puede resolver el servidor...

gracias

---

### Post by Hei Ku on 2007-08-27
podes conectarte al mismo sitio a traves del browser?
otra cosa, pusiste el mismo numero de puerto? Puede ser que utilicen correo seguro, y entonces cambia el numero de puerto, como es el caso con Ciudad Internet.

---

### Post by Vero1 on 2007-08-28
Hola Hei Ku,

No ha probado ingresar a Speedy con el browser pero lo voy a  hacer.
Ahora, pasa una cosa curiosa.
He enviado dos mails y han llegado. No lo entiendo.
Si me dice que no puede resolver al Servidor, cómo es que los mails que envié llegaron?????
Está tildada la opción de autenticación del Servidor.
No dá opción de poner puertos.

Voy a seguir intentando. 

Gracias y saludos:)

---

### Post by Vero1 on 2007-08-28
Hola de nuevo,

Desde el Browser sí puedo ingresar lo mas bien

la dirección es: [http://www.speedy.com.ar](http://www.speedy.com.ar)

Alguien me sugirió poner detrás del Servidor los numeros de puertos. Ni siquiera así me sirvió.

Algun comentario?

Ah, me equivoqué. No es el Nautilus si no Evolution. Disculpas.

saludos

---

### Post by Vero1 on 2007-08-28
Hola,

Vuelvo a exponer mi problema, ya que no entiendo lo que está pasando y tampoco lo puedo resolver.

Tengo como Servidor de Internet a Speedy.com.ar

Despues de configurar Evolution, me resulta imposible enviar o recibir correo.

Me sale una ventanita que dice: Nombre o servicio desconocido.

He reconfigurado muchas veces Evolution pero no lo consigo.

Aclaro que si pongo la dirección de Speedy en el browser me conecta perfectamente.

Si a alguien se le ocurre algo, quedaré agradecida:)

saludos

---

### Post by Hei Ku on 2007-08-28
El tema es que probablemente el servidor de correo de speedy sea algo como mail.speedy.com.ar. Otros que tengan speedy te pueden decir mejor.

Y fijate si en Windows tenes alguna forma de autenticacion en particular. De acuerdo a eso cambian los puertos, que supongo que Evolution los debe seleccionar automaticamente. No te puedo decir bien porque uso KMail sobre KDE.

---

### Post by marianom on 2007-08-28
> **Vero1 said:**
> Hola,

Vuelvo a exponer mi problema, ya que no entiendo lo que está pasando y tampoco lo puedo resolver.



Por favor, si es el mismo tema mantené la discusión en un solo thread. Si se pierder bajo otros posts después de un tiempo prudencial se puede hacer un bump pero para focalizar las respuestas de grupo, mantengamos la charla en un solo lugar.

Gracias.

---

### Post by marianom on 2007-08-28
Tenes que usar la info que está [aca]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=158&root=132#detalle").

> Tipo de Servidor de Correo es POP3

Servidor de correo entrante POP es: pop.speedy.com.ar

Servidor de correo saliente SMTP es: mail.speedy.com.ar

Nombre de Cuenta esta formado por su usuario con el dominio: [email]usuario@speedy.com.ar[/email]  (ejemplo para el usuario vilma el nombre de cuenta sería [email]vilma@speedy.com.ar[/email]).

Tildar la opción Mi servidor requiere autenticación


Me imagino que Evolution te dará lugares para configurar está información sin que haya lugar a dudas así que, por favor, asegurate que esta información especifica es la que estás usando. Si es así y no funciona, nos contas.

---

### Post by Vero1 on 2007-08-29
Hola marianom,
Gracias por responder.

El problema debe estar en que el usuario de conexión con contraseña no es el mismo que el usuario de correo(en este caso yo).

Ponéle que el usuario de conexión sea vilma@speedy y el usuario de la cuenta sea [email]Jorge@speedy.com.ar[/email]. 

Para enviar es: mail.speedy.com.ar
Para recibir es: pop.speedy.com.ar

He intentado todas las formas posibles.

Lo curioso es que enviar, envía pero lo recibo en Windows, en Evolution imposible. Sé que es problema de configuración pero no sé cómo solucionarlo.

Disculpa que haya enviado un nuevo thread pero creí que iba a ser mas clara la explicación.

En fin, lo que me confunde es el usuario de conexión que no soy yo.

saludos

---

### Post by Vero1 on 2007-08-29
> **Hei Ku said:**
> El tema es que probablemente el servidor de correo de speedy sea algo como mail.speedy.com.ar. Otros que tengan speedy te pueden decir mejor.

Y fijate si en Windows tenes alguna forma de autenticacion en particular. De acuerdo a eso cambian los puertos, que supongo que Evolution los debe seleccionar automaticamente. No te puedo decir bien porque uso KMail sobre KDE.

Hola Hei Ku,
Gracias igual por tratar de ayudar.
Efectivamente, para enviar por speedy es:mail.speedy.com.ar

El problema se lo acabo de explicar a marianom. 

Estoy confundida porque el usuario de conexión no soy yo. Ya probé de todas las formas.
En fin, tendré que esperar que alguien que tenga Speedy me pueda aclarar un poco.

saludos

---

### Post by msangil on 2007-08-29
@Vero1

El usuario de conexión no tendría que ver con tu problema. Teóricamente el mail es independiente.

De tanto tocar cosas en la configuración capaz tildaste algo de más (tipo algún "Usar conexión segura - Encriptación TSL").

Probá borrar la cuenta en el Evolution y configurarla de cero con los settings por defecto.

Llamaste ya a soporte técnico de Speedy? Pediles de última que te digan todos los settings necesarios y te ayudamos aunque sea a configurar la cuenta en el Thunderbird en vez del Evolution.

No te gastes en explicarles que usás Linux porque en el call center te van a preguntar con qué se come.

---

### Post by Vero1 on 2007-08-29
Hola y gracias por contestar.

No configuré nada  mas que lo que tengo en Windows.

Ahora sale un cartel que dice siempre lo mismo pero al final acota:

Tubería rota.

Traté de buscar en ayuda pero no encuentro nada al respecto.

Sabés qué significa?

Gracias:)

p.d.
Con Speedy prefiero no hablar porque empiezan con las pavadas y la verdad es que nunca me solucionan nada...

---

### Post by Vero1 on 2007-08-29
> **Vero1 said:**
> Hola y gracias por contestar.

No configuré nada  mas que lo que tengo en Windows.

Ahora sale un cartel que dice siempre lo mismo pero al final acota:

Tubería rota.

Traté de buscar en ayuda pero no encuentro nada al respecto.

Sabés qué significa?

Gracias:)

p.d.
Con Speedy prefiero no hablar porque empiezan con las pavadas y la verdad es que nunca me solucionan nada...

En cuanto a Thunderbird me comentaron que tiene poca vida, es cierto?

---

### Post by msangil on 2007-08-29
El Thunderbird está muy bueno. Ya van por la versión 2.0.0.6
Hace poco lo separaron del proyecto del Firefox para darle un poco más de protagonismo.

Lo que tiene de malo comparado con el Evolution es que no tenés las funciones adicionales de Calendario, Notas y Tareas (no sé si a vos te interesa eso). Es sólo para mail por ahora. En la última versión le metieron unas cuantas mejoras a lo existente. Por ejemplo mi cuenta de gmail no necesita configuración de ningún tipo. Entra directo.

El Evolution en ese sentido se parece más al Outlook del Office.

No tengo idea qué será lo de la "tubería rota". Por qué no probás aunque sea 5 minutos con el Thunderbird a ver si por una de esas anda de una y te sacás el problema de encima?

Sabés dónde encontrarlo?
Aplicaciones / Añadir y quitar / Thnderbird Mail (le hacés click en la cajita y apretás Aplicar).

---

### Post by Vero1 on 2007-08-29
Gracias msangil,

Lo unico que me interesa del correo es el correo mismo.
Ahora voy a probar lo que me decís.
Despues te digo:)

---

### Post by Vero1 on 2007-08-29
> **Vero1 said:**
> Gracias msangil,

Lo unico que me interesa del correo es el correo mismo.
Ahora voy a probar lo que me decís.
Despues te digo:)

Hola msangil,

Ya está instalado y funcionando muy bien. No me encontré con problemas.

Muchas gracias.
saludos:)

---

### Post by msangil on 2007-08-29
Un placer. Agradeceles en realidad a los muchachos de Mozilla que lo programaron.

Please agregale "[SOLVED]" en el título del thread así ya saben todos que este post está solucionado.

Éxitos!

---

### Post by Vero1 on 2007-08-30
En realidad el hecho de poder usar el correo te lo debo a vos que me diste la idea.

Gracias de nuevo y saludos:)

---

