---
title: "Ubuntu no inicia interficie grafica"
date: 2010-09-17
forum: Catalan Team
---

### Post by antoniu on 2010-09-17
Hola;
Ahir, quan estava amb el firefox al goear es va quedar com mig penjat fins que es va tancar sol, llavors ja vaig aprofitar per a tancar l'ordinador i li va costar molt.

Avui al mati semblava que anes be (ha sortit la pantalla de benvinguda de l'ubuntu) pero enlloc d'aparèixer la pantalla on s'escull l'usuari i escriure la contrasenya em surt a l'estil msdos, escric el meu usuari, la contrasenya i els accepta però continua sense obrir la interficie gràfica.

Com ho puc solucionar?
gràcies

---

### Post by wgarcia on 2010-09-17
Un cop que arribes a aquesta pantalla que dius "msdos", o sigui la consola de text i la línia de comandes, prova d'entrar la següent instrucció:

/etc/init.d/gdm restart

que hauria de reiniciar l'entorn gràfic. Si no ho fa i dóna algun error posa'l aquí a veure si algú pot esbrinar que està passant.

---

### Post by antoniu on 2010-09-17
em diu:
rather the invoking init scripts througt /etc/init.d, use the service(8) utility, e.g. service gdm restart.

Since the script you are attemting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart gmd
start: Rejected send message, 1 matched rules; type="method_call", sender="1.25" (uid=1000 pid=1559 comm"start) interface="com.ubuntu.Upstart0_6.job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by antoniu on 2010-09-17
He trobat gent que fent cntrl+alt+f7 els hi apareixia; a mi em surt la pantalla amb un _ parpadejant.

si faig startx salta a aquesta pantalla pero torna a l'anterior

i si per exemple escric gimp em diu:
error while loading shared libraries
/usr/lib/libatk-1.0.so0: invalid ELF header

---

### Post by antoniu on 2010-09-17
ara he fet cp xorg.conf.failsafe xorg.conf
 i al fer startx em surt molts (EE) FBDEV(0): FBIOUTPUTCMPA: Invalid argument

---

### Post by antoniu on 2010-09-17
Dacord...ara estic amb el livecd...hi ha alguna manera darreglarho des daqui

---

### Post by wgarcia on 2010-09-18
Sí, no recordava que ara s'ha de donar
service gdm restart

que pots provar, però tot apunta a què està desconfigurat. 

Prova de tornar a la línia de comandes (no des del live cd, sinó reiniciant) i dóna la següent instrucció

sudo dpkg-reconfigure xserver-xorg

a veure si ho arregla.

---

### Post by antoniu on 2010-09-19
Vaig desinstal·lar lo de xserver (Crec, ara mateix no trobo el fòrum d'on ho vaig veure) i quan ho volia tornar a instal·lar no em deixava perquè no tenia internet...ara si s'engega es queda a la pantalla de benviguda i no fa res més.

Al final m'he l'he instal·lat de nou creant una partició i quan pugui ho borraré i ho instal·laré tot de nou.

---

