---
title: "Logitech MX610 on ubuntu"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-06-29
is there any app. that will make full use of all the buttons on my Logitech MX610 mouse?
thank you,

---

### Post by linuxwizard on 2007-06-29
[https://help.ubuntu.com/community/Logitech_MX610](https://help.ubuntu.com/community/Logitech_MX610)

---

### Post by melenor on 2007-12-21
I am not sure what the command to start "xbindkeys"
EDIT: Got this to work thanks


 when i try to compile the hack with
"./configure, make, sudo make install"
and it says
"bash: ./configure,: No such file or directory"
i am unsure about this any help would be nice


Also when i tried to make and make install the Pidgin plugin for MX610 i got this 

gcc mx610-notification.c -O2 -Wall -fpic -g -I/usr/local/include -I/usr/local/include/gtk-2.0 -I/usr/local/include/glib-2.0 -I/usr/local/include/pango-1.0 -I/usr/local/include/atk-1.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/lib/gtk-2.0/include -I/usr/include -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include `pkg-config --cflags gtk+-2.0 pidgin` -shared -o mx610-notification.so
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
mx610-notification.c:40:20: error: notify.h: No such file or directory
mx610-notification.c:41:20: error: plugin.h: No such file or directory
mx610-notification.c:42:21: error: version.h: No such file or directory
mx610-notification.c:43:19: error: debug.h: No such file or directory
mx610-notification.c:44:18: error: cmds.h: No such file or directory
mx610-notification.c:45:21: error: gtkconv.h: No such file or directory
mx610-notification.c:46:19: error: prefs.h: No such file or directory
mx610-notification.c:47:22: error: gtkprefs.h: No such file or directory
mx610-notification.c:48:22: error: gtkutils.h: No such file or directory
mx610-notification.c:49:23: error: gtkplugin.h: No such file or directory
mx610-notification.c:50:22: error: gtkblist.h: No such file or directory
mx610-notification.c:64: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
mx610-notification.c: In function &#8216;mx610_close_device&#8217;:
mx610-notification.c:71: warning: implicit declaration of function &#8216;purple_debug_info&#8217;
mx610-notification.c:73: error: &#8216;file&#8217; undeclared (first use in this function)
mx610-notification.c:73: error: (Each undeclared identifier is reported only once
mx610-notification.c:73: error: for each function it appears in.)
mx610-notification.c:74: warning: implicit declaration of function &#8216;purple_input_remove&#8217;
mx610-notification.c:75: warning: implicit declaration of function &#8216;fclose&#8217;
mx610-notification.c: In function &#8216;mx610_open_device&#8217;:
mx610-notification.c:92: warning: implicit declaration of function &#8216;purple_prefs_get_string&#8217;
mx610-notification.c:93: warning: initialization makes pointer from integer without a cast
mx610-notification.c:98: warning: implicit declaration of function &#8216;purple_debug_error&#8217;
mx610-notification.c:109: error: &#8216;file&#8217; undeclared (first use in this function)
mx610-notification.c:109: warning: implicit declaration of function &#8216;fdopen&#8217;
mx610-notification.c:117: warning: implicit declaration of function &#8216;purple_input_add&#8217;
mx610-notification.c:117: error: &#8216;PURPLE_INPUT_READ&#8217; undeclared (first use in this function)
mx610-notification.c: In function &#8216;mx610_set_im&#8217;:
mx610-notification.c:178: warning: initialization makes pointer from integer without a cast
mx610-notification.c:186: warning: implicit declaration of function &#8216;purple_timeout_add&#8217;
mx610-notification.c: In function &#8216;get_pending_list&#8217;:
mx610-notification.c:229: warning: initialization makes pointer from integer without a cast
mx610-notification.c:231: warning: initialization makes pointer from integer without a cast
mx610-notification.c:236: warning: implicit declaration of function &#8216;pidgin_conversations_find_unseen_list&#8217;
mx610-notification.c:236: error: &#8216;PURPLE_CONV_TYPE_IM&#8217; undeclared (first use in this function)
mx610-notification.c:237: error: &#8216;PIDGIN_UNSEEN_TEXT&#8217; undeclared (first use in this function)
mx610-notification.c:238: warning: assignment makes pointer from integer without a cast
mx610-notification.c:242: warning: assignment makes pointer from integer without a cast
mx610-notification.c:246: error: &#8216;PURPLE_CONV_TYPE_CHAT&#8217; undeclared (first use in this function)
mx610-notification.c:248: warning: assignment makes pointer from integer without a cast
mx610-notification.c:251: error: &#8216;PIDGIN_UNSEEN_NICK&#8217; undeclared (first use in this function)
mx610-notification.c:252: warning: assignment makes pointer from integer without a cast
mx610-notification.c: At top level:
mx610-notification.c:263: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
mx610-notification.c: In function &#8216;mx610not_button_press_cb&#8217;:
mx610-notification.c:298: warning: implicit declaration of function &#8216;ferror&#8217;
mx610-notification.c:298: error: &#8216;file&#8217; undeclared (first use in this function)
mx610-notification.c:306: warning: implicit declaration of function &#8216;fscanf&#8217;
mx610-notification.c:306: warning: incompatible implicit declaration of built-in function &#8216;fscanf&#8217;
mx610-notification.c:316: warning: implicit declaration of function &#8216;pidgin_conv_present_conversation&#8217;
mx610-notification.c:317: error: &#8216;PurpleConversation&#8217; undeclared (first use in this function)
mx610-notification.c:317: error: expected expression before &#8216;)&#8217; token
mx610-notification.c:330: warning: implicit declaration of function &#8216;pidgin_blist_toggle_visibility&#8217;
mx610-notification.c: At top level:
mx610-notification.c:338: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
mx610-notification.c:387: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PurplePrefType&#8217;
mx610-notification.c:394: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PurplePrefType&#8217;
mx610-notification.c: In function &#8216;mx610not_prefs_device_cb&#8217;:
mx610-notification.c:397: warning: initialization makes pointer from integer without a cast
mx610-notification.c: At top level:
mx610-notification.c:414: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
mx610-notification.c:423: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
mx610-notification.c:437: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
mx610-notification.c:448: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ui_info&#8217;
mx610-notification.c:453: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
mx610-notification.c:482: warning: data definition has no type or storage class
mx610-notification.c:482: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PURPLE_INIT_PLUGIN&#8217;
mx610-notification.c:482: warning: parameter names (without types) in function declaration
make: *** [mx610-notification.so] Error 1


thank you for any help

---

