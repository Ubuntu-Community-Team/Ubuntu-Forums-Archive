---
title: "Mal muntatge de iPod (instalar software a iPod?)"
date: 2009-08-20
forum: Catalan Team
---

### Post by LitusMayol on 2009-08-20
Bones familia!

Avui ma germana m'ha brindat l'oportunitat de jugar amb el seu iPod vell: tinc herència! És un iPod Nano de 4Gb de 2a generació. 

Però ara venen els problemes.

[LIST=1]
[*]**L'iPod  i l'Amarok** Amb l'Amarok em dona problemes. Quan l'intento conectar em diu que 

*Dispositiu de suports: no s'ha pogut trobat iTunesDB al dispositiu muntat a /media/IPOD ANNA____. Hauria de provar d'inicialitzar el vostre iPod?*

Clicko a "*inicialitzar*" i...

*Dispositiu de suports: No s'ha pogut inicialitzar l'iPod muntat a /media/IPOD ANNA____*

I prou. A més em monta a */media* fins a quatre dispositius "IPOD ANNA____". Només un conté les dades i tot plegat... I els altres perquè es monten?

Puc fer-hi alguna cosa?

[*]**Instal·lar software a l'iPod?** L'altra opció podria ser instal·lar-hi un software nou, a mi em sona haver llegit que hi havia algun software per iPod que era lliure... Però no sé ni on ho vaig llegir ni ho he trobat *googlejant*.
[/LIST]


Alguna idea? ;)
Merci!

---

### Post by LitusMayol on 2009-08-20
Per la opció d'instal·lar he trobat el sistema *iPodLinux*. Però no les tinc totes, segons la [Wiki]("http://es.wikipedia.org/wiki/IPodLinux"):
> "El proyecto soporta los reproductores de primera, segunda y tercera generación de iPod[...]"

Però per molt que intento adreçar-me a "http://www.ipodlinux.org/" no aconsegueixo conectar-hi (ni Firefox ni Chromium me la carreguen). Per acabar-ho d'adobar, la majoria de pàgines on he trobat tutorials ([exemple 1]("http://ipodlinuxinstl.sourceforge.net/download.php"), [exemple 2]("http://lineupblog.com/2007/03/21/como-instalar-linux-en-un-ipod/"))asseguren que NO SUPORTA més enllà de 1a i 2a generació.

Algú en sap res?

---

### Post by papapep on 2009-08-20
Eii...veig que no hem perdut les velles costums, eh???

[http://tinyurl.com/kqmxjs](http://tinyurl.com/kqmxjs) 

(segona ocurrència) :twisted:

---

### Post by lluisanunez on 2009-08-22
GTKpod. És als repos d'ubuntu i et fa la gestió de l'ipod, reconeix ipod nano 4ª generació.
Ipodlinux jo el vaig insta&#322;lar fa anys en un ipod clàssic, però a part de canviar la poma per un pingüí no vaig millorar res.

---

### Post by LitusMayol on 2009-08-24
> **papapep said:**
> Eii...veig que no hem perdut les velles costums, eh???

[http://tinyurl.com/kqmxjs](http://tinyurl.com/kqmxjs) 

(segona ocurrència) :twisted:

**Papapep**! Ja saps, les costums no es perden... tot i que aquest cop ja ho havia solucionat (en el segon post ja he trobat cosetes! :P)

> **lluisanunez said:**
> GTKpod. És als repos d'ubuntu i et fa la gestió de l'ipod, reconeix ipod nano 4ª generació.
Ipodlinux jo el vaig insta&#322;lar fa anys en un ipod clàssic, però a part de canviar la poma per un pingüí no vaig millorar res.
[B]
lluisanunez[/B]! Crec que no m'he explicat, el problema és que el software d'*Apple* no funciona correctament (però no el de l'ordinador, sinó el de l'iPod). Com vas instal·lar Ipodlinux? Vas tenir algun problema?

Jo anava a seguir [aquesta guia]("http://ipodlinux.sourceforge.net/installation.shtml#Linux"). Però en el pas de "*Partitioning*" ja tinc problemes...

En el pas *Locating*:
```
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI  SCSI revision: 00

```

Però en el *Partitioning*(em salto el *Backup*, perquè si l'iPod es fa malbé no suposa cap problema):

Segons aquesta guia "*scsi5*" equival a "*sdf*":
```
litus@mayolets:~$ fdisk /dev/sdf

No s'ha pogut obrir /dev/sdf
litus@mayolets:~$
```

Aleshores faig probo això, també sense èxit:
```
litus@mayolets:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/litus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=litus)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1004,utf8,umask=077,flush)
/dev/sdc2 on /media/IPOD ANNA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1004,utf8,umask=077,flush)
litus@mayolets:~$ fdisk /dev/sdc2

No s'ha pogut obrir /dev/sdc2
litus@mayolets:~$ 

```

Suggerències?

---

### Post by lluisanunez on 2009-08-24
Vaig fer servir la mateixa guia, sense problemes. 
Estàs segur que te'l munta a /dev i no a /media?
Si el software apple està fet malbé, potser et pot ajudar fer prèviament això:
[Restoring iPod to factory settings]("http://support.apple.com/kb/HT1339?viewlocale=en_US")

---

### Post by LitusMayol on 2009-08-24
> **lluisanunez said:**
> Vaig fer servir la mateixa guia, sense problemes. 
Estàs segur que te'l munta a /dev i no a /media?
Si el software apple està fet malbé, potser et pot ajudar fer prèviament això:
[Restoring iPod to factory settings]("http://support.apple.com/kb/HT1339?viewlocale=en_US")

¬¬ Brutal.

Simplement. Brutal. Resulta que com que no l'havia conectat a Windows ni a l'iTunes no havia pogut resoldre-ho... Tan bon punt com l'he conectat a l'ordinador de mun pare l'iTunes ha saltat dient-me que el software estava malmès i que si volia restaurar-lo. Un parell de clicks... i PAM! Solucionat...!!

Merci! 
(demà probaré el tema de IpodLinux, tu lluisanunez m'ho recomanes? o creus que és millor deixar el programari de sèrie?)

---

### Post by LitusMayol on 2009-08-26
Ei familia!

Porto un parell de dies intentant el tema de la instal·lació de *iPodLinux* i no hi ha manera...

Amb [aquesta guia]("http://ipodlinux.sourceforge.net/installation.shtml#Linux") no hi ha hagut manera. No hi va haver manera d'instal·lar el kernel. El terminal no em reconeixia "*make_fw*" com a ordre de re! Vaig decidir que buscava una altra cosa...

Aleshores vaig trobar [aquesta altra guia]("http://wlmtips.com/2008/04/25/linux-friday-how-to-install-ipodlinux-on-your-ipod/"), que parla d'uns instal·lador que té interfície gràfica. Després de descarregar l'instalador de [MegaDownload]("http://megadownload.net/download/mu/3ynuvar2/ipod-linux.rar") avui he porbat d'instal·lar-lo. I no hi ha manera. L'instal·lador no troba l'iPod. Com si no esitgués conectat (us adjunto una captura de la finestreta). El tema és que m'he assegurat de que cap aplicació estigués usant l'iPod, que l'iPod està conectat i per descomptat està en format Windows i no Mac.

Alguna idea? :S

Gràcies!

---

### Post by lluisanunez on 2009-08-27
> **LitusMayol said:**
> 
(demà probaré el tema de IpodLinux, tu lluisanunez m'ho recomanes? o creus que és millor deixar el programari de sèrie?)

Com et vaig dir, les úniques millores van ser el logo del Tux en comptes de la poma, un scroll de missatges en terminal molt guai a l'inici, la font dels menus (en la meva opinió més lletgeta) i algun joc. Això sí, [molava molt més amb el Tux]("http://www.flickr.com/photos/lluisanunez/25934361/")
L'autèntica millora és fer servir l'ipod amb linux i gtkpod i veure's lliure de les grapes de l'Itunes

---

