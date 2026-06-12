---
title: "bug every time i restart pld help"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by violin on 2007-04-16
every time i open ubuntu i received this bug.  I dont know what todo .help me pls





Memory status: size: 30089216 vsize: 0 resident: 30089216 share: 0 rss: 4571136
rss_rlim: 0
CPU usage: start_time: 1176762305 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0
timeout: 0 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/mixer_applet2'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225884912 (LWP 5013)]
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb78d1323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ea01b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb76985f5 in xmlParseChunk () from /usr/lib/libxml2.so.2
#5  0xb772ebfe in xmlReaderForFile () from /usr/lib/libxml2.so.2
#6  0xb772f93b in xmlTextReaderRead () from /usr/lib/libxml2.so.2
#7  0xb7f85410 in gst_registry_xml_write_cache ()
   from /usr/lib/libgstreamer-0.10.so.0
#8  0xb7f85d13 in gst_registry_xml_read_cache ()
   from /usr/lib/libgstreamer-0.10.so.0
#9  0xb7f2f8fb in gst_init () from /usr/lib/libgstreamer-0.10.so.0
#10 0xb7f3047c in gst_init () from /usr/lib/libgstreamer-0.10.so.0
#11 0xb7910814 in g_option_context_parse () from /usr/lib/libglib-2.0.so.0
#12 0xb7f2f0b1 in gst_init_check () from /usr/lib/libgstreamer-0.10.so.0
#13 0xb7f2f222 in gst_init () from /usr/lib/libgstreamer-0.10.so.0
#14 0x0804f534 in main ()

Thread 1 (Thread -1225884912 (LWP 5013)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb78d1323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ea01b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb76985f5 in xmlParseChunk () from /usr/lib/libxml2.so.2
No symbol table info available.
#5  0xb772ebfe in xmlReaderForFile () from /usr/lib/libxml2.so.2
No symbol table info available.
#6  0xb772f93b in xmlTextReaderRead () from /usr/lib/libxml2.so.2
No symbol table info available.
#7  0xb7f85410 in gst_registry_xml_write_cache ()
   from /usr/lib/libgstreamer-0.10.so.0
No symbol table info available.
#8  0xb7f85d13 in gst_registry_xml_read_cache ()
   from /usr/lib/libgstreamer-0.10.so.0
No symbol table info available.
#9  0xb7f2f8fb in gst_init () from /usr/lib/libgstreamer-0.10.so.0
No symbol table info available.
#10 0xb7f3047c in gst_init () from /usr/lib/libgstreamer-0.10.so.0
No symbol table info available.
#11 0xb7910814 in g_option_context_parse () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb7f2f0b1 in gst_init_check () from /usr/lib/libgstreamer-0.10.so.0
No symbol table info available.
#13 0xb7f2f222 in gst_init () from /usr/lib/libgstreamer-0.10.so.0
No symbol table info available.
#14 0x0804f534 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by violin on 2007-04-16
any help

---

