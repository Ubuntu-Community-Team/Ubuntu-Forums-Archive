---
title: "keyring daemon is not available, how to install and run it?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-23
Hi
Thank you for reading my post
I am trying to use f-spot to upload files to my picasaweb album and it return an error like:

```

An unhandled exception was thrown: The keyring daemon is not available

  at Gnome.Keyring.Ring.SendRequest (System.IO.MemoryStream stream) [0x00000] 
  at Gnome.Keyring.Ring.GetDefaultKeyring () [0x00000] 
  at FSpot.GoogleAccountManager.WriteAccounts () [0x00000] 
  at FSpot.GoogleAccountManager.MarkChanged (Boolean write, FSpot.GoogleAccount changed_account) [0x00000] 
  at FSpot.GoogleAccountManager.MarkChanged () [0x00000] 
  at FSpot.GoogleAccountManager.ReadAccounts () [0x00000] 
  at FSpot.GoogleAccountManager..ctor () [0x00000] 
  at FSpot.GoogleAccountManager.GetInstance () [0x00000] 
  at FSpot.GoogleExport..ctor (IBrowsableCollection selection) [0x00000] 
  at MainWindow.HandleExportToPicasa (System.Object sender, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Application:gtk_main ()
  at Gtk.Application.Run () [0x00000] 
  at Gnome.Program.Run () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

gnome-keyring-sharp (0.1.0.0)
System.Xml (2.0.0.0)
google-sharp (0.1.0.0)
FlickrNet (2.1.2.19557)
SmugMugNet (0.0.0.0)
pango-sharp (2.10.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.10.0.0)
gtkhtml-sharp (2.16.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.3.5.0)
Mono.GetOptions (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-16-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"


```

what should i do?

---

### Post by legolas_w on 2007-06-23
any comment?

thanks

---

### Post by legolas_w on 2007-06-23
any comment?



thanks

---

### Post by ElijahLofgren on 2007-07-10
I ran into this problem too and found the answer here: [Re: Picasa Web album export](http://osdir.com/ml/gnome.apps.f-spot/2006-10/msg00021.html)

For some reason, you need to run 3 commands before you run f-spot, so launching f-spot like this works:
```

eval `gnome-keyring-daemon` && export GNOME_KEYRING_SOCKET && export GNOME_KEYRING_PID && f-spot

```

Hope this helps,

Elijah

---

