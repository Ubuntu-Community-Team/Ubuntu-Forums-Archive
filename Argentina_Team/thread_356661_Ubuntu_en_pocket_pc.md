---
title: "Ubuntu en pocket pc?"
date: 2007-02-08
forum: Argentina Team
---

### Post by Nemesis Teufel on 2007-02-08
Saben si hay alguna version de ubuntu para pocket pc? o alguna distro para no utilizar la cagada de windows ce?

---

### Post by DuckMan on 2007-02-08
justamente estaba explorando el tema, igual depende del modelo, yo tengo una DELL AXIM, y se puede instalar un linux en una memoria CF

[http://www.clanbv.org/public/axim.html](http://www.clanbv.org/public/axim.html)

es posible, pero no se si sirve

---

### Post by Nemesis Teufel on 2007-02-10
> **DuckMan said:**
> justamente estaba explorando el tema, igual depende del modelo, yo tengo una DELL AXIM, y se puede instalar un linux en una memoria CF

[http://www.clanbv.org/public/axim.html](http://www.clanbv.org/public/axim.html)

es posible, pero no se si sirve

Claroo, justito justito. Yo me quiero comprar una dell axim, creo que el modelo x51v.
Vos que modelos tenes?

---

### Post by Nemesis Teufel on 2007-02-11
Estoy decidido por la x51v, lo unico q no me convenceria seria la imposibilidad de tener linux, pero bue.. se ve q se hace. 
Ahi en la pagina q me pasaste dice: Dell Axim.. pero no especifica el modelo.. por lo que lei mas que el modelo tiene q ver con el micro y los kernels que son los q traen problemas. Se que para una v50 hay linux, pero es bastante menos potente.

---

### Post by MeduZa on 2007-02-11
yo estoy terminando de leerme los how-to y le voy a poner el linux a la ipaq 2215 que tengo :)

---

### Post by Nemesis Teufel on 2007-02-11
> **MeduZa said:**
> yo estoy terminando de leerme los how-to y le voy a poner el linux a la ipaq 2215 que tengo :)

mas detalles por favor.. que linux? pone algun link o algo plz.

---

### Post by Nemesis Teufel on 2007-02-11
Aca encontre alguna pagina con buena info: 
[http://www.seguridadwireless.net/foro/index.php/topic,920.0.html](http://www.seguridadwireless.net/foro/index.php/topic,920.0.html)

---

### Post by MeduZa on 2007-02-12
estoy siguendo [esta guia]("http://handhelds.org/moin/moin.cgi/HpIpaqH2200CardBoot") para ponerle el Familiar Linux 0.8.4 con el GPE pero tambien quiero probar el Opie (son como gnome y KDE a lo que una desktop) por ahora hice todo pero no me arranca, no se porque, estoy usando el HaRET controlado por el Wrap-haret por si las moscas.
Aun no me animo a ponerlo en la rom lo quiero probar primero y despues veo como lo pongo en rom

Por ahora no me arranca pero sigo probando

alguien me puede explicar que hace esta linea:
sed "s%/dev/mtdblock3%/dev/mmcblk0p2%;s/jffs2/ext2/" \
     /mnt/sdb2/etc/fstab > /tmp/fstab && cp /tmp/fstab /mnt/sdb2/etc/fstab 

en mi caso seria:

sudo sed "s%/dev/mtdblock3%/dev/mmcblk0p2%;s/jffs2/ext2/"      /media/usbdisk/etc/fstab > /tmp/fstab && cp /tmp/fstab /media/usbdisk/etc/fstab 

y me arroja este error:

cp: cannot create regular file `/media/usbdisk/etc/fstab': Permission denied

---

### Post by Nemesis Teufel on 2007-02-12
> **MeduZa said:**
> estoy siguendo esta guia para ponerle el Familiar Linux 0.8.4 con el GPE pero tambien quiero probar el Opie (son como gnome y KDE a lo que una desktop) por ahora hice todo pero no me arranca, no se porque, estoy usando el HaRET controlado por el Wrap-haret por si las moscas.
Aun no me animo a ponerlo en la rom lo quiero probar primero y despues veo como lo pongo en rom


1. Que modelo de ppc tenes? 
2. Lo estas instalando en la Compact Flash?

---

### Post by DuckMan on 2007-02-12
creo q hay ppc con linux de fabrica :O y parece q van como piña, yo me tiraria por eso..

la mia es viejita , axim v5 creo..

---

### Post by MeduZa on 2007-02-12
> **Nemesis Teufel said:**
> 1. Que modelo de ppc tenes? 
2. Lo estas instalando en la Compact Flash?

1. es una Ipaq 2215 que viene con windolin mobile 2003

2. puse el booteo en la ipaq rom file system y el systema en una SD

> **DuckMan said:**
> creo q hay ppc con linux de fabrica :O y parece q van como piña, yo me tiraria por eso..

la mia es viejita , axim v5 creo..

si hay varias que traen linux de fabrica, en esta lista:

[http://handhelds.org/moin/moin.cgi/SupportedHandheldSummary]("http://handhelds.org/moin/moin.cgi/SupportedHandheldSummary")

salen las que traen el linux de fabrica y soportan familiar

EDIT: [aca encontre mas info sobre distros]("http://69.56.212.74/ppc_articulos_ver.asp?id_articulo=83")

---

### Post by Nemesis Teufel on 2007-02-13
Aca mas info sobre ppc con Linux de fabrica:

[http://en.wikipedia.org/wiki/Sharp_Zaurus#Zaurus_models](http://en.wikipedia.org/wiki/Sharp_Zaurus#Zaurus_models)

Realmente son horribles, 0 practicas con ese teclado. Luego tienen algo bueno pero malo: tienen disco rigido. No quiero caminar con ese disco rigido girando mientras escucho mp3 o si lo enchufo en el auto, sufrir con cada bache.

---

### Post by MeduZa on 2007-02-13
bueno parece que anda =D> :biggrin: :-D

ahora a sacar el virus q tiene digo el windows CE y poner linux ;)

si todo anda bien veo como meterle ubuntu xD jajajajaj capas ande

---

### Post by Nemesis Teufel on 2007-02-14
> **MeduZa said:**
> bueno parece que anda =D> :biggrin: :-D

ahora a sacar el virus q tiene digo el windows CE y poner linux ;)

si todo anda bien veo como meterle ubuntu xD jajajajaj capas ande

QUIERO QUIERO! Pero antes necesito una ppc :(

---

### Post by BlackHero on 2007-02-17
felicidades =) muy bueno lo tuyo =)




en realidad tener ppc si esta bueno sirve demasiado para muchas cosas =) pero en caso tenia la opcion de comprarme otra laptop o una desert eagle adivinen como ya tenia una satellite me compre una desert :D .50 :D

---

