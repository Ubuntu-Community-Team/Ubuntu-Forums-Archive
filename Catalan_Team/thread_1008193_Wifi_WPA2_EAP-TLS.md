---
title: "Wifi WPA2 EAP-TLS"
date: 2008-12-11
forum: Catalan Team
---

### Post by jaff77 on 2008-12-11
Hola estic intentant montar un sistema per autenticar clients inalàmbrics WPA2 per EAP-TLS amb freeradius.
De moment he montat sa infraestructura de PKI amb OpenSSL, creant un certificat per la CA i un pel client.
He instal·lat el freeradius des del Synaptic i quan intent executar-lo (radiusd -X, segons la documentació qu he trobat), me diu:
~$ radiusd -X
El programa «radiusd» es troba en els paquets següents:
 * radiusd-livingston
 * yardradius
 * xtradius
Proveu: sudo apt-get install <paquet seleccionat>
bash: radiusd: command not found

Com pot ser que el Synaptic no instal·li l'executable del freeradius (doncs que m'ha instal·lat?)? o és que ho he d'executar d'una altra manera? he d'instal·lar algun d'aquests 3 programes que me diu, quin?
Alguna ajuda? 
Gràcies

---

### Post by argggg on 2008-12-11
Jo crec que per iniciar el dimioni de freeradius has de posar
/etc/init.d/freeradius start

---

### Post by jaff77 on 2008-12-17
D'acord. Resulta que cercant ([http://ubuntuforums.org/showthread.php?t=419718&highlight=FreeRADIUS+EAP]("http://ubuntuforums.org/showthread.php?t=419718&highlight=FreeRADIUS+EAP")), he trobat que la versió de freeradius del repositori d'ubuntu no duu suport per EAP i q per tant s'ha d'intal·lar a mà. 
He seguit aquestes passes:

[I]tar zxvf freeradius-1.1.x.tar.gz
cd freeradius-1.1.x/

dpkg-buildpackage -rfakeroot 
# might prompt you to install missing dependencies
# if so apt-get install pkg1 pkg2 ...
# compilation will take some time, just relax ;-)

dpkg -i freeradius_1.1.3-0_i386.deb[/I]

però quan arribo a la darrera comanda, me surt l'error:

[I]sudo dpkg -i ../freeradius_2.1.3-0_i386.deb
(Reading database ... 121631 files and directories currently installed.)
Unpacking freeradius (from ../freeradius_2.1.3-0_i386.deb) ...
dpkg: error processing ../freeradius_2.1.3-0_i386.deb (--install):
 trying to overwrite `/usr/bin/rlm_dbm_cat', which is also in package freeradius-utils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ../freeradius_2.1.3-0_i386.deb[/I]

He quedat enrocat aquí, alguna ajuda.

---

### Post by RainCT on 2008-12-17
Prova a editar el fitxer debian/control i a sota de "Binary: freeradius" afegir la línia "Replaces: freeradius-utils", i llavors tornant a crear el .deb amb dpkg-buildpackage.

---

### Post by jaff77 on 2008-12-18
No surt la paraula Binary al meu fitxer.

---

### Post by jaff77 on 2008-12-19
Aquest és el meu fitxer "control"
Alguna ajuda?

---

### Post by PatrickVogeli on 2008-12-19
em sembla que ho has de posar a sota de package: freeradius

salut

---

### Post by RainCT on 2008-12-20
> **PatrickVogeli said:**
> em sembla que ho has de posar a sota de package: freeradius

Exacte, se me n'ha anat l'olla XD.

---

### Post by jaff77 on 2008-12-22
Gràcies, error superat però ara me'n surten de nous (què difícil és instal·lar això, no?)

pc:~/freeradius-server-2.1.3$ sudo dpkg -i ../freeradius_2.1.3-0_i386.deb

(Reading database ... 121631 files and directories currently installed.)
Unpacking freeradius (from ../freeradius_2.1.3-0_i386.deb) ...
Replacing files in old package freeradius-utils ...
dpkg: error processing ../freeradius_2.1.3-0_i386.deb (--install):
 trying to overwrite `/usr/share/man/man1/radeapclient.1.gz', which is also in package freeradius-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 ../freeradius_2.1.3-0_i386.deb

Alguna suggerència?
Gràcies

---

