---
title: "Using vuze azureus on gutsy"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-11-10
I can't seem to use the Azureus Vuze system properly. 
I installed it to /opt directory and created a link in my menu.

However, when I try to run Azureus, it doesn't start up sometimes. Here is the error from the command line:
noorez@noorez-laptop:~$ azureus 
Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
Passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]

This happens even if I quit azureus properly.


Also, when it does start, I get these error messages:

Failed to access torrent file ". Ensure sufficient temporary file space available (check browser cache usage).

and

" could not be opened:
Not a File

---

### Post by noorez on 2007-11-10
Here is what the command line gives me when the application starts properly. According to the output, there are some InvocationTargetException thrown. Is this a problem with the installation?



Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)], InvocationTargetException
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/mozilla for GRE
        Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Browser check failed with: XPCOM error -2147467259, InvocationTargetException
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" -Dazureus.script="/opt/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Locale Initializing took 332ms
   Core: 25ms for Loading Plugin : azemp
   Core: 25ms for Loading Plugin : azplugins
   Core: 28ms for Loading Plugin : azrating
   Core: 25ms for Loading Plugin : azupnpav
   Core: 126ms for Loading Plugin : Built In
   Core: 91ms for Initializing Global Torrent Manager
   Core: 51ms for Initializing Plugin: Tracker Static Pages
   Core: 92ms for Initializing Plugin: UPnP Media Server
   Core: 25ms for Initializing Plugin: DownloadRemoveRulesPlugin
   Core: 25ms for Initializing Plugin: UPnP
Analysing /opt/azureus/hs_err_pid6596.log
Core Initializing took 624ms
DEBUG::Sun Nov 11 03:18:45 GMT 2007  ExternalStimulus debug
   Core: 187ms for Initializing Plugin: azlocaltracker
GUI Initializing took 101ms
skin init took 604ms
createWindow init took 151ms
skin layout took 229ms
skin widgets init took 325ms
shell.open took 164ms
processStartupDMS took 0ms
DEBUG::Sun Nov 11 03:18:47 GMT 2007::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::587:
  Inconsistent stream length for 'http://192.168.1.1:2869/IGatewayDeviceDescDoc': expected = 3450, actual = 3451
    ResourceDownloaderURLImpl$2::runSupport::349,AEThread::run::69
DEBUG::Sun Nov 11 03:18:47 GMT 2007::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::587:
  Inconsistent stream length for 'http://192.168.1.1:2869/WanIPConnectionDescDoc': expected = 13757, actual = 13758
    ResourceDownloaderURLImpl$2::runSupport::349,AEThread::run::69

(gecko:6803): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Java6u3/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/Java6u3/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]

(gecko:6803): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1

---

