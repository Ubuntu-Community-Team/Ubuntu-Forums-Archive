---
title: "Crear sistema d' arxius enllassats"
date: 2010-09-06
forum: Catalan Team
---

### Post by esviel on 2010-09-06
Es tracta d' una pràctica de la que no m'en surto , consisteix en crear un sistema d' arxius dintre d' una carpeta que s' ha de veure com un directori qualsevol.
  el guió que tinc es aquest:
**dd if=/dev/zero of=arxiu bs=4096 count=10000**
ho faig i el resultat anunciat es "41MB copiasts"
desprès toca fer 
**mkdir punt_muntatge **
(i jo aqui li donc un nom al directori i no se si li haig de donar cap mes indicació,pero em crea una carpeta al home.
**mkfs -t  ext4 arxiu**
seguidament ,
**mount -t arxiu "punt muntatge" -o loop**

aqui m'adverteix que no es un dispositiu especial de blocs i demana confirmació per continuar,confirmo i em surt un paragraf llarguissim que no entenc. 
   Puc operar amb "arxiu", copiar-hi coses i enviar-ho al directori"punt_muntatge", però en fer **umount** em respon que "no esta muntat".
    Agrairé qualsevol comentari.

---

### Post by papapep on 2010-09-06
Si treus la "t" a la última ordre, t'hauria de funcionar:

```
mount path/arxiu path/punt_muntatge -o loop
```

Salut.

---

### Post by esviel on 2010-09-08
> **papapep said:**
> Si treus la "t" a la última ordre, t'hauria de funcionar:

```
mount path/arxiu path/punt_muntatge -o loop
```

Salut.

He provat l'indicació. Desprès he copiat un arxiu al "arxiu" que havia preparat i desprès l'he enviat al directori"punt_muntatge".
  Però en fer UMOUNT  path/"punt_muntatge" la resposta és: "punt..." no esta al fstab(i no en sou el root) .
   Ho torno a provar amb el sudo su i la resposta és:no està muntat.

---

### Post by papapep on 2010-09-08
> Desprès he copiat un arxiu al "arxiu" que havia preparat i desprès l'he enviat al directori"punt_muntatge".
Però en fer UMOUNT path/"punt_muntatge" la resposta és: "punt..." no esta al fstab(i no en sou el root) .
Ho torno a provar amb el sudo su i la resposta és:no està muntat. 

No entenc què has fet en concret. Copia aquí les ordres exactes que poses i les respostes, quan n'hi hagi, del sistema. Així treballarem amb dades i no amb interpretacions.

Salut.

---

### Post by esviel on 2010-09-09
trufat@aprenent-laptop:~$ dd if=/dev/zero of=sobre bs=4096 count=10000 
10000+0 registres llegits 
10000+0 registres escrits 
40960000 octets (41 MB) copiats, 0,189873 s, 216 MB/s 
trufat@aprenent-laptop:~$ mkdir capsa 
trufat@aprenent-laptop:~$ mkfs -t ext4 sobre 
mke2fs 1.41.9 (22-Aug-2009) 
el sobre no és un dispositiu especial de blocs. 
Voleu continuar de totes maneres? (s,n)s 
Etiqueta del sistema de fitxers= 
Tipus de sistema operatiu: Linux 
Mida del bloc=1024 (log=0) 
Mida del fragment=1024 (log=0) 
10000 nodes-i, 40000 blocs 
2000 blocs (5.00%) reservats per al superusuari 
Bloc de dades inicial=1 
Màxim de blocs del sistema de fitxers=41156608 
5 grups de blocs 
8192 blocs per grup, 8192 fragments per grup 
2000 nodes-i per grup 
Còpies de seguretat del superbloc desades en els blocs: 
	8193, 24577 
Escriptura de les taules de nodes-i:fet                            
Creació del registre de transaccions (4096 blocs): fet 
Escriptura de la informació dels súperblocs i de comptabilitat del sistema de fitxers:fet 
This filesystem will be automatically checked every 24 mounts or 
180 days, whichever comes first.  Use tune2fs -c or -i to override. 
trufat@aprenent-laptop:~$ sudo su 
[sudo] password for trufat: 
root@aprenent-laptop:/home/trufat# mount /home/trufat/sobre /home/trufat/capsa -o loop 
   ara  apareix una icona de dispositiu (capsa) a l'escriptori
root@aprenent-laptop:/home/trufat# exit 
exit 
trufat@aprenent-laptop:~$ cp /home/trufat/Escriptori/mates2.pdf /home/trufat/sobre
     dintre del directori destí hi ha una carpeta lost&found que és del root i l'arxiu “sobre”
trufat@aprenent-laptop:~$ sudo su 
[sudo] password for trufat: 
root@aprenent-laptop:/home/trufat# chown -R trufat capsa 
root@aprenent-laptop:/home/trufat# exit 
exit 
trufat@aprenent-laptop:~$ cp /home/trufat/sobre /home/trufat/capsa 
     ( l'ordre anterior no se si calia)
trufat@aprenent-laptop:~$ 
trufat@aprenent-laptop:~$ sudo su 
root@aprenent-laptop:/home/trufat# umount /home/trufat/capsa 
       S'ha desmuntat i reinicio
trufat@aprenent-laptop:~$ sudo su

[sudo] password for trufat: 

root@aprenent-laptop:/home/trufat# mount /home/trufat/sobre /home/trufat/capsa -o loop

/home/trufat/sobre: No such file or directory

 En fi que l' idea es tenir un directori que es un sistema d'arxius dintre d'una carpeta que no es visible.He arribat a crear el dispositiu però quelcom he fet malament i no el puc tornar a muntar. [COLOR="Black"]**Anexo el texte en word, que resulta de mes bon llegir.Gràcies**[/COLOR]

---

### Post by esviel on 2010-09-09
trufat@aprenent-laptop:~$ dd if=/dev/zero of=sobre bs=4096 count=10000 
10000+0 registres llegits 
10000+0 registres escrits 
40960000 octets (41 MB) copiats, 0,189873 s, 216 MB/s 
trufat@aprenent-laptop:~$ mkdir capsa 
trufat@aprenent-laptop:~$ mkfs -t ext4 sobre 
mke2fs 1.41.9 (22-Aug-2009) 
el sobre no és un dispositiu especial de blocs. 
Voleu continuar de totes maneres? (s,n)s 
Etiqueta del sistema de fitxers= 
Tipus de sistema operatiu: Linux 
Mida del bloc=1024 (log=0) 
Mida del fragment=1024 (log=0) 
10000 nodes-i, 40000 blocs 
2000 blocs (5.00%) reservats per al superusuari 
Bloc de dades inicial=1 
Màxim de blocs del sistema de fitxers=41156608 
5 grups de blocs 
8192 blocs per grup, 8192 fragments per grup 
2000 nodes-i per grup 
Còpies de seguretat del superbloc desades en els blocs: 
	8193, 24577 
Escriptura de les taules de nodes-i:fet                            
Creació del registre de transaccions (4096 blocs): fet 
Escriptura de la informació dels súperblocs i de comptabilitat del sistema de fitxers:fet 
This filesystem will be automatically checked every 24 mounts or 
180 days, whichever comes first.  Use tune2fs -c or -i to override. 
trufat@aprenent-laptop:~$ sudo su 
[sudo] password for trufat: 
root@aprenent-laptop:/home/trufat# mount /home/trufat/sobre /home/trufat/capsa -o loop 
   ara  apareix una icona de dispositiu (capsa) a l'escriptori
root@aprenent-laptop:/home/trufat# exit 
exit 
trufat@aprenent-laptop:~$ cp /home/trufat/Escriptori/mates2.pdf /home/trufat/sobre
     dintre del directori destí hi ha una carpeta lost&found que és del root i l'arxiu “sobre”
trufat@aprenent-laptop:~$ sudo su 
[sudo] password for trufat: 
root@aprenent-laptop:/home/trufat# chown -R trufat capsa 
root@aprenent-laptop:/home/trufat# exit 
exit 
trufat@aprenent-laptop:~$ cp /home/trufat/sobre /home/trufat/capsa 
     ( l'ordre anterior no se si calia)
trufat@aprenent-laptop:~$ 
trufat@aprenent-laptop:~$ sudo su 
root@aprenent-laptop:/home/trufat# umount /home/trufat/capsa 
       S'ha desmuntat i reinicio
trufat@aprenent-laptop:~$ sudo su

[sudo] password for trufat: 

root@aprenent-laptop:/home/trufat# mount /home/trufat/sobre /home/trufat/capsa -o loop

/home/trufat/sobre: No such file or directory

 En fi que l' idea es tenir un directori que es un sistema d'arxius dintre d'una carpeta que no es visible.He arribat a crear el dispositiu però quelcom he fet malament i no el puc tornar a muntar. [COLOR="Black"]**Anexo el texte en word, que resulta de mes bon llegir.Gràcies**[/COLOR]

---

### Post by papapep on 2010-09-10
```

dd if=/dev/zero of=sistema_de_fitxers bs=4096 count=10000
mkdir fitxer_muntat
mkfs -t ext4 sistema_de_fitxers
mount sistema_de_fitxers fitxer_muntat -o loop

```

Fent això, jo puc ficar i treure informació sense problemes de dins el directori "fitxer_muntat". Ho he provat i no tinc cap problema en fer-ho.
En reiniciar, no t'ha de desaparéixer el fitxer que has creat, potser l'intentaves muntar indicant un camí erroni. 
Si fas:

```
ls -la /home/trufat/sobre
```

veuràs si és on penses que ha de ser o no, abans d'intentar muntar-lo.

> Anexo el texte en word, que resulta de mes bon llegir.Gràcies

Adjuntes un document de processador de text, no un "word". No és aquest el millor lloc per emprar aquesta nomenclatura :)

---

