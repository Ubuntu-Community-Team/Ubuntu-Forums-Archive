---
title: "URGENT Looking glass error"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by mitch707 on 2008-04-05
LG3D Dir         : /usr/share/lg3d/
LGCONFIG         : file:////etc//lg3d/lgconfig_1p_x.xml
LG_SETTINGS      :  -Dlg.etcdir=/etc/ -Dlg.resourcedir=/usr/share/lg3d/resources/ -Dlg.use3dtoolkit=true -Dlg.fws.mode=app -Dlg.lgserverdisplay=:1 -Dawt.toolkit=org.jdesktop.lg3d.awt.xlg3dtoolkit  -Dlg.fws.x11.interfaceRequired=5.0
LGX11HOME        : /usr/share/lg3d//lib/linux-i686/lg3d-x11
X Server Version : dev-0-9-0-3
JAVA_HOME        : /usr/share/lg3d-jdk
CLASSPATH        : /usr/share/lg3d//lib/lg3d-core.jar:/usr/share/lg3d//lib/lg3d-demo-apps.jar:/usr/share/lg3d//ext/j3d-contrib-utils.jar:/usr/share/lg3d//ext/escher-0.2.2.lg.jar:/usr/share/lg3d//ext/satin-v2.3.jar:/usr/share/lg3d//ext/app/bgmanager.jar:
PATH             : /usr/share/lg3d-jdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/usr/share/lg3d//lib/i386
LD_LIBRARY_PATH  : /usr/share/lg3d//lib/linux-i686/lg3d-x11/exports/lib:/usr/share/lg3d//lib/linux-i686::/usr/share/lg3d//lib/linux-i686/lg3d-x11/exports/lib:/usr/share/lg3d//lib:/usr/share/lg3d//ext/escher/platform/linux/i686/lib
JAVACMD          : /usr/share/lg3d-jdk/bin/java -client -XX:CompilerThreadPriority=4 -Xms128m -Xmx256m -XX:+UseConcMarkSweepGC -XX:+DisableExplicitGC -Dlg.appcodebase=file:///usr/share/lg3d//ext/app  -Dj3d.useFreeLists=false -Xbootclasspath/a:/usr/share/lg3d//lib/lg3d-awt-toolkit.jar:/usr/share/lg3d//lib/fws-x11-kbd-utils.jar    -Dj3d.sortShape3DBounds=true -Dlg.configurl=file:////etc//lg3d/lgconfig_1p_x.xml -Dlg.displayconfigurl=file:////etc//lg3d/displayconfig/j3d1x1  -Dlg.etcdir=/etc/ -Dlg.resourcedir=/usr/share/lg3d/resources/ -Dlg.use3dtoolkit=true -Dlg.fws.mode=app -Dlg.lgserverdisplay=:1 -Dawt.toolkit=org.jdesktop.lg3d.awt.xlg3dtoolkit  -Dlg.fws.x11.interfaceRequired=5.0 org.jdesktop.lg3d.displayserver.Main
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.Main main
INFO: 
	LG3D Version              : 1-0-0
	LG3D Build Time           : 09:33 PST 19 Dec 2006(0612190933)
	LG3D Build Type           : 
	LG3D Java Version         : 1.6.0-rc

	Java Version              : 1.6.0-rc
	Java Vendor               : Sun Microsystems Inc.
	Java Class Version        : 50.0
	Java Class Path           : /usr/share/lg3d//lib/lg3d-core.jar:/usr/share/lg3d//lib/lg3d-demo-apps.jar:/usr/share/lg3d//ext/j3d-contrib-utils.jar:/usr/share/lg3d//ext/escher-0.2.2.lg.jar:/usr/share/lg3d//ext/satin-v2.3.jar:/usr/share/lg3d//ext/app/bgmanager.jar:
	App Codebase              : file:///usr/share/lg3d//ext/app

	OS Name                   : Linux
	OS Arch                   : i386
	OS Version                : 2.6.22-14-generic

	Def. Locale Language Code : en
	Def. Locale Country Code  : US

Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig loadConfig
INFO: Loading config file:////etc//lg3d/lgconfig_1p_x.xml
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig loadConfig
INFO: Config file contents:
	<?xml version="1.0" encoding="UTF-8"?> 
	<java version="1.4.2_04" class="java.beans.XMLDecoder"> 
	 <object class="org.jdesktop.lg3d.displayserver.LgConfig"> 
	  <void property="x11IntegrationEnabled"> 
	   <boolean>true</boolean>
	  </void> 
	  <void property="clientServer"> 
	   <boolean>false</boolean>
	  </void> 
	  <void property="foundationWinSys"> 
	   <string>org.jdesktop.lg3d.displayserver.fws.x11.WinSysX11</string>
	  </void> 
	 </object> 
	</java> 

Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig loadConfig
INFO: Finished loading config
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig logConfig
CONFIG: SceneManager org.jdesktop.lg3d.scenemanager.glassy.GlassySceneManager
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig logConfig
CONFIG: FoundationWinSys org.jdesktop.lg3d.displayserver.fws.x11.WinSysX11
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig logConfig
CONFIG: NativeWinIntegration org.jdesktop.lg3d.displayserver.nativewindow.x11.X11IntegrationModule
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig logConfig
CONFIG: NativeWinLookAndFeel org.jdesktop.lg3d.scenemanager.utils.decoration.GlassyNativeWindowLookAndFeel
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig logConfig
CONFIG: ClientServer false
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.LgConfig logConfig
CONFIG: X11IntegrationEnabled true
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.DisplayServerControl initialize
CONFIG: Display configuration overridden by lg.displayconfigurl property to file:////etc//lg3d/displayconfig/j3d1x1
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.DisplayServerControl initialize
CONFIG: Using DefaultUniverseFactory
Apr 5, 2008 5:55:16 PM org.jdesktop.lg3d.displayserver.socketconnector.ServerHandler <init>
SEVERE: Unhandled error, see /var/tmp/lgserver.log for details.
java.lang.UnsatisfiedLinkError: /usr/share/lg3d-jdk/jre/lib/i386/libj3dcore-ogl.so: /usr/lib/libGL.so.1: undefined symbol: XDamageAdd
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at javax.media.j3d.NativePipeline$1.run(NativePipeline.java:138)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.media.j3d.NativePipeline.loadLibrary(NativePipeline.java:135)
	at javax.media.j3d.NativePipeline.loadLibraries(NativePipeline.java:95)
	at javax.media.j3d.MasterControl.loadLibraries(MasterControl.java:785)
	at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUniverse.java:259)
	at javax.media.j3d.GraphicsConfigTemplate3D.getBestConfiguration(GraphicsConfigTemplate3D.java:302)
	at java.awt.GraphicsDevice.getBestConfiguration(GraphicsDevice.java:158)
	at com.sun.j3d.utils.universe.Viewer.<init>(Viewer.java:543)
	at com.sun.j3d.utils.universe.ConfigView.createViewer(ConfigView.java:466)
	at com.sun.j3d.utils.universe.ConfigContainer.processViews(ConfigContainer.java:726)
	at com.sun.j3d.utils.universe.ConfigContainer.processConfig(ConfigContainer.java:675)
	at com.sun.j3d.utils.universe.ConfigContainer.<init>(ConfigContainer.java:235)
	at com.sun.j3d.utils.universe.ConfigContainer.<init>(ConfigContainer.java:171)
	at org.jdesktop.lg3d.displayserver.DefaultUniverseFactory.createUniverse(Unknown Source)
	at org.jdesktop.lg3d.displayserver.DisplayServerControl.initialize(Unknown Source)
	at org.jdesktop.lg3d.displayserver.AppConnectorPrivate.getAppConnector(Unknown Source)
	at org.jdesktop.lg3d.displayserver.socketconnector.ServerHandler.<init>(Unknown Source)
	at org.jdesktop.lg3d.displayserver.Main.main(Unknown Source)

---

### Post by Saya on 2008-04-07
What exactly is causing you problems? (some context of the log please)

---

### Post by SunnyRabbiera on 2008-04-07
looking glass is still experimental, heck i dont think its even being developed anymore...

---

### Post by msgyrd on 2008-04-07
Random log data isn't that useful without an explanation of the error.  Since I don't see anything Ubuntu related in the log, I would suggest you look at Project Looking Glass's forums at: [http://forums.java.net/jive/category.jspa?categoryID=47](http://forums.java.net/jive/category.jspa?categoryID=47) they are more likely to have answers for your problems.

From the little information supplied, this looks like the problem area: ```
SEVERE: Unhandled error, see /var/tmp/lgserver.log for details.
java.lang.UnsatisfiedLinkError: /usr/share/lg3d-jdk/jre/lib/i386/libj3dcore-ogl.so: /usr/lib/libGL.so.1: undefined symbol: XDamageAdd
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.jav  a:1751)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java  :166:cool:
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1030)
    at javax.media.j3d.NativePipeline$1.run(NativePipelin  e.java:13:cool:
    at java.security.AccessController.doPrivileged(Native Method)
    at javax.media.j3d.NativePipeline.loadLibrary(NativeP  ipeline.java:135)
    at javax.media.j3d.NativePipeline.loadLibraries(Nativ  ePipeline.java:95)
    at javax.media.j3d.MasterControl.loadLibraries(Master  Control.java:785)
    at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUn  iverse.java:259)
    at javax.media.j3d.GraphicsConfigTemplate3D.getBestCo  nfiguration(GraphicsConfigTemplate3D.java:302)
    at java.awt.GraphicsDevice.getBestConfiguration(Graph  icsDevice.java:15:cool:
    at com.sun.j3d.utils.universe.Viewer.<init>(Viewer.ja  va:543)
    at com.sun.j3d.utils.universe.ConfigView.createViewer  (ConfigView.java:466)
    at com.sun.j3d.utils.universe.ConfigContainer.process  Views(ConfigContainer.java:726)
    at com.sun.j3d.utils.universe.ConfigContainer.process  Config(ConfigContainer.java:675)
    at com.sun.j3d.utils.universe.ConfigContainer.<init>(  ConfigContainer.java:235)
    at com.sun.j3d.utils.universe.ConfigContainer.<init>(  ConfigContainer.java:171)
    at org.jdesktop.lg3d.displayserver.DefaultUniverseFac  tory.createUniverse(Unknown Source)
    at org.jdesktop.lg3d.displayserver.DisplayServerContr  ol.initialize(Unknown Source)
    at org.jdesktop.lg3d.displayserver.AppConnectorPrivat  e.getAppConnector(Unknown Source)
    at org.jdesktop.lg3d.displayserver.socketconnector.Se  rverHandler.<init>(Unknown Source)
    at org.jdesktop.lg3d.displayserver.Main.main(Unknown Source)     
```It appears that you're missing some java libraries, or it can't find them if they are installed.  Take a look at the "/var/tmp/lgserver.log" file that it suggests for more details/information.

---

