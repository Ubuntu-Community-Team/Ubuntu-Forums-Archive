---
title: "Fixing a broken package"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by wgw on 2007-03-28
(Disclaimer: newbie level 0, i.e two weeks into Ubuntu)

I got wifi-radar running smoothly, then did a reinstall of network manager. Now the wifi-radar window is not coming up (though on boot I connect to the wireless fine). 

So, in all likelyhood, installing network manager over wifi-radar has broken the latter. 

My question: what is the best way to repair a broken package? I could reinstall, but I'm a little worried that a reinstall might clobber some of my time-consuming configuration.

Network manager is supposed to be off -- I don't see it as a running process in system monitor. (In fact, that is probably why I was having trouble with it in the first place: the applet was running and appeared on the task bar, but nm itself was probably not running....)

Should I try a reinstall of wifi-radar? Should I backup anything before hand? 

Thanks for any suggestions.

---

### Post by dbbolton on 2007-03-28
try this :

```
sudo aptitude install -f
```

---

### Post by wgw on 2007-03-28
Thanks for the suggestion... I got some scary messages (see at end). 

The most scary among them is the removal of sysvinit. I have done that before, and I believe it broke my system (but got it back by booting from the cd and then apt-get sysinit). But maybe the upstart-compat-sysv replaces sysvinit?

If it breaks other packages,  I can always reinstall them. I suppose it is silly to think that the -f option is all about breaking packages rather than fixing them! 

I think I have talked mysefl into it. So here goes.




aptitude install -f output: 

The following packages are BROKEN:
  easycam gstreamer0.8-pitfdll gxineplugin j2re1.4 j2re1.4-mozilla-plugin 
  libxine-extracodecs skype 
The following NEW packages will be installed:
  startup-tasks system-services ubuntu-minimal upstart upstart-compat-sysv 
  upstart-logd 
The following packages will be REMOVED:
  camorama camstream cpp-3.4 gcc-3.4 gcc-3.4-base gsfonts-x11 
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad 
  gstreamer0.10-plugins-ugly gxine java-common liba52-0.7.4 libdvdread3 
  libgsm1 libgstreamer0.8-0 libid3tag0 libmad0 libmms0 libmodplug0c2 
  libmpcdec3 libmpeg2-4 libqt3-mt libsidplay1 libswfdec0.3 libwavpack0 
  libxine-main1 libxine1 libxvmc1 numlockx ogle ogle-gui p7zip sysvinit 
  unace wifi-radar 
0 packages upgraded, 6 newly installed, 36 to remove and 0 not upgraded.
Need to get 171kB of archives. After unpacking 41.0MB will be freed.
The following packages have unmet dependencies:
  gxineplugin: Depends: gxine (>= 0.5.0) but it is not installable
  libxine-extracodecs: Depends: libmad0 (>= 0.15.1b) but it is not installable
  j2re1.4-mozilla-plugin: Depends: gsfonts-x11 but it is not installable
  skype: Depends: libqt3-mt but it is not installable or
                  libqt3c102-mt (>= 3:3.3.3.2) which is a virtual package.
  j2re1.4: Depends: java-common but it is not installable
  easycam: Depends: gcc-3.4 but it is not installable
  gstreamer0.8-pitfdll: Depends: libgstreamer0.8-0 (>= 0.8.4) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
cpp-3.4 [3.4.6-3ubuntu1 (edgy, now)]
gcc-3.4 [3.4.6-3ubuntu1 (edgy, now)]
gcc-3.4-base [3.4.6-3ubuntu1 (edgy, now)]
gsfonts-x11 [0.20build1 (edgy, now)]
gxine [0.5.7-1ubuntu6 (edgy, now)]
java-common [0.25ubuntu1 (edgy, now)]
libgstreamer0.8-0 [0.8.12-2 (edgy, now)]
libmad0 [0.15.1b-2.1 (edgy, now)]
libmodplug0c2 [1:0.7-5 (edgy, now)]
libqt3-mt [3:3.3.6-3ubuntu3 (edgy, now)]
libxine1 [1.1.2+repacked1-0ubuntu3.4 (edgy-security, now)]
libxvmc1 [2:1.0.2-0ubuntu2 (edgy, now)]
p7zip [4.42.dfsg.1-2 (edgy, now)]

Leave the following dependencies unresolved:
rhythmbox recommends gstreamer0.10-plugins-ugly
Score is -787

---

### Post by wgw on 2007-03-28
It didn't break my system, but it did remove wifi-radar. I reinstalled but I still have the same problem. Here is the aptitude install -f output now:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  wifi-radar 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 213kB will be freed.
Do you want to continue? [Y/n/?] n


*Edit*
The wireless connection comes up even if the wifi-radar window does not

---

### Post by dbbolton on 2007-03-28
ok, do these commands in this order:
```
sudo aptitude autoclean
sudo aptitude purge wifi-radar
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install wifi-radar
```

---

### Post by wgw on 2007-03-29
Thanks for the suggestions. This is what I got when I autocleaned (eek!):

Del firefox-gnome-support 2.0.0.2+0dfsg-0ubuntu0.6.10 [83.8kB]
Del libnspr4 2:1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10 [158kB]
Del libnss3 2:1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10 [786kB]
Del firefox 2.0.0.2+0dfsg-0ubuntu0.6.10 [9225kB]
Del language-pack-en 1:6.10+20070115 [358kB]
Del language-pack-gnome-en 1:6.10+20070115 [342kB]
Del fuse-utils 2.6.3-0givre2 [77.5kB]
Del libntfs-3g0 1:1.0-1 [90.1kB]
Del ntfs-3g 1:1.0-1 [36.4kB]
Del ntfs-config 0.5.5-1 [43.1kB]
Del libfuse2 2.6.3-0givre2 [71.2kB]
Del pmount 0.9.13-1givre4 [74.0kB]
Del rar 3.30-2 [246kB]
Del p7zip 4.20-1 [1417kB]
Del unrar-nonfree 3.4.3-1build1 [85.3kB]
Del numlockx 1.0-17ubuntu1 [10.2kB]
Del nvidia-settings 1.0-3ubuntu6 [504kB]
Del java-common 0.23ubuntu3 [74.2kB]
Del gsfonts-x11 0.17ubuntu3 [9282B]
Del initscripts 2.86.ds1-1.1ubuntu6 [33.8kB]
Del sysvinit 2.86.ds1-1.1ubuntu6 [97.3kB]
Del libgstreamer0.8-0 0.8.11-1ubuntu1 [677kB]
Del gstreamer0.8-pitfdll 0.8.1-1ubuntu1 [56.4kB]


Then I reinstalled wifi-radar, and launching from terminal prompt I got all the error messages that are below. (I did gksudo as well: same result.)

Looks like something is very wrong!

 

b@b-laptop:~$ sudo wifi-radar
dhclient3 --version 2>&1
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/sbin/wifi-radar:692: Warning: invalid (NULL) pointer instance
  self.window = gtk.Dialog('WiFi Radar', None, gtk.DIALOG_MODAL )
/usr/sbin/wifi-radar:692: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.window = gtk.Dialog('WiFi Radar', None, gtk.DIALOG_MODAL )
/usr/sbin/wifi-radar:703: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.close_button = gtk.Button( "Close", gtk.STOCK_CLOSE )
/usr/sbin/wifi-radar:703: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  self.close_button = gtk.Button( "Close", gtk.STOCK_CLOSE )
/usr/sbin/wifi-radar:703: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  self.close_button = gtk.Button( "Close", gtk.STOCK_CLOSE )
/usr/sbin/wifi-radar:790: GtkWarning: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_new: assertion `context != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_set_attributes: assertion `layout != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_set_alignment: assertion `layout != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_set_width: assertion `layout != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: PangoWarning: pango_layout_get_extents: assertion `layout != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 10
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width -1191411 and height -1050097
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width 1 and height -1050085
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width -1191411 and height 0
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width -1191411 and height 1
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_enable_synchronized_configure: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_user_data: assertion `window != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_style_attach: assertion `window != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_style_set_background: assertion `GTK_IS_STYLE (style)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_paint_flat_box: assertion `GTK_IS_STYLE (style)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_type_hint: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_accept_focus: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_focus_on_map: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_modal_hint: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gtk_window_realize_icon: assertion `widget->window != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: Warning: g_object_ref: assertion `G_IS_OBJECT (object)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_back_pixmap: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: _gtk_tree_view_column_realize_button: assertion `tree_view->priv->header_window != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_drawable_get_display: assertion `GDK_IS_DRAWABLE (drawable)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_register_dnd: assertion `window != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_show: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_hide: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_invalidate_rect: assertion `window != NULL' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_unmaximize: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_unstick: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_deiconify: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_unfullscreen: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_keep_above: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:790: GtkWarning: gdk_window_set_keep_below: assertion `GDK_IS_WINDOW (window)' failed
  self.window.show_all()
/usr/sbin/wifi-radar:794: GtkWarning: gdk_window_invalidate_rect: assertion `window != NULL' failed
  self.disconnect_button.hide()
/usr/sbin/wifi-radar:794: GtkWarning: _gtk_style_peek_property_value: assertion `GTK_IS_STYLE (style)' failed
  self.disconnect_button.hide()
Segmentation fault (core dumped)

---

### Post by wgw on 2007-03-29
So, found one problem; must give the command: xhost +local:username

That allows me to bring up the wifi-radar screen. 

Now, I must go back and try to get the wireless connected. 

Not easy to fix packages!

---

### Post by dbbolton on 2007-03-29
that's crazy. i think you should probably file a bug report- only if you want to and have time.

---

### Post by wgw on 2007-03-30
Thanks for the suggestions. For the moment I don't know yet what part is buggy. Could be I simply need a startup option that will set the local host. 

So, more investigation, will have to deal with the wireless problem. Network Manager does not seem to be working, nor wifi-radar. I will go through systematically the how-to for wireless connections (again!)

Thanks for the pointers -- now at least my packages seem tidy!

---

### Post by wgw on 2007-03-30
A bit more information: the application does not launch properly (not without xhost +local) when I am logged in as myself, but will when I su to root. So, it is a permissions problem... which are yet another mystery. I will try a simple purge and reinstall of wifi-radar.

---

### Post by dbbolton on 2007-03-30
did you try launching it from Applications > Internet > WiFi Radar

---

### Post by wgw on 2007-03-30
Applications > Internet > WiFi Radar gives the same problem: no window.

---

### Post by dbbolton on 2007-03-30
that's definitely a bug. it should bring up the "start administrative process" prompt, like gksudo

---

### Post by wgw on 2007-03-31
Yep, a bug. I am going to continue to see how it works; i.e. where the problem lies. I know it is a permission problem -- no doubt a security "feature"! And no doubt some clever thing I did unwittingly.

The good news is that I finally got NetworkManager running. It now connects properly to my wireless; the fix was on Launchpad: gtk-update-icon-cache -f /usr/share/icons/hicolor/.

Thanks for following along; your reactions allowed me to believe I had not totally lost my mind! Still, I think I must have put a wrinkle in my installation at some point. 
Debugging it is going to teach me a lot about ubuntu -- the hard way! (I'd rather read a book...)

Again, thanks! (I will put the solution here, if I am able to track down the source of the problem.)

---

### Post by dbbolton on 2007-03-31
you're welcome.

and thank you for getting involved and not just throwing your hands in the air like so many do.

---

