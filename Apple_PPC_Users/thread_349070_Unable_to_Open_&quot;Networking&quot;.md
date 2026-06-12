---
title: "Unable to Open &quot;Networking&quot;"
date: 2007-01-29
forum: Apple PPC Users
---

### Post by jernomer on 2007-01-29
Hi,

I am very new to Linux, and I am unable to open Networking (System > Administration > Networking) - it keeps crashing on me. Therefore, no Internet. Any help? Thanks.

Here is the crash report (kind of long):

Memory status: size: 13807616 vsize: 0 resident: 40955904 share: 0 rss: 40955904 rss_rlim: 0
CPU usage: start_time: 179 rtime: 0 utime: 1170113529 stime: 0 cutime:78 cstime: 0 timeout: 71 it_real_value: 0 frequency: 7

Backtrace was generated from '/usr/bin/network-admin'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 805543248 (LWP 4727)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x0eb43334 in __waitpid_nocancel () from /lib/libpthread.so.0
#0  0x0eb43334 in __waitpid_nocancel () from /lib/libpthread.so.0
#1  0x0ff20d30 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#2  <signal handler called>
#3  0x0f1b6920 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#4  0x0f18a568 in g_hash_table_remove_all () from /usr/lib/libglib-2.0.so.0
#5  0x0f18b1f8 in g_hash_table_insert () from /usr/lib/libglib-2.0.so.0
#6  0x0fb5bb4c in pango_fc_font_map_get_type ()
   from /usr/lib/libpangoft2-1.0.so.0
#7  0x0f5a4758 in pango_font_map_load_fontset ()
   from /usr/lib/libpango-1.0.so.0
#8  0x0f5a2164 in pango_context_get_font_description ()
   from /usr/lib/libpango-1.0.so.0
#9  0x0f5a24d8 in pango_itemize_with_base_dir ()
   from /usr/lib/libpango-1.0.so.0
#10 0x0f5ac92c in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#11 0x0f5ad2d0 in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#12 0x0f8b6e00 in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#14 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#15 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#16 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#17 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#18 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#19 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#20 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#21 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#22 0x0f87ad78 in gtk_frame_new () from /usr/lib/libgtk-x11-2.0.so.0
#23 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#24 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#25 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#26 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#27 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#28 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#29 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#30 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#31 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#32 0x0fa1362c in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#33 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#34 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#35 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#36 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#37 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#38 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#39 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#40 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#41 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#42 0x0f8f3960 in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
#43 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#44 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#45 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#46 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#47 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#48 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#49 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#50 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#51 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#52 0x0fa1362c in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#53 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#54 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#55 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#56 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#57 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#58 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#59 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#60 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#61 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#62 0x0fa1362c in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#63 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#64 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#65 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#66 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#67 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#68 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#69 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#70 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#71 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#72 0x0fa285e4 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#73 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#74 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#75 0x0f3063bc in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#76 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#77 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#78 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#79 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#80 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#81 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#82 0x0fa28ba0 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#83 0x0fa33f4c in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#84 0x0f317190 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#85 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#86 0x0f3063bc in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#87 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#88 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#89 0x0f31bef8 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#90 0x0fa21a5c in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#91 0x10011234 in ?? ()
#92 0x0e9bc728 in __libc_init_first () from /lib/libc.so.6
#93 0x0e9bc728 in __libc_init_first () from /lib/libc.so.6
#94 0x0e9bc728 in __libc_init_first () from /lib/libc.so.6

Thread 1 (Thread 805543248 (LWP 4727)):
#0  0x0eb43334 in __waitpid_nocancel () from /lib/libpthread.so.0
No symbol table info available.
#1  0x0ff20d30 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0x0f1b6920 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0x0f18a568 in g_hash_table_remove_all () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0x0f18b1f8 in g_hash_table_insert () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0x0fb5bb4c in pango_fc_font_map_get_type ()
   from /usr/lib/libpangoft2-1.0.so.0
No symbol table info available.
#7  0x0f5a4758 in pango_font_map_load_fontset ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#8  0x0f5a2164 in pango_context_get_font_description ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#9  0x0f5a24d8 in pango_itemize_with_base_dir ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#10 0x0f5ac92c in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#11 0x0f5ad2d0 in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#12 0x0f8b6e00 in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#22 0x0f87ad78 in gtk_frame_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#23 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#30 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#31 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0x0fa1362c in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#36 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#38 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#41 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#42 0x0f8f3960 in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#43 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#44 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#45 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#46 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#47 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#48 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#49 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#50 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#51 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#52 0x0fa1362c in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#53 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#54 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#55 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#56 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#57 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#58 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#59 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#60 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#61 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#62 0x0fa1362c in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#63 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#64 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#65 0x0f3064d4 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#66 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#67 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#68 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#69 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#70 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#71 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#72 0x0fa285e4 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#73 0x0f31655c in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#74 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#75 0x0f3063bc in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#76 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#77 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#78 0x0f31eee0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#79 0x0f94a70c in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#80 0x0f94aa18 in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#81 0x0fa2030c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#82 0x0fa28ba0 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#83 0x0fa33f4c in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#84 0x0f317190 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#85 0x0f3045cc in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#86 0x0f3063bc in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#87 0x0f31a6ac in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#88 0x0f31bd2c in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#89 0x0f31bef8 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#90 0x0fa21a5c in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#91 0x10011234 in ?? ()
No symbol table info available.
#92 0x0e9bc728 in __libc_init_first () from /lib/libc.so.6
No symbol table info available.
#93 0x0e9bc728 in __libc_init_first () from /lib/libc.so.6
No symbol table info available.
#94 0x0e9bc728 in __libc_init_first () from /lib/libc.so.6
No symbol table info available.
#0  0x0eb43334 in __waitpid_nocancel () from /lib/libpthread.so.0

---

