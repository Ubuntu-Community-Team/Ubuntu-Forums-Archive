---
title: "3 Questions"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-13
Q#1) Howcome if there are minimized windows on desktop #1, (I have ubuntu installed with the kubuntu packages) they are still there in desktops #2,3,4?
This doesn't happen in ubuntu!

Q#2) How come when trying to play a song in amaroK or rhythmbox in kubuntu, it says "Gstreamer error..."?

Q#3) What is the kubuntu equivalent of the "startup programs" tab in sessions (in GNOME)?

---

### Post by frodon on 2006-04-14
2) install all the gstreamer plugins : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by user1397 on 2006-04-14
[quote=frodon]2) install all the gstreamer plugins : [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")[/quote]
Thanks for the reply, but I already uninstalled kde so...

---

### Post by ComplexNumber on 2006-04-14
[quote=erik1397]Thanks for the reply, but I already uninstalled kde so...[/quote] what do you mean exactly? gstreamer is part of gnome's architecture, but kde uses it too, and will do so more and more as time goes on. have you tried going on the command line and  typing: "gst-register'? this will register the gstreamer plugins so that amarok and others can make use of it.

---

### Post by user1397 on 2006-04-14
[quote=ComplexNumber]what do you mean exactly? gstreamer is part of gnome's architecture, but kde uses it too, and will do so more and more as time goes on. have you tried going on the command line and  typing: "gst-register'? this will register the gstreamer plugins so that amarok and others can make use of it.[/quote]
Ah thanks this worked!

---

