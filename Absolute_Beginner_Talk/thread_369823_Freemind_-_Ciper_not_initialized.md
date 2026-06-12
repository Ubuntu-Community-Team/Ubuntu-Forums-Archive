---
title: "Freemind - Ciper not initialized"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by sunspots on 2007-02-25
Hi 
I installed Freemind on Ubuntu Dapper v6.06 and have been able to get it started. I then opened a Freemind map created on Freemind on Windows XP Professional. The Freemind map is encrypted. 
 
When I try to toggle the encryption to decrypt the mind map I get the following error 
 
java.lang.IllegalStateException: Cipher not initialized 
 
The full transcript to the above error: 
Default (System) Look & Feel: javax.swing.plaf.metal.MetalLookAndFeel 
Warning: the font you have set as standard - null - is not available. 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
22/02/2007 22:53:08 freemind.modes.ModesCreator getAllModes 
INFO: Modes:[freemind.modes.browsemode.BrowseMode, freemind.modes.filemode.FileMode, freemind.modes.mindmapmode.MindMapMode] 
22/02/2007 22:53:08 freemind.modes.ModesCreator getMode 
INFO: Initializing mode MindMap 
22/02/2007 22:53:08 freemind.modes.mindmapmode.MindMapController <init> 
INFO: createIconActions 
22/02/2007 22:53:09 freemind.modes.mindmapmode.MindMapController <init> 
INFO: createNodeHookActions 
22/02/2007 22:53:11 freemind.modes.mindmapmode.MindMapController <init> 
INFO: mindmap_menus 
22/02/2007 22:53:11 freemind.modes.mindmapmode.MindMapController <init> 
INFO: MindMapPopupMenu 
22/02/2007 22:53:11 freemind.modes.mindmapmode.MindMapController <init> 
INFO: MindMapToolBar 
22/02/2007 22:53:11 freemind.modes.mindmapmode.MindMapController <init> 
INFO: setAllActions 
22/02/2007 22:53:11 freemind.modes.ModesCreator getMode 
INFO: Done: Initializing mode MindMap 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module. 
22/02/2007 22:54:49 freemind.controller.MainToolBar setZoomComboBox 
INFO: setZoomComboBox is called with 1.0. 
22/02/2007 22:54:49 freemind.extensions.HookFactory getClassLoader 
INFO: file /usr/share/freemind/plugins/time/time_plugin.jar exists = true 
22/02/2007 22:54:49 freemind.extensions.HookFactory getClassLoader 
INFO: file /usr/share/java/jcalendar.jar exists = true 
22/02/2007 22:54:49 freemind.modes.mindmapmode.MindMapController startupController 
INFO: mScheduledActions are executed: 4 
22/02/2007 22:54:49 freemind.modes.ControllerAdapter registerMouseWheelEventHandler 
INFO: Registered MouseWheelEventHandler accessories.plugins.UnfoldAll$Registration@b6ef8 
java.lang.IllegalStateException: Cipher not initialized 
at javax.crypto.Cipher.c(DashoA13*..) 
at javax.crypto.Cipher.doFinal(DashoA13*..) 
at freemind.modes.mindmapmode.EncryptedMindMapNode$DesEncrypter.decrypt(EncryptedMindMapNode.java:434) 
at freemind.modes.mindmapmode.EncryptedMindMapNode.decryptXml(EncryptedMindMapNode.java:304) 
at freemind.modes.mindmapmode.EncryptedMindMapNode.checkPassword(EncryptedMindMapNode.java:128) 
at freemind.modes.mindmapmode.EncryptedMindMapNode.decrypt(EncryptedMindMapNode.java:94) 
at accessories.plugins.EncryptNode.doPasswordCheckAndDecryptNode(EncryptNode.java:230) 
 
 
--------------------- 
Can anyone give me any clues how I reslove ths issue. 
Thanks

---

### Post by Scunizi on 2007-03-12
I haven't played with Freemind in a while.  Does it have an xml export function? or a way to export to another type of file?  If so you might try loading VYM on the linux side (I find it much better than Freemind) and then importing it.  If it will export to a MindManager format, VYM will import that as well.

---

### Post by sunspots on 2007-03-18
Thanks for the reply and tip. I'll have a closer look VYM. I noticed that it has a Windows version, so I can work between the two systems. Freemind doesn't seem to offer (v0.8.0) any xml or MindManger export.

---

### Post by sunspots on 2007-03-18
Looking back at the web site, I see that VYM does not recommend the windows port due to an error. See web site for further details.
[http://www.insilmaril.de/vym/#id50368](http://www.insilmaril.de/vym/#id50368)

---

### Post by Soarer on 2007-03-18
> **Scunizi said:**
> I haven't played with Freemind in a while.  Does it have an xml export function? or a way to export to another type of file?  If so you might try loading VYM on the linux side (I find it much better than Freemind) and then importing it.  If it will export to a MindManager format, VYM will import that as well.

Hi -  I have just started using VYM and it seems to do most of what I want (though an export to DOC or OO format would be nice). I can't see how it can import MindManger maps. Could you explain, please?

---

### Post by Scunizi on 2007-03-18
I'm using Vym version 1.8.1 which I compiled from source a while ago.  I still have the deb I made if you want it.  It's 2.9meg.  It does have an OO export, however when initiating it, it builds a number of xml files.  I haven't been able to get OO to load anything other than the text of the files as opposed to the graphic functionality.  It will also export to LaTex, Xml, Taskjuggler, webpage xhtml and a couple of others.  I've used the webpage export and it works well.  I've attached a copy for your viewing pleasure.

Edit:  My actual deb file was created with alien.. I didn't compile from source.

---

### Post by Soarer on 2007-03-18
Thanks Scunizi for alerting me to that. I created the .deb with alien too - seems to work fine and imports from MM files and exports to OO. Much more useful now :)

It gives a couple of errors when run from the command line, but everything seems to function.

---

### Post by Scunizi on 2007-03-18
How did you get it to export to OO?

---

### Post by Soarer on 2007-03-18
File > Export > Open Office 

It seems to only produce presentations, but I can live with that.

---

### Post by Scunizi on 2007-03-18
Strange.  I tried that with my copy and it produced a bunch of files but will not load as a presentation.  It will only display the contents (text) of the files inside of writer even when I try to force it in another app.

---

### Post by Soarer on 2007-03-18
For me, it produces a .zip file. If I use an OO application to open that .zip file, I get a presentation. This works also if I try to use the word processor to open it - it loads Impress & opens the file.

---

### Post by Scunizi on 2007-03-18
I hadn't tried opening the zip file with OO.  I unpacked it then tried.  It does open for me like it does you but with limited results.

---

