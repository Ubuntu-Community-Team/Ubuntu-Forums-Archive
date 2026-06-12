---
title: "No puc muntar un partició"
date: 2014-07-28
forum: Catalan Team
---

### Post by Satboy on 2014-07-28
Hola,
 He instal·lat el S.O. lleuger **Watt OS** (basat en Debian) en un ordidandor de sobretaula vell, m'he adonat que no em munta una partició a on hi tinc dades importants guardades i voldria que se'm muntés automàticament cada vegada que inicii l'ordinador.He fet un nsab i curiosament hi surt la partició però no la munta.

[IMG]http://i62.tinypic.com/358bg34.jpg[/IMG]

 la partició en qüestió és la **/dev/sda3**  

 Veig que diu alguna cosa d'un error, i a la principal (sda1) també.

 Moltes gràcies! ;)

---

### Post by wgarcia on 2014-07-28
Si l'intentes muntar manualment, per exemple creant un directori al teu home que es digui "/home/<el-teu-usuari>/prova" i fent

```
sudo mount /dev/sda3 /home/<el-teu-usuari>/prova
```

surt algun error?

---

### Post by jmaspons on 2014-07-28
Hola,
Em sembla que et falta afegir el punt de muntatge de la partició entre la tirallonga de caràcters i ext4. Mira que la carpeta del punt de muntatge existeixi i tingui els permissos adequats.

Pel tema dels errors, no et preocupis. És un paràmetre que especifica que si es troben errors en muntar la partició es torna a intentar però sense permisos d'escriptura (Read Only). Si vols remenar mira a [http://manpages.ubuntu.com/manpages/trusty/man8/mount.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/mount.8.html) i [http://manpages.ubuntu.com/manpages/trusty/en/man5/fstab.5.html](http://manpages.ubuntu.com/manpages/trusty/en/man5/fstab.5.html)

Salut!

---

### Post by Satboy on 2014-07-28
> **jmaspons said:**
> Hola,
Em sembla que et falta afegir el punt de muntatge de la partició entre la tirallonga de caràcters i ext4
...

Hola,
 Gràcies a tots dos, com puc solventar-ho això?

Dew! ;)

---

### Post by wgarcia on 2014-07-29
Però has pogut muntar la partició manualment mitjançant la comanda que et comentava?

---

### Post by Satboy on 2014-07-29
> **wgarcia said:**
> Però has pogut muntar la partició manualment mitjançant la comanda que et comentava?

 Hola,
 Ara si que ho he fet:

> 
david@linux:~$ sudo mount /dev/sda3 /home/Varis/prova
[sudo] password for david: 
mount: el punt de muntatge /home/Varis/prova no existeix
david@linux:~$ 


Dew! ;)

---

### Post by wgarcia on 2014-07-29
Has creat un directori a la teva carpeta d'usuari que es digui "prova"? En altre paraules, existeix el directori /home/varis/prova?

---

### Post by Satboy on 2014-07-31
> **wgarcia said:**
> Has creat un directori a la teva carpeta d'usuari que es digui "prova"? En altre paraules, existeix el directori /home/varis/prova?

 Hola,
 Ostres no, em pensava que només era de prova.

 A veure, ara ho provo amb un arxiu que ja existeixi:

 > 
david@linux:~$ sudo mount /dev/sda3 /home/Varis/Jocs
[sudo] password for david: 
mount: el punt de muntatge /home/Varis/Jocs no existeix
david@linux:~$ sudo mount /dev/sda3 /home/Varis/Fotos
mount: el punt de muntatge /home/Varis/Fotos no existeix
david@linux:~$ sudo mount /dev/sda3 /home/Varis/Varis
mount: el punt de muntatge /home/Varis/Varis no existeix
david@linux:~$ 

Ho he provat vàries vegades i res de res!

 Dew! ;)

---

### Post by wgarcia on 2014-07-31
Segur que els directoris aquests existeixen? Per exemple, funciona 

```
ls /home/Varis/Jocs
```

?

No hi ha algun problema amb les majúscules a "Varis"?

---

### Post by Satboy on 2014-07-31
> **wgarcia said:**
> Segur que els directoris aquests existeixen? Per exemple, funciona 

```
ls /home/Varis/Jocs
```

?

No hi ha algun problema amb les majúscules a "Varis"?

 Hola,
 Si, la majúscula és correcta.

 He provat el què m'has dit:

> david@linux:~$ sudo ls /home/Varis/Jocs
[sudo] password for david: 
ls: no s’ha pogut accedir a /home/Varis/Jocs: El fitxer o directori no existeix
david@linux:~$ 


 Dew! ;)

---

### Post by wgarcia on 2014-07-31
Doncs això: "El fitxer o directori no existeix", potser et falta el nom de la teva carpeta d'inici, tot el camí hauria de ser /home/<carpeta-d'inici>/Varis/Jocs (suposant que el directori Varis/Jocs existeix a la teva carpeta d'inici.

---

### Post by Satboy on 2014-08-01
Hola,
Doncs, efectivament, no hi ha punt de muntatge, però com ho puc solventar?

 [IMG]http://i59.tinypic.com/iyk5sm.jpg[/IMG]

 Potser amb la versió Live del **GParted**?

 Dew! ;)

---

### Post by wgarcia on 2014-08-01
Suposant que el directori existeix, per muntar la partició es pot fer amb l'ordre:

```
sudo mount /dev/sda3 <nom del directori>
```

El problema és que "/home/Varis/Jocs" no existeix. El <nom del directori> ha de ser un directori existent al teu sistema. Si realment hi ha un directori "Varis/Jocs" a la teva carpeta d'inici, la ruta hauria d'incloure el teu nom d'usuari, per exemple en el meu cas seria /home/wgarcia/Varis/Jocs. Pots obrir una terminal i fer 

```
pwd
```

?

Així podràs veure què has de posar després de "/home".

---

### Post by Satboy on 2014-08-01
Hola,
 AIxò ja és com un bucle!

> david@linux:~$ pwd
/home/david
david@linux:~$ 


 > david@linux:~$ cd /home/david/Varis/Jocs
bash: cd: /home/david/Varis/Jocs: El fitxer o directori no existeix
david@linux:~$ 


 Dew!;)

---

### Post by wgarcia on 2014-08-01
I 

```
ls Varis
```

què dóna?

---

### Post by jmaspons on 2014-08-01
Per crear una carpeta pots fer-ho amb qualsevol gestor de fitxers o amb la comanda següent:
```

mkdir /home/david/Varis

```
Això crearà la carpeta Varis dins de la teva carpeta d'usuari (assumint que el teu nom d'usuari és david).

Si vols crear una carpeta fora de la teva carpeta d'usuari potser necessitaràs executar la comanda com a root (sudo *commanda*). I si després vols muntar-la i accediri com a usuari caldrà que li donis els permisos adients (e.g. sudo chown david /home/Varis).

Un cop tens la carpeta creada i hagis comprovat que pots muntar la partició, pots corregir el fitxer fstab perquè es munti automàticament:
```

# /dev/sda3
UUID=19caf42c-75b6-4fa7-b129-b060ae9539a6            /home/david/Varis            ext4                 defaults           0        2

```

A veure si ara hi ha sort.
Salut!

---

### Post by Satboy on 2014-08-05
Hola,
 Tornant al tema i un cop fet el què em vas suggerir, ara el sistema ja em reconeix la unitat:

 [IMG]http://i59.tinypic.com/2jfm6gl.jpg[/IMG]

 Però no m'hi deixa entrar:

 [IMG]http://i61.tinypic.com/14myxee.jpg[/IMG]

 Dew i gràcies per la paciència!

---

