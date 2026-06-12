---
title: "How do I run Envy?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-21
I downloaded and unpacked it to my Home>User folder but how do I run it?

---

### Post by Daveth on 2007-07-21
have a read of 

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by ukulele_ninja on 2007-07-21
I tried that but it doesnt work, can anyone translate?

---

### Post by aysiu on 2007-07-21
Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb
sudo dpkg -i envy_0.9.6-0ubuntu2_all.deb
sudo apt-get install -f
sudo envy -g
```

---

### Post by Skidpad on 2007-07-21
If you downloaded the .deb package, all you need to do is double-click on it, and it will begin the installation process.

---

### Post by aysiu on 2007-07-21
> **Skidpad said:**
> If you downloaded the .deb package, all you need to do is double-click on it, and it will begin the installation process.
But it will be missing dependencies, won't it?

---

### Post by ukulele_ninja on 2007-07-21
> **aysiu said:**
> Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb
sudo dpkg -i envy_0.9.6-0ubuntu2_all.deb
sudo apt-get install -f
sudo envy -g
```




Heres what my result was..... It didnt work :(





ryan@Ted:~$ wget -c [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0u](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0u)
buntu2_all.deb
--09:29:35--  [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2)
_all.deb
           => `envy_0.9.6-0ubuntu2_all.deb'
Resolving albertomilone.com... 68.178.232.90
Connecting to albertomilone.com|68.178.232.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 456,032 (445K) [text/plain]

100%[====================================>] 456,032      141.90K/s    ETA 00:00

09:29:38 (141.23 KB/s) - `envy_0.9.6-0ubuntu2_all.deb' saved [456032/456032]

ryan@Ted:~$ sudo dpkg -i envy_0.9.6-0ubuntu2_all.deb
Password:
Selecting previously deselected package envy.
(Reading database ... 114859 files and directories currently installed.)
Unpacking envy (from envy_0.9.6-0ubuntu2_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on python-vte; however:
  Package python-vte is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
ryan@Ted:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxul-common libnspr4-0d libxul0d gstreamer0.10-x libmozjs0d libnss3-0d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  debhelper dh-make dpatch fakeroot gettext html2text intltool-debian
  module-assistant po-debconf python-vte xserver-xorg-dev
Suggested packages:
  curl cvs gettext-doc python-vte-dbg
Recommended packages:
  patchutils libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  debhelper dh-make dpatch fakeroot gettext html2text intltool-debian
  module-assistant po-debconf python-vte xserver-xorg-dev
0 upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 3147kB of archives.
After unpacking 12.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main python-vte 1:0.16.1-0ubuntu1 [156
kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main xserver-xorg-dev 2:1.2.0-3ubuntu8
 [296kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe module-assistant 0.10.10 [88.
5kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main fakeroot 1.5.10ubuntu2 [101kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main html2text 1.3.2a-3 [115kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gettext 0.16.1-1ubuntu2 [1616kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main intltool-debian 0.35.0+20060710.1
 [31.6kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main po-debconf 1.0.8 [111kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main debhelper 5.0.42ubuntu1 [514kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main dh-make 0.42 [33.6kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main dpatch 2.0.21 [84.3kB]
Fetched 3147kB in 33s (93.8kB/s)
Selecting previously deselected package python-vte.
(Reading database ... 115067 files and directories currently installed.)
Unpacking python-vte (from .../python-vte_1%3a0.16.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-dev.
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.2.0-3ubuntu8_amd64.d
eb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.10_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.5.10ubuntu2_amd64.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_amd64.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-1ubuntu2_amd64.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) .
..
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.8_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.42ubuntu1_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../archives/dh-make_0.42_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.21_all.deb) ...
Setting up python-vte (0.16.1-0ubuntu1) ...

Setting up xserver-xorg-dev (1.2.0-3ubuntu8) ...
Setting up module-assistant (0.10.10) ...
Setting up fakeroot (1.5.10ubuntu2) ...

Setting up html2text (1.3.2a-3) ...

Setting up gettext (0.16.1-1ubuntu2) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.8) ...
Setting up debhelper (5.0.42ubuntu1) ...
Setting up dh-make (0.42) ...
Setting up dpatch (2.0.21) ...
Setting up envy (0.9.6-0ubuntu2) ...
ryan@Ted:~$ sudo envy -g
true
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could
not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/share/envy/gtkenvy.py:58: Warning: invalid (NULL) pointer instance
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: Warning: g_signal_connect_data: assertion `G_TYPE
_CHECK_INSTANCE (instance)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_widget_grab_default: assertion `G
TK_WIDGET_CAN_DEFAULT (widget)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: Screen for GtkWindow not set; you mus
t always set
a screen for a GtkWindow before using the window
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_pango_context_get_for_screen: ***
ertion `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_context_set_font_description:
 assertion `context != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_context_set_base_dir: asserti
on `context != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_context_set_language: asserti
on `context != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_new: assertion `contex
t != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_set_text: assertion `l
ayout != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_set_attributes: assert
ion `layout != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_set_alignment: asserti
on `layout != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_set_ellipsize: asserti
on `PANGO_IS_LAYOUT (layout)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_set_single_paragraph_m
ode: assertion `PANGO_IS_LAYOUT (layout)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_set_width: assertion `
layout != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: PangoWarning: pango_layout_get_extents: assertion
 `layout != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_screen_get_display: assertion `GD
K_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_display_get_pointer: assertion `G
DK_IS_DISPLAY (display)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_screen_get_n_monitors: assertion
`GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_screen_get_monitor_geometry: asse
rtion `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_screen_get_default_colormap: asse
rtion `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_colormap_get_visual: assertion `G
DK_IS_COLORMAP (colormap)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_screen_get_root_window: assertion
 `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_new: assertion `GDK_IS_WIN
DOW (parent)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_enable_synchronized_config
ure: assertion `GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_user_data: assertion `
window != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_style_attach: assertion `window !
= NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_style_set_background: assertion `
GTK_IS_STYLE (style)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_paint_flat_box: assertion `GTK_IS
_STYLE (style)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_type_hint: assertion `
GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_accept_focus: assertio
n `GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_focus_on_map: assertio
n `GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_modal_hint: assertion
`GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_window_realize_icon: assertion `w
idget->window != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_geometry_hints: assert
ion `GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_move: assertion `GDK_IS_WI
NDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: Warning: g_object_ref: assertion `G_IS_OBJECT (ob
ject)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_invalidate_rect: assertion
 `window != NULL' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_unmaximize: assertion `GDK
_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_unstick: assertion `GDK_IS
_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_deiconify: assertion `GDK_
IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_unfullscreen: assertion `G
DK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_keep_above: assertion
`GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_set_keep_below: assertion
`GDK_IS_WINDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_window_show: assertion `GDK_IS_WI
NDOW (window)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_settings_get_for_screen: assertio
n `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gdk_cursor_new_for_display: assertion
 `GDK_IS_DISPLAY (display)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: Warning: g_object_get: assertion `G_IS_OBJECT (ob
ject)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: gtk_window_set_screen: assertion `GDK
_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
/usr/share/envy/gtkenvy.py:58: GtkWarning: Ignoring the separator setting
  self.wTree = gtk.glade.XML(self.gladefile)

(gtkenvy.py:9964): libglade-WARNING **: could not find a parent that handles int
ernal children for `vbox'

(gtkenvy.py:9964): libglade-WARNING **: could not find a parent that handles int
ernal children for `vbox'

(gtkenvy.py:9964): libglade-WARNING **: could not find a parent that handles int
ernal children for `vbox'

(gtkenvy.py:9964): libglade-WARNING **: could not find a parent that handles int                                                              ernal children for `vbox'

(gtkenvy.py:9964): libglade-WARNING **: could not find a parent that handles int                                                              ernal children for `vbox'
/usr/share/envy/gtkenvy.py:136: GtkWarning: gtk_settings_get_for_screen: asserti                                                              on `GDK_IS_SCREEN (screen)' failed
  self.term = vte.Terminal()
/usr/share/envy/gtkenvy.py:503: GtkWarning: Screen for GtkWindow not set; you mu                                                              st always set
a screen for a GtkWindow before using the window
  gtk.main()
/usr/share/envy/gtkenvy.py:503: GtkWarning: gdk_screen_get_display: assertion `G                                                              DK_IS_SCREEN (screen)' failed
  gtk.main()
/usr/share/envy/gtkenvy.py:503: GtkWarning: gdk_keymap_get_for_display: assertio                                                              n `GDK_IS_DISPLAY (display)' failed
  gtk.main()
/usr/share/envy/gtkenvy.py:503: Warning: invalid (NULL) pointer instance
  gtk.main()
/usr/share/envy/gtkenvy.py:503: Warning: g_signal_connect_data: assertion `G_TYP                                                              E_CHECK_INSTANCE (instance)' failed
  gtk.main()

---

### Post by ukulele_ninja on 2007-07-21
> **Skidpad said:**
> If you downloaded the .deb package, all you need to do is double-click on it, and it will begin the installation process.

I unpacked it but when you click the deb file it opens up Kate but that is in it is 2.0

---

### Post by pndragon on 2007-07-21
> **ukulele_ninja said:**
> I unpacked it but when you click the deb file it opens up Kate but that is in it is 2.0
For Kubuntu:

Install Gdebi.

Right click>Open With>Other>Gdebi

---

### Post by ukulele_ninja on 2007-07-21
How do I get the Gdebi program?

---

### Post by pndragon on 2007-07-21
sudo apt-get install gdebi

---

### Post by Skidpad on 2007-07-21
> **aysiu said:**
> But it will be missing dependencies, won't it?
Good question, but the way I interpret Alberto's description of Envy, the .deb package resolves them automatically.
Take a look:

" [i]What is Envy?:

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (ATI and Nvidia cards are supported). However "Manual installation" is also available
2) download the right version of the proprietary driver for your ATI or Nvidia card from ATI or Nvidia's websites
3) handle the dependencies (compilers, OpenGL, etc.) (according to your OS version and kernel) required to build the module
4) install/uninstall the driver
5) set up your xorg.conf (i.e. the configuration file of the Xserver) for you (according to your system specifications)
6) restart the Xserver for you (if you wish so) (this feature is available only in the textual interface)[/i]"

#3 is what I was looking at.  So, I just downloaded the .deb and started installing it.  It checked for dependencies - mine were all satisfied.  
So if #3 above is true, and my dependencies weren't met, it would satisfy them...can't say for sure though.

Regardless, your terminal command(s) solves them.  Thanks.

---

### Post by ukulele_ninja on 2007-07-21
I thought this was supposed to make beryl run properly... it still just makes my windows boarders dissapear... the system icon tray appears now but I dont know what any of the editing things mean when you try configure it.

---

### Post by ukulele_ninja on 2007-07-21
How do I check to see if it worked properly?

---

### Post by pndragon on 2007-07-21
If it worked properly, when you restarted your xserver, you saw a Nvida logo.

If Beryl isn' t working properly, you've got other problems.

---

### Post by ukulele_ninja on 2007-07-22
I dont have Nvidida I have ATI

---

### Post by Frak on 2007-07-24
Just so you know, to install missing dependencies:
```
sudo apt-get -f install
```

---

