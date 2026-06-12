---
title: "Hola a todos y comentario sobre Evolution"
date: 2007-03-01
forum: Argentina Team
---

### Post by Ferdydurke on 2007-03-01
Este post tiene dos finalidades:
1. Primero que nada, saludarlos a todos. Me convertí hace poco en Usuario de Ubuntu, aunque vengo hace rato con Linux en general. Primero, Mandrake-Mandriva, y después Tuquito, otra distro nacional que todavía conservo y aún participo en su comunidad. Pero quise darle una oportunidad a Ubuntu, que por lo que experimenté es una distribución genial y muy cómoda para el usuario. Así que espero ser de ayuda en todo lo que se pueda, en especial en campañas y difusión, ya que dejo la parte técnica a los que saben.
2. Segundo, no sé si a uds. le pasó, pero a mí si y fue una experiencia compartida con un amigo hoy. Aparentemente, después de actualizar ubuntu 6.06, evolution deja de funcionar. Cada vez que se quiere iniciar, sale el mismo cartelito que indica que la aplicación se cerró inesperadamente. Presupongo que se debe a alguna actualización, ya que lo que pasó fue esto:
a) Instalé ubuntu dapper la primera vez el fin de semana y lo tuve andando hasta hoy. evolution andaba perfectamente. Hoy reinstalé mis dos sistemas amados (Tuquito primero y Ubuntu dapper después), para dejar el grub de Ubuntu como principal, entré en Ubuntu, actualicé, y sopresivamente evolution no anda. Tira ese mensaje de error.
b) Pero lo curioso es que mi amigo (Ubuntero y Tuquitero como yo) tenía su sistema ya instalado, actualizó hoy y evolution dejó de funcionar. Tira el mismo error: la aplicación se cierra inesperadamente.
De acá que presupongo, desde mis casi nulos conocimientos, que hay un problema con algún paquete reciente. Como recomendaba actualizar a eft, es lo que estoy haciendo ahora, a ver si el problema se soluciona. Pero quería comentar este tema por si alguno tuvo esta experiencia.
Después cuento cómo sigue el asunto.
Desde ya, abrazos a todos, gracias por permitirme participar, y difundamos linux.

---

### Post by edu65 on 2007-03-01
Por lo visto se trata de un problema con el paquete "libnss". 

Como solución temporal, te sugiero que abras una terminal y 
escribas lo siguiente:

cd /usr/lib
sudo ln -s firefox/libfreebl3.so 

(Te solicitará tu "password")

Después de eso, evolution deberia funcionar.

!Suerte!

---

### Post by BlackHero on 2007-03-02
hola ferdydurke sos bienvenido a esta comunidad ubuntera internacion y a la argentina porsupuesto man te doy la binevenida en nombre  todos nos ayudamos entre todos =) no tengo idea de evo por que no uso gestor de email :P aguante firefox =)

---

### Post by Ferdydurke on 2007-03-02
Estimada gente Ubuntera: gracias por la bienvenida. Cuento que ayer (una y media de la mañana, uf) terminó de actualizar la versión a 6.10, y todo anda de maravillas. De todas maneras, gracias edu65 por la respuesta. La agendé y voy a pasársela a mi colega Linuxero para que vea si le sirve. Por lo que sé, él todavía no actualizó.
Gracias a todos y aguante el Soft Libre!!!!
Abrazos

---

