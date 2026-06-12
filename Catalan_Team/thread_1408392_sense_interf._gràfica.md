---
title: "sense interf. gràfica"
date: 2010-02-16
forum: Catalan Team
---

### Post by Razlo on 2010-02-16
Bé, després de buscar solucions pel meu compte i per fòrums de casa i de fora he decidit demanar-vos ajuda.

Info prèvia:
Vaig amb el karmic koala des de fa una setmana, i tinc una partició x l'xp, una x a root, i l'altra per a /home. (en un portàtil)

Resulta que amb una sessió oberta vaig notar que no se m'obrien noves finestres, i que tampoc no podia sortir de la sessió pel botó de la barra. No recordo més símptomes perquè de seguida vaig decidir apagar pel botó del portàtil.

Un cop al grub, trio carregar l'ubuntu, i després del logo blanc passa una pantalla escrita impossible de llegir, ni una lletra, i em passa a una sessió en terminal (tty1).

He provat de fer startx, però té un problema en fer-ho i fent ctrl+f7 només hi ha el cursor "_" fent pampallugues sense cap mena de text. Si carrego ubuntu sense fer startx no passa res en pitjar ctrl+f7.

També he provat el típic:
```
dpkg-reconfigure xserver-xorg
```
i això també:
```
gnome-settings-daemon --no-daemon --debug
```
perquè en un full d'error que he trobat semblava haver-hi problemes carregant algun dimoni del gnome.

Abans de tenir el problema acabava d'instal·lar uns paquets per fer servir el uim per escriure en japonès, els quals van fer la seva feina, i estava buscant la manera de fer un debug correcte amb l'anjuta, instal·lant el paquet gdb i altres relacionats. He provat desinstal·lant el gdb (s'han desinstal·lat dos paquets més amb ell) però no venia d'aquí el problema.

També vaig instal·lar la glib des d'un ftp, fent make i tot això... pot ser que em causés problemes?

Gràcies a tots!

PD: mentre espero resposta aniré tirant amb l'XP, però si no, tinc pensat de reinstal·lar root. Amb això no perdria les dades del /home oi? tenint en compte que els tinc en dues particions.

EDIT:
fitxer d'error: /home/ferran/.xsession-errors
escurço una mica el text perquè no he sabut posar-lo en spoiler.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.

(gnome-settings-daemon:1850): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1850): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
GNOME_KEYRING_SOCKET=/tmp/keyring-CcKZl7/socket
SSH_AUTH_SOCK=/tmp/keyring-CcKZl7/socket.ssh
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
[correctes]
Checking for Software Rasterizer: Not present. 
[...]
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator

(nautilus:1942): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** Message: adding killswitch idx 0 state 1
** Message: adding killswitch idx 2 state 1
** Message: Reading of RFKILL events failed
** Message: killswitch 0 is 1
** Message: killswitch 2 is 1
** Message: killswitches state 1

(polkit-gnome-authentication-agent-1:1948): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1948): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: killswitch 0 is 1
** Message: killswitch 2 is 1
** Message: killswitches state 1
** (gnome-panel:1938): DEBUG: Adding applet 0.
** (gnome-panel:1938): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1938): DEBUG: Adding applet 1. [també 2]
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (gnome-panel:1938): DEBUG: Adding applet 3. [també 4]

** (nautilus:1942): WARNING **: No marshaller for signature of signal 'UploadFinished'

[altre cop amb 'DownloadFinished' i amb 'ShareCreateError']

Initializing nautilus-gdu extension
** (gnome-panel:1938): DEBUG: Adding applet 5.[també 6]
I/O warning : failed to load external entity "/home/ferran/.compiz/session/109ee7df22c692e6ab126624333233160900000017780022"

(gnome-panel:1938): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
** (gnome-panel:1938): DEBUG: Adding applet 7. [també 8 i 9]
** (nm-applet:1954): DEBUG: foo_client_state_changed_cb
** (gnome-panel:1938): DEBUG: Adding applet 10. [també 11,12 i 13]
** (nm-applet:1954): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 31435 1266274800 1266243365
evolution-alarm-notify-Message:  Tue Feb 16 00:00:00 2010

evolution-alarm-notify-Message:  Mon Feb 15 15:16:05 2010


(firefox:2180): GLib-WARNING **: g_set_prgname() called multiple times

(anjuta:2176): Gdk-WARNING **: losing last reference to undestroyed window

[24 missatges més amb problemes de l'anjuta]

(anjuta:2176): GLib-GObject-WARNING **: invalid uninstantiatable type `area_updated' in cast to `SymbolDBViewLocals'

(anjuta:2176): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `SymbolDBView'
anjuta: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
/usr/lib/gnome-screensaver/gnome-screensaver-gl-helper: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime

anjuta: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
[dos cops més]

Traceback (most recent call last):
  File "/usr/bin/software-center", line 27, in <module>
    import gobject
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gobject/__init__.py", line 26, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/usr/lib/pymodules/python2.6/gtk-2.0/glib/__init__.py", line 22, in <module>
    from glib._glib import *
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/glib/_glib.so: 

undefined symbol: g_assertion_message
nautilus: symbol lookup error: /usr/lib/libgio-2.0.so.0:
[dos cops més]

** (gnome-panel:1938): DEBUG: Removing applet 13.

[...removent applets del 13 al 3]

** (gnome-panel:1938): DEBUG: Removing applet 3.

(gnome-panel:1938): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

[...tot failed]

(nautilus:1942): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

--- Hash table keys for warning below:
--> ferran
--> inode/directory
--> Nom Complet Complet
--> l2054

(nautilus:1942): Eel-WARNING **: "unique eel_ref_str" hash table still has 4 elements at quit time (keys above)

(nautilus:1942): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
/usr/bin/gconftool-2: symbol lookup error: /usr/bin/gconftool-2: undefined symbol: g_option_context_set_translation_domain
gnome-session[1778]: WARNING: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '32512'
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
:0.0: X IO error.
uim <-> XIM bridge. Supporting multiple locales.
Using full-synchronous XIM event flow
Supported conversion engines:
  direct (*)
  anthy (ja)
XMODIFIERS=@im=uim registered, selecting direct (*) as default conversion engine
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

[...Fatal errors]

temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 26031 requests (26030 known processed) with 1 events remaining.
Xsession: X session started for ferran at dl feb 15 17:21:16 CET 2010
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.
E: main.c: S'ha produÃ¯t un error en iniciar el dimoni.
x-session-manager: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for ferran at dl feb 15 17:22:54 CET 2010
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.
E: main.c: S'ha produÃ¯t un error en iniciar el dimoni.
x-session-manager: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for ferran at dl feb 15 17:25:40 CET 2010
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.
E: main.c: S'ha produÃ¯t un error en iniciar el dimoni.
x-session-manager: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for ferran at dl feb 15 17:37:30 CET 2010
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.
E: main.c: S'ha produÃ¯t un error en iniciar el dimoni.
x-session-manager: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for ferran at dl feb 15 17:38:45 CET 2010
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.
E: main.c: S'ha produÃ¯t un error en iniciar el dimoni.
x-session-manager: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for ferran at dt feb 16 15:43:10 CET 2010
Setting IM through im-switch for locale=ca_ES.
Start IM through /home/ferran/.xinput.d/ca_ES linked to /etc/X11/xinit/xinput.d/uim-toolbar.
E: main.c: S'ha produÃ¯t un error en iniciar el dimoni.
x-session-manager: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
```

Perdoneu la parrafada :/

---

### Post by SiscoGarcia on 2010-02-17
> **Razlo said:**
> [...] tinc pensat de reinstal·lar root. Amb això no perdria les dades del /home oi? tenint en compte que els tinc en dues particions.

Ja has provat de recuperar les dades amb un CD autònom? No en fas cap esment, per això t'ho pregunto.

---

### Post by Razlo on 2010-02-17
Bé, tinc ple accés a les dades des del live cd, així que pels documents personals no pateixo.

Fa molt poc que havia "decorat" el gnome al meu gust (temes, pantalla d'inici, dreceres) i justament és el gnome que peta. M'agradaria recuperar tot el que fos possible evitant el que m'hagi fet petar, és clar.

Avui tornaré a mirar si esbrino què coi dec haver tocat, però és que no he aconseguit treure cap pista significativa ni de la xarxa ni d'aquí :S

Gràcies per respondre :)

---

### Post by Razlo on 2010-02-24
Al final he acabat reinstal·lant, de fet, ja fa dies que ho vaig fer. Tot i això, fa poc vaig trobar una possible solució mig de casualitat. Es tracta de baixar la versió de la libglib2.0-0 de 2.22.3 a 2.22.2

Els passos per fer-ho són:
· anar al synaptic i buscar libglib
· seleccionar libglib2.0-0 i, a la pestanya de paquet, força versió... i li poseu la versió anterior
· fer el mateix amb libglib2.0-data

És possible que algú tingui un problema amb la mateixa causa però efectes diferents, per això penjo la solució a través del synaptic. Per fer-ho a través de la terminal no deu ser gens difícil, però jo no ho sé fer :P

El motiu d'això, vaig llegir, és que la versió més nova de la libglib () és inestable, i tot i que corregeix errors de l'anterior, també pot portar problemes, com ha estat el meu cas.

Potser això no ho soluciona, però si algú te aquest problema potser l'ajuda.

Salut companys!

---

