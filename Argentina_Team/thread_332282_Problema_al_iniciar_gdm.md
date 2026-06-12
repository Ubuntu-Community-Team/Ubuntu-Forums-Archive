---
title: "Problema al iniciar gdm"
date: 2007-01-05
forum: Argentina Team
---

### Post by quaid on 2007-01-05
Las cosa es asi:

Ayer actualize (no em acuerdo q pero era un choclo de cosas) cuestion q andaba todo bien hasta hoy, arranco , bootea, pasa la splash screen y cuando deberia de aparecer el cartel de nvidia beta drivers se queda en negro y muere la pc.

Ctrl+alt+F(1-6) no funciona completamente muerta queda. El recovery mode no me funciona el teclado , es usb y se paga y queda asi asi q no puedo loguearme.

Yo me preguntaba en grub existe una manera para q inicie en modo consola, yo me acuerdo q con fedora Core 1  y 2 agregaba init 3 y listo, en grub ahora no funciona.

Alguna sugerencia , idea, para mi q es el driver nvidia q algo se le jodio, me parece.
Si fuese de Xorg me tendria q aparecer la pantalla azul. Si fuese de GDM supongo q tb.

pero no puedo acceder al modo consola, asi q no se com ohacer, alguna sugerencia?

---

### Post by beuno on 2007-01-05
Agrega al final de la linea el runlevel:

```
/boot/vmlinuz-2.6.15-8-386 root=/dev/hda1 ro quiet splash 3
```

Si no te funciona 3, proba 2.

---

### Post by Ptero-4 on 2007-01-05
El unico que funcionará es el 1 porque ubuntu tiene los runlevels 2 hasta el 5 configurados para arrancar gdm.

---

### Post by quaid on 2007-01-05
ya pude iniciarlo en consola (con un teclado sunshine del 94) pero en los logs no hay ningun error excepto q no tengo la ruta de los font cyrillic pero eso es lo de menos, en los logs de gdm ni en los de xorg salta ningun error... cada vez estoy mas confundido

-------------------------------------------------------------------------------

Ya esta solucionado, como lo sospechaba eran los drivers nvidia, reinstale los ultimos y por ahora (toco madera) andan bien. Todabia me quede con la duda del xq no anda el teclado usb  en modo.

Cierrenlo tildenlo com osolucionado, gracias a todos por la mano , y lo del 1 en grub no funciona, debe de haber una forma, no se cual sera.

---

### Post by ariel on 2007-01-05
cuando te pasa una cosa asi, lo mas facil es bootear en modo consola y editar xorg.conf

sudo vi /etc/X11/xorg.conf

buscas la linea que dice 
Driver     "nvidia"

y la cambias por 
Driver      "nv"

y despues podes cargar el entorno grafico a mano:
sudo /etc/init.d/gdm start

esto hace que en lugar del driver propietario ("nvidia"), X use el driver open source que sera lento pero es de fierro.

salu2

---

### Post by quaid on 2007-01-05
> **ariel said:**
> cuando te pasa una cosa asi, lo mas facil es bootear en modo consola y editar xorg.conf

sudo vi /etc/X11/xorg.conf

buscas la linea que dice 
Driver     "nvidia"

y la cambias por 
Driver      "nv"

y despues podes cargar el entorno grafico a mano:
sudo /etc/init.d/gdm start

esto hace que en lugar del driver propietario ("nvidia"), X use el driver open source que sera lento pero es de fierro.

salu2
Exactamente eso hice le puse el driver nv y listo pude instalar el nuevo nvidia tranquilo. el mayor quilombo era el q no podia iniciar en recovery mode, espero q esto sea util para alguien

---

### Post by lavaramano on 2007-01-06
resulta que a mi me pasa algo parecido.
o sea, arranca todo bien y cuando deberia arrancar la pantalla de login.. "crashea" X 2 o 3 veces y despues de eso salta un mensajito que me dice 'Aparentemente el servidor se cae. se va a probar con otra" o algo por el estilo (despues posteo bien lo que dice el cartelito, aunque de todas formas eso que escribi ahi se parece bastante).

y recien despues de eso, aparece el menu de login.
no es que signifique la muerte de nadie, pero es bastante denso prender la maquina y tener que esperar a que termine de crashear para poder logearme..

probe reconfigurando xserver-xorg, pero tampoco soluciono mucho.
de hecho, creo que el problema esta en el gdm, porque en un momento lo deshabilite y me arrancaba en modo consola, despues ponia "startx" y andaba perfecto.
el problema de eso, es que al no tener al gdm, cada vez que enchufaba algo tenia que montarlo manualmente (cosa que tampoco me molestaba, pero a veces no sabia el nombre del device de algunos dispositivos y no podia montarlos..)

pd: si a alguien le interesa, la placa que tengo es una ati radeon xpress 200m.

---

