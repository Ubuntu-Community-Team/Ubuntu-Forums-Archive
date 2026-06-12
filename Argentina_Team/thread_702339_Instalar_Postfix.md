---
title: "Instalar Postfix"
date: 2008-02-20
forum: Argentina Team
---

### Post by zergiomp on 2008-02-20
Buenas a todos. Para empezar, decir que soy un novato, tanto en el foro, como usuario de Linux. Y pido mil disculpas si me equivoco en cualquier cosa de mi post.

Pues nada, al grano. Empecé a instalar Postfix, siguiendo el manual mas escueto que encontré (por que la verdad, era el que vi mas accesible para mis conocimientos con Linux y ademas, se ceñia a los objetivos que quiero lograr. Instalar Postfix y Spamassasin, para luego integrarlos con Moodle en mi Ubuntu. Pero esto es otra historia, me centraré en ello). Total, que una vez que llegué a la configuración del fichero dovecot.conf (que por lo que vi, es un servidor imap y pop3, facilito de instalar y configurar) pues puse lo que viene en este manual --> [http://www.abartiateam.com/documentacion/postfix/servidor_de_correo_mediante_postfix.pdf](http://www.abartiateam.com/documentacion/postfix/servidor_de_correo_mediante_postfix.pdf)

Guarde la configuración cambiada del fichero y una vez reinicio el servicio, me aparece el siguiente error:

Error: Error in configuration file /etc/dovecot/dovecot.conf line 25: Unknown setting: imap_listen
Fatal: Invalid configuration in /etc/dovecot/dovecot.conf

Estube buscando información por internet, pero no encuentro gran ayuda, la verdad...Bueno, espero que me puedan echar una mano con mi problemilla.

Gracias!

---

### Post by faktorqm on 2008-02-20
primer resultado en el google despues de poner "dovecot.conf":

[http://www.brennan.id.au/12-Sendmail_Server.html](http://www.brennan.id.au/12-Sendmail_Server.html)

y dice:

```

protocols = imap imaps pop3s

protocol imap {
listen = 127.0.0.1
ssl_listen = *
ssl_disable = no
}

```

---

