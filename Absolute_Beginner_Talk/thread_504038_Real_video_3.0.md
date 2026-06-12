---
title: "Real video 3.0"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-07-18
I have installed realplay to watch som .ram files on the internet.

It works fine in firefox but I want to see a bigger picture. Clicking on the "External player" opens Totem but then I got the message 

"Totem could not play 'rtsp://qstream-rm.qbrick.com/00928/mellan/packat/070716packat.rm'.

Video codec 'Real Video 3.0' is not handled. You might need to install additional plugins to be able to play some types of movies"

Somebody now what to do?

---

### Post by Gabn on 2007-07-18
copy that link and then open up realplay  you should find a open url in file and copy the link into there.

---

### Post by hannulan on 2007-07-19
> **Gabn said:**
> copy that link and then open up realplay  you should find a open url in file and copy the link into there.

I have tested that to but get the same error-message. Do I need somekind of codec to play Real video 3.0?

---

### Post by gaelfx on 2007-07-28
well, I don't know how to fix your codec problem, but I can tell you that I've had troubles myself viewing rtsp with RealPlayer (which I find ridiculous, since it can't even play it's own formats properly, c'est la vie). My problem is that video is jerky when I view an RTSP stream, to the point that it renders anything unwatchable. On the same connection, I can view it perfectly on my mac :(.

At any rate, if you want to fix the problem of which external player should be used, you need to change how the OS handles the url you are using so type this in terminal:

```
gconf-editor
```

This will allow you to change how Gnome handles certain file-types by default. Go to Desktop->Gnome->url-handlers and select RTSP (or whatever you want to change). In lieu of totem, type realplay, but keep the "%s", since that tells it to use whatever location is sent by the requesting application. Hope you understand!

---

