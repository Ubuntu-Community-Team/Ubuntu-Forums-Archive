---
title: "[SOLVED] Pidgin crash"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Jim Jesus on 2008-02-09
When ever I am using Pidgin, it crashes about every 5 minutes. If I just have it running but am not talking to anyone at the moment, it will work indefinitely, but when I get into conversation, it crashes every few minutes. Is there a way to fix this?

---

### Post by spiderbatdad on 2008-02-09
there is a setting somewhere to ping the server to keep the connection alive, perhaps setting it to ping less frequently...the server may think you are spamming during your conversation.

---

### Post by jan quark on 2008-02-09
run pidgin through the terminal

simply type pidgin and press enter

the next time when it crashes there should be some error messages
it would be helpful to know it

---

### Post by spiderbatdad on 2008-02-09
also I recommend gyache.deb as a Yahoo client that supports video.

---

### Post by Jim Jesus on 2008-02-09
> **jan quark said:**
> run pidgin through the terminal

simply type pidgin and press enter

the next time when it crashes there should be some error messages
it would be helpful to know it

Unfortunately, this didn't tell me much, after it crashed, the screen went gray like usual, then when I selected force quit, it just said "killed" in the terminal. I didn't get anything of interest in the terminal I don't think, but I'll post it just in case.(really long, sorry)
```
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

(pidgin:12482): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:12482): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Killed
```

---

### Post by LookTJ on 2008-02-09
What version of Pidgin do you have? Some old versions of Pidgin caused crashes to some people, you can try to install the latest Pidgin version from http;//pidgin.im/

---

### Post by Jim Jesus on 2008-02-09
> **Taylor said:**
> What version of Pidgin do you have? Some old versions of Pidgin caused crashes to some people, you can try to install the latest Pidgin version from http;//pidgin.im/
Well I downloaded the new version. But I don't really know how to install something from a ".tar.bz2". Could someone explain it to me. I know that really wasn't the purpose of the thread, but it would be very helpful.

---

### Post by jordanmthomas on 2008-02-09
[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)
Obviously, you'll probably need to use a different filename when untarring, but this should give you the gist of it.

Also, pidgin has a debug mode that should print more out to the console if you want to try it again:
```
pidgin -d
```

---

### Post by Jim Jesus on 2008-02-09
> **jordanmthomas said:**
> [http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)
Obviously, you'll probably need to use a different filename when untarring, but this should give you the gist of it.

Also, pidgin has a debug mode that should print more out to the console if you want to try it again:
```
pidgin -d
```
Thank you for the help with this. I got the new version, and it doesn't seem to be crashing at all.

---

### Post by Dr.Ninethousand on 2008-03-05
Pidgin often crashes for me as well, right when it's starting up..  

I couldn't find the newest (4.2.0) in .deb form, or on the repositories I already had..

if anyone else is looking, I found it in the repository shown here:

[http://backports.trausch.us/about/](http://backports.trausch.us/about/)

---

