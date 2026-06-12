---
title: "Totem can't play mp3"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-26
hey ... I am trying to listen to an mp3 file ... but totem is giving me this error:

Totem couldn't play 'file:///home/isos/Desktop/03.mp3'

There were no decoders found to handle the stream, you might need to install the corresponding plugins


Please help ... what are the corresponding plugins?

---

### Post by OffHand on 2006-04-26
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by jazzmuzik on 2006-04-26
Search on "restricted formats" and follow those instructions on that link to get mp3 working. (sorry, don't have the link handy)

---

### Post by gummylindz on 2006-04-26
um that happened to me too, but i can't help you cus i only just started using ubuntu like 2 weeks ago hehehe sorry

---

### Post by testube_babies on 2006-04-26
Make sure you have [enabled the universe and multiverse repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto") and then open a terminal and type:

```
sudo apt-get install  gstreamer0.8-mad
```

---

### Post by Isoss on 2006-04-26
hey .. thanks a lot it's working now.

so how many formats does this gstreamer support?

---

### Post by mostwanted on 2006-04-26
[QUOTE=Isoss]hey .. thanks a lot it's working now.

so how many formats does this gstreamer support?[/QUOTE]

Check it out yourself (do a search on gstreamer in synaptic). 0.8 supports pretty much any audio format, video is a bit lacking, though 0.10 improves massively on this. I suspect that by time we reach 1.0 it will be the default for most apps on Linux systems.

---

### Post by Isoss on 2006-04-26
great. thanks a lot

---

