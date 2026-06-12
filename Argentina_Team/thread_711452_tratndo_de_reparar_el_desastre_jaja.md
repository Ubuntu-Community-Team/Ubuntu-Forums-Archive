---
title: "tratndo de reparar el desastre jaja"
date: 2008-02-29
forum: Argentina Team
---

### Post by andy_91 on 2008-02-29
[[IMG]http://img206.imageshack.us/img206/646/pantallazomz2.th.png[/IMG]](http://img206.imageshack.us/my.php?image=pantallazomz2.png)

bueno necesito una manita para arreglar un poco el desastre que hice mi Xubuntu(el ADN dice que usa xfce secion)

primero: como se llama ese buscador de iconito naranja que parese un rayo(el que esta al lado de la bandeja de sistema), por que lo saque y ahora lo quiero de vuelta y nose como ponerlo

segundo:un porta papeles como el clipman o el de kde que no me acuerdo como se llama para el panel de gnome hay?

[[IMG]http://img253.imageshack.us/img253/5180/759302qg2.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=759302qg2.jpg)


y por ultimo eso? que es y como se lo instalo a mi pc es que me gusto

a la flecha la hice por que lo quiero del otro lado (uso imágenes y capturas para guiarme de como voy a dejar mi escritorio)

bueno es todo por ahora jaja desde ya gracias

---

### Post by faktorqm on 2008-02-29
loco vos estas re limado! que queres hacer con ese engendro linuxero mutante? si lo queres mantener, esta buenisimo! pero eso (me parece) que anda mas lento aun que un gnome "limpio" en una 486 DX2. si lo queres sacar, podes empezar aprobar con "sudo apt-get remove gnome-desktop-data gnome-desktop-environment --purge" o algo por el estilo. Si lo queres dejar, empeza a sacar servicios de cosas por que debes tener los de gnome mas lo de xfce, va en realidad no estoy seguro, debes tener xfce desktop pero con gnome-panel....... no se con certeza. te copas y posteas un "ps ax" a ver que tenes corriendo? Salu2!

---

### Post by andy_91 on 2008-02-29
[[IMG]http://img213.imageshack.us/img213/4941/procesoslc8.th.png[/IMG]](http://img213.imageshack.us/my.php?image=procesoslc8.png)

bueno aca les dejo los procesos del sistema nose si era eso lo que nesesitaban

y si por ahora planeo conservar el desastre jaja XD(solo por ahora)

a y otra cosa como configuro la papelera para que funcine con thunar ?

es que sino instalo el nautilus el icono del panel de papelera no anda

---

### Post by andy_91 on 2008-02-29
> **andy_91 said:**
> [[IMG]http://img213.imageshack.us/img213/4941/procesoslc8.th.png[/IMG]](http://img213.imageshack.us/my.php?image=procesoslc8.png)

bueno aca les dejo los procesos del sistema nose si era eso lo que nesesitaban

y si por ahora planeo conservar el desastre jaja XD(solo por ahora)

a y otra cosa como configuro la papelera para que funcine con thunar ?

es que sino instalo el nautilus el icono del panel de papelera no anda
andy@andy-desktop:~$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00 [migration/0]
    4 ?        SN     0:00 [ksoftirqd/0]
    5 ?        S<     0:00 [watchdog/0]
    6 ?        S<     0:00 [events/0]
    7 ?        S<     0:00 [khelper]
   26 ?        S<     0:00 [kblockd/0]
   27 ?        S<     0:00 [kacpid]
   28 ?        S<     0:00 [kacpi_notify]
  109 ?        S<     0:00 [kseriod]
  131 ?        S      0:00 [pdflush]
  132 ?        S      0:00 [pdflush]
  133 ?        S<     0:00 [kswapd0]
  184 ?        S<     0:00 [aio/0]
 1907 ?        S<     0:00 [ata/0]
 1908 ?        S<     0:00 [ata_aux]
 1910 ?        S<     0:00 [scsi_eh_0]
 1911 ?        S<     0:00 [scsi_eh_1]
 1924 ?        S<     0:00 [ksuspend_usbd]
 1925 ?        S<     0:00 [khubd]
 2249 ?        S<     0:00 [kjournald]
 2454 ?        S<s    0:00 /sbin/udevd --daemon
 3368 ?        S<     0:00 [kpsmoused]
 3794 ?        Ss     0:00 /usr/sbin/pppd call dsl-provider
 3948 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 3949 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 3952 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 3954 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 3955 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 3956 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4134 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 4184 ?        S<     0:00 [kondemand/0]
 4247 ?        Ss     0:00 /sbin/syslogd -u syslog
 4302 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4304 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4325 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4341 ?        Ss     0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 4355 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 4368 ?        Ss     0:00 /usr/bin/system-tools-backends
 4369 ?        S      0:00 dbus-daemon --session --print-address --nofork
 4388 ?        Ss     0:00 /usr/sbin/hald
 4389 ?        S      0:00 hald-runner
 4442 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event1
 4445 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event4
 4446 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event5
 4447 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event6
 4454 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/a
 4455 ?        Ss     0:00 /usr/sbin/cupsd
 4479 ?        S      0:01 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 4561 ?        Ss     0:00 avahi-daemon: registering [andy-desktop.local]
 4562 ?        Ss     0:00 avahi-daemon: chroot helper
 4576 ?        Rs     0:00 /usr/sbin/dhcdbd --system
 4596 ?        Ss     0:00 /usr/sbin/hcid -x -s
 4606 ?        S      0:00 /usr/lib/bluetooth/bluetoothd-service-audio
 4607 ?        S      0:00 /usr/lib/bluetooth/bluetoothd-service-input
 4612 ?        S<     0:00 [krfcommd]
 4643 ?        Ss     0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4646 ?        S      0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4720 ?        Ss     0:00 /usr/sbin/atd
 4734 ?        Ss     0:00 /usr/sbin/cron
 4923 ?        S      0:00 /usr/lib/gamin/gam_server
 5201 tty7     Ss+    6:51 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
 5218 ?        Ss     0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xser
 5258 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5261 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session startxfce4
 5262 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-add
 5268 ?        S      0:02 /usr/lib/libgconf2-4/gconfd-2 6
 5271 ?        Sl     0:03 /usr/bin/xfce4-session
 5276 ?        Ss     0:18 gnome-screensaver
 5277 ?        Ss     0:03 xfce-mcs-manager
 5279 ?        Ss     0:00 kdein  
 5282 ?        S      0:00 dcops  
 5285 ?        S      0:00 klaun  
 5287 ?        S      0:03 kded   
 5292 ?        S      0:00 gnome-keyring-daemon
 5293 ?        S      0:19 xfwm4 --sm-client-id 117f0001010001204229777000000482
 5295 ?        S      0:04 Thunar --sm-client-id 117f000101000120422977800000048
 5296 ?        Sl     0:30 /usr/bin/xfdesktop --sm-client-id 117f000101000120431
 5301 ?        S      0:39 gnome-panel --sm-config-prefix /gnome-panel-sGLmvg/ -
 5302 ?        S      0:00 update-notifier --sm-config-prefix /update-notifier-B
 5305 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5307 ?        Ss     0:01 nm-applet --sm-disable
 5311 ?        Ss     0:00 gnome-power-manager --sm-config-prefix /gnome-power-m
 5317 ?        Ss     0:00 python /usr/share/system-config-printer/applet.py
 5321 ?        SNsl   0:01 trackerd
 5338 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5343 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 5384 ?        S      0:00 kio_f  
 5392 ?        S      0:00 /bin/sh /usr/bin/firefox
 5404 ?        S      0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/fire
 5408 ?        Sl     3:58 /usr/lib/firefox/firefox-bin
 5504 ?        Z      0:03 [eog] <defunct>
 5516 ?        Z      0:03 [eog] <defunct>
 5600 ?        S      0:01 xfce4-terminal
 5601 ?        S      0:00 gnome-pty-helper
 5602 pts/0    Ss     0:00 bash
 5618 pts/0    R+     0:00 ps ax
 


a jeje era un camando :P

bueno cai tarde

bueno les dejo las dos cosas por las dudas

---

### Post by santiagoward2000 on 2008-03-03
Hola Andy!
Por curiosidad, ¿cómo lo arreglaste? ¿Pudiste salvarlo o te cansaste y reinstalaste Xubuntu de cero?

---

### Post by andy_91 on 2008-03-03
jajase bueno inicie urli de 0 y despues le instale gnome y desde gnome istale un pequeño paquete llamado ubuntu-desktop jajaja y asi quedo

lo malo es que es  ubuntu 7.04 jaja pero cuando salga ubuntu 8 lo actualizo jaja

ahora tengo ubuntu y kde on fachada de windows por si las dudas nose algun invitado o algo o por divercion XD

---

### Post by andy_91 on 2008-03-03
> **andy_91 said:**
> 
y por ultimo eso? que es y como se lo instalo a mi pc es que me gusto

a la flecha la hice por que lo quiero del otro lado (uso imágenes y capturas para guiarme de como voy a dejar mi escritorio)

bueno es todo por ahora jaja desde ya gracias

[[IMG]http://img253.imageshack.us/img253/5180/759302qg2.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=759302qg2.jpg)

jaja alguien me ayuda con eso jaja todavía no lo resolví jaja

---

