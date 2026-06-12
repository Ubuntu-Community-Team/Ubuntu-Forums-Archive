---
title: "Ubuntu problem!"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by mbv93 on 2006-11-05
hey i've got this problem i installed ubuntu 6.10 edgy eft, i am very happy i installed the flash player plug-in for firefox correctly but i don-t know why every time i enter a website with some flash animation, game or banner firefox closes!! can you help me!! ](*,)

---

### Post by localuser on 2006-11-05
Were things working correctly before the flash plug-in installation?

If so, then how did you install the flash plug-in?

---

### Post by mbv93 on 2006-11-05
everything was working correctly the thing is that i needed the plug-in well i downloaded the plug-in to the desktop i extracted the files and executed the installer on the terminal

---

### Post by localuser on 2006-11-05
In Firefox, enter the following into the address bar and hit enter

about : plugins

You should see an entry for Shockwave Flash...what do you see *exactly* in that section?

---

### Post by mbv93 on 2006-11-05
Shockwave Flash
MIME Type 	                 Description 	      Suffixes Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
:-D

---

### Post by taurus on 2006-11-05
What version of flash does it say?

---

### Post by mbv93 on 2006-11-05
Shockwave Flash 7.0 r68

---

### Post by localuser on 2006-11-05
It doesn't look like you have a complete install...

I would recommend that you install Automatix and have it install the proper flash plug-in.  Automatix will also allow you to install many other things you'll probably need very soon.

To install Automatix go to...

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

then follow the directions at the section titled "Installing Automatix2 with Apt"

Once installed, you'll get a launcher icon for Automatix in Applications | System Tools

See if that helps.

---

### Post by mbv93 on 2006-11-05
i installed automatix but i don-t know if i am finished - Reading package lists... Done after this appears this mbv93@mbv93-desktop:~$ sudo apt-get install automatix2 

 and nothing happens am i finished?

---

### Post by djroadrash on 2006-11-05
hola amigo mbv93, porfavor pon todo lo que haz hecho pues tu reporte no dice nada de lo que hayas hecho, por lo poquito que pusiste parece que no hizo nada. claro que realmente no pusiste nada. si installaste automatix correctamente, te debe salir un icono de automatix en tus menus en la barra de la parte de arriba en aplications/system tools creo, pon todo el mensaje que te produce la console cuando instalaste automatix y la forma en que lo hiciste. usa el # en la toolbar de la respuesta en ubuntu forums y pon todo el code que sale en console  entre los dos #. asi es como se debe hacer. recuerda que tienes que introducir todos los repositorios antes de tratar de instalar automatix tambien pon que sistema usas, edgy o dapper o cual?. suerte.

---

### Post by taurus on 2006-11-05
> **djroadrash said:**
> hola amigo mbv93, porfavor pon todo lo que haz hecho pues tu reporte no dice nada de lo que hayas hecho, por lo poquito que pusiste parece que no hizo nada. claro que realmente no pusiste nada. si installaste automatix correctamente, te debe salir un icono de automatix en tus menus en la barra de la parte de arriba en aplications/system tools creo, pon todo el mensaje que te produce la console cuando instalaste automatix y la forma en que lo hiciste. usa el # en la toolbar de la respuesta en ubuntu forums y pon todo el code que sale en console  entre los dos #. asi es como se debe hacer. recuerda que tienes que introducir todos los repositorios antes de tratar de instalar automatix. suerte.
Can you please at least reply it in English so others can read it???

---

### Post by mbv93 on 2006-11-05
oie si te fijas en los perfiles en mi nombre alado dice ubuntu 6.10 edgy eft y al principio del tema tambn menciono que uso edgy eft ;) y por cierto segui todos los pasos para instalar automatix como lo dije al final me salio eso
(replying to the spanish guy)

---

### Post by localuser on 2006-11-05
> **mbv93 said:**
> i installed automatix but i don-t know if i am finished - Reading package lists... Done after this appears this mbv93@mbv93-desktop:~$ sudo apt-get install automatix2 

 and nothing happens am i finished?

Do you have an Automatix icon in Applications | System Tools?

---

### Post by taurus on 2006-11-05
> **mbv93 said:**
> oie si te fijas en los perfiles en mi nombre alado dice ubuntu 6.10 edgy eft y al principio del tema tambn menciono que uso edgy eft ;) y por cierto segui todos los pasos para instalar automatix como lo dije al final me salio eso
(replying to the spanish guy)
Okay, I don't really want to hand out any infraction so please post/reply in English since this is an English forum...

---

### Post by mbv93 on 2006-11-05
localuser clicking on applications i don't see system tools only accesories, games, graphics, internet, office, sound and video and add/remove

---

### Post by taurus on 2006-11-05
What about open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo automatix2
```

---

### Post by mbv93 on 2006-11-05
sudo: automatix2: command not found
:mad:

---

### Post by taurus on 2006-11-05
Did you really install automatix2 at all?  What does your /etc/apt/sources.list look like then?

```
more /etc/apt/sources.list
```

---

### Post by mbv93 on 2006-11-05
```
deb http://mx.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://mx.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
--more--(62%)

```

---

### Post by taurus on 2006-11-05
Hit the space bar for the next 24 lines...

---

### Post by mbv93 on 2006-11-05
i already found my problem thanks for the help i wrote the thing that i needed to write on the sources list on the terminal :D

---

