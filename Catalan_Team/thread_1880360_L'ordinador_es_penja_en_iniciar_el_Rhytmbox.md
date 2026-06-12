---
title: "L'ordinador es penja en iniciar el Rhytmbox"
date: 2011-11-13
forum: Catalan Team
---

### Post by lo gambusí on 2011-11-13
Hola,

Sóc un melòman, i d'unes setmanes ençà la cosa ha empitjorat i lo número d'arxius mp3 del meu disc dur s'ha disparat considerablement gràcies al prèstec de discs durs portàtils que m'han fet companys. Parlem de 70GB de música, unes 40000 cançons.

Això ha coincidit amb l'actualització a la darrera versió d'Ubuntu.

La qüestió és que, no sé si pel número d'arxius que ha de llegir, o si per l'actualització, cada vegada que intento iniciar el Rhytmbox se'm queda "fregit" i no hi ha manera de  fer-lo anar: es bloqueja l'ordinador i directament l'he de reiniciar. 

Això és quelcom que no em passava des d'aquells foscos anys en què feia servir Windows, i fa molt poca gràcia. La cosa empitjora si tenim en compte que faig servir el mateix Rhytmbox per posar música al meu reproductor portàtil i per tant m'és impossible escoltar la nova música fora de l'ordinador.

Suposo que hi deu haver alguna manera de reduïr els processos que fa servir lo meu portàtil i "relaxar-lo" o alguna cosa així, però no tinc ni idea de com fer-ho. O potser hauria de canviar de reproductor? O de versió d'Ubuntu i tornar-me'n a l'anterior? No m'importaria gaire, perquè personalment no m'agraden gens les darreres versions. Això de l'Unity no m'acaba de convèncer.

Resumint: em podríeu aconsellar i donar un copet de mà? :P

No sabria dir-vos el meu model de portàtil, fa un parell d'anys que el tinc. Suposo que es pot comprovar d'alguna manera, no?

Gràcies per tot! :)

---

### Post by wgarcia on 2011-11-14
El penjament pot ser per problemes gràfics o per carregar tant el sistema que deixa de respondre. Quan dius que es bloqueja l'ordinador, queda tot congelat o encara pots moure el ratolí però clicant arreu no respon res?

Algunes estratègies per diagnosticar el problema:

1) si tens extensions al Rythmbox, deshabilitar-les totes i anar-les habilitant una per una a veure si alguna causa el penjament.

2) entrar amb la sessió "Unity 2D" i veure si es continua penjant, això donaria indicació que és un problema gràfic.

3) Quan està penjat entrar "CONTROL ALT F1", això et donarà accés a una consola si el que està congelat és l'entorn gràfic, entres l'usuari i la clau, i un cop a la consola entres "w" i intro. A la primera línia surt una cosa com:

```
 06:54:52 up 21:56,  0 users,  load average: 0.03, 0.12, 0.18
```

que mostra la càrrega del sistema, a veure si és un problema de massa càrrega.

4) inicia el rythmbox des d'una terminal, obrint una terminal i entrant "rythmbox", a veure si surten missatges que donin informació sobre el penjament

---

### Post by lo gambusí on 2011-11-14
No, quan dic que es qeuda penjat és que es queda totalment penjat: no puc ni moure el ratolí.

De moment he deshabilitat els connectors, com dius, a veure com em reacciona.

A banda he intentat obrir-ho amb la consola i no puc fer-ho (?!)

> oriol@oriol-laptop:~$ rhytmbox
No s'ha trobat cap ordre anomenada «rhytmbox». Potser volíeu dir:
 Ordre «rhythmbox» del paquet «rhythmbox» (main)
rhytmbox: no s'ha trobat l'ordre


---

### Post by wgarcia on 2011-11-15
El tema de la consola és que has entrat "rhytmbox" en comptes de "rythmbox", et falta una "h".

---

### Post by lo gambusí on 2011-11-24
Hòstia, "es de ser inútiles". Perdó.

Mira, ho he provat i m'ha passat exactament això. I la consola em diu:

> oriol@oriol-laptop:~$ rhythmbox

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:2820): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed
*** glibc detected *** rhythmbox: free(): invalid pointer: 0x00007fd60ebad200 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7fd60e88ba96]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7fd60e88fd7c]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_strfreev+0x29)[0x7fd60ee32f69]
/usr/lib/librhythmbox-core.so.4(+0x9d946)[0x7fd6106d0946]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7fd60f2d90a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x2102a)[0x7fd60f2eb02a]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x851)[0x7fd60f2f46b1]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7fd60f2f4852]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x9bfb1)[0x7fd60fac1fb1]
/usr/lib/x86_64-linux-gnu/libffi.so.6(ffi_call_unix64+0x4c)[0x7fd607559a14]
/usr/lib/x86_64-linux-gnu/libffi.so.6(ffi_call+0x1e5)[0x7fd607559435]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_generic+0x197)[0x7fd60f2d9567]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7fd60f2d90a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x20e5f)[0x7fd60f2eae5f]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x623)[0x7fd60f2f4483]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7fd60f2f4852]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x9c2ce)[0x7fd60fac22ce]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x98fba)[0x7fd60fabefba]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_invoke_full+0x55)[0x7fd60ee15f85]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x990cc)[0x7fd60fabf0cc]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(g_settings_backend_changed+0xa1)[0x7fd60fabf5f1]
/usr/lib/gio/modules/libdconfsettings.so(+0x57bb)[0x7fd5fc2357bb]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x9cbd9)[0x7fd60fac2bd9]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x9cd49)[0x7fd60fac2d49]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7fd60f2d90a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x2102a)[0x7fd60f2eb02a]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x851)[0x7fd60f2f46b1]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7fd60f2f4852]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x11fc7)[0x7fd60f2dbfc7]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_notify+0x500)[0x7fd60f2de000]
/usr/lib/libgtk-3.so.0(+0x22a223)[0x7fd61020e223]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7fd60f2d90a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x2081a)[0x7fd60f2ea81a]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x851)[0x7fd60f2f46b1]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7fd60f2f4852]
/usr/lib/libgtk-3.so.0(+0x229b9d)[0x7fd61020db9d]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7fd60f2d90a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x2081a)[0x7fd60f2ea81a]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x851)[0x7fd60f2f46b1]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7fd60f2f4852]
/usr/lib/libgtk-3.so.0(+0x9545d)[0x7fd61007945d]
/usr/lib/libgtk-3.so.0(+0x152e58)[0x7fd610136e58]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7fd60f2d90a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x20e5f)[0x7fd60f2eae5f]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x623)[0x7fd60f2f4483]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7fd60f2f4852]
/usr/lib/libgtk-3.so.0(+0x280f39)[0x7fd610264f39]
/usr/lib/libgtk-3.so.0(gtk_propagate_event+0xca)[0x7fd61013663a]
/usr/lib/libgtk-3.so.0(gtk_main_do_event+0x32b)[0x7fd610136a3b]
/usr/lib/libgdk-3.so.0(+0x47102)[0x7fd60fdaf102]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x1dd)[0x7fd60ee13a5d]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x45258)[0x7fd60ee14258]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_loop_run+0x162)[0x7fd60ee14792]
/usr/lib/libgtk-3.so.0(gtk_main+0x8d)[0x7fd610135e1d]
rhythmbox(main+0x3a6)[0x4028c6]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7fd60e83430d]
rhythmbox[0x402c29]
======= Memory map: ========
00400000-00405000 r-xp 00000000 08:01 11273730                           /usr/bin/rhythmbox
00604000-00605000 r--p 00004000 08:01 11273730                           /usr/bin/rhythmbox
00605000-00606000 rw-p 00005000 08:01 11273730                           /usr/bin/rhythmbox
00d9a000-04653000 rw-p 00000000 00:00 0                                  [heap]
7fd5dade8000-7fd5dade9000 ---p 00000000 00:00 0 
7fd5dade9000-7fd5db5e9000 rw-p 00000000 00:00 0 
7fd5db5e9000-7fd5db5ea000 ---p 00000000 00:00 0 
7fd5db5ea000-7fd5dbdea000 rw-p 00000000 00:00 0 
7fd5dbdea000-7fd5dbdeb000 ---p 00000000 00:00 0 
7fd5dbdeb000-7fd5dc5eb000 rw-p 00000000 00:00 0 
7fd5dc5eb000-7fd5dc5ee000 r-xp 00000000 08:01 11287795                   /usr/lib/x86_64-linux-gnu/gconv/UTF-16.so
7fd5dc5ee000-7fd5dc7ed000 ---p 00003000 08:01 11287795                   /usr/lib/x86_64-linux-gnu/gconv/UTF-16.so
7fd5dc7ed000-7fd5dc7ee000 r--p 00002000 08:01 11287795                   /usr/lib/x86_64-linux-gnu/gconv/UTF-16.so
7fd5dc7ee000-7fd5dc7ef000 rw-p 00003000 08:01 11287795                   /usr/lib/x86_64-linux-gnu/gconv/UTF-16.so
7fd5dc7ef000-7fd5dc803000 r-xp 00000000 08:01 11279712                   /usr/lib/gstreamer-0.10/libgstflac.so
7fd5dc803000-7fd5dca02000 ---p 00014000 08:01 11279712                   /usr/lib/gstreamer-0.10/libgstflac.so
7fd5dca02000-7fd5dca03000 r--p 00013000 08:01 11279712                   /usr/lib/gstreamer-0.10/libgstflac.so
7fd5dca03000-7fd5dca04000 rw-p 00014000 08:01 11279712                   /usr/lib/gstreamer-0.10/libgstflac.so
7fd5dca04000-7fd5dca0a000 r-xp 00000000 08:01 11279812                   /usr/lib/gstreamer-0.10/libgstcoreindexers.so
7fd5dca0a000-7fd5dcc09000 ---p 00006000 08:01 11279812                   /usr/lib/gstreamer-0.10/libgstcoreindexers.so
7fd5dcc09000-7fd5dcc0a000 r--p 00005000 08:01 11279812                   /usr/lib/gstreamer-0.10/libgstcoreindexers.so
7fd5dcc0a000-7fd5dcc0b000 rw-p 00006000 08:01 11279812                   /usr/lib/gstreamer-0.10/libgstcoreindexers.so
7fd5dd40c000-7fd5dd40d000 ---p 00000000 00:00 0 
7fd5dd40d000-7fd5ddc0d000 rw-p 00000000 00:00 0 
7fd5ddc0d000-7fd5ddc17000 r-xp 00000000 08:01 11275011                   /usr/lib/gstreamer-0.10/libgstgio.so
7fd5ddc17000-7fd5dde16000 ---p 0000a000 08:01 11275011                   /usr/lib/gstreamer-0.10/libgstgio.so
7fd5dde16000-7fd5dde17000 r--p 00009000 08:01 11275011                   /usr/lib/gstreamer-0.10/libgstgio.so
7fd5dde17000-7fd5dde18000 rw-p 0000a000 08:01 11275011                   /usr/lib/gstreamer-0.10/libgstgio.so
7fd5dde18000-7fd5dde28000 r-xp 00000000 08:01 11272690                   /usr/lib/libva.so.1.0.12
7fd5dde28000-7fd5de027000 ---p 00010000 08:01 11272690                   /usr/lib/libva.so.1.0.12
7fd5de027000-7fd5de028000 r--p 0000f000 08:01 11272690                   /usr/lib/libva.so.1.0.12
7fd5de028000-7fd5de029000 rw-p 00010000 08:01 11272690                   /usr/lib/libva.so.1.0.12Avortat
oriol@oriol-laptop:~$ 


---

