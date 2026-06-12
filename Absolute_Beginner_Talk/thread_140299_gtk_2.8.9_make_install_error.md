---
title: "gtk 2.8.9 make install error"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by shishio on 2006-03-05
Hi,

I was trying to install gtk+ 2.8.9. 
The ./configure ran fine.
But when I run make install, I get the following error:

gdkasync.c: In function '_gdk_x11_send_client_message_async':
gdkasync.c:216: error: dereferencing pointer to incomplete type
gdkasync.c: In function '_gdk_x11_set_input_focus_safe':
gdkasync.c:323: error: dereferencing pointer to incomplete type
gdkasync.c: In function '_gdk_x11_get_window_child_info':
gdkasync.c:623: error: dereferencing pointer to incomplete type
make[3]: *** [gdkasync.lo] Error 1

I'm lost here... any idea?

---

