---
title: "sense espai en &quot;/&quot;"
date: 2009-12-21
forum: Catalan Team
---

### Post by quitus on 2009-12-21
Darrerament em van sortint avisos de la falta d'espai en el directori arrel, vaig arribar al punt que ni tant sols em deixava obrir el synaptic perquè no podia copiar no se quin arxiu, vaig aconseguir fer una mica d'espai però no crec que duri gaire. A veure que em dieu.

marcimerce@marcimerce-desktop:~$ df -h
S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda4              28G   25G  1,7G  94% /
udev                  502M  268K  501M   1% /dev
none                  502M  524K  501M   1% /dev/shm
none                  502M  300K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda3              54G   35G   18G  67% /home
/dev/sdb1             232G  137G   83G  63% /media/sda1
/dev/loop0            681M  681M     0 100% /tmp/tmpQUZXZv
/dev/sdc1              15G  7,1G  7,9G  48% /media/90CE-3878

---

### Post by oriolsbd on 2009-12-22
Hola,

Per eliminar els fitxers .deb de paquets ja instal·lats, pots executar la comanda següent:
```
sudo apt-get autoclean
```

Per eliminar llibreries que ja no utilitza cap programa, executa el següent:
```
sudo apt-get autoremove
```

De tota manera, en aquesta partició hi tens assignats 28GB, i tens el /home separat. No sé si és normal que t'ocupi tant. Hauries d'analitzar una mica on tens tan espai ocupat. Segur que et pot ajudar l'analitzador que es troba a "Aplicacions>Accessoris>Analitzador de l'ús dels discs". En aquesta eina, executa el menú "Analitzador>Escaneja el sistema de fitxers". Segur que et dóna alguna pista.

Salut!

---

### Post by Rubunter on 2009-12-22
No és massa bona solució, però amb tune2fs pots guanyar un 5% de capacitat, que actualment està reservada.

---

### Post by kimet on 2009-12-22
A mes del que et diu l'oriolsbd, pots instal.lar:

_localepurge_, per eliminar els paquets d'idiomes que no son necesaris i _deborphan_ per localitzar els paquets orfes i desinstalar.los posteriorment.

Salut.

---

### Post by quitus on 2009-12-22
> **oriolsbd said:**
> Hola,

Per eliminar els fitxers .deb de paquets ja instal·lats, pots executar la comanda següent:
```
sudo apt-get autoclean
```

Per eliminar llibreries que ja no utilitza cap programa, executa el següent:
```
sudo apt-get autoremove
```

De tota manera, en aquesta partició hi tens assignats 28GB, i tens el /home separat. No sé si és normal que t'ocupi tant. Hauries d'analitzar una mica on tens tan espai ocupat. Segur que et pot ajudar l'analitzador que es troba a "Aplicacions>Accessoris>Analitzador de l'ús dels discs". En aquesta eina, executa el menú "Analitzador>Escaneja el sistema de fitxers". Segur que et dóna alguna pista.

Salut!

Després d'executar les dues ordres he aconseguit 1,5 GB més, amb la qual cosa ja tinc una mica més d'espai per seguir treballant, però l'origen del meu fil es aquest, que no és normal. Ja vaig executar el baobab i la informació que obtinc es curiosa, ja que em diu que el directori arrel ocupa 5,1GB dels quals 4,2 pertany al directori "usr"

Penso que hi ha alguna cosa en la partició sda4 que està ocupant la major part de l'espai, que no pertany al directori arrel, però no se com inspeccionar-ho. 

salut

---

### Post by papapep on 2009-12-22
Prova amb aquesta ordre:

```
find / -type f -size +20000k -exec ls -lh {} \; 2> /dev/null | awk '{ print $NF ": " $5 }'  | sort -nrk 2,2 > analisi_fitxers.txt
```

Un cop acabi hauries de tenir dins analisi_fitxers.txt els fitxers més grans de 20 Mb ordenats de major a menor, a veure si tens alguna sorpresa.

També pots fer un llistat dins d'un directori on tinguis molta teca per veure què hi tens més gran:

```
du -sk * | sort -nr
```

---

### Post by quitus on 2009-12-22
> **papapep said:**
> 

Un cop acabi hauries de tenir dins analisi_fitxers.txt els fitxers més grans de 20 Mb ordenats de major a menor, a veure si tens alguna sorpresa.


Doncs si que hi ha sorpreses, apareixen un munt d'arxius de vídeo alguns els reconec, altres no. Aquests arxius apareixen sense cap mena d'indicació de la seva ubicació, es a dir sense /media/...  
Això deu indicar que es troben en aquesta partició sda4 on es troba el directori arrel? Com es que no els puc veure amb el nautilus? Com els puc eliminar? Com han arribat fins aquí?

Quantes preguntes...

salut i gracies.




EDITO:M'he avançat. Els arxius que he comentat els tinc localitzats, el que passa es que en no aparèixer la ubicació...
seguim com abans.

---

