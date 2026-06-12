---
title: "Shall I install this or not :O"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Matthew83 on 2006-04-22
Hello community, 
I am perplexed. I'd need to install the 'ligtk2.0-dev' package from Synaptic but it warns me that the installation will automatically disinstall several packets such as:  

x-window-system-core
xorg-common
xorg-driver
[...]
xserver-common
xserver-driver-synaptics
xserver-xorg
xserver-xorg-core
and so on
...

Actually I'm a bit worried about what the consequences might be.
Can anybody assure me I can proceed fearless :D ? 

thank you

---

### Post by Qrk on 2006-04-22
Is this package in the breezy repositories or is it in some others that you may have added? 

Is the package really *ligtk2.0-dev* or is it *libgtk2.0-dev*?

At any rate, don't intall it, xorg is the part of ubuntu that makes the graphical interface. See if libgtk2.0-dev, which is probably the one you want to install, has the same problems.

---

### Post by Mustard on 2006-04-22
You definitely DON'T want to proceed with that. :)

---

### Post by mostwanted on 2006-04-22
Gtk is a GUI toolkit. If you don't have a graphical environment why would you want to install it anyway?

---

### Post by Matthew83 on 2006-04-22
Here i am :)
Sorry, it's libgtk2.0-dev.
The problem is that I executed 'make install' in the /gtk directory of Ethereal packag because i wanna write a gtktap for it but it gave me lots of errors, the first of which is 'cannote find gtk.h'. Then I thought I had to install libgtk2.0-dev which contained the headers I needed.

what should I do :(?

---

### Post by mostwanted on 2006-04-22
forget it :)

Honestly, I don't know. Can you give us the exact message it's giving you?

---

### Post by Matthew83 on 2006-04-22
[QUOTE=mostwanted]forget it :)

Honestly, I don't know. Can you give us the exact message it's giving you?[/QUOTE]


Here is the result of make install :(

> 
about_dlg.c:30:21: error: gtk/gtk.h: No such file or directory
In file included from about_dlg.c:32:
../epan/filesystem.h:105: error: syntax error before &#8216;gboolean&#8217;
../epan/filesystem.h:116: error: syntax error before &#8216;deletefile&#8217;
../epan/filesystem.h:116: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;del etefile&#8217;
../epan/filesystem.h:116: warning: data definition has no type or storage class
../epan/filesystem.h:122: error: syntax error before &#8216;gboolean&#8217;
../epan/filesystem.h:133: error: syntax error before &#8216;file_exists&#8217;
../epan/filesystem.h:133: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;fil e_exists&#8217;
../epan/filesystem.h:133: warning: data definition has no type or storage class
../epan/filesystem.h:138: error: syntax error before &#8216;files_identical&#8217;
../epan/filesystem.h:138: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;fil es_identical&#8217;
../epan/filesystem.h:138: warning: data definition has no type or storage class
In file included from about_dlg.c:34:
about_dlg.h:38: error: syntax error before &#8216;*&#8217; token
about_dlg.h:38: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;splash_new&#8217;
about_dlg.h:38: warning: data definition has no type or storage class
about_dlg.h:45: error: syntax error before &#8216;*&#8217; token
about_dlg.h:52: error: syntax error before &#8216;*&#8217; token
about_dlg.h:59: error: syntax error before &#8216;*&#8217; token
In file included from about_dlg.c:35:
ui_util.h:106: error: syntax error before &#8216;*&#8217; token
ui_util.h:106: error: syntax error before &#8216;type&#8217;
ui_util.h:106: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;window_new&#8217;
ui_util.h:106: warning: data definition has no type or storage class
ui_util.h:116: error: syntax error before &#8216;*&#8217; token
ui_util.h:116: error: syntax error before &#8216;type&#8217;
ui_util.h:116: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;window_new_wit h_geom&#8217;
ui_util.h:116: warning: data definition has no type or storage class
ui_util.h:122: error: syntax error before &#8216;*&#8217; token
ui_util.h:122: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;splash_window_ new&#8217;
ui_util.h:122: warning: data definition has no type or storage class
ui_util.h:129: error: syntax error before &#8216;*&#8217; token
ui_util.h:132: error: syntax error before &#8216;*&#8217; token
ui_util.h:142: error: syntax error before &#8216;*&#8217; token
ui_util.h:149: error: syntax error before &#8216;*&#8217; token
ui_util.h:155: error: syntax error before &#8216;*&#8217; token
ui_util.h:161: error: syntax error before &#8216;*&#8217; token
ui_util.h:183: error: syntax error before &#8216;*&#8217; token
ui_util.h:190: error: syntax error before &#8216;*&#8217; token
ui_util.h:215: error: syntax error before &#8216;*&#8217; token
ui_util.h:226: error: syntax error before &#8216;*&#8217; token
ui_util.h:226: error: syntax error before &#8216;*&#8217; token
ui_util.h:227: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;scrolled_windo w_new&#8217;
ui_util.h:227: warning: data definition has no type or storage class
ui_util.h:240: error: syntax error before &#8216;*&#8217; token
ui_util.h:240: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;ctree_new&#8217;
ui_util.h:240: warning: data definition has no type or storage class
ui_util.h:248: error: syntax error before &#8216;*&#8217; token
ui_util.h:249: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;ctree_new_with _titles&#8217;
ui_util.h:249: warning: data definition has no type or storage class
ui_util.h:264: error: syntax error before &#8216;*&#8217; token
ui_util.h:264: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;simple_list_ne w&#8217;
ui_util.h:264: warning: data definition has no type or storage class
ui_util.h:270: error: syntax error before &#8216;*&#8217; token
ui_util.h:283: error: syntax error before &#8216;*&#8217; token
ui_util.h:283: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;xpm_to_widget&#8217;
ui_util.h:283: warning: data definition has no type or storage class
ui_util.h:292: error: syntax error before &#8216;*&#8217; token
ui_util.h:292: error: syntax error before &#8216;*&#8217; token
ui_util.h:292: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;xpm_to_widget_ from_parent&#8217;
ui_util.h:292: warning: data definition has no type or storage class
In file included from about_dlg.c:36:
dlg_utils.h:98: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:98: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;dlg_window_ne w&#8217;
dlg_utils.h:98: warning: data definition has no type or storage class
dlg_utils.h:115: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:115: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;file_selecti on_new&#8217;
dlg_utils.h:115: warning: data definition has no type or storage class
dlg_utils.h:123: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:131: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:145: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:169: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:169: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;dlg_button_r ow_new&#8217;
dlg_utils.h:169: warning: data definition has no type or storage class
dlg_utils.h:178: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:182: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:183: error: syntax error before &#8216;GtkAccelGroup&#8217;
dlg_utils.h:183: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;dlg_radio_bu tton_new_with_label_with_mnemonic&#8217;
dlg_utils.h:183: warning: data definition has no type or storage class
dlg_utils.h:185: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:186: error: syntax error before &#8216;GtkAccelGroup&#8217;
dlg_utils.h:186: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;dlg_check_bu tton_new_with_label_with_mnemonic&#8217;
dlg_utils.h:186: warning: data definition has no type or storage class
dlg_utils.h:188: error: syntax error before &#8216;*&#8217; token
dlg_utils.h:189: error: syntax error before &#8216;GtkAccelGroup&#8217;
dlg_utils.h:189: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;dlg_toggle_b utton_new_with_label_with_mnemonic&#8217;
dlg_utils.h:189: warning: data definition has no type or storage class
In file included from about_dlg.c:46:
gtkglobals.h:43: error: syntax error before &#8216;*&#8217; token
gtkglobals.h:43: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;top_level&#8217;
gtkglobals.h:43: warning: data definition has no type or storage class
gtkglobals.h:46: error: syntax error before &#8216;*&#8217; token
gtkglobals.h:46: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;packet_list&#8217;
gtkglobals.h:46: warning: data definition has no type or storage class
gtkglobals.h:49: error: syntax error before &#8216;*&#8217; token
gtkglobals.h:49: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;tree_view&#8217;
gtkglobals.h:49: warning: data definition has no type or storage class
gtkglobals.h:52: error: syntax error before &#8216;*&#8217; token
gtkglobals.h:52: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;byte_nb_ptr&#8217;
gtkglobals.h:52: warning: data definition has no type or storage class
gtkglobals.h:55: error: syntax error before &#8216;*&#8217; token
gtkglobals.h:55: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;main_display _filter_widget&#8217;
gtkglobals.h:55: warning: data definition has no type or storage class
about_dlg.c:51: error: syntax error before &#8216;*&#8217; token
about_dlg.c:51: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;about_plugins _page_new&#8217;
about_dlg.c:51: warning: data definition has no type or storage class
about_dlg.c:54: error: syntax error before &#8216;*&#8217; token
about_dlg.c:63: error: syntax error before &#8216;*&#8217; token
about_dlg.c:63: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;about_etherea l_w&#8217;
about_dlg.c:63: warning: data definition has no type or storage class
about_dlg.c:67: error: syntax error before &#8216;*&#8217; token
about_dlg.c: In function &#8216;about_ethereal&#8217;:
about_dlg.c:69: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
about_dlg.c:69: error: (Each undeclared identifier is reported only once
about_dlg.c:69: error: for each function it appears in.)
about_dlg.c:69: error: &#8216;msg_label&#8217; undeclared (first use in this function)
about_dlg.c:69: error: &#8216;icon&#8217; undeclared (first use in this function)
about_dlg.c:69: warning: left-hand operand of comma expression has no effect
about_dlg.c:69: warning: statement with no effect
about_dlg.c:74: error: &#8216;parent&#8217; undeclared (first use in this function)
about_dlg.c:75: warning: implicit declaration of function &#8216;gtk_container_add&#8217;
about_dlg.c:75: warning: implicit declaration of function &#8216;GTK_CONTAINER&#8217;
about_dlg.c:75: error: &#8216;main_vb&#8217; undeclared (first use in this function)
about_dlg.c:77: warning: implicit declaration of function &#8216;gtk_label_new&#8217;
about_dlg.c:77: error: &#8216;title&#8217; undeclared (first use in this function)
about_dlg.c: At top level:
about_dlg.c:87: error: syntax error before &#8216;*&#8217; token
about_dlg.c:89: warning: return type defaults to &#8216;int&#8217;
about_dlg.c: In function &#8216;splash_new&#8217;:
about_dlg.c:90: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
about_dlg.c:90: error: &#8216;win&#8217; undeclared (first use in this function)
about_dlg.c:91: error: &#8216;main_lb&#8217; undeclared (first use in this function)
about_dlg.c:93: error: &#8216;main_vb&#8217; undeclared (first use in this function)
about_dlg.c:101: warning: implicit declaration of function &#8216;gtk_widget_realize&#8217;
about_dlg.c:103: warning: implicit declaration of function &#8216;gtk_vbox_new&#8217;
about_dlg.c:104: warning: implicit declaration of function &#8216;gtk_container_border _width&#8217;
about_dlg.c:111: warning: implicit declaration of function &#8216;gtk_object_set_data&#8217;
about_dlg.c:111: warning: implicit declaration of function &#8216;GTK_OBJECT&#8217;
about_dlg.c:113: warning: implicit declaration of function &#8216;gtk_widget_show_all&#8217;
about_dlg.c: At top level:
about_dlg.c:121: error: syntax error before &#8216;*&#8217; token
about_dlg.c: In function &#8216;splash_update&#8217;:
about_dlg.c:123: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
about_dlg.c:123: error: &#8216;main_lb&#8217; undeclared (first use in this function)
about_dlg.c:125: error: &#8216;win&#8217; undeclared (first use in this function)
about_dlg.c:127: warning: implicit declaration of function &#8216;gtk_object_get_data&#8217;
about_dlg.c:128: warning: implicit declaration of function &#8216;gtk_label_set_text&#8217;
about_dlg.c:128: warning: implicit declaration of function &#8216;GTK_LABEL&#8217;
about_dlg.c:128: error: &#8216;message&#8217; undeclared (first use in this function)
about_dlg.c:132: warning: implicit declaration of function &#8216;gtk_events_pending&#8217;
about_dlg.c:132: warning: implicit declaration of function &#8216;gtk_main_iteration&#8217;
about_dlg.c: At top level:
about_dlg.c:136: error: syntax error before &#8216;*&#8217; token
about_dlg.c: In function &#8216;splash_destroy&#8217;:
about_dlg.c:138: error: &#8216;win&#8217; undeclared (first use in this function)
about_dlg.c:140: warning: implicit declaration of function &#8216;gtk_widget_destroy&#8217;
about_dlg.c: At top level:
about_dlg.c:145: error: syntax error before &#8216;*&#8217; token
about_dlg.c:147: warning: return type defaults to &#8216;int&#8217;
about_dlg.c: In function &#8216;about_ethereal_page_new&#8217;:
about_dlg.c:148: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
about_dlg.c:148: error: &#8216;main_vb&#8217; undeclared (first use in this function)
about_dlg.c:148: error: &#8216;msg_label&#8217; undeclared (first use in this function)
about_dlg.c:148: warning: left-hand operand of comma expression has no effect
about_dlg.c:148: warning: statement with no effect
about_dlg.c:174: warning: implicit declaration of function &#8216;gtk_label_set_justif y&#8217;
about_dlg.c:174: error: &#8216;GTK_JUSTIFY_FILL&#8217; undeclared (first use in this functio n)
about_dlg.c: At top level:
about_dlg.c:198: error: syntax error before &#8216;*&#8217; token
about_dlg.c: In function &#8216;about_folders_row&#8217;:
about_dlg.c:200: error: &#8216;table&#8217; undeclared (first use in this function)
about_dlg.c:200: error: &#8216;label&#8217; undeclared (first use in this function)
about_dlg.c:200: error: &#8216;dir&#8217; undeclared (first use in this function)
about_dlg.c:200: error: &#8216;tip&#8217; undeclared (first use in this function)
about_dlg.c: At top level:
about_dlg.c:204: error: syntax error before &#8216;*&#8217; token
about_dlg.c:206: warning: return type defaults to &#8216;int&#8217;
about_dlg.c: In function &#8216;about_folders_page_new&#8217;:
about_dlg.c:207: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
about_dlg.c:207: error: &#8216;table&#8217; undeclared (first use in this function)
about_dlg.c:211: error: &#8216;scrolledwindow&#8217; undeclared (first use in this function)
about_dlg.c: At top level:
about_dlg.c:276: error: syntax error before &#8216;*&#8217; token
about_dlg.c:280: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:280: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;about_page&#8217;
about_dlg.c:280: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;folders_page &#8217;
about_dlg.c:280: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;plugins_page &#8217;
about_dlg.c:280: warning: data definition has no type or storage class
about_dlg.c:285: error: syntax error before &#8216;if&#8217;
about_dlg.c:297: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;about_ethere al_w&#8217;
about_dlg.c:297: error: conflicting types for &#8216;about_ethereal_w&#8217;
about_dlg.c:63: error: previous declaration of &#8216;about_ethereal_w&#8217; was here
about_dlg.c:297: warning: initialization makes integer from pointer without a ca st
about_dlg.c:297: error: initializer element is not constant
about_dlg.c:297: warning: data definition has no type or storage class
about_dlg.c:303: error: syntax error before &#8216;(&#8217; token
about_dlg.c:303: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_window_s et_position&#8217;
about_dlg.c:303: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;GTK_WIN_POS_ CENTER&#8217;
about_dlg.c:303: error: syntax error before &#8216;)&#8217; token
about_dlg.c:308: error: syntax error before &#8216;(&#8217; token
about_dlg.c:308: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_containe r_border_width&#8217;
about_dlg.c:310: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;main_vb&#8217;
about_dlg.c:310: error: initializer element is not constant
about_dlg.c:310: warning: data definition has no type or storage class
about_dlg.c:311: error: syntax error before &#8216;(&#8217; token
about_dlg.c:311: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_containe r_border_width&#8217;
about_dlg.c:312: error: syntax error before &#8216;(&#8217; token
about_dlg.c:312: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_containe r_add&#8217;
about_dlg.c:312: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;main_vb&#8217;
about_dlg.c:312: error: syntax error before &#8216;)&#8217; token
about_dlg.c:314: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;main_nb&#8217;
about_dlg.c:314: warning: implicit declaration of function &#8216;gtk_notebook_new&#8217;
about_dlg.c:314: error: initializer element is not constant
about_dlg.c:314: warning: data definition has no type or storage class
about_dlg.c:315: error: syntax error before &#8216;(&#8217; token
about_dlg.c:315: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_box_pack _start&#8217;
about_dlg.c:315: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;main_nb&#8217;
about_dlg.c:315: error: syntax error before &#8216;!&#8217; token
about_dlg.c:317: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;about_page&#8217;
about_dlg.c:317: error: conflicting types for &#8216;about_page&#8217;
about_dlg.c:280: error: previous declaration of &#8216;about_page&#8217; was here
about_dlg.c:317: warning: initialization makes integer from pointer without a ca st
about_dlg.c:317: error: initializer element is not constant
about_dlg.c:317: warning: data definition has no type or storage class
about_dlg.c:318: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:318: error: conflicting types for &#8216;page_lb&#8217;
about_dlg.c:280: error: previous declaration of &#8216;page_lb&#8217; was here
about_dlg.c:318: error: initializer element is not constant
about_dlg.c:318: warning: data definition has no type or storage class
about_dlg.c:319: error: syntax error before &#8216;(&#8217; token
about_dlg.c:319: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_notebook _append_page&#8217;
about_dlg.c:319: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;about_page&#8217;
about_dlg.c:319: error: conflicting types for &#8216;about_page&#8217;
about_dlg.c:280: error: previous declaration of &#8216;about_page&#8217; was here
about_dlg.c:319: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:319: error: conflicting types for &#8216;page_lb&#8217;
about_dlg.c:280: error: previous declaration of &#8216;page_lb&#8217; was here
about_dlg.c:319: error: syntax error before &#8216;)&#8217; token
about_dlg.c:327: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;folders_page &#8217;
about_dlg.c:327: error: conflicting types for &#8216;folders_page&#8217;
about_dlg.c:280: error: previous declaration of &#8216;folders_page&#8217; was here
about_dlg.c:327: warning: initialization makes integer from pointer without a ca st
about_dlg.c:327: error: initializer element is not constant
about_dlg.c:327: warning: data definition has no type or storage class
about_dlg.c:328: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:328: error: conflicting types for &#8216;page_lb&#8217;
about_dlg.c:280: error: previous declaration of &#8216;page_lb&#8217; was here
about_dlg.c:328: error: initializer element is not constant
about_dlg.c:328: warning: data definition has no type or storage class
about_dlg.c:329: error: syntax error before &#8216;(&#8217; token
about_dlg.c:329: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_notebook _append_page&#8217;
about_dlg.c:329: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;folders_page &#8217;
about_dlg.c:329: error: conflicting types for &#8216;folders_page&#8217;
about_dlg.c:280: error: previous declaration of &#8216;folders_page&#8217; was here
about_dlg.c:329: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:329: error: conflicting types for &#8216;page_lb&#8217;
about_dlg.c:280: error: previous declaration of &#8216;page_lb&#8217; was here
about_dlg.c:329: error: syntax error before &#8216;)&#8217; token
about_dlg.c:332: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;plugins_page &#8217;
about_dlg.c:332: error: conflicting types for &#8216;plugins_page&#8217;
about_dlg.c:280: error: previous declaration of &#8216;plugins_page&#8217; was here
about_dlg.c:332: warning: initialization makes integer from pointer without a ca st
about_dlg.c:332: error: initializer element is not constant
about_dlg.c:332: warning: data definition has no type or storage class
about_dlg.c:333: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:333: error: conflicting types for &#8216;page_lb&#8217;
about_dlg.c:280: error: previous declaration of &#8216;page_lb&#8217; was here
about_dlg.c:333: error: initializer element is not constant
about_dlg.c:333: warning: data definition has no type or storage class
about_dlg.c:334: error: syntax error before &#8216;(&#8217; token
about_dlg.c:334: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_notebook _append_page&#8217;
about_dlg.c:334: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;plugins_page &#8217;
about_dlg.c:334: error: conflicting types for &#8216;plugins_page&#8217;
about_dlg.c:280: error: previous declaration of &#8216;plugins_page&#8217; was here
about_dlg.c:334: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;page_lb&#8217;
about_dlg.c:334: error: conflicting types for &#8216;page_lb&#8217;
about_dlg.c:280: error: previous declaration of &#8216;page_lb&#8217; was here
about_dlg.c:334: error: syntax error before &#8216;)&#8217; token
about_dlg.c:338: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;bbox&#8217;
about_dlg.c:338: warning: initialization makes integer from pointer without a ca st
about_dlg.c:338: error: initializer element is not constant
about_dlg.c:338: warning: data definition has no type or storage class
about_dlg.c:339: error: syntax error before &#8216;(&#8217; token
about_dlg.c:339: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_box_pack _start&#8217;
about_dlg.c:339: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;bbox&#8217;
about_dlg.c:339: error: syntax error before numeric constant
about_dlg.c:341: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;ok_btn&#8217;
about_dlg.c:341: error: initializer element is not constant
about_dlg.c:341: warning: data definition has no type or storage class
about_dlg.c:342: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;window_set_c ancel_button&#8217;
about_dlg.c:342: warning: parameter names (without types) in function declaratio n
about_dlg.c:342: error: conflicting types for &#8216;window_set_cancel_button&#8217;
ui_util.h:142: error: previous declaration of &#8216;window_set_cancel_button&#8217; was her e
about_dlg.c:342: warning: data definition has no type or storage class
about_dlg.c:344: error: syntax error before &#8216;(&#8217; token
about_dlg.c:344: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_signal_c onnect&#8217;
about_dlg.c:345: error: syntax error before &#8216;(&#8217; token
about_dlg.c:345: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_signal_c onnect&#8217;
about_dlg.c:347: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gtk_widget_s how_all&#8217;
about_dlg.c:347: warning: parameter names (without types) in function declaratio n
about_dlg.c:347: warning: data definition has no type or storage class
about_dlg.c:348: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;window_prese nt&#8217;
about_dlg.c:348: warning: parameter names (without types) in function declaratio n
about_dlg.c:348: error: conflicting types for &#8216;window_present&#8217;
ui_util.h:129: error: previous declaration of &#8216;window_present&#8217; was here
about_dlg.c:348: warning: data definition has no type or storage class
about_dlg.c:349: error: syntax error before &#8216;}&#8217; token
about_dlg.c:352: error: syntax error before &#8216;*&#8217; token


---

### Post by Matthew83 on 2006-04-23
Here I am
I've been told that the problem was due to the fact I had added a repository I shouldn't add, that is 

 deb [http://ftp.it.debian.org/debian](http://ftp.it.debian.org/debian) unstable main contrib non-free

Now the problem is that when I try to apt-get install libgtk2.0-dev It doesn't because it tells me that some of the dependencies are not going to be installed (such as libcairo2).  I was told this is because I probably installed some packages for Debian unstable which make it impossible to resolve the Depends now. 
I was suggested to create a apt/preferences file so configured:

Package: *
Pin: release a=hoary
Pin-Priority: 1100

but when I open Synaptic it tells me that preferences'  package header is missing

1) What is supposed to be the proper preferences format? 
2) Can you suggest me anything else to solve the problem?

---

### Post by adamkane on 2006-04-23
Use this for long error messages:

[ quote]
blah
blah
[ /quote]

---

