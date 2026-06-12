---
title: "Pidgin 2.0 Beta 7 (ex Gaim) deb"
date: 2007-05-02
forum: Argentina Team
---

### Post by QUASAR_FREAK on 2007-05-02
Les dejo el deb de Pidgin que encontré en el lado en ingles de Ubuntu, anda mucho mejor que la beta 6.

[Pidgin 2.0.0 Beta7]("http://rapidshare.com/files/28813389/pidgin_2.0.0beta7-1_i386.deb.html")

Mirrors:

[pidgin_2.0.0beta7-1_i386.deb]("http://www.theyateleyforums.com/pidgin_2.0.0beta7-1_i386.deb")
[pidgin_2.0.0beta7-1_i386.deb]("http://iramos.net/zoo/deb/pidgin_2.0.0beta7-1_i386.deb")

Screenshots:

[[IMG]http://img470.imageshack.us/img470/6885/0502072nd4.th.jpg[/IMG]]("http://x04d.com/pics/050207-3.jpg")

[[IMG]http://img454.imageshack.us/img454/7149/pidgingl1.th.jpg[/IMG]]("http://img454.imageshack.us/my.php?image=pidgingl1.jpg")

Thread original:
[http://ubuntuforums.org/showthread.php?t=429255&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=429255&highlight=pidgin)

---

### Post by valucha on 2007-05-03
[COLOR="DarkOrchid"]me salta este error.. tenés idea de qué hacer :S[/COLOR][IMG]http://img375.imageshack.us/img375/2825/problemagaimxo0.png[/IMG]

---

### Post by Al_maverick on 2007-05-03
Proba a poner en la consola:

```
sudo apt-get install libatk
```

Si te tira un error, posteá acá el mensaje completo.

Si anda bien, probá de vuelta el pidgin.

---

### Post by sdm_cacto on 2007-05-03
Che, Q no sabes donde puedo encontrar algun .deb q contanga los principales plugins para pidgin?? El q mas necesito es Guifications o algo que cumpla la funcion de mostrarme un cartelito cuando se conecta alguien.

salu2

muy buen aporte

valucha q fuente usas?? esta muy copada

salu3

---

### Post by valucha on 2007-05-03
[COLOR="DarkOrchid"]Fijate acá [http://www.pidgin.im/plugins.php](http://www.pidgin.im/plugins.php)[/COLOR]

---

### Post by valucha on 2007-05-03
> **Al_maverick said:**
> Proba a poner en la consola:

```
sudo apt-get install libatk
```

Si te tira un error, posteá acá el mensaje completo.

Si anda bien, probá de vuelta el pidgin.

[COLOR="DarkOrchid"]Ya lo había probado...
[/COLOR]
```
E: No se pudo encontrar el paquete libatk

```

---

### Post by Teamgeist on 2007-05-03
```
sudo apt-get install libatk1.0-0
```

Greetings from Germany!

---

### Post by valucha on 2007-05-03
```
libatk1.0-0 ya está en su versión más reciente.

```
[COLOR="DarkOrchid"]y sigue sin funcionar.[/COLOR]:(

---

### Post by marianom on 2007-05-03
¡¡¡Ahora yo, ahora yo!!! 

```
sudo apt-get install libatk1.0-dev
```

Y si ese no anda, mete todo lo que encuentres [aca]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libatk&searchon=names&subword=1&version=feisty&release=all").

---

### Post by valucha on 2007-05-03
[COLOR="DarkOrchid"]And the winner issssssssss....



nadie, pero tenía muchas ganas de decirlo...

Sigue sin funcionar.. ¿Qué me dice?, lo mismo que puse en la imágen, ¿Qué instalé? absolutamente todo lo que me dijeron... ¿Qué uso? Ubuntu Edgy... ¿Qué podría hacer? Dejarme de ***** y seguir con el beta 6 :)...

No se preocupen muchachos, cuando será será.[/COLOR]

---

### Post by marianom on 2007-05-03
Que mal, estaba seguro que ganaba. Esperemos que aparezca Quasar y que te dé todas las dependencias que tiene.

---

### Post by valucha on 2007-05-03
[QUOTE=alguien en el foro en inglés]This DEB-package is for feisty only.[/QUOTE]
[COLOR="DarkOrchid"]That's why[/COLOR]

---

### Post by DuckMan on 2007-05-03
jajaja :P me mato el germano entrando

bueno, solo para feisty :O o actualizas y resolves tus problemas contractuales o usaras gaim (?)

---

### Post by Al_maverick on 2007-05-03
Fijate, quizas hay un .deb para edgy

---

### Post by matog on 2007-05-03
Algo para AMD64?

---

### Post by Al_maverick on 2007-05-04
Ya salio la version 2.0 final. Por lo que vi, solo esta el source. Todavia no hay paquetes especificos para las distros.

[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234")

---

### Post by sdm_cacto on 2007-05-04
> **Al_maverick said:**
> Ya salio la version 2.0 final. Por lo que vi, solo esta el source. Todavia no hay paquetes especificos para las distros.

[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234")

Me estoy bajando la version de windows (sacrilegio!!) para ver si tiene nuevas features, en un rato comento

......

Bueno, ya lo probe en windows y lo veo igual q antes.. habra q buscar un changelog pero la pagina esta caida

---

### Post by marianom on 2007-05-04
Ya lo compilé e instalé y por ahora veo solo cambio de iconos. Pero se ve bien....
En caso que a alguien le de ganas, así lo instalé:

Pasos obligatorios:

0- Descarguen la versión tar.gz de sourceforge.
1- Backup de directorio .gaim actual:
	```
mkir bk_gaim
cp .gaim bk_gaim
```
2- Descomprimir:  
```
tar -xvzf pidgin-2.0.0.tar.gz
```

Desde el código

1- Configurar:
```
cd pidgin-2.0.0
./configure
```
2- Making code 'n coffe
	```
sudo make
```
	vayan a disfrutar un rico cafe y a ver "Los Padrinos Mágicos"
3- Opcional: Desinstalar versión actual de gaim con método preferido.
Reinstalar de ser necesario paquetes nautilus-sendto y ubuntu-desktop.
4- Instalar nueva versión
```
sudo make install
```

Con Checkinstall

1- Configurar:
```
cd pidgin-2.0.0
auto-apt run ./configure

```
2- Making code 'n coffe
```
sudo make
```
	vayan a disfrutar un rico cafe y a ver "Los Padrinos Mágicos"
3- Instalar nueva versión
```
sudo checkinstall
```

Ahora tendrán la versión instalada y un paquete .deb en el directorio. La información del sistema estará también correctamente actualizada con la versión de pidgin.

---

### Post by sdm_cacto on 2007-05-05
[Aca]("http://download.ubuntu.pl/_Feisty_Fawn/pidgin/old/") les dejo los debs de la version final de Pidgin 2.0 y tambien sus Plugins

---

### Post by spg76 on 2007-05-05
> **sdm_cacto said:**
> [Aca]("http://download.ubuntu.pl/_Feisty_Fawn/pidgin/old/") les dejo los debs de la version final de Pidgin 2.0 y tambien sus Plugins

Gracias sdm_cacto, pero me parece que el link que querías poner era [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/)

---

### Post by tr4nce on 2007-05-06
Al parecer aparte de los íconos Tango incluye el Custom Message del status de los miembros de tu lista. Alguien confirma si también para MSN? Por que tenía entendido que esa función en el gai* (:P) era para el Jabber.

---

### Post by matog on 2007-05-08
Bastante feo...me quedo con el último Gaim, al menos en interfaz...

---

### Post by QUASAR_FREAK on 2007-05-08
copiale los iconos viejos de gaim ensima y listo, no kambio mas ke eso la interfaz. =P

---

