---
title: "Problemes amb la connexio entre Amarok 1.4 i MySQL de LAMPP"
date: 2009-05-11
forum: Catalan Team
---

### Post by mcako on 2009-05-11
Hola, 
Vaig configurar l'Amarok perquè em guardés la meva col·lecció de música a una base de dades de MySQL. Com que Amarok només pot connectar-se a MySQL a través de la direcció /var/run/mysqld/mysqld.sock i jo vaig instal·lar MySQL a través de LAMPP, el socket de MySQL es troba a /opt/lampp/var/mysql/mysql.sock, de manera que vaig haver de crear un enllaç simbòlic tal com vaig llegir en un altre fòrum:
```
ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock
```
El problema és que quan reinicio el sistema l'enllaç simbòlic i la carpeta "mysqld" que havia creat a /var/run/ desapareix.

És normal això? hi ha alguna manera de fer-ho persistent?

Se m'havia passat pel cap fer un script que comprovés si existeix l'enllaç i sinó que el creés, però segur que hi deu haver una solució més senzilla.

---

### Post by marteljorge on 2009-05-11
> **mcako said:**
> Hola, 
Vaig configurar l'Amarok perquè em guardés la meva col·lecció de música a una base de dades de MySQL. Com que Amarok només pot connectar-se a MySQL a través de la direcció /var/run/mysqld/mysqld.sock i jo vaig instal·lar MySQL a través de LAMPP, el socket de MySQL es troba a /opt/lampp/var/mysql/mysql.sock, de manera que vaig haver de crear un enllaç simbòlic tal com vaig llegir en un altre fòrum:
```

```
El problema és que quan reinicio el sistema l'enllaç simbòlic i la carpeta "mysqld" que havia creat a /var/run/ desapareix.

És normal això? hi ha alguna manera de fer-ho persistent?

Se m'havia passat pel cap fer un script que comprovés si existeix l'enllaç i sinó que el creés, però segur que hi deu haver una solució més senzilla.

Se m'acut:
```
sudo echo "ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock" > /etc/init.d/mysqld.sck.bint
sudo chmod -x /etc/init.d/mysqld.sck.bint
```

---

### Post by mcako on 2009-05-11
Gràcies per l'ajuda, però no tinc aquest fitxer mysqld.sck.bint dins de la carpeta init.d, representa que l'he de crear? Potser posant la comanda per crear el link simbolic dins de /etc/rc.local també funcionaria no?
Segons tinc entès el rc.local es un script que s'executa a l'inici que es pot modificar per entaforar-hi tot el que vulguis. Però d'aquesta manera m'està creant un enllaç simbòlic a cada arrancada.
De totes maneres segueixo sense entendre perquè s'esborren els fitxers que poso a run, que representa la carpeta /var/run?

**Edit:**
Ara he estat provant la comanda, però estic pensant que he de ser root per poder executar aquesta comanda. No hi haurà cap problema si ho poso al rc.local?

---

### Post by marteljorge on 2009-05-11
Primer, la comanda què he escrit és per crearl-o.
Home, el què he escrit és un script d'autoinici, però necessites ser "sudoer", no "root". Suposo què pel rc.local hauries de fer:```
echo "ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock" > ~/rc.local

```

---

### Post by mcako on 2009-05-11
No m'he explicat gaire bé. Al final ho he solucionat posant lo següent a l'arxiu /etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo mkdir /var/run/mysqld
sudo ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock
exit 0
```

Crec que els "sudos" no hi pinten res, però bueno..
Ara cada cop que arranca el sistema m'intenta crear la carpeta i el link.
Gràcies igualment per l'ajuda!

---

