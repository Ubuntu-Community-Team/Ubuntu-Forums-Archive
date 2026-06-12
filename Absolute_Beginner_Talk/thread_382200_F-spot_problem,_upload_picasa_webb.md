---
title: "F-spot problem, upload picasa webb"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by jah2007 on 2007-03-11
Hello
I cant upload to picasa webbalbum with F-spot??

Is there a known problem?

/J

---

### Post by Parksy on 2007-03-12
I'm having a problem as well: f-spot can't seem to authenticate with my Google account.

No idea how to fix it though.

---

### Post by kaffekopp on 2007-04-22
Have this problem, too. Think I read somewhere that it's due to a change google made to picasa-web. In that case, we'll just have to wait until an updated version of f-spot is out. Or? Anyone have any other info, know of patches, fixes, etc?

---

### Post by suoko on 2007-08-22
this is the error I get with f-spot 0.22 and dapper:
(f-spot 0.35 on dapper gives no problem however)
An unhandled exception was thrown: Object reference not set to an instance of an object

in <0x0019e> Mono.Google.Picasa.PicasaWeb:GetAlbums ()
in <0x0005b> FSpot.GoogleExport:PopulateAlbumOptionMenu (Mono.Google.Picasa.PicasaWeb picasa)
in <0x003d9> FSpot.GoogleExport:Connect (FSpot.GoogleAccount selected, System.String token, System.String text)
in <0x00011> FSpot.GoogleExport:Connect (FSpot.GoogleAccount selected)
in <0x0000c> FSpot.GoogleExport:Connect ()
in <0x0000a> FSpot.GoogleExport:HandleAccountSelected (System.Object sender, System.EventArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x00093> GLib.Signal:voidObjectCallback (IntPtr handle, IntPtr gch)
in (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.OptionMenu:gtk_option_menu_set_menu (intptr,intptr)
in <0x0003a> Gtk.OptionMenu:set_Menu (Gtk.Widget value)
in <0x002a4> FSpot.GoogleExport:PopulateGoogleOptionMenu (FSpot.GoogleAccountManager manager, FSpot.GoogleAccount changed_account)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_GoogleAccountManager_GoogleAccount (FSpot.GoogleAccountManager,FSpot.GoogleAccount)
in <0x00028> FSpot.GoogleAccountManager:MarkChanged (Boolean write, FSpot.GoogleAccount changed_account)
in <0x00024> FSpot.GoogleAccountManager:AddAccount (FSpot.GoogleAccount account, Boolean write)
in <0x0000f> FSpot.GoogleAccountManager:AddAccount (FSpot.GoogleAccount account)
in <0x0004d> FSpot.GoogleAccountDialog:HandleAddResponse (System.Object sender, Gtk.ResponseArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_ResponseArgs (object,Gtk.ResponseArgs)
in <0x00100> Gtk.Dialog:ResponseSignalCallback (IntPtr arg0, Int32 arg1, IntPtr gch)
in (wrapper native-to-managed) Gtk.Dialog:ResponseSignalCallback (intptr,int,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x00007> Gnome.Program:Run ()
in <0x007c0> FSpot.Driver:Main (System.String[] args)
.NET Version: 2.0.50727.42

Assembly Version Information:

Mono.Security (2.0.0.0)
System.Web (2.0.0.0)
System.Xml (2.0.0.0)
gnome-keyring-sharp (0.1.0.0)
FlickrNet (1.1.0.0)
google-sharp (0.1.0.0)
pango-sharp (2.8.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.8.0.0)
gtkhtml-sharp (2.8.0.0)
gconf-sharp (2.8.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
gdk-sharp (2.8.0.0)
gnome-vfs-sharp (2.8.0.0)
NDesk.DBus (0.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (0.0.0.0)
atk-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
f-spot (0.2.2.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.15-28-k7 i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

---

### Post by moeFinley on 2007-10-21
I can create albums but when it comes to uploading photos I get an error 400 from the server.  Is it just me?

---

### Post by flyfishin on 2007-10-24
I get random 400 error codes.  Some pictures upload just fine, others fail.  I was able to create a new album.

---

### Post by drunken_sapo on 2007-11-25
> **flyfishin said:**
> I get random 400 error codes.  Some pictures upload just fine, others fail.  I was able to create a new album.


Same here using f-spot 0,40 on ubuntu gutsy. I'm able to create albums and upload photos, but, from time to time I get random 400 errors. I wasn't able to determine any pattern in this. I'm pretty sure it isn't the names, nor the file sizes.
It would be great if someone could help us here.
Thanks in advance.

---

