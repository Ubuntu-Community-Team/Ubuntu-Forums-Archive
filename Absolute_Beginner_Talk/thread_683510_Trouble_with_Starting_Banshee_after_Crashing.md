---
title: "Trouble with Starting Banshee after Crashing"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by bvc310 on 2008-01-31
Hi, I was trying to delete my entire song list of about 2000 songs and had problems with crashing. In turn i found that I was able to delete about 500 at a time. I deleted all but 500 of them and when trying to delete the last ones, banshee crashed again. I tried to restart it but received errors so I uninstalled banshee and tried reinstalling via: > sudo apt-get install banshee. I however am still getting errors, here is a copy of my error report, if anyone can lend me some guidance it would be much appreciated, i have read through as many threads as i could find with similar problems but none have yet so fixed my issue. It is crashing immediately at start up of the application btw.

> An unhandled exception was thrown: The given key was not present in the dictionary.

  at System.Collections.Generic.Dictionary`2[System.Int32,Banshee.Base.TrackInfo].get_Item (Int32 ) [0x00000] 
  at Banshee.Sources.PlaylistSource.LoadFromDatabase () [0x00000] 
  at Banshee.Sources.PlaylistSource..ctor (Int32 id) [0x00000] 
  at Banshee.Sources.PlaylistUtil.LoadSources () [0x00000] 
  at Banshee.Sources.LibrarySource.LoadPlaylists () [0x00000] 
  at Banshee.Sources.LibrarySource..ctor () [0x00000] 
  at Banshee.Sources.LibrarySource.get_Instance () [0x00000] 
  at Banshee.PlayerUI.OnStartupRunFinished (System.Object o, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Banshee.Base.ComponentInitializer.OnRunFinished () [0x00000] 
  at Banshee.Base.ComponentInitializer.Run () [0x00000] 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

System.Configuration (2.0.0.0)
glade-sharp (2.10.0.0)
Boo.Lang.Compiler (1.0.0.0)
Banshee.Plugins.Recommendation (0.13.1.19715)
Banshee.Plugins.Radio (0.13.1.19715)
Banshee.Plugins.Podcast (0.13.1.19713)
Banshee.Plugins.NotificationAreaIcon (0.13.1.19712)
Banshee.Plugins.MiniMode (0.13.1.19711)
Banshee.Plugins.MetadataSearch (0.13.1.19710)
Banshee.Plugins.Bookmarks (0.13.1.19708)
Banshee.Plugins.Audioscrobbler (0.13.1.19707)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.13.1.19706)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.13.1.19706)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.13.1.19705)
Banshee.MediaEngine.GStreamer (0.13.1.19704)
System.Xml (2.0.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.13.1.19699)
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
Banshee.Base (0.13.1.19702)
banshee (0.13.1.19704)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.22-14-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

---

### Post by skymera on 2008-01-31
delete the .banshee folder in your home the retry loading it.

usually fixes it.

---

### Post by bvc310 on 2008-01-31
Thanks, I tried to do that before but there is no .banshee folder in my home directory. I went to /home/brian/ and checked, there is no folder even after viewing the hidden files with CRTL+H

---

### Post by bvc310 on 2008-03-24
bump. I gave up for a while and decided to use rhythmbox instead but now have decided to give it another go since i miss banshee so much. does anyone have any ideas of what I can do to resolve this issue?

---

### Post by kpkeerthi on 2008-03-24
It is $HOME/.config/banshee

---

### Post by bvc310 on 2008-03-24
thank you so much. thats where it was. i couldnt find it until now. Works like a charm now.
Ty so much

---

