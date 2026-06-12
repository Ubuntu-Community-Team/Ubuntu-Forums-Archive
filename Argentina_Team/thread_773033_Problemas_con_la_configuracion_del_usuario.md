---
title: "Problemas con la configuracion del usuario"
date: 2008-04-28
forum: Argentina Team
---

### Post by santisantermer on 2008-04-28
Hola, creo que meti la pata. Creo que modifiqué los permisos en mi carpeta de usuario y al ingresar a mi sesión no aparece personalizada.
Me tira un cartel que dice que no se esta tomando el archivo $home/.dmrc
y que debería funcional con el Permiso 644.
Tambien me aparece un cartel preguntandome que estaba haciendo cuando se me colgo y me solicita una direcciòn de e-mail. Me respondieron con este texto:

 deskbar-applet | general | Ver: unspecified
          Summary: crash in Deskbar: Estaba tratando de corre...
          Product: deskbar-applet
          Version: unspecified
         Platform: All
       OS/Version: All
           Status: UNCONFIRMED
         Severity: critical
         Priority: High
        Component: general
       AssignedTo: [email]deskbar-applet-maint@gnome.bugs[/email]
       ReportedBy: [email]santisantermer@gmail.com[/email]
        QAContact: [email]deskbar-applet-maint@gnome.bugs[/email]
    GNOME version: 2.21/2.22
  GNOME milestone: Unspecified


What were you doing when the application crashed?
Estaba tratando de corregir un error en los permisos. Me aparece un error que
no se estan tomando los permisos 644. No se esta tomando en cuenta el archivo
$home/.dmrc


Distribution: Ubuntu 8.04 (hardy)
Gnome Release: 2.22.1 2008-04-15 (Ubuntu)
BugBuddy Version: 2.22.0

System: Linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10400090
Selinux: No
Accessibility: Disabled
GTK+ Theme: OSX-theme
Icon Theme: OSX

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout:
0 it_real_value: 0 frequency: 0



----------- .xsession-errors ---------------------
 File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line
165, in draw_on_square
   self.draw_complete_thumb(context, side, thumbheight, 0, 0, n, True, True)
 File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line
100, in draw_complete_thumb
   self.draw_retangle_with_background_over(context, w, h, x, y,n, squared)
 File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line
111, in draw_retangle_with_background_over
   pixbuf = self.get_pixbuf_background(w, h,squared)
 File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line
232, in get_pixbuf_background
   self.bgpixbuf_for_squared = gtk.gdk.pixbuf_new_from_file(url2)
gobject.GError: No se ha podido abrir el archivo
«/media/disk/Imágenes/Bolivia 2008/IMG_0708.JPG»: No existe el fichero ó
directorio
ERROR: execution of prepared query SetOption failed due to unable to open
database file with return code 14
** (trackerd:6133): WARNING **: could not open
/home/santiago/.local/share/tracker/tracker.log
ERROR: execution of prepared query InsertServiceType failed due to unable to
open database file with return code 14
** (trackerd:6133): WARNING **: could not open
/home/santiago/.local/share/tracker/tracker.log
--------------------------------------------------
Traceback (most recent call last):
 File "/usr/lib/deskbar-applet/deskbar-applet", line 30, in applet_factory
   tray = DeskbarTray(applet)
 File "/usr/lib/python2.5/site-packages/deskbar/ui/DeskbarTray.py", line 47,
in __init__
   self.__setup_mvc()
 File "/usr/lib/python2.5/site-packages/deskbar/ui/DeskbarTray.py", line 88,
in __setup_mvc
   self.__core.run()
 File "/usr/lib/python2.5/site-packages/deskbar/core/CoreImpl.py", line 54, in
run
   self._setup_keybinder()
 File "/usr/lib/python2.5/site-packages/deskbar/core/CoreImpl.py", line 75, in
_setup_keybinder
   self.set_keybinding( self.get_keybinding() )
 File "/usr/lib/python2.5/site-packages/deskbar/core/CoreImpl.py", line 167,
in set_keybinding
   self._gconf.set_keybinding(binding)
 File "/usr/lib/python2.5/site-packages/deskbar/core/GconfStore.py", line 178,
in set_keybinding
   self._client.set_string(self.GCONF_KEYBINDING, binding)
GError: No se puede sobreescribir un valor de solo lectura: No se puede
sobreescribir un valor de solo lectura: El valor de
«/apps/deskbar/keybinding» es una fuente sólo de lectura en la parte
superior de su configuración


Alquien sabe como puedo solucionar esto? Desde ya les voy a agradecer cualquier ayuda que puedan darme.
Saludos,
Santiago.

---

### Post by margori on 2008-04-29
> **santisantermer said:**
> Creo que modifiqué los permisos en mi carpeta de usuario y al ingresar a mi sesión no aparece personalizada.
Me tira un cartel que dice que no se esta tomando el archivo $home/.dmrc
y que debería funcional con el Permiso 644.

A mi me pasó lo mismo. El problema básicamente radica en que cada usuario tiene su carpeta personal con exclusividad de escritura, es decir su grupo y todos los demás tienen a lo sumo acceso de lectura.

Yo lo arreglé simplemente cambiando los permisos en el cuadro de diálogo de propiedades de la carpeta personal. Por supuesto tu tienes que ser el propietario de esa carpeta.

Espero te sirva. Pueden haber algunos detalles que se me están escapando. Sería bueno que le dieras una mirada a la ayuda de los comandos chown y chmod, sobretodo para saber de permisos y seguridad.

---

