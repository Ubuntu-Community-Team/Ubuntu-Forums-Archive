---
title: "HELP! splash screen manager"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by liberatetheking on 2007-06-19
Hi, i am brand new to Ubuntu and I think it is absolutely amazing. The only problem is that its confusing! Im trying to make my computer as a whole look all pretty but i cant seem to get the splash screens to work... I installed Gnome Splash Screen Manager, but whenever i try to run it and install a splash i get this error in the Terminal. 
```
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

```

I dont know if that is normal (unlikely) or not but whenever i do install a splash it doesnt show up at boot up so im guessing thats the problem. Any help is much appreciated, Thank You.

Viva La Linux!

---

### Post by testube_babies on 2007-06-19
These errors are to be expected and don't really mean anything.  Which splash screen are you trying to change?  gnome-splashscreen-manager is for the splash you see between logging in and the desktop, not the boot menu screen (GRUB splash) or the OS loading screen (Usplash).

---

### Post by liberatetheking on 2007-06-19
Hmmm thanks for the quick response and I did not know that. That solved it haha.
If its not too much trouble can you explain to me how to install and/or use Grub Splash and Usplash? Thank you.

---

### Post by testube_babies on 2007-06-19
Here's GRUB:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up)

Usplash can be a bit difficult to customize.  You can search synaptic for usplash images (the only options are the Ubuntu, Kubuntu, and Xubuntu splashes) and then change it according to these instructions:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_the_USplash_Screen_when_you_boot_or_shutdown_the_computer](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_the_USplash_Screen_when_you_boot_or_shutdown_the_computer)

---

### Post by liberatetheking on 2007-06-19
thanks again bro

Viva La Linux! hahaha

---

