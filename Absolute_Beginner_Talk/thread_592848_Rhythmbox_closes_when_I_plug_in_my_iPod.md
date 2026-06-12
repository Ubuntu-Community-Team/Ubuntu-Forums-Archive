---
title: "Rhythmbox closes when I plug in my iPod"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-10-26
I can run Rhythmbox without my iPod plugged in.  Then when I have Rhythmbox running and I plug in my iPod, Rhythmbox closes.

Any ideas?

---

### Post by MegaJim on 2007-10-26
start rhythmbox from a terminal and check out the error messages when it dies.

---

### Post by dmber on 2007-10-26
WHY???

now it works fine!

wow.

---

### Post by MegaJim on 2007-10-26
:guitar:

---

### Post by happydan on 2007-10-27
```
(rhythmbox:5600): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)
```

this is what i get when it crashes. its an ipod classic 80gb. any help would be appreciated

EDIT:
i get this when i try with hipo:

```
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GLib.GException: Icon 'multimedia-player-ipod-standard-monochrome' not present in theme
  at Gtk.IconTheme.LoadIcon (System.String icon_name, Int32 size, IconLookupFlags flags) [0x00000] 
  at Hipo.HipoMainWindow.GetDeviceIcon (IPod.Device device) [0x00000] 
  at Hipo.PlaylistView+<>c__CompilerGenerated4.<>c__AnonymousMethod13 (System.Object +13, System.EventArgs +14) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Gtk.Application+InvokeCB.Invoke () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 

   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Timeout+TimeoutProxy.Handler ()
   at GLib.Timeout+TimeoutProxy.Handler ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.Run ()
   at Gnome.Program.Run ()
   at Hipo.HipoMainWindow.CreateWindow ()
   at Hipo.HipoMain.Main ()
```

---

### Post by happydan on 2007-11-01
hey, can anyone help me on this? i dont want to have to resort to using itunes in windows! ive installed gutsy on a friends machine to ween her off microsoft and really need to prove to both her and myself this is a viable alternative...

---

### Post by eric p on 2007-11-01
try amarok

---

### Post by happydan on 2007-11-01
ok, i think i figured it out... i needed to register the ipod for it to work. now it just wont play back m4a files... im trying a different codec pack for that.

EDIT: sorry, m4b files.

---

### Post by varanasi on 2007-12-06
I'm having the same problem.  (I have an ipod mini running rockbox.)  How did you "register" your ipod?

---

### Post by varanasi on 2007-12-06
Got it.  I had to untick the ipod plugin in Rhythmbox and tick the mtp one.  

Having now played around with Rhythmbox a bit, I think I would rather use Nautilus and some other music player, since I have all my tunes and podcasts arranged in directories.

---

### Post by altonbr on 2008-01-03
Sorry, what do you have to do? I get this error:
> (rhythmbox:6989): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

I don't know what 'register my ipod' means and the MTP plugin isn't working :S

---

### Post by TWeerts on 2008-05-20
how do you register the ipod?

where can i find the option to "untick" the ipod plugin?

---

### Post by altonbr on 2008-05-20
> **TWeerts said:**
> how do you register the ipod?

where can i find the option to "untick" the ipod plugin?

As far as I know, you can only register your iPod through iTunes in Windows or on a Mac (unforuntately). This is people Apple only wants you to use their software and have encrypted their API (method of communicating with it) so you can't illegally register it.

Once that is done, iPod support is found in "Edit > Plugins" and should be enabled by default.

---

