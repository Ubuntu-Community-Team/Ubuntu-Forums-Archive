---
title: "Samba y Firestarter (smb &amp; iptables)"
date: 2007-04-29
forum: Argentina Team
---

### Post by DuckMan on 2007-04-29
Bueno, este es uno de los misterios q me queda por debelar en ubuntu, por alguna razon, tengo una carpeta compartida en samba , con el servicio de samba habilitado desde firestarter (puertos 137-139 445) , pero cuando este gui del iptables esta activado, no veo la red, cuando lo apago *dejandome en bolas por la internet* si puedo explorar mi red.

alguna respuesta ? :O

---

### Post by sebas.rhcp on 2007-04-29
Nose siempre dicen que el firestarter es facil y funciona bien pero a mi nunca me resulto, me pasaba lo mismo que a vos y al final termine configurando manualmente las iptables.

---

### Post by Al_maverick on 2007-04-29
Probablemente te este faltando algun otro puerto mas, aparte de los q ya pusiste (dns, etc.)

Lo que podes probar es fijandote en la solapa de eventos, para ver si hay paquetes bloqueados, y entonces habilitarle esos puertos en la solapa de politicas. Acordate de activar la politica despues de ingresarla.

---

### Post by MeduZa on 2007-05-01
a mi me pasa lo mismo, y es q faltan puertos estoy seguro pero como nunca supe cuales son agregue toda la lan a trusted y con eso safo, pero yo preferiria la otra manera, yo ademas del samba agregue 2 o 3 cosas mas pero siempre me pasa q no pueden imprimir o no ven las carpetas compartidas
en un post lei q es porque el iptables no esta leyendo el browcast de datos o algo asi.
alguien que sepa podria postiar cuales son los puertos q se usan para samba y cups?

---

### Post by Al_maverick on 2007-05-01
Los puertos son los correctos, pero tambien tenes que habilitar el broadcast para la red local.

---

### Post by DuckMan on 2007-05-01
y como se hace eso...

porq los puertos se habilitan bien, pero algo esta faltando/andando mal

---

### Post by Al_maverick on 2007-05-01
Eso esta en Editar/Preferencias.
Dentro de Preferencias: Cortafuegos/Opciones avanzadas --> Tráfico de difusión
Fijate que tengas desmarcado Bloquear tráfico de difusión de la red interna. Depende como sea la topologia de tu red, también vas a tener que desmarcar Bloquear tráfico de difusión de la red externa. 
En ese caso no te preocupes porque los broadcast no deberian pasar a traves del router.

Si el firestarter esta en ingles (suertudo!), esta en edit/preferences/firewall/advanced options. Block broadcast

Google-fu: [http://www.fs-security.com/docs/preferences.php](http://www.fs-security.com/docs/preferences.php)

---

### Post by DuckMan on 2007-05-01
hice eso, y habilite el puerto 32775 (Sun-RPC portmap) , no se si esta de mas, pero trataba de conectarse por ahi la otra pc... ahora anda de lujo

no se si lo ultimo esta de mas, ya lo probare. creo q desmarcando las dos casillas era la solucion, porq la de interna ya estaba desmarcada

gracias por develar el misterio!!

---

### Post by lucho115 on 2007-05-02
El problema es el broadcast, en el caso de no hacerlo tenes q hacer una regla para cada ip y una para tu ip , se entiende?
Saludos

---

