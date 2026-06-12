---
title: "Error while playing a video in totem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-14
When playing a ogg video in totem the following error occured

> ** (totem:10150): WARNING **: Error connecting to D-Bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:10150): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(totem:10150): GStreamer-CRITICAL **: gst_value_set_fraction: assertion `denominator != 0' failed

** (totem:10150): CRITICAL **: gst_video_calculate_display_ratio: assertion `num > 0' failed
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 70 error_code 11 request_code 141 minor_code 19)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.) 

---

### Post by ashmew2 on 2008-02-14
how about running the same file after executing the following line ?
```

sudo /etc/init.d/dbus start
```

If it says already running , Then
```

sudo /etc/init.d/dbus restart
```

?

---

### Post by ashmew2 on 2008-02-14
lol...In 1 hour , you have posted 2 threads regarding your ONE problem...Isnt it the same one @ [http://ubuntuforums.org/showthread.php?p=4329967](http://ubuntuforums.org/showthread.php?p=4329967) ?
Not fair..

---

### Post by adi_das on 2008-02-14
same problem

---

### Post by hyperair on 2008-02-14
Could you post the video that causes this problem? Does it work when you play other videos?

---

