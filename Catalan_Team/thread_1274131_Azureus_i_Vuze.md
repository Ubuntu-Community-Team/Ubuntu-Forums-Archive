---
title: "Azureus i Vuze"
date: 2009-09-24
forum: Catalan Team
---

### Post by MiquelBLL on 2009-09-24
Feia servir el Deluge normalment pero al sortir la nova versio de Azureus anomenada Vuze em va agradar força per tot allo de baixar videos en HD i l´utilitzaba normalment finses que avans d´ahir vaig fer un ¨autoremove¨ i s´em va des-instal.lar el Vuze i estic intentant tornarlo a instal.lar i no puc no em surt la mateixa interficie del programa amb lo del HD i a mes sempre em queda instal.lada la versio 3.1.  L´altra vegada que vaig instal.lar Vuze em va sortir sense problemes i em sortia l´acces a Aplicacions/Internet/Vuze pero ara s´em queda instal.lada la versio anterior i no la 4. he provat de des-instal.lar-ho completament amb Synaptic pero no tinc manera d´instal.lar la versio 4.

---

### Post by MiquelBLL on 2009-09-28
Ja ho tinc arreglat, era simplement descomprimir i copiar el fitxer baixat de la pagina de Vuze i copiar-lo on estava avans vuze que era usr/share/vuze  i editar el menu principal i fer un enllaç.

---

### Post by jinglada on 2009-11-10
> **MiquelBLL said:**
> Ja ho tinc arreglat, era simplement descomprimir i copiar el fitxer baixat de la pagina de Vuze i copiar-lo on estava avans vuze que era usr/share/vuze  i editar el menu principal i fer un enllaç.

Jo també uso Vuze, en versió 3.1.1.0, i al engegar em surt l'actualitzador per a la versió 4.2.0.8 
L'he executada molts cops i no funciona i es queda la 3.1.1.0
En el meu cas el tinc instal·lat a: /usr/bin/vuze
Em pots dir exactament quin fitxer has copiat?

---

### Post by MiquelBLL on 2009-11-13
Tens que donar permisos a la carpeta per que es pugui actualitzar, aixo m´ho va fer un amic que encara no ho tinc clar. Si no pots esborrar la versio 3 i instal.lar la 4 directament crec.

---

### Post by jinglada on 2009-11-15
> **MiquelBLL said:**
> Tens que donar permisos a la carpeta per que es pugui actualitzar, aixo m´ho va fer un amic que encara no ho tinc clar. Si no pots esborrar la versio 3 i instal.lar la 4 directament crec.

1) vaig donar permisos d'usuari a les carpetes  /usr/bin/vuze i /usr/bin/azureus i fa la mateixa història, diu que l'actualitza però no ho fa.

2) Desinstal·lo la versió 3 i instal·lo la 4 i vet ací el resultat:

joan@joan-laptop:~/vuze/vuze$ ./azureus
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/firefox for GRE
	Can not use GRE from /usr/lib/firefox because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-addons for GRE
	Can not use GRE from /usr/lib/xulrunner-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/mozilla for GRE
	Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-addons for GRE
	Can not use GRE from /usr/lib/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-1.9.1.6pre for GRE
	Can not use GRE from /usr/lib/xulrunner-1.9.1.6pre because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-3.0.10 for GRE
	Can not use GRE from /usr/lib/firefox-3.0.10 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-3.5.6pre for GRE
	Can not use GRE from /usr/lib/firefox-3.5.6pre because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner for GRE
	Can not use GRE from /usr/lib/xulrunner because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-1.9.0.15 for GRE
	Can not use GRE from /usr/lib/xulrunner-1.9.0.15 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/seamonkey for GRE
GRE found at /usr/lib/seamonkey.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuzehas better luck.
setting LD_LIBRARY_PATH to: /usr/lib/seamonkey
setting MOZILLA_FIVE_HOME to: /usr/lib/seamonkey
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/joan/vuze/vuze" -Dazureus.install.path="/home/joan/vuze/vuze" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/joan/vuze/vuze/Azureus2.jar ; file:/home/joan/vuze/vuze/swt.jar ; file:/home/joan/vuze/vuze/
DEBUG::Sun Nov 15 07:35:16 CET 2009::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::67:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.5) from [http://eclipse.org/swt](http://eclipse.org/swt)

(2) No write access to '/tmp'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::110,Main::<init>::88,Main::main::255,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::57,DelegatingMethodAccessorImpl::invoke::43,Method::invoke::616,MainExecutor$1::run::37,Thread::run::636
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:182)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:90)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:67)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
joan@joan-laptop:~/vuze/vuze$ 
--------------------

Total: no tinc Azureus i Vuze!

---

### Post by papapep on 2009-11-15
> vaig donar permisos d'usuari a les carpetes /usr/bin/vuze i /usr/bin/azureus

Ens has de posar la ordre que has executat, per entendre-ho.

> No write access to '/tmp'

Has de canviar els permisos que tens a /tmp. Fes:

```
sudo chmod 777 /tmp
```

---

### Post by jinglada on 2009-11-15
> **papapep said:**
> Ens has de posar la ordre que has executat, per entendre-ho.



Has de canviar els permisos que tens a /tmp. Fes:

```
sudo chmod 777 /tmp
```

Gràcies papapep!

fet: drwxrwxrwx  17 root root  12288 2009-11-15 14:04 tmp

i els directoris de l'aplicació: /usr/bin/vuze i /usr/bin/azureu ara ja no hi son perquè vaig desinstal·lar la versió 3 de l'aplicació. Els permisos d'usuari 'joan' en lloc de 'root' els havia donat amb Alt-F2->gksu nautilus->propietats.

He tornat a instal·lar la versio 4 i fa el mateix.

No serà pas això que diu quasi al començament?:

Java exec found in PATH. Verifying...
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM

---

### Post by jinglada on 2009-11-20
Mentre espero que algú em pugui ajudar he tornat a instal·lar la versió 3.1.1.0 des de Synaptic.
Salut a tothom.

---

