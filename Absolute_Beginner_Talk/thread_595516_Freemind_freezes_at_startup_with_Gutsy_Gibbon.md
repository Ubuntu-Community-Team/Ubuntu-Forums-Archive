---
title: "Freemind freezes at startup with Gutsy Gibbon"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by unixer on 2007-10-28
Hi,

Using Gutsy Gibbon, when I start Freemind it freezes and I have to kill it making it unusable.  Here is what I have when trying to start it from a terminal window:

:~$ freemind

Looking for user properties:
/home/bfay/.freemind/user.properties

User properties found.
Default (System) Look & Feel: javax.swing.plaf.metal.MetalLookAndFeel
Warning: the font you have set as standard - null - is not available.
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module.
28-Oct-07 9:26:44 PM freemind.modes.ModesCreator getAllModes
INFO: Modes:[freemind.modes.browsemode.BrowseMode, freemind.modes.filemode.FileMode, freemind.modes.mindmapmode.MindMapMode]
28-Oct-07 9:26:44 PM freemind.modes.ModesCreator getMode
INFO: Initializing mode MindMap
28-Oct-07 9:26:44 PM freemind.modes.mindmapmode.MindMapController <init>
INFO: createIconActions
28-Oct-07 9:26:44 PM freemind.modes.mindmapmode.MindMapController <init>
INFO: createNodeHookActions
28-Oct-07 9:26:45 PM freemind.modes.mindmapmode.MindMapController <init>
INFO: mindmap_menus
28-Oct-07 9:26:45 PM freemind.modes.mindmapmode.MindMapController <init>
INFO: MindMapPopupMenu
28-Oct-07 9:26:45 PM freemind.modes.mindmapmode.MindMapController <init>
INFO: MindMapToolBar
28-Oct-07 9:26:45 PM freemind.modes.mindmapmode.MindMapController <init>
INFO: setAllActions
28-Oct-07 9:26:45 PM freemind.modes.ModesCreator getMode
INFO: Done: Initializing mode MindMap
Killed


Someone has an idea of what might be wrong with it?

thanks,
Bernard

---

### Post by indrajal on 2007-12-25
Happened to me as well. Open up /etc/environment and make sure you have the following:
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/

Also, add java to the path variable which should already exist
PATH="....:/usr/lib/jvm/java-6-sun-1.6.0.03/bin/"

I restarted my system but I'm guessing logging out and logging back in would also work. Freemind should start up after that.

---

### Post by dhedrick on 2008-02-05
I can get Freemind to install and open, but I can't install the plugin to allow me to convert to PDF (freemind-plugins-svg) it doesn't show up in Synaptic, and when I try to install off the download page, I get an error that I need libbatik-java package installed (it's a dependency issue), but I can't locate libbatik-java in package manager either - any advice?

Thanks!

---

