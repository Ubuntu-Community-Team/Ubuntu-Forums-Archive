---
title: "Can't sync ipod with banshee"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-06-02
I plug in my ipod and it won't sync.

> Banshee encountered a fatal error
Cannotcast source type from destination type 

and the error details

> An unhandled exception was thrown: Cannot cast from source type to destination type.

at Banshee.Dap.DapDevice.HandleTranscodeErrors (Banshee.Base.BatchTranscoder) <0x0015d>
at <>c__CompilerGenerated69.<>c__AnonymousMethod70 (object,System.EventArgs) <0x00016>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_object_EventArgs (object,System.EventArgs) <0x0003e>
at InvokeCB.Invoke () <0x0001a>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x0002c>
at TimeoutProxy.Handler () <0x0002a>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x00036>
in (unmanaged) 0xb7f223c5
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Gnome.Program.Run () <0x00007>
at Banshee.BansheeEntry.Startup (string[]) <0x007f4>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_string[] (string[]) <0x00037>
at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.CleanRoomStartup/StartupInvocationHandler,string[]) <0x000ae>

.NET Version: 2.0.50727.42

Assembly Version Information:

System.Configuration (2.0.0.0)
glade-sharp (2.10.0.0)
Boo.Lang.Compiler (1.0.0.0)
Banshee.Plugins.Recommendation (0.12.1.12341)
Banshee.Plugins.Radio (0.12.1.12340)
Banshee.Plugins.Podcast (0.12.1.12339)
Banshee.Plugins.NotificationAreaIcon (0.12.1.12337)
Banshee.Plugins.MiniMode (0.12.1.12336)
Banshee.Plugins.MetadataSearch (0.12.1.12335)
Banshee.Plugins.MMKeys (0.12.1.12336)
Banshee.Plugins.Audioscrobbler (0.12.1.12332)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.12.1.12331)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.12.1.12331)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.12.1.12330)
Banshee.MediaEngine.GStreamer (0.12.1.12329)
System.Xml (2.0.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.12.1.12322)
Last.FM (0.0.0.0)
NDesk.DBus (1.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gnome-sharp (2.16.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.12.1.12326)
banshee (0.12.1.12328)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-16-386 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"



---

### Post by rickycodie on 2007-06-02
i know that you're looking to fix banshee, but have you considered trying amarok, exaile, or rythmbox( itunes equivelent)?

i have used them all at one time or another and i love exaile.

---

### Post by phoenix23 on 2007-06-02
I'd really like to fix Banshee.

It worked fine before I installed gtkpod, so I'm guessing it has something to do with that. The software is uninstalled now, so how do I undo the effects? My ipod works fine when I plug it into itunes on a vista box, but it wont work in banshee anymore.

---

### Post by rickycodie on 2007-06-02
here's a couple options 
[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

and 
[http://www.gtkpod.org/TROUBLESHOOTING](http://www.gtkpod.org/TROUBLESHOOTING)
this is all i could find on the problem that you are having, i will look harder

---

### Post by rickycodie on 2007-06-02
just a gee whiz, have you unnstalled banshee and reinstalled it? 
sometimes that helps.

---

### Post by rickycodie on 2007-06-02
[http://banshee-project.org/Troubleshooting](http://banshee-project.org/Troubleshooting)
and
[http://banshee-project.org/Support](http://banshee-project.org/Support)
are my last options i hope this helps.

---

### Post by wild_oscar on 2007-06-19
Any update on this?

The exact same thing happened to me, I gave up Banshee with the impression it was a failure project and tried Amarok.

I'm more or less satisfied with Amarok, except:

a) doesn't have a "sync with ipod" option

b) I can't seem to update to the ipod the files I have made changes in the tag (ex: add lyrics), which is a bummer.

---

