---
title: "Codecs"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by jbmswow on 2008-01-24
Where do I find codes to play mp3s in ubuntu 6??
Thanks

---

### Post by taurus on 2008-01-24
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by y-lee on 2008-01-24
See the [ Restricted drivers page]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Mze on 2008-01-24
Since you're using Ubuntu 6.xx

Try this [link]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs")

Bookmark the page for the future. Lots of useful how tos on one page

---

### Post by stchman on 2008-01-24
> **jbmswow said:**
> Where do I find codes to play mp3s in ubuntu 6??
Thanks

Here is how to install proprietary codes in Ubuntu.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

This will let you play MP3s, MPEG2, MPEG4, etc.

---

### Post by jbmswow on 2008-01-24
I have tried all of the last three suggestions and they all come back saying that gstreamer cannot be founf.  Any Ideas or suggestions.

Thanks

---

### Post by taurus on 2008-01-24
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by guitodd on 2008-01-24
system>Administration>Synaptic Package Manager

search for Gstreamer..  There is a good/bad/ugly set of codecs.    I grabbed all of them and got everything working.

---

### Post by stchman on 2008-01-24
> **jbmswow said:**
> I have tried all of the last three suggestions and they all come back saying that gstreamer cannot be founf.  Any Ideas or suggestions.

Thanks

Make sure the main, universe, multiverse, and restricrted repositories are enabled.

---

