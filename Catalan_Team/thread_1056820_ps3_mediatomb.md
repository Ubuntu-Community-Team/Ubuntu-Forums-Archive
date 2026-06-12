---
title: "ps3 mediatomb"
date: 2009-02-01
forum: Catalan Team
---

### Post by quitus on 2009-02-01
doncs això m'agradaria poder configurar el mediatomb per poder veure "tots" els formats de video de qualitat com mkv i mts2 que la ps3 no els reconeix.

salut

---

### Post by jerec on 2009-02-01
Molt bona elecció!

Per no tornar a escriure el que ja esta escrit, et remeto a un altre fòrum on ja vaig comentar les noves funcionalitats del Mediatomb 0.12

En el primer missatge trobaràs informació per tal fet:
Mes avall hi ha penjat el meu config.xml preparat per fer encoding de vídeo espero que et serveixi.

[http://www.elotrolado.net/hilo_mediatomb-0-12-0-nuevas-e-interesantes-funcionalidades_1160634]("http://www.elotrolado.net/hilo_mediatomb-0-12-0-nuevas-e-interesantes-funcionalidades_1160634")

---

### Post by quitus on 2009-02-03
No ha sigut ràpid, però he fet tot el que indicava el howto que comentes.

tot sembla que ha anat bé, fins que he compilat el mediatomb 0.12 que m'ha llençat el següent error:

/usr/local/lib/libavcodec.so.52: undefined reference to `av_lzo1x_decode'
/usr/local/lib/libavcodec.so.52: undefined reference to `av_memcpy_backptr'
/usr/local/lib/libavcodec.so.52: undefined reference to `av_random_init'
/usr/local/lib/libavcodec.so.52: undefined reference to `av_lfg_init'
/usr/local/lib/libavcodec.so.52: undefined reference to `av_gcd'
collect2: ld returned 1 exit status
make[2]: *** [mediatomb] Error 1


no tinc ni idea de que està passant, amb prou feines he anat solventant els petits problemes que han sortit (el meu angles es molt elemental) fins que he arribat aquí.

gracies i salut.

---

### Post by jerec on 2009-02-04
Aixi dons, et recomano abans de compilar el 0.12.0, que val mes que posis el anterior 0.11.0 directament dels repositoris de mediatomb
[http://mediatomb.cc/pages/download#debian_ubuntu]("http://mediatomb.cc/pages/download#debian_ubuntu")

Despres quant el tinguis funcionant, ja et pots atrevir a compilar des de el subversion de mediatomb el nou per tastar les noves funcionalitats.

---

### Post by quitus on 2009-02-05
Sembla que ja està. S'ha de eliminar de /usr/local/lib els arxius que donen errors, libavcodec en el meu cas. 
Desprès m'ha sortit un error de sqlite en inicialitzar el mediatomb, per la qual cosa només cal reiniciar l'ordinador.

Ara falta editar el config.


salut

edito: he provat de canviar el config.xml pel teu, jerec, pero no funciona, les adreces son diferents. El teu config.xml no serà del mediatomb 0.11? de totes maneres he provat de canviar només les parts importants i tampoc funciona, no puc veure els VOB ni m2ts

---

### Post by jerec on 2009-02-08
No, tinc els dos, tant el 0.11 com el 0.12

Repassa be el config.xml, el que hi ha penjat es el meu, però has de canviar coses segons la configuració de la teva maquina
Segur que has vist que el meu esta configurat per anar amb MySql i no amb SqlLite, també veuràs que hi ha els usuaris ficticis perquè els editis amb els que tens tu.
També la IP has de posar la del teu servidor, fixat que forço fer servir sempre el port 49152.

Si vols fer servir el MySql, es fàcil:
 - Instal·la el servidor MySql
 - Crea una base de dades ex: mediatomb
 - Crea un usuari ex: mediatomb amb permisos a la base de dades mediatomb
 -  Crea les taules a la base de dades amb el fitxer que tens a:
     /usr/local/share/mediatomb/mysql.sql 
     o a: 
     /usr/share/mediatomb/mysql.sql
    # mysql -u root -p mediatomb < /usr/share/mediatomb/mysql.sql

llegeix la secció "4.2.2. Using MySQL Database"
del readme.txt del mediatomb:
[http://mediatomb.cc/readme.txt]("http://mediatomb.cc/readme.txt")

Abans mira que el transcode funcioni, el mediatomb no fa res mes que ajudar-se d'ell per descodificar els arxius que tu li diguis.

---

### Post by quitus on 2009-02-09
> **jerec said:**
> 

Abans mira que el transcode funcioni, el mediatomb no fa res mes que ajudar-se d'ell per descodificar els arxius que tu li diguis.

potser es una pregunta tonta, però... com provo el transcode?

salut.

---

