---
title: "Salt 4.0"
date: 2009-07-11
forum: Catalan Team
---

### Post by Mitxi on 2009-07-11
Hola,
Algú Coneix el SALT 4.0? I sap com fer-lo funcionar en Ubuntu 9.04? El tinc instal·lat i em dona el següent error:
"Cal iniciar el servidor SALT4"
Ajudeu-me per favor!!

---

### Post by lluisanunez on 2009-07-12
Ja has vist la pàgina del programa [http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm](http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm) ?
Diu:
"El Salt 4.0 presenta importants novetats respecte al Salt 3.0:

    * El Salt 4.0 no funciona de manera autònoma, sinó que s’instal·la sobre el programa Writer, l’editor de textos del paquet d’OpenOffice, en la barra de ferramentes del qual apareixeran les icones amb les funcions i les utilitats del programa. Així, disposarà de totes les possibilitats d’un programa d’edició de textos com és el Writer.

---

### Post by lpargemi on 2009-07-14
> **Mitxi said:**
> 
"Cal iniciar el servidor SALT4"

Parlo de memòria, i a més no he provat SALT4. A SALT3 per consultar les bases de dades el programa es connectava a un servidor remot, i aquest enllaç calia iniciar-lo amb una acció manual. 

Per altra banda em sembla que la distribució amb què funcionava (corregiu-me si m'equivoco) era Red-Hat. A Ubuntu no vaig aconseguir instal.lar-lo, i el feia anar des de Virtualbox sobre un XP, des d'on es feia la inicialització. Després des d'openoffice es feia com comenta la lluisanunez

Lluís

---

### Post by tonisilves on 2009-09-27
No funciona a ubuntu. Si algú sap fer-lo anar?

---

### Post by dmartinez116 on 2009-09-27
Que me perdone l'autor original, però no recorde d'on ho vaig traure:

```
 Nou SALT 4.0 només per a OpenOffice.org
http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm

Instruccions Ubuntu (provat a Ubuntu 8.04 Hardy):
1.- Descarregar versió Linux: http://www.edu.gva.es/polin/docs/salt4.tgz
2.- Descomprir l'arxiu (fer doble clic damunt i polsar el botó per a extreure).
3.- Fer doble click damunt dels arxius deb i instal•lar-los en el següent ordre (per a no tindre problemes de dependències):
salt-common_4.0-1_all.deb
salt-data_4.0-1_all.deb
salt-help_4.0-1_all.deb
salt-server_4.0-1_i386.deb
salt-ooo-addons_4.0-1_i386.deb
salt_4.0-1_all.deb
4.- Obrir una terminal des de Aplicacions > Accessoris > Terminal
5.- Fiqueu: sudo /etc/init.d/salt-server start
6.- Podeu tancar la terminal

Ja teniu instal•lat el Salt!!

Ara a la barra de l'OpenOffice teniu 2 menús més: Salt i Utilitats del Salt. Per a traduir un text, seleccioneu-ho i trieu en el menú Salt l'opció adient. També inclou corrector (encara que el del OpenOffice.org és també útil).

El salt-server s'instal•la com a servei. Cada vegada que inicieu l'Ubuntu, s'engegarà per defecte.
```

---

### Post by manuelserrat on 2009-11-03
Jo he instal-lat Salt4 a Ubuntu 9.04 amb un procediment molt semblant al de l'anterior post, peró més còmode:

(tret de la pàgina oficial del SALT [http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm](http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm))

S&#8217;ha de  descarregar el fitxer [salt4.tgz]("http://www.edu.gva.es/polin/docs/salt4.tgz") i executar:
tar xzf salt4.tgz -C /tmp
sudo dpkg -i /tmp/salt*.deb
sudo apt-get -f   install


En el meu cas, no em cal iniciar el servici amb sudo /etc/init.d/salt-server start, ja que el procés d'instal.lació crea els enllaços necessaris a /etc/rc5.d per a que el servici s'inicie quan s'inicialitza l'ordinador.

Tot i això, he detectat un problema que encara no he solucionat: la meua esposa no pot usar el SALT perquè li apareix el mateix missatge que al post inicial, "Cal iniciar el servidor SALT4". I el salt-server es troba iniciat, així que crec que es deu a algun tema de drets d'accés (jo estic al grup Admin, i la meua dona no).

Estic investigant-ho, en quant ho resolga ho diré al fòrum.

Salutacions

---

### Post by chaumo on 2010-02-02
Hola, 

Yo he tenido problemas al instalarlo en Ubuntu 9.10 por las dependencias (pide python 2.5 y no acepta la python 2.6 que viene con la Karmic), no sé si en la 9.04 también pasará.

También he visto que el servidor intenta arrancar usando python 2.5 y si no existe falla. 
En mi caso lo he solucionado parcheando el .deb para que acepte versiones superiores a la 2.5. al instalar y cambiando el server para que busque python2 (cualquier versión).

He colgado la solución y el .deb parcheado en [mi web]("http://www.ruizarjona.com/especiales/tips-tools/linux-ubuntu/instalar-salt-4-ubuntu-910-solucion-problemas") , y les he enviado un mail para que lo corrijan o lo tengan en cuenta en futuras versiones.

Espero sirva de ayuda.

---

