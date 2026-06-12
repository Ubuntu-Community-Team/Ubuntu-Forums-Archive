---
title: "Problemas amb oss_compat"
date: 2010-12-30
forum: Catalan Team
---

### Post by falsospam on 2010-12-30
Fa dies que quan actualitzo el sistema o instal·lo quelcom nou :

"oss-compat: el subprocés installed post-installation script retornà el codi d'eixida d'error 2 "
 
En principi pel demés cap problema vaig reportar el error...dies,dies,dies .. vaig remenar per internet a sant google ... dies, dies,dies ; ja ni m'hen recordava i avui instalo el tuxguitar i altre cop oss..... algú ha tingut el mateix problema i la sol·lucionat ?

---

### Post by wgarcia on 2011-01-01
Has provat de reinstal·lar oss-compat a veure si desapareix el problema? Una primera possibilitat és

sudo apt-get install -reinstall oss-compat

i si aquest no funcionés 

sudo apt-get remove --purge oss-compat 
sudo apt-get install oss-compat

---

### Post by falsospam on 2011-01-12
> **wgarcia said:**
> Has provat de reinstal·lar oss-compat a veure si desapareix el problema? Una primera possibilitat és

sudo apt-get install -reinstall oss-compat

i si aquest no funcionés 

sudo apt-get remove --purge oss-compat 
sudo apt-get install oss-compat

Si ja ho he probat d'altres vegades i el resultat es :
dpkg: s'ha produït un error en processar oss-compat (--purge):
 el subprocés installed pre-removal script retornà el codi d'eixida d'error 2
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en netejar:
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 oss-compat
E: Sub-process /usr/bin/dpkg returned an error code (1)
Tambè he probat de reinstalar el paquet i de eliminar-lo amb el Synaptic, però res de res no hi ha manera de fer-lo fora i de eliminar aquest error pel que se oss-compat es un paquet que proporciona compatibilitat del so amb "ALSA". A mi l'error no hem fa mès nosa que embrutar el terminal cada cop que instal·lo o actualitzo quelcom. Sembla ser que oss-compat es un paquet que esta per desapareixer el que no se es com s'ha instalat al meu OS

---

### Post by wgarcia on 2011-01-12
Unes instruccions que m'han servit a vegades per remoure paquets rebels són:

sudo dpkg --remove --force-remove-reinstreq oss-compat
sudo dpkg --purge --force-remove-reinstreq oss-compat

prova amb aquestes a veure si hi ha sort.

---

### Post by falsospam on 2011-01-13
Noi res de res hem sonaba de haber-ho fet altres cops, pero no pot amb ell:

dpkg: s'ha produït un error en netejar:
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 oss-compat

tant en el proces de purge com el de remove. No se per quins set sous no hi ha manera de desfer-se d'aquest paquet. Algú te alguna idea? potser que tingui dependencies d'altres paquets o es que en el seu dia no es va instalar correctament?

---

### Post by wgarcia on 2011-01-14
Les instruccions per a la instal·lació del paquet es guarden a la carpeta:

/var/lib/dpkg/info/

Què surt si fas:

ls /var/lib/dpkg/info/oss*

?

---

### Post by falsospam on 2011-01-20
Perdona el temps que fa però la feina ....

Hem surt:

/var/lib/dpkg/info/oss-compat.list     /var/lib/dpkg/info/oss-compat.postinst
/var/lib/dpkg/info/oss-compat.md5sums  /var/lib/dpkg/info/oss-compat.prerm

ara no se perque ho vols aixo?

---

### Post by falsospam on 2011-01-20
Perdona el temps que fa però la feina ....

Hem surt:

/var/lib/dpkg/info/oss-compat.list     /var/lib/dpkg/info/oss-compat.postinst
/var/lib/dpkg/info/oss-compat.md5sums  /var/lib/dpkg/info/oss-compat.prerm

cat .postinst és buit
cat .md5sums es buit 
cat .prerm es buit

cat .list :
/.
/etc
/etc/modprobe.d
/lib
/lib/oss-compat
/lib/oss-compat/linux
/usr
/usr/share
/usr/share/doc
/usr/share/doc/oss-compat
/usr/share/doc/oss-compat/copyright
/usr/share/doc/oss-compat/changelog.gz

---

### Post by wgarcia on 2011-01-21
Prova de desinstal·lar oss-compat i veure si aquests dos fitxers oss-compat.postinst i oss-compat.prerm, encara hi són. Si és el cas remou-los i mira si ara les actualitzacions no donen error. 

De totes maneres després reinstal·la l'oss-compat perquè em sembla que és necessari per molts paquets que encara no han estat actualitzats per funcionar bé amb el sistema de so pulseaudio.

---

### Post by falsospam on 2011-01-22
El problema es que no puc desinstalar-lo ara he probat de eliminar els fitxers oss-* amb sudo nautilus ..

instalo Apaga els llums desde el centre de progarmari i ....

tot ok!!!!

Sembla que [Solved]

Actualitzo i ....
tot ok !!!

En resum :
El error oss-compat nº2 quan no es pot des-instalar, borrar directament del la carpeta
var/lib/dpkg/oss-c*

Pero ara no tinc so!!

---

### Post by falsospam on 2011-01-22
En reinicia he recuperat el so!

i corretjeixo la sol·luciò es borrar
/var/lib/dpkg/info/oss-*

en actualitzar i reiniciar tot torna a funcionar!

---

