---
title: "FSCK - dev. busy"
date: 2019-06-15
forum: Argentina Team
---

### Post by Vero1 on 2019-06-15
Ubuntu 18.04-

Cada vez que arranco la máquina, me sale un aviso de ERROR en Ubuntu, preguntando si quiero informar. Digo que sí, en cada ocasión pero el error sigue saliendo.
 
Tengo problemas de cuelgues. Trato de correr FSCK pero me informa que el dev. sda3 (donde está Raiz) está montado y no puede chequear.

Se puede desmontar Raíz para poder hacer el chequeo de todos los archivos?

Si la respuesta es sí, en qué forma? Traté de desmontar con Terminal pero me contesta que está ocupado.

Gracias y saludos

---

### Post by Bashing-om on 2019-06-15
Vero1; Hello -

As a file system is dynamic and constantly changing fsck cannot get a handle on it, One must conduct a file system check while the target is not mounted,

In this case I highly recommend that the file system check be ran from a live environment ( DVD or USB).

From the liveUSB - :try ubuntu mode - activate a terminal. and execute:
swap off if necessary:
```

sudo parted -l

```
so you know the target partition,

the file system checks:
```

change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required

sudo e2fsck -C0 -p -f -v /dev/sda1

#if errors: -y auto answers yes for fixes needing response see: man e2fsck

sudo e2fsck -f -y -v /dev/sda1

```
See: fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Vero1 on 2019-06-16
Thank you for your quick response. As English is not my first language, I will copy your post and with the help of a Translator I'll see what will I do.

Regards

---

### Post by Bashing-om on 2019-06-16
Vero1; Good :)

As English is the only language I can function in .. my hat is off to you to even try to relate in other than your native tongue.

Will await and see further how we can help.

[INDENT][INDENT]all in this together
[/INDENT][/INDENT]

---

### Post by Vero1 on 2019-06-16
You are really a very kind person :-) Thanks.
I owe very much to Facebook, where I am an Admin. my capacity of "speaking" English a little better than before :-)
Will come back when I`ll have news.
Thanks again for your help.

Regards

---

### Post by Vero1 on 2019-06-19
Hi, good morning.
I did what you told me. The result was no errors.
On the other hand, I am still recieving the internal error of Ubuntu, despite of sending in each occasion the report, as they ask.
I can't make a print-screen, but it says:

ExecutablePath

/usr/bin/baloo_file_extractor

Please, can you tell me what to do?

Thanks and regards.

---

### Post by Bashing-om on 2019-06-19
Vero1 ; Very well :)


Then it is an app that is now misbehaving ?

See:[https://community.kde.org/Baloo/Debugging](https://community.kde.org/Baloo/Debugging)
for possible solutions and/or add your input to the bug tracker.

-we can do that-

---

### Post by Vero1 on 2019-06-21
Thank you very much. I'll see. After will comment you.
Regards.

---

### Post by Vero1 on 2019-06-21
Hi, I went to :[https://community.kde.org/Baloo/Debugging](https://community.kde.org/Baloo/Debugging) and apparently it belongs to KDE, but I have no KDE. Why is this Baloo on my Ubuntu?
Can't I uninstall it some way? 

Thanks.

---

### Post by Bashing-om on 2019-06-21
Vero1; Hummm ...
1)
> 
Why is this Baloo on my Ubuntu?

No idea why it is installed - it is not default in my system.

2)
> 
Can't I uninstall it some way? 

Most likely can be safely removed.

Let's see about that removal :)
post back the outputs of terminal commands:
```

ls -al /usr/bin/baloo_file_extractor
dpkg -l baloo
apt policy baloo

```
 and I bet the package manager will happily remove baloo from the system.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Vero1 on 2019-06-21
Here are the responses:

veronica@veronica-MS-7A15:~$ ls -al /usr/bin/baloo_file_extractor
-rwxr-xr-x 1 root root 129168 mar 12  2018 /usr/bin/baloo_file_extractor
veronica@veronica-MS-7A15:~$ dpkg -l baloo
Deseado=desconocido(U)/Instalar/eliminaR/Purgar/retener(H)
| Estado=No/Inst/ficheros-Conf/desempaqUetado/medio-conF/medio-inst(H)/espera-disparo(W)/pendienTe-disparo
|/ Err?=(ninguno)/requiere-Reinst (Estado,Err: mayúsc.=malo)
||/ Nombre         Versión      Arquitectura Descripción
+++-==============-============-============-=================================
un  baloo          <ninguna>    <ninguna>    (no hay ninguna descripción dispo
veronica@veronica-MS-7A15:~$ apt policy baloo
baloo:
  Instalados: (ninguno)
  Candidato:  4:5.44.0-0ubuntu1
  Tabla de versión:
     4:5.44.0-0ubuntu1 500
        500 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) bionic/universe amd64 Packages
        500 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) bionic/universe i386 Packages

Thanks and what have I to do now?

---

### Post by Bashing-om on 2019-06-21
Vero1; yuk -

seems I may have mislead you - the package names in ubuntu are baloo-kf5 and/or baloo4.

What shows for terminal command:
```

balooctl status

```

as we look for what baloo is all about prior to trying to remove,

[INDENT][INDENT]there is that means that seems right, but
[/INDENT][/INDENT]

---

### Post by Vero1 on 2019-06-22
The response is: (it is in Spanish, sorry)

veronica@veronica-MS-7A15:~$ balooctl status
El indexador de archivos de Baloo está en ejecución
Estado del indexador: Indexando contenido de archivos
Indexado 2533 / 2534 archivos
El tamaño actual del índice es 84,16 MiB
veronica@veronica-MS-7A15:~$ 

Hope this help :-)

Thanks.
p.s.
I'm keeping recieve the error mentioned before, to be send to Ubuntu.

---

### Post by Bashing-om on 2019-06-22
Vero1; Ouch !

I do not find a way to remove the baloo app !

As the indexer still has that last file to index, I highly doubt that one can disable baloo to keep it from running.

Best I can advise at this time is to follow through with the bug report, See then what the developers have to advise.

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by Vero1 on 2019-06-25
Hello Bushing-om:
Excuseme but I had some problems and couldn't answer you.
Don't worry, some day will be fixed my problem :-)
Thank you for your attempt to help me.

Kind regards,

Vero1

---

