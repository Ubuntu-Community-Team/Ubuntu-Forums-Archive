---
title: "Problema amb el Amarok"
date: 2009-10-12
forum: Catalan Team
---

### Post by albert-I on 2009-10-12
Bon dia

Amb el meu usuari i sols amb el meu tinc problemes per que Amarok em funcioni.

He vist que els altres reproductors i similars funcionen i no se si es problema del phonon_xine o familia.

Agrairia l'ajuda per aquest problema. 

Aquest és l'error que em dona el gestor de petades de KDE(el nom de gestor de petades és de fabrica)

Application: Amarok (amarok), signal: Segmentation fault
pthread_cond_timedwait@@GLIBC_2.3.2 ()
    at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_timedwait.S:217
	in ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_timedwait.S
[Current thread is 0 (LWP 15861)]

Thread 5 (Thread 0x7ff33eb3d950 (LWP 15862)):
#0  pthread_cond_timedwait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_timedwait.S:217
#1  0x00007ff343a50f91 in ?? () from /usr/lib/libxine.so.1
#2  0x00007ff354f773ba in start_thread (arg=<value optimized out>) at pthread_create.c:297
#3  0x00007ff3527cdfcd in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#4  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7ff33d8ca950 (LWP 15863)):
[KCrash Handler]
#5  0x00007ff343a6b9b0 in xine_post_input () from /usr/lib/libxine.so.1
#6  0x00007ff343cd8139 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#7  0x00007ff343cbce5a in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#8  0x00007ff343cbd009 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#9  0x00007ff343cbfb32 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#10 0x00007ff343cadbb1 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#11 0x00007ff353ecdf4d in QApplicationPrivate::notify_helper (this=0x1b064b0, receiver=0x1ae7420, e=0x1b99a30) at kernel/qapplication.cpp:4056
#12 0x00007ff353ed618a in QApplication::notify (this=0x7fff5e2dba00, receiver=0x1ae7420, e=0x1b99a30) at kernel/qapplication.cpp:4021
#13 0x00007ff355cc6abb in KApplication::notify (this=0x7fff5e2dba00, receiver=0x1ae7420, event=0x1b99a30) at /build/buildd/kde4libs-4.3.2/kdeui/kernel/kapplication.cpp:302
#14 0x00007ff35334c6ac in QCoreApplication::notifyInternal (this=0x7fff5e2dba00, receiver=0x1ae7420, event=0x1b99a30) at kernel/qcoreapplication.cpp:610
#15 0x00007ff35334d31a in QCoreApplicationPrivate::sendPostedEvents (receiver=0x0, event_type=0, data=0x1c48d20) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:213
#16 0x00007ff353375e03 in postEventSourceDispatch (s=<value optimized out>) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:218
#17 0x00007ff34b3f620a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#18 0x00007ff34b3f98e0 in ?? () from /usr/lib/libglib-2.0.so.0
#19 0x00007ff34b3f9a7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#20 0x00007ff353375a8f in QEventDispatcherGlib::processEvents (this=0x1c20ea0, flags=<value optimized out>) at kernel/qeventdispatcher_glib.cpp:327
#21 0x00007ff35334af42 in QEventLoop::processEvents (this=<value optimized out>, flags={i = 1032626064}) at kernel/qeventloop.cpp:149
#22 0x00007ff35334b314 in QEventLoop::exec (this=0x7ff33d8c9fd0, flags={i = 1032626144}) at kernel/qeventloop.cpp:201
#23 0x00007ff35325fdc8 in QThread::exec (this=<value optimized out>) at thread/qthread.cpp:487
#24 0x00007ff343cac62c in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#25 0x00007ff353262d35 in QThreadPrivate::start (arg=0x1ae7420) at thread/qthread_unix.cpp:188
#26 0x00007ff354f773ba in start_thread (arg=<value optimized out>) at pthread_create.c:297
#27 0x00007ff3527cdfcd in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#28 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7ff33cebf950 (LWP 15866)):
#0  0x00007ff3527c4496 in *__GI___poll (fds=0x7ff33cebef60, nfds=1, timeout=333) at ../sysdeps/unix/sysv/linux/poll.c:87
#1  0x00007ff33cec4969 in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
#2  0x00007ff354f773ba in start_thread (arg=<value optimized out>) at pthread_create.c:297
#3  0x00007ff3527cdfcd in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7ff33c6be950 (LWP 15867)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:261
#1  0x00007ff343a62353 in ?? () from /usr/lib/libxine.so.1
#2  0x00007ff354f773ba in start_thread (arg=<value optimized out>) at pthread_create.c:297
#3  0x00007ff3527cdfcd in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#4  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7ff356197790 (LWP 15861)):
#0  pthread_cond_timedwait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_timedwait.S:217
#1  0x00007ff353262785 in thread_sleep (ti=0x7fff5e2dad70) at thread/qthread_unix.cpp:297
#2  0x00007ff3532628ee in QThread::msleep (msecs=200) at thread/qthread_unix.cpp:323
#3  0x00007ff343cd024a in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#4  0x00007ff34f315130 in ?? () from /usr/lib/libphonon.so.4
#5  0x00007ff35271e6ed in *__GI_exit (status=1) at exit.c:75
#6  0x00007ff353f2b6a8 in qt_xio_errhandler () at kernel/qapplication_x11.cpp:707
#7  0x00007ff355cc64d8 in KApplication::xioErrhandler (this=0x7fff5e2dba00, dpy=0x1b1d1b0) at /build/buildd/kde4libs-4.3.2/kdeui/kernel/kapplication.cpp:408
#8  0x00007ff351de76e4 in _XIOError () from /usr/lib/libX11.so.6
#9  0x00007ff351deea1f in ?? () from /usr/lib/libX11.so.6
#10 0x00007ff351def345 in _XEventsQueued () from /usr/lib/libX11.so.6
#11 0x00007ff351dc6f0a in XFlush () from /usr/lib/libX11.so.6
#12 0x00007ff353f1e611 in QWidget::setCursor (this=0x1e48d00, cursor=@0x7fff5e2dafb0) at kernel/qwidget.cpp:4623
#13 0x00007ff3542ea095 in QSizeGripPrivate::init (this=0x1e44060) at widgets/qsizegrip.cpp:241
#14 0x00007ff3542ea473 in QSizeGrip (this=0x1e48d00, parent=0x1e2dc50) at widgets/qsizegrip.cpp:212
#15 0x00007ff3542f8c78 in QStatusBar::setSizeGripEnabled (this=0x1e2dc50, enabled=<value optimized out>) at widgets/qstatusbar.cpp:496
#16 0x00007ff3542f90c8 in QStatusBar (this=0x1e2dc50, parent=0x1b9ab00) at widgets/qstatusbar.cpp:285
#17 0x00007ff355db3fb6 in KStatusBar (this=0x7fff5e2dacf4, parent=0x0) at /build/buildd/kde4libs-4.3.2/kdeui/widgets/kstatusbar.cpp:74
#18 0x00007ff3556ad001 in StatusBar::StatusBar () from /usr/lib/libamaroklib.so.1
#19 0x00007ff35570642e in MainWindow::MainWindow () from /usr/lib/libamaroklib.so.1
#20 0x00007ff3556e8bf7 in App::continueInit () from /usr/lib/libamaroklib.so.1
#21 0x00007ff3556e9b2b in App::App () from /usr/lib/libamaroklib.so.1
#22 0x000000000053305b in _start ()
217	in ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_timedwait.S

---

### Post by orestesmas on 2009-10-12
Si només és amb el teu usuari pots provar d'eliminar els fitxers de configuració de l'Amarok, a veure si s'arregla:

- Surt de l'amarok totalment (que no quedi ni la icona a la safat adel sistema)
- Esborra els fitxers /home/usuari/.kde/share/config/amarok*
- Prova de tornar a arrencar. Si segueix petant torna a repetir tot el procés i llavors esborra també el directori /home/usuari/.kde/share/apps/amarok ATENCIÓ. En fer això t'esborrarà la informació sobre les cançons que tenies, i l'hauràs de tornar a regenerar (però no esborra les cançons en si, que són en una altra banda)

A veure què tal...

---

### Post by albert-I on 2009-10-25
> **orestesmas said:**
> Si només és amb el teu usuari pots provar d'eliminar els fitxers de configuració de l'Amarok, a veure si s'arregla:

- Surt de l'amarok totalment (que no quedi ni la icona a la safat adel sistema)
- Esborra els fitxers /home/usuari/.kde/share/config/amarok*
- Prova de tornar a arrencar. Si segueix petant torna a repetir tot el procés i llavors esborra també el directori /home/usuari/.kde/share/apps/amarok ATENCIÓ. En fer això t'esborrarà la informació sobre les cançons que tenies, i l'hauràs de tornar a regenerar (però no esborra les cançons en si, que són en una altra banda)

A veure què tal...

Vaig posar-ho al web dels errors de KDE (bugs.kde.org)i em van dir que era un error del phonon. El problema es que el bugzilla no em tira. I al final també em dona un problema al iniciar el meu usuari. 

Solució:

Esperar que surti el 9.10 i instal·lar-ho tot de nou. Així faig neteja i podré aprofitar totes les coses noves i no aniré amb remores.

---

