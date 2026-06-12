---
title: "HELP ! Fatal Error with my Cowbell !"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-05-06
I got a fatal error message from my Cowbell, here are the details:

An unhandled exception was generated:

libglib-2.0.so
in (wrapper managed-to-native) Cowbell.Base.SafeUri:g_filename_from_uri (intptr,intptr,intptr)
in <0x00027> Cowbell.Base.SafeUri:UriToFilename (System.String uri)
in <0x000a6> Cowbell.Base.Filesystem:Import (System.String[] uris)
in <0x0004d> Cowbell.Gui.MainWindow:OnFileOpenActivate (System.Object o, System.EventArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventA rgs (object,System.EventArgs)
in <0x00093> GLib.Signal:voidObjectCallback (IntPtr handle, IntPtr gch)
in (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x00007> Cowbell.Gui.Gui:Show ()
in <0x00459> Cowbell.Runtime:Main (System.String[] args)

Version: 0.2.7
Runtime Version: 1.1.4322.2032
Assemblies:
gdk-sharp (2.8.0.0)
atk-sharp (2.8.0.0)
glade-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
System (1.0.5000.0)
System.Xml (1.0.5000.0)
glib-sharp (2.8.0.0)
cowbell (0.0.0.0)
mscorlib (1.0.5000.0)

How do I fix my CowBell?

:-({|=

---

### Post by Mustard on 2006-05-06
How did you install your Cowbell?

---

### Post by RAV TUX on 2006-05-07
[QUOTE=Mustard]How did you install your Cowbell?[/QUOTE]

with Synaptic Package Manager....it was working fine before.

---

### Post by Chasehead on 2006-05-07
I know your solution!

YOU NEED MORE COWBELL!!!

---

### Post by Mustard on 2006-05-07
Did it start happening after the recent security updates?

---

### Post by RAV TUX on 2006-05-08
[QUOTE=Mustard]Did it start happening after the recent security updates?[/QUOTE]


yes I think so, but I was also experimented with a number of software pakages and it may have been something I did on my part.

Last night I reloaded Ubuntu from scratch and set up a dual boot of Ubuntu and Kubuntu...just to experiment with KDE a bit. 

initial impression: I still like Gnome the best.

I think I will stick with what I have done in the past and run Gnome and enable a few KDE programs.

---

