---
title: "Virtualbox a tots els usuaris"
date: 2009-12-01
forum: Catalan Team
---

### Post by toni f on 2009-12-01
Bon dia a tothom,

Fa poc que faig servir Ubuntu però no hem puc desempallegar d'un altre SO. Faig servir virtualbox i tinc varis problemes:

- Tinc varis usuaris creats, però només apareix a un el SO que he instal.lat, es possible fer servir aquesta instal.lació per l'altre usuari? 

- Trobo que funciona molt lent, es possible fer-lo rutllar més ràpid?

- No es veuen gairebé els gràfics, cal que instal.li drivers també?

Ens veiem, 

Dew!!

---

### Post by akyra on 2009-12-01
Hola,
> - Tinc varis usuaris creats, però només apareix a un el SO que he instal.lat, es possible fer servir aquesta instal.lació per l'altre usuari? 

Has de anar a Sistema->Usuaris, i afegir el grup VirtualBox a tots els usuaris.

> - Trobo que funciona molt lent, es possible fer-lo rutllar més ràpid?

Depen de la màquina que tinguis, però en el cas de la memòria ha de ser menor de la meitat de la memòria física del teu ordinador. Si virtualitzas un XP amb 512MB hauries de funcionar (si en poses 1GB millor, però hauries de tenir com a mínim 2GB en el teu ordinador).

> - No es veuen gairebé els gràfics, cal que instal.li drivers també?

Amb les Guest Adittions crec que faràs prou.

Salut

---

### Post by toni f on 2009-12-02
Hummmmmm, hem sembla que soc molt totxo.

Arribo a usuaris, hi surten dos usuaris i el root. He posat el pass per accedir a propietats i gestió de grups però no trobo res on pugui enllaçar el virtualbox ni res de res. 

Disculpeu les molèsties.

P.D. Et ben juro que porto des d'ahir provant i res de res, ja et dic soc molt...... totxo!!!!

---

### Post by akyra on 2009-12-03
Quan instal·les VirtualBox, normalment es crea un grup VirtualBox, i normalment es troba a la gestio de grups, com a mínim totes les vegades que ho he instal·lat a estat així.

L'usuaria amb el que l'has instal·lat hauria de tenir aquest grup creat.

Ja diràs el que.

Adeu

---

### Post by toni f on 2009-12-03
Osti (amb perdó) no trobo res, entro dins de la pestanya
gestiona a grups / parametres dels grups i hem surt un llistat però no trobo res que s'asembli a virtualbox o l'altre SO

Res que no hi ha manera, a veure si aquests 4 dies puc fer un intensiu jejeje 

ens veiem!

---

### Post by PatrickVogeli on 2009-12-03
A gestiona els grups, has de tenir, a la llista, vboxusers, llavors cliques propietats i alla has de tenir tots els usuaris posats.

Això fara que puguis utilitzar el virtualbox amb tots els usuaris, però no et compartirà res encara.

Per compartir-ho, una manera ràpida, pero una mica xapucera, és crear un enllaça simbolic d'un usuari a un altre. Per example, l'usuari Pepito és el que te configurat i funcionant el virtualbox i també vols tenir el mateix a l'usuari Pere i Joan. Pots fer el següent:

mv /home/Joan/.Virtualbox /home/Joan/.Virtualbox-old
mv /home/Pere/.Virtualbox /home/Pere/.Virtualbox-old
ln -s /home/Pepito/.Virtualbox /home/Pere/
ln -s /home/Pepito/.Virtualbox /home/Joan/

tingues en compte que això ni es elegant i segurament presenta riscos de seguretat, però farà el fet.

Salut

---

### Post by toni f on 2009-12-04
Hem sembla que la cosa es complica, no hi es vbouxers (m'ho he remirat varis cops per si de cas).

N'hi ha un que diou winbindd_priv (es l'unic que s'assembla a l'altre SO)La resta hem semblen igual de sospitosos  ;D

Miraré de fer un llistat de tot el que hem surt a paràmetres dels grups. 
Es extrany, vaig instal.lar virtualbox des dels repositoris (no se si això ajuda)

PatrickVogeli 
M'has deixat intrigat quan et refereixes que puc tenir riscos de seguretat, no ho entenc. Et refereixes a virus?

Gràcies de nou,

Ens veiem!

---

### Post by akyra on 2009-12-04
No té res que veure amb virus.

Crec que el que es refereix en Patrick es que pots tenir accés a la carpeta /home d'un altre usuari. No sé si també cal tenir accés d'escriptura per que no peti el virtualbox.

Adeu.

---

### Post by toni f on 2009-12-04
Ah! Si el risc es aquest no hem preucupa, gràcies.

Pel que fa al que hem surt a paràmetres dels grups el que surt es el següent:

root             kmen              list        libuuid      admin
daemon           dialout           irc         syslog       saned
bin              fax               scr         fuse         pulse
sys              voice             gnats       lpadmin      pulse-access
adm              cdrom             shadow      ssl-cert     gdm
tty              floppy            utmp        messagebus   toni
disk             tape              video       contrab      sambashare
lp               sudo              sasl        mlocate      winbindd_priv
mail             audio             plugdev     ssh          patricia
news             dip               staff       avahi        rtkit
uucp             www-data          games       netdev
man              backup            users       couchdb
proxy            operator          nogroup     haldaemon

Es aqui on haig de buscar el vbouxusers?

Doncs això, ens veiem!!

---

### Post by toni f on 2009-12-16
Hola,

No voldria fer-me pesat amb el tema ni incomplir cap norma.

Encara estic amb el tema, buscant el vboxusers.....

He mirat altres informacions i la conclusió a la que he arribat es que per que surti el vboxusers deu ser una opció de quan l'instal.lo. Vaig ben encaminat? Haig d'instal.lar de nou tot virtualbox+l'altre SO?

Merci.

---

### Post by papapep on 2009-12-16
> - Tinc varis usuaris creats, però només apareix a un el SO que he instal.lat, es possible fer servir aquesta instal.lació per l'altre usuari?

Quan dius això vols dir que la màquina virtual que has creat només la pot executar un usuari, però que el Virtualbox (el programa que les gestiona) el veuen tots els teus usuaris?

De ser així, el que has de fer es ficar el fitxer .vdi (el disc dur virtual que conté l'altre sistema operatiu que has instal·lat dins el Virtualbox) sigui a un lloc on tots els usuaris tinguin plens drets d'accés.

Per exemple, crees un directori de nom maquinesVirtuals (pot ser el nom que a tu més t'agradi) dins /home:

```
sudo mkdir /home/maquinesVirtuals
```

li dones permisos d'accés totals:

```
sudo chmod 777 /home/maquinesVirtuals
```

i mous el disc dur virtual dins aquesta carpeta. Normalment els discs dur són dins /home/elteuusuari/.VirtualBox/HardDisks). Suposant que el teu disc dur es digui laltresistema.vdi, faries:

```
sudo mv /home/elteusuari/.VirtualBox/HardDisks/laltresistema.vdi /home/maquinesVirtuals/laltresistema.vdi
```

Ara només quedarà assegurar que tots els usuaris poden accedir al fitxer .vdi:

```
sudo chmod 777 /home/maquinesVirtuals/laltresistema.vdi
```

Evidentment, has de canviar tots els "elteusuari" i "laltresistema.vdi" pel nom que tinguis tu a cada element.
A nivell de seguretat aquesta solució no es faria mai a nivell d'una empresa o amb dades sensibles, ja que tots els usuaris tenen el mateix dret d'accés, però a nivell casolà, normalment, no té més implicacions.

Si tens dubtes o alguna ordre no acaba d'anar com s'espera, enganxa aquí tant la ordre que has posat (exactament, fes copia-ferra, per no cometre errors tipogràfics) com el missatge/resposta que et doni el sistema.

Salut.

---

### Post by toni f on 2009-12-17
Gràcias papapep per facilitar-me tant clarament l'informació.

He probat el que m'indiques i el resultat es aquest:

[HTML]toni@batpc:~$ sudo mv /home/toni/.VirtualBox/HardDisks/xp.vdi /home/maquinesVirtuals/xp.vdi
[sudo] password for toni: 
mv: ha fallat stat() sobre «/home/toni/.VirtualBox/HardDisks/xp.vdi»: No such file or directory
toni@batpc:~$ 
[/HTML]

Entenc que no troba la carpeta ni l'arxiu que li demano, he buscat amb l'eina "cercar fitxers" posant virtualbox i m'envia a usr/share o a usr/lib i ha dintre no trobo l'altre sistema operatiu. He buscat també per *.vdi i no troba res de res. Totes les cercas estan fetes dins de la carpeta "sistema de fitxers". 

Començo a pensar que no ho vaig instalar correctament tot i fer-ho des dels repositoris.

Estic buscant erroneament? l'he instal.lat a un altre ordinador? o m'he equivocat de casa? ;D Ja no ho se, ara en serio com puc trobar l'arxiu .vdi? Crec que la resta puc aconseguir-ho, he apres a crear la carpeta, a donar-li privilegis i fins aquí. M'agrada el que faig i el que feu, gràcies de nou.

Apa, ens veiem!

---

### Post by papapep on 2009-12-17
I si fas un:

```
ls -la /home/toni/.VirtualBox/HardDisks
```

què et surt? enganxa-ho aquí mateix.

Vas arribar a instal·lar el sistema operatiu dins (crear la màquina virtual) Virtualbox? primer m'ha semblat, pel que deies, que era que sí, però ara ja em fas dubtar...si vas a executar el Virtualbox al menú d'aplicacions, veus alguna màquina virtual creada al gestor de màquines virtuals, com la de la imatge que adjunto?

---

### Post by toni f on 2009-12-17
Iep! Aqui ja surt quelcom que busco

[HTML]toni@batpc:~$ ls -la /home/toni/.VirtualBox/HardDisks
total 1218616
drwxr-xr-x 2 toni toni       4096 2009-12-13 15:32 .
drwxr-xr-x 4 toni toni       4096 2009-12-13 15:55 ..
-rw------- 1 toni toni 1247846912 2009-12-17 08:05 XP.vdi
toni@batpc:~$ 
[/HTML]

I aqui la captura

[IMG][[IMG]http://img704.imageshack.us/img704/5683/capturai.th.png[/IMG]](http://img704.imageshack.us/i/capturai.png/)[/IMG]

---

### Post by papapep on 2009-12-17
Doncs, toni f, en Gnu/Linux: xp **!=** XP :)

Àltrament dit: si repeteixes les ordres que abans t'han fallat posant bé aquest cop el nom del fitxer .vdi que vols moure, t'hauria de funcionar tot plegat.

---

### Post by toni f on 2009-12-18
Fantàstic papapep!!! 

Solucionat i rutllant. En treuré profit gràcies, ens veiem.

---

