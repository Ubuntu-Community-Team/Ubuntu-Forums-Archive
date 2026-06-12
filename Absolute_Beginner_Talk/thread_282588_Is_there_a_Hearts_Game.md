---
title: "Is there a Hearts Game?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by LostHere on 2006-10-23
I haven't installed Unbuntu yet. I'm wondering if there is an English language version of my favorite windows game, Hearts? I can't seem to find it searching linux forums, etc...If not, someone needs to create it ASAP.

Thanks

---

### Post by Sef on 2006-10-23
There was one that was being developed.  Not sure what the situation is now on it.

Update: [Hearts]("http://ubuntuforums.org/showthread.php?t=168699&highlight=hearts") thread.

Update 2: [Hearts]("http://www.jejik.com/hearts") for Gnome

---

### Post by ReaderRat on 2006-10-23
I searched the Synaptic Package Manager, and I did not find Hearts.
Sorry...

---

### Post by tubasoldier on 2006-10-23
> **LostHere said:**
> I haven't installed Unbuntu yet. I'm wondering if there is an English language version of my favorite windows game, Hearts? I can't seem to find it searching linux forums, etc...If not, someone needs to create it ASAP.

Thanks

There seems to be a few. I did not check Ubuntu repositories but at Sorceforge.net a search for hearts returns about five different choices. 

And if you are into Solitaire check out PySol. It has every solitaire type game you can think of. It is totally sweet. And it has sound and mulitple card decks. 

Good Luck! Hope this helps!

---

### Post by aysiu on 2006-10-23
*gnome-hearts* will be in the Universe repositories as of Edgy (to be released this Thursday). If you have no idea what the hell that means, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In the meantime, try this: ```
wget -c http://www.jejik.com/files/gnome-hearts/gnome-hearts_0.1.2-1_i386.deb
sudo dpkg -i gnome-hearts_0.1.2-1_i386.deb
```

---

### Post by Sef on 2006-10-23
> gnome-hearts will be in the Universe repositories as of Edgy 

Another reason to update to Edgy Eft.

---

### Post by ububug on 2006-10-25
Hearts crashes every time I try to start it. I had previously installed it from the package directly from [http://www.jejik.com/hearts/download](http://www.jejik.com/hearts/download) and it worked well. After upgrading to Edgy and installing gnome-hearts it just crashes with the following message from the Bug Buddy:
```

Memory status: size: 66486272 vsize: 0 resident: 66486272 share: 0 rss: 12636160 rss_rlim: 0
CPU usage: start_time: 1161825492 rtime: 0 utime: 62 stime: 0 cutime:58 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/games/gnome-hearts'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225070928 (LWP 11309)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb748634b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f621b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0804e068 in cards_image_set_size ()
#5  0x0804ec67 in on_configure_event ()
#6  0xb7a84b00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb755479b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#8  0xb7564b93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#9  0xb7565e7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#10 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#11 0xb7b985f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7a02240 in gtk_drawing_area_new () from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7561199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#14 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#15 0xb755487d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#16 0xb756502a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#17 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#18 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#19 0xb7b9d7ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7b941b2 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#21 0xb7561199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#22 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#23 0xb755487d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#24 0xb756502a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#25 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#26 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#27 0xb7b9d7ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7badb91 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb7561199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#30 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#31 0xb755479b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#32 0xb756502a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#33 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#34 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#35 0xb7b9d7ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#36 0xb79ef74c in gtk_container_resize_children ()
   from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb7baddf4 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb7561b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#39 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#40 0xb755479b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#41 0xb75651e3 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#42 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#43 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#44 0xb79ef7e3 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#45 0xb79ef863 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb74daaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#47 0xb74dc802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#48 0xb74df7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#49 0xb74dfb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#50 0xb7a7f574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#51 0x08051f42 in main ()

Thread 1 (Thread -1225070928 (LWP 11309)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb748634b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f621b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0804e068 in cards_image_set_size ()
No symbol table info available.
#5  0x0804ec67 in on_configure_event ()
No symbol table info available.
#6  0xb7a84b00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb755479b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb7564b93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb7565e7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb7b985f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7a02240 in gtk_drawing_area_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7561199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb755487d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb756502a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb7b9d7ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0xb7b941b2 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0xb7561199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#23 0xb755487d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb756502a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb7b9d7ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#28 0xb7badb91 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#29 0xb7561199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#31 0xb755479b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#32 0xb756502a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#33 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb7b9d7ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#36 0xb79ef74c in gtk_container_resize_children ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#37 0xb7baddf4 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0xb7561b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0xb7552fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#40 0xb755479b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#41 0xb75651e3 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#42 0xb75660b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#43 0xb7566279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#44 0xb79ef7e3 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#45 0xb79ef863 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0xb74daaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#47 0xb74dc802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#48 0xb74df7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#49 0xb74dfb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#50 0xb7a7f574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#51 0x08051f42 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

---

### Post by sander marechal on 2006-10-31
Hello there. I am the creator of gnome-hearts.

The game crashes at startup due to a last-minute cgange in the gnome-games-data package. The "Bonded" cardset used to be a PNG file but was replaced by an SVG file. Gnome Hearts uses the bonded.png file as a default cardset.

I am working on a 0.1.3 release that fixes this issue and makes sure the game will never crash on a missing cardset again (by falling back to another style). In the mean time you can change the default yourself. Open ~/.gnome-hearts.cfg in the text editor and replace the bonded.png card style with another card style - e.g. paris.svg. Then try starting gnome-hearts again.

> in the meantime, try this:
```
wget -c http://www.jejik.com/files/gnome-hearts/gnome-hearts_0.1.2-1_i386.deb
sudo dpkg -i gnome-hearts_0.1.2-1_i386.deb
```

For Dapper people, it would probably be better to simply add my personal repository to your sources.list so you get automated updates. See [my repositories page](http://www.jejik.com/pages/repositories/) for more details. The short version:

```

## Lone Wolves APT Repository
deb http://packages.jejik.com/ubuntu dapper main
deb-src http://packages.jejik.com/ubuntu dapper main

```

---

### Post by Toddy on 2006-10-31
Thanks Sander.  Changing bonded.png to bonded.svg got Hearts working on my Edgy install.  I was wondering why I Hearts wouldn't run when I migrated to Edgy.

---

### Post by sander marechal on 2006-11-06
Gnome Hearts 0.1.3 is out which permanenty fixes this bug. Dapper people should see it automatically if they use my repository. If not, then you can download it at [http://www.gnome-hearts.org/download](http://www.gnome-hearts.org/download)

I have no idea when it will appear in Edgy. I undestand a temporary fix has been committed but I hope they replace it with 0.1.3 because the temporary fix isn't very nice (it causes two SVG cardsets to load. It works, but with 10+ seconds to load an SVG set om my AMD64 it's not very nice to users on slow systems).

---

### Post by aum11 on 2007-01-01
Thanks for hearts coming to Ubuntu.  

However, have been unable to get hearts working under edgy with either of the 2 edits suggested here...that is changing this file:
/usr/share/gnome-hearts/gnome-hearts.cfg

so that bonded.png was changed to either bonded.svg or paris.svg.

What needs to change here for it to work?

Thanks.

---

### Post by aum11 on 2007-01-02
Any help for this please?

---

### Post by sander marechal on 2007-01-08
After you edit /usr/share/gnome-hearts/gnome-hearts.cfg you should delete ~/.gnome-hearts.cfg. When you start hearts, it will copy the new cfg file from /usr/share/gnome-hearts to your home directory, containing your edits.

---

### Post by aum11 on 2007-01-08
Thanks so much Sander...that did the trick.
Thanks for Your good work with the creation of Hearts under Ubuntu...nice to have it back again.

---

### Post by mahiyar on 2007-01-14
Instead of changing and fiddling all the config files I installed the 0.13 version, I hope that when edgy repositories are updated, I do not run into conflicts. BTW great programme and great card design, love it. Keep up the good work.

---

### Post by sander marechal on 2007-01-14
> **mahiyar said:**
> BTW great programme and great card design, love it. Keep up the good work.

Thanks, but the design is not mine. I'm simply re-using the gnome-games cardsets and backgrounds. I hope I can have someone finish the set below for me someday. I'm not a good enough artist to do it myself.

[img]http://www.jejik.com/images/hearts/hearts_bling.png[/img]

---

