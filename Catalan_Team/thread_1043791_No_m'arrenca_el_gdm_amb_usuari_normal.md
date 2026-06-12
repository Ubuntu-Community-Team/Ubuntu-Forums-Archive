---
title: "No m'arrenca el gdm amb usuari normal"
date: 2009-01-18
forum: Catalan Team
---

### Post by tanreb20 on 2009-01-18
Bon vespre amics.

Avui despres de instalar i desinstalar i fer cose svaries (usplash, splashy, startupmanager...) he apagat la maquina i al tornar a ngegar m'ha saltat amb diferents errors.

el primer em deia que en el daemons/noseq no estava /var/lib/gdm peroq  aquet no existia, he aconseguit solventar aquest error modificant els permisos de /var/lib/gdm i posan a 777, almenys aixi entro fins al gdm.

Pero ara quan intento accedir en mode usuari normal em salta aquest error un tant extrany.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=ca_ES.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied
```

He mirat l'arxiu default pero no hi ha rés d'exrany:

```
#
# This configuration provides default IM setting (user edittable)
# See im-switch(8) and /usr/share/doc/im-switch/README.Debian .

#
# Define IM for traditional X application with XIM
#
#  XIM server name used for XMODIFIERS="@im=$XIM"
#  XIM program /path/filename
#  XIM program command line arguments
#
#  These were traditional setting before uim and scim for CJK languages
#  Language   LC_CTYPE     XIM server XMODIFIERS              Start key
#  Japanese   ja_JP*       kinput2    "@im=kinput2"           Shift-Space
#  Korean     ko_KR*       ami        "@im=Ami"               Shift-Space
#  Chinese(T) zh_TW.Big5   xcin       "@im=xcin-zh_TW.big5"   Ctrl-Space
#  Chinese(S) zh_CN.GB2312 xcin       "@im=xcin-zh_CN.GB2312" Ctrl-Space
# 
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
# Set following variable to non-zero string if program set itself as deamon
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
#
# Define GTK and QT IM module
#   They may or may not be using xim as the IM.
#
GTK_IM_MODULE=
QT_IM_MODULE=

#
# Define lists of packages neded for above IM to function
#
DEPENDS=

#
# Define X start up hook script to update IM environment
#

```

He intentat amb un dpkg-reconfigure gdm pero rés, u deixa tot com estava.

No se per on tirar, desde el root puc accedir pero amb l'usuari normal(alorma) no, alguna ajuda?

Faig servir linux mint 6 felicia, basat en ubuntu 8.10 intrepid ibex en un portatil toshiba a210

GRACIES

---

### Post by argggg on 2009-01-19
El que jo faria. 

-Crear un nou usuari i entrar amb aquest (si et funciona t'ho copies tot cap aquest)

-Recupera la copia de seguretat que tothom a de tenir (sobretot si "toques" coses). O reinstala de 9

Si no vols, no pots fer cap de les 2 coses i encara vols recuperar. 

Ens hauries de dir si vas fer servir els comandaments: chmod or chown i si es que si que es el que vas posar (potser ho pots trobar a mirant dins de /home/[usuari]/.bash_history) i si no han fet gaire mal podem intentar reconstruir els permisos.

Fes copia de seguretat abans de fer res.

Un enllaç cap a una posible solució:
[http://ubuntuforums.org/archive/index.php/t-942717.html](http://ubuntuforums.org/archive/index.php/t-942717.html)

---

### Post by tanreb20 on 2009-01-19
He mirat el bash_history peor no surten els chmod que vaig fer.

Basicament per arreglar lo del gdm i que pogue entrar coma a minim al gdm vaig fer:

```
sudo chmod 777(al final vai posar aquets) /var/lig/gdm
```

He intentst crear un altre usuari pero tamopoc funbciona, nomes puv entrar amb root

---

