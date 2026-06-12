---
title: "amarok GStreamer error on New user"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-11-25
hello, I'm using amarok on my primary user account and it work fine. I created new user accounts but I cannot play mp3, ogg, etc... in amarok, it says something about GStreamer, and run gst-register, but the command is invalid. Is this a bug? how can I fix this?

Thank you

---

### Post by ssam on 2005-11-25
is this new user in the audio group? in the users control panel you can choose what the user is allowed to do, one of the options is to allow use to use audio (by adding them to the audio group). maybe this is the problem.

if not try running

```
gst-register-0.8
```

this makes gstreamer refresh its list of pluggins. (i think in the futrue (gstreamer 0.10) this wont need to be done.)

---

