---
title: "Programs Keep Randomly Closing"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by nathanscottdaniels on 2008-01-30
I am using Xubutu 7.1

All of my programs keep closing randomly whenever a specific thing happens.  I haven't pinpointed what closes most of them but there are some games that I have.

On gnibbles, as soon as me or a cpu easts a food, the program closes with these errors:

```
:/usr/games$ gnibbles

(gnibbles:6310): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(gnibbles:6310): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gnibbles:6310): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(gnibbles:6310): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
Segmentation fault

```

and in connect four, whenever it is the AI's turn. it crashes with these errors:

```
:/usr/games$ gnect

(gnect:6812): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(gnect:6812): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gnect:6812): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(gnect:6812): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
Segmentation fault (core dumped)

```

and in iagno, whenever I make a move, it crashes with these errors:

```
:/usr/games$ iagno

(iagno:6868): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(iagno:6868): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(iagno:6868): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(iagno:6868): GStreamer-CRITICAL **: gst_bus_timed_pop: assertion `GST_IS_BUS (bus)' failed
Segmentation fault (core dumped)

```

Please help!  Firefox closes too sometimes and that is bad!

System Info:
80GB HD
1.5GB RAM
Windows XP MCE and Xubuntu 7.10
AMD Turion 64 1.7 GHz
ATI Radeon Xpress something

---

### Post by Cypher on 2008-01-30
Looks like your GLIB libraries are broken..the code is failing some assertion (it kinda means what it sounds like) about data and basically bailing out. The core file that's been dumped can help debug this, but in your case I'd suggest you ensure that you're up to date with all the latest updates for Xubuntu..

Show us the output of
```

dpkg -l | grep libglib
dpkg -l | grep libgstreamer

```

---

### Post by Brian96 on 2008-02-25
> **Cypher said:**
> Looks like your GLIB libraries are broken..the code is failing some assertion (it kinda means what it sounds like) about data and basically bailing out. The core file that's been dumped can help debug this, but in your case I'd suggest you ensure that you're up to date with all the latest updates for Xubuntu..

Show us the output of
```

dpkg -l | grep libglib
dpkg -l | grep libgstreamer

```

I'm having the same problem. Here is the output you suggested posting:

```


 dpkg -l | grep libglib
ii  libglib-perl                               1:1.152-1                                 Perl interface to the GLib and GObject libra
ii  libglib1.2                                 1.2.10-17build1                           The GLib library of C routines
ii  libglib2-ruby1.8                           0.16.0-3ubuntu1                           Glib 2 bindings for the Ruby language
ii  libglib2.0-0                               2.14.1-1ubuntu1                           The GLib library of C routines
ii  libglib2.0-data                            2.14.1-1ubuntu1                           Common files for GLib library
ii  libglibmm-2.4-1c2a                         2.14.0-0ubuntu1                           C++ wrapper for the GLib toolkit (shared lib

```

```

 dpkg -l | grep libgstreamer
ii  libgstreamer-plugins-base0.10-0            0.10.14-1ubuntu3                          GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.14-1ubuntu3                          Core GStreamer libraries and elements

```

---

### Post by Gregory@Feanor on 2008-05-03
Hey,

Did any of you find a fix for this? I'm having the same problem.

I have the same output as Brian and Nathan (apart from the Ruby entry).

Not sure what to do. Reinstalled libglib and libgstreamer. Everything is properly updated. Only thing left to do is update to 8.04.

---

### Post by Gregory@Feanor on 2008-05-03
Well I installed Hardy Heron and that fixed it. Not sure how I would have done it otherwise.

---

### Post by imperius1 on 2008-05-06
I'm having the same problems under a fresh install of Hardy:

This is Firefox crashing:

(firefox:6014): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

I've also had the same type of error when running Rhythmbox (of course I can't replicate the error when I write this post). How should one rebuild the GLIB libraries if they are causing the problem, as mentioned in Cypher's post?

---

