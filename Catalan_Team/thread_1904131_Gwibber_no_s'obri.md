---
title: "Gwibber no s'obri"
date: 2012-01-04
forum: Catalan Team
---

### Post by Joan A. on 2012-01-04
Bon dia!

No sé què passa però avui he volgut obrir Gwibber per llegir el meu Twitter i no hi ha manera. També ho he intentat des de la terminal i m'ha donat el següent error:

> ** (gwibber:2221): CRITICAL **: file service.c: line 2679: unexpected error: Error al llamar StartSereviceByName para com.Gwibber.Service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (gwibber:2221): CRITICAL **: file messages.c: line 361: unexpected error: Error al llamar StartSereviceByName para com.Gwibber.Messages: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

** (gwibber:2221): CRITICAL **: file service.c: line 2679: unexpected error: Error al llamar StartSereviceByName para com.Gwibber.Service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (gwibber:2221): CRITICAL **: file messages.c: line 361: unexpected error: Error al llamar StartSereviceByName para com.Gwibber.Messages: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

** (gwibber:2221): CRITICAL **: file connection.c: line 414: unexpected error: Error al llamar StartSereviceByName para com.Gwibber.Connection: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2221): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2221): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (gwibber:2221): CRITICAL **: file urlshorten.c: line 346: unexpected error: Error al llamar StartSereviceByName para com.Gwibber.URLShorten: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)
Violación de segmentoEsper que qualqú pugui ajudar-me. Moltes gràcies per avançat i salut! ;)

---

### Post by Joan A. on 2012-01-11
Pareix que el problema era d'una actualizació. En un parell d'hores va arribar una altra actualització i el problema es va solucionar.

Gràcies!

---

